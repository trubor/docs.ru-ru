---
title: Написание пользовательского хост-приложения среды выполнения .NET Core
description: Узнайте, как разместить среду выполнения .NET Core из машинного кода для поддержки сложных сценариев, требующих управления ее работой.
author: mjrousos
ms.topic: how-to
ms.date: 12/21/2018
ms.openlocfilehash: a05e1e1d09f1f988ad8354f98521681e3f6cbea8
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875854"
---
# <a name="write-a-custom-net-core-host-to-control-the-net-runtime-from-your-native-code"></a>Написание пользовательского хост-приложения NET Core для управления средой выполнения .NET из машинного кода

Как и весь управляемый код, приложения .NET Core выполняются основным приложением. Основное приложение отвечает за запуск среды выполнения (включая такие компоненты, как JIT и сборщик мусора) и вызов управляемых точек входа.

Размещение среды выполнения .NET Core является расширенным сценарием, и в большинстве случаев разработчикам .NET Core не нужно беспокоиться о размещении, так как процессы сборки .NET Core предоставляют основное приложение по умолчанию для запуска приложений .NET Core. Но в отдельных ситуациях бывает удобно разместить среду выполнения .NET Core явным образом — либо как средство вызова управляемого кода в собственном процессе, либо для получения большего контроля над работой среды выполнения.

В этой статье приводится обзор действий, необходимых для запуска среды выполнения .NET Core из машинного кода и выполнения в нем управляемого кода.

## <a name="prerequisites"></a>Предварительные требования

Так как основные приложения являются собственными, в этом учебнике рассматривается создание приложения C++ для размещения .NET Core. Вам потребуется среда разработки C++ (например, предоставляемая в [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)).

Потребуется также и простое приложение .NET Core для проверки основного приложения, поэтому следует установить пакет [.NET Core SDK](https://dotnet.microsoft.com/download) и [создать небольшое тестовое приложение .NET Core](with-visual-studio.md) (например, приложение "Hello World"). Достаточно приложения "Hello World", созданного с помощью нового шаблона для консольного проекта .NET Core.

## <a name="hosting-apis"></a>Размещение API

Есть два разных API, которые могут использоваться для размещения .NET Core. В этой статье (и связанных с ней [примерах](https://github.com/dotnet/samples/tree/main/core/hosting)) рассматриваются два возможных варианта.

* Предпочтительный способ для размещения среды выполнения .NET Core в .NET Core 3.0 и более поздних версиях — это библиотеки API `nethost` и `hostfxr`. Эти точки входа решают все сложности по поиску и настройке среды выполнения для инициализации, а также поддерживают как запуск управляемого приложения, так и вызов статического управляемого метода.
* Предпочтительный способ размещения среды выполнения .NET Core в версиях до .NET Core 3.0 — API [`coreclrhost.h`](https://github.com/dotnet/runtime/blob/main/src/coreclr/hosts/inc/coreclrhost.h). Этот API предоставляет функции для облегчения запуска и остановки среды выполнения и вызова управляемого кода (либо путем запуска управляемого EXE-файла, либо путем вызова статических управляемых методов).

## <a name="sample-hosts"></a>Примеры основного приложения

[Пример основного приложения](https://github.com/dotnet/samples/tree/main/core/hosting), в котором демонстрируются описанные в учебнике ниже действия, доступны в репозитории dotnet/samples на сайте GitHub. Комментарии в примерах четко соответствуют пронумерованным шагам в этих учебниках. Инструкции по загрузке см. в разделе [Просмотр и скачивание примеров](../../samples-and-tutorials/index.md#view-and-download-samples).

Помните, что пример основного приложения предназначен для учебных целей, поэтому в нем реализована минимальная проверка ошибок, а удобочитаемость поставлена выше эффективности.

## <a name="create-a-host-using-nethosth-and-hostfxrh"></a>Создание узла с помощью `nethost.h` и `hostfxr.h`

Следующая процедура описывает применение библиотек `nethost` и `hostfxr` для запуска среды выполнения .NET Core в собственном приложении и вызова управляемого статического метода. В этом [примере](https://github.com/dotnet/samples/tree/main/core/hosting/HostWithHostFxr) используются заголовок `nethost` и библиотеки, установленные в составе пакета SDK для .NET, чтобы скопировать файлы [`coreclr_delegates.h`](https://github.com/dotnet/runtime/blob/main/src/native/corehost/coreclr_delegates.h) и [`hostfxr.h`](https://github.com/dotnet/runtime/blob/main/src/native/corehost/hostfxr.h) из репозитория [dotnet/runtime](https://github.com/dotnet/runtime).

### <a name="step-1---load-hostfxr-and-get-exported-hosting-functions"></a>Шаг 1. Загрузка `hostfxr` и получение экспортированных функций размещения

Библиотека `nethost` предоставляет функцию `get_hostfxr_path` для поиска библиотеки `hostfxr`. Библиотека `hostfxr` предоставляет функции для размещения среды выполнения .NET Core. Полный список этих функций можно найти в статье [`hostfxr.h`](https://github.com/dotnet/runtime/blob/main/src/native/corehost/hostfxr.h) и в [документации по проектированию стандартного размещения](https://github.com/dotnet/runtime/blob/main/docs/design/features/native-hosting.md). В этом примере и руководстве в целом применяются следующие элементы.

* `hostfxr_initialize_for_runtime_config`. инициализирует контекст узла и подготавливает среду выполнения .NET Core к инициализации, используя указанную конфигурацию среды выполнения.
* `hostfxr_get_runtime_delegate`. получает делегат для функций среды выполнения.
* `hostfxr_close`. закрывает контекст узла.

Для поиска библиотеки `hostfxr` используется `get_hostfxr_path`. После этого она загружается с извлечением всех экспортов.

[!code-cpp[HostFxrHost#LoadHostFxr](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadHostFxr)]

### <a name="step-2---initialize-and-start-the-net-core-runtime"></a>Шаг 2. Инициализация и запуск среды выполнения .NET Core

Функции `hostfxr_initialize_for_runtime_config` и `hostfxr_get_runtime_delegate` инициализируют и запускают среду выполнения .NET Core, используя конфигурацию среды выполнения для управляемого компонента, которая будет загружена. Функция `hostfxr_get_runtime_delegate` используется для получения делегата среды выполнения, который позволяет загрузить управляемую сборку и получить указатель на функцию для статического метода в этой сборке.

[!code-cpp[HostFxrHost#Initialize](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#Initialize)]

### <a name="step-3---load-managed-assembly-and-get-function-pointer-to-a-managed-method"></a>Шаг 3. Загрузка управляемой сборки и получение указателя на функцию для управляемого метода

Делегат среды выполнения вызывается для загрузки управляемой сборки и получения указателя на функцию для управляемого метода. Этот делегат ожидает получить в качестве входных данных путь к сборке, имя типа и имя метода, а затем возвращает указатель на функцию, который можно использовать для вызова управляемого метода.

[!code-cpp[HostFxrHost#LoadAndGet](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadAndGet)]

Передавая `nullptr` в качестве имени типа делегата при вызове делегата среды выполнения, этот пример применяет подпись по умолчанию для управляемого метода:

```csharp
public delegate int ComponentEntryPoint(IntPtr args, int sizeBytes);
```

Вы можете использовать другую подпись, указав имя типа делегата при вызове делегата среды выполнения.

### <a name="step-4---run-managed-code"></a>Шаг 4. Выполнение управляемого кода

Теперь собственный узел может вызывать управляемый метод и передавать ему нужные параметры.

[!code-cpp[HostFxrHost#CallManaged](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#CallManaged)]

## <a name="create-a-host-using-coreclrhosth"></a>Создание узла с помощью `coreclrhost.h`

Следующая процедура описывает применение API `coreclrhost.h` для запуска среды выполнения .NET Core в нативном приложении и вызова управляемого статического метода. Фрагменты кода в этом документе могут использовать некоторые API-интерфейсы Windows, но [полный пример основного приложения](https://github.com/dotnet/samples/tree/main/core/hosting/HostWithCoreClrHost) содержит пути кода для Windows и Linux.

[Узел corerun](https://github.com/dotnet/runtime/tree/main/src/coreclr/hosts/corerun) демонстрирует более сложный и приближенный к реальности кроссплатформенный пример размещения с применением файла `coreclrhost.h`.

### <a name="step-1---find-and-load-coreclr"></a>Шаг 1. Поиск и загрузка CoreCLR

Интерфейсы API среды выполнения .NET Core находятся в *coreclr.dll* (в Windows), в *libcoreclr.so* (на платформе Linux) или в *libcoreclr.dylib* (в macOS). Первым шагом для размещения .NET Core является загрузка библиотеки CoreCLR. Некоторые основные приложения проверяют разные пути или используют входные параметры для поиска библиотеки, пока другие могут загрузить ее по заранее определенному пути (рядом с основным приложением, например, или из известного расположения на компьютере).

После обнаружения библиотека загружается с помощью `LoadLibraryEx` (в Windows) или `dlopen` (в Linux или macOS).

[!code-cpp[CoreClrHost#1](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#1)]

### <a name="step-2---get-net-core-hosting-functions"></a>Шаг 2. Получение функций размещения .NET Core

В CoreClrHost есть несколько важных методов, полезных для размещения .NET Core:

* `coreclr_initialize`. запускает среду выполнения .NET Core и задает AppDomain по умолчанию (и только его).
* `coreclr_execute_assembly`. выполняет управляемую сборку.
* `coreclr_create_delegate`. создает указатель на функцию для управляемого метода.
* `coreclr_shutdown`. завершает среду выполнения .NET Core.
* `coreclr_shutdown_2`. аналогично `coreclr_shutdown`, но возвращает код выхода управляемого кода.

После загрузки библиотеки CoreCLR следующим шагом является получение ссылки на эти функции с помощью `GetProcAddress` (в Windows) или `dlsym` (в Linux или macOS).

[!code-cpp[CoreClrHost#2](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#2)]

### <a name="step-3---prepare-runtime-properties"></a>Шаг 3. Подготовка свойств среды выполнения

Прежде чем запустить среду выполнения, необходимо подготовить некоторые свойства, чтобы задать поведение (особенно касающиеся загрузчика сборок).

Ряд общих свойств:

* `TRUSTED_PLATFORM_ASSEMBLIES` Это список путей сборок (с разделителями ";" в Windows и ":" в Linux), которые среда выполнения сможет разрешить по умолчанию. Некоторые основные приложения имеют жестко заданные манифесты со списком сборок, которые можно загрузить. Другие добавляют в этот список все библиотеки в определенных местах (рядом с *coreclr.dll*, например).
* `APP_PATHS` Это список путей для поиска сборки, когда ее не удается найти в списке доверенных платформенных сборок (TPA). Так как основное приложение имеет больший контроль над тем, какие сборки загружаются с помощью списка доверенных платформенных сборок, рекомендуется определить, загрузку каких сборок оно ожидает, и явным образом перечислить их. Если же необходима проверка во время выполнения, это свойство позволяет реализовать и этот сценарий.
* `APP_NI_PATHS` Этот список очень похож на APP_PATHS за исключением того, что он обозначает пути для поиска образов в машинном коде.
* `NATIVE_DLL_SEARCH_DIRECTORIES` Это свойство представляет собой список путей, по которым загрузчик ищет собственные библиотеки, вызываемые через p/invoke.
* `PLATFORM_RESOURCE_ROOTS` Этот список содержит пути для поиска вспомогательных сборок ресурсов (в подкаталогах для конкретных языков и региональных параметров).

В этом примере основного приложения список доверенных платформенных сборок создается простым указанием всех библиотек в текущем каталоге:

[!code-cpp[CoreClrHost#7](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#7)]

Так как пример простой, вполне достаточно использовать свойство `TRUSTED_PLATFORM_ASSEMBLIES`:

[!code-cpp[CoreClrHost#3](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#3)]

### <a name="step-4---start-the-runtime"></a>Шаг 4. Запуск среды выполнения

API `coreclrhost.h` запускают среду выполнения и создают домен приложения по умолчанию в рамках одного вызова. Функция `coreclr_initialize` принимает базовый путь, имя и свойства, описанные ранее, и возвращает дескриптор обратно в основное приложение с помощью параметра `hostHandle`.

[!code-cpp[CoreClrHost#4](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#4)]

### <a name="step-5---run-managed-code"></a>Шаг 5. Выполнение управляемого кода

После запуска среды выполнения основное приложение может вызывать управляемый код. Это можно сделать двумя способами. Пример кода в этом руководстве использует функцию `coreclr_create_delegate` для создания делегата для управляемого статического метода. Этот API принимает [имя сборки](../../standard/assembly/names.md), имя типа с указанием пространства имен и имя метода в качестве входных данных и возвращает делегат, который может использоваться для вызова метода.

[!code-cpp[CoreClrHost#5](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#5)]

В этом примере основное приложение теперь может вызвать `managedDelegate` для запуска метода `ManagedWorker.DoWork`.

Кроме того, функция `coreclr_execute_assembly` может использоваться для запуска управляемого исполняемого файла. Этот API принимает путь к сборке и массив аргументов в качестве входных параметров. Он загружает сборку по этому пути и вызывает ее метод main.

```c++
int hr = executeAssembly(
        hostHandle,
        domainId,
        argumentCount,
        arguments,
        "HelloWorld.exe",
        (unsigned int*)&exitCode);
```

### <a name="step-6---shutdown-and-clean-up"></a>Шаг 6. Завершение работы и очистка

Наконец, когда основное приложение закончило выполнение управляемого кода, работа среды выполнения .NET Core завершается с помощью `coreclr_shutdown` или `coreclr_shutdown_2`.

[!code-cpp[CoreClrHost#6](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#6)]

CoreCLR не поддерживает повторную инициализацию или выгрузку. Не вызывайте `coreclr_initialize` еще раз или выгрузите библиотеку CoreCLR.

## <a name="conclusion"></a>Заключение

После создания основного приложения его можно проверить, запустив из командной строки и передав любые аргументы, которые оно ожидает. При указании запускаемого приложения .NET Core для основного приложения обязательно используйте библиотеку DLL, созданную `dotnet build`. Исполняемые EXE-файлы, созданные `dotnet publish` для автономных приложений, фактически являются основным приложением .NET Core по умолчанию (таким образом, в ключевых сценариях приложение можно запустить непосредственно из командной строки); пользовательский код компилируется в DLL-файл с тем же именем.

Если изначально что-то работает неправильно, еще раз убедитесь, что *coreclr.dll* находится в расположении, ожидаемом основным приложением, все необходимые библиотеки Framework включены в список доверенных платформенных сборок, а разрядность CoreCLR (32- или 64-разрядная версия) соответствует сборке основного приложения.

Размещение среды выполнения .NET Core — это расширенный сценарий, который многие разработчики не используют. Но он может сильно пригодиться тем, кому нужно запускать управляемый код из собственного процесса либо требуется расширенный контроль над поведением среды выполнения .NET Core.
