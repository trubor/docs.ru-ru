---
title: Fuslogvw.exe (средство просмотра журнала привязки сборок)
description: Используйте Fuslogvw.exe, средство просмотра журнала привязки сборок. Это средство выводит подробные сведения о привязке сборок, помогающие определить причину, по которой .NET не находит сборку во время выполнения.
ms.date: 03/30/2017
helpviewer_keywords:
- failed assembly binds
- Fuslogvw.exe
- displaying failed assembly bind details
- assemblies [.NET Framework], failed assembly binds
- locating assemblies
- Assembly Binding Log Viewer
ms.assetid: e32fa443-0778-4cc3-bf36-5c8ea297d296
ms.openlocfilehash: d9c028507c19ef8599e58b38dcdf15af2ede1dee
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102259282"
---
# <a name="fuslogvwexe-assembly-binding-log-viewer"></a>Fuslogvw.exe (средство просмотра журнала привязки сборок)

Средство просмотра журнала привязки сборок выводит подробные сведения об ошибках привязки сборок. Эта информация поможет определить причину, по которой .NET Framework не находит сборку во время выполнения. Ошибки обычно вызваны развертыванием сборки в неверном расположении, использованием машинного образа, который более не является допустимым, а также несовпадением версий или языков и региональных параметров. Если среде CLR не удается найти сборку, обычно в приложении отображается исключение <xref:System.TypeLoadException>.

> [!IMPORTANT]
> Средство просмотра Fuslogvw.exe необходимо запускать с правами администратора.

Эта программа автоматически устанавливается вместе с Visual Studio. Чтобы запустить средство, используйте [оболочку командной строки для разработчиков](/visualstudio/ide/reference/command-prompt-powershell) с учетными данными администратора.

В командной строке введите следующую команду:

```console
fuslogvw
```

В средстве просмотра отображаются записи всех ошибок привязки сборок. При каждом сбое средство просмотра описывает следующее:

- приложение, которое инициировало создание привязки;
- сборка, для которой предназначена привязка, включая имя, версию, язык и региональные параметры, а также открытый ключ;
- дата и время возникновения сбоя.

## <a name="how-to"></a>Инструкции...

- [Изменение представления расположения журнала](#change-the-log-location-view)
- [Просмотр сведений об определенном сбое](#view-details-about-a-specific-failure)
- [Удаление записей](#delete-entries)
- [Обновление пользовательского интерфейса](#refresh-the-user-interface)
- [Изменение параметров журнала](#change-the-log-settings)
- [Просмотр диалогового окна "О программе"](#view-the-about-dialog)

### <a name="change-the-log-location-view"></a>Изменение представления расположения журнала

1. Чтобы просмотреть ошибки привязки для всех типов приложений, выберите параметр **По умолчанию**. Записи журнала по умолчанию хранятся в каталогах для отдельных пользователей на жестком диске в кэше WinINet.

2. Чтобы просмотреть ошибки привязки в пользовательском каталоге, выберите параметр **Настраиваемый**. Необходимо указать расположение, в котором среда выполнения будет размещать журналы. Для этого задайте имя каталога в диалоговом окне **Параметры журнала**. Каталог должен быть пустым и содержать только создаваемые средой выполнения файлы. Если в этом каталоге находится исполняемый файл и он создает ошибку, которую требуется занести в журнал, ошибка не будет зарегистрирована, так как средство просмотра попытается создать каталог с именем исполняемого файла. Кроме того, попытка запустить исполняемый файл из местоположения журнала завершится сбоем.

    > [!NOTE]
    > Рекомендуется использовать расположение привязки по умолчанию, а не настраиваемое расположение. Среда выполнения хранит расположение привязки, используемое по умолчанию, в кэше WinINet и потому автоматически очищает его. Настраиваемое расположение привязки необходимо очищать вручную.

### <a name="view-details-about-a-specific-failure"></a>Просмотр сведений об определенном сбое

1. Выберите имя приложения нужной записи в средстве просмотра.

2. Нажмите кнопку **Просмотреть журнал**. Также можно дважды щелкнуть выбранную запись.

    Средство отобразит следующие сведения о выбранной ошибке привязки:

    - причина возникновения ошибки, например "файл не найден" или "несоответствие версий";

    - сведения о приложении, выполнявшем привязку, в том числе имя, корневой каталог приложения (AppBase) и описание закрытого пути поиска при его наличии;

    - идентификатор сборки, которую ищет средство;

    - описание любых примененных политик версий приложения, издателя и администратора;

    - сведения о том, была ли обнаружена сборка в [глобальном кэше сборок](../app-domains/gac.md);

    - список всех проверенных URL-адресов.

Приведенная ниже запись журнала содержит подробные сведения об ошибке привязки сборки.

```output
*** Assembly Binder Log Entry  (3/5/2007 @ 12:54:20 PM) ***

The operation failed.
Bind result: hr = 0x80070002. The system cannot find the file specified.

Assembly manager loaded from:  C:\WINNT\Microsoft.NET\Framework\v2.0.50727\fusion.dll
Running under executable  C:\Program Files\Microsoft.NET\FrameworkSDK\Samples\Tutorials\resourcesandlocalization\graphic\cs\graphicfailtest.exe
--- A detailed error log follows.

=== Pre-bind state information ===
LOG: DisplayName = graphicfailtest.resources, Version=0.0.0.0, Culture=en-US, PublicKeyToken=null
 (Fully-specified)
LOG: Appbase = C:\Program Files\Microsoft.NET\FrameworkSDK\Samples\Tutorials\resourcesandlocalization\graphic\cs\
LOG: Initial PrivatePath = NULL
LOG: Dynamic Base = NULL
LOG: Cache Base = NULL
LOG: AppName = NULL
Calling assembly : graphicfailtest, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
===

LOG: Processing DEVPATH.
LOG: DEVPATH is not set. Falling through to regular bind.
LOG: Policy not being applied to reference at this time (private, custom, partial, or location-based assembly bind).
LOG: Post-policy reference: graphicfailtest.resources, Version=0.0.0.0, Culture=en-US, PublicKeyToken=null
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources.DLL.
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources/graphicfailtest.resources.DLL.
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources.EXE.
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources/graphicfailtest.resources.EXE.
LOG: All probing URLs attempted and failed.
```

### <a name="delete-entries"></a>Удаление записей

Чтобы удалить запись из журнала:

1. Выберите запись в средстве просмотра.

2. Нажмите кнопку **Удалить запись**.

Чтобы удалить все записи из журнала:

- Нажмите кнопку **Удалить все**.

### <a name="refresh-the-user-interface"></a>Обновление пользовательского интерфейса

- Нажмите кнопку **Обновить**. Средство просмотра не выявляет новые записи во время работы автоматически. Чтобы показать эти записи, нажмите кнопку **Обновить**.

### <a name="change-the-log-settings"></a>Изменение параметров журнала

Нажмите кнопку **Параметры**, чтобы открыть диалоговое окно **Параметры журнала**.

### <a name="view-the-about-dialog"></a>Просмотр диалогового окна "О программе"

Нажмите кнопку **О программе**.

## <a name="binding-logs-for-native-images"></a>Журналы привязки собственных образов

По умолчанию средство Fuslogvw.exe записывает в журнал обычные запросы на привязку сборок. В журнал также можно включить привязки сборок для образов в машинном коде, созданных с помощью программы [Ngen.exe (генератор образов в машинном коде)](ngen-exe-native-image-generator.md).

### <a name="log-assembly-binds-for-native-images"></a>Запись в журнал привязок сборок для собственных образов

- В группе **Категории журналов** выберите параметр **Образцы в машинном коде**.

Следующий журнал иллюстрирует ошибку, вызванную зависимостью, которая не существовала в момент создания для приложения машинного образа. Если зависимости во время выполнения отличаются от зависимостей при выполнении Ngen.exe, привязка к машинному образу не допускается.

```output
*** Assembly Binder Log Entry  (12/8/2006 @ 5:22:07 PM) ***

The operation failed.
Bind result: hr = 0x80070002. The system cannot find the file specified.

Assembly manager loaded from:  E:\Windows\Microsoft.NET\Framework64\v2.0.50727\mscorwks.dll
Running under executable  E:\test\App.exe
--- A detailed error log follows.

LOG: Start binding of native image App, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
LOG: IL assembly loaded from E:\test\App.exe.
LOG: Start validating native image App, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
LOG: Start validating all the dependencies.
LOG: [Level 1]Start validating native image dependency mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089.
LOG: Dependency evaluation succeeded.
LOG: [Level 1]Start validating IL dependency b, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
WRN: Dependency assembly was not found at ngen time, but is found at binding time. Disallow using this native image.
WRN: No matching native image found.
LOG: Bind to native image assembly did not succeed. Use IL image.
```

Следующий журнал иллюстрирует ошибку привязки машинного образа, вызванную различиями в настройках параметров безопасности при выполнении приложения и при создании машинного образа.

```output
*** Assembly Binder Log Entry  (12/8/2006 @ 5:29:09 PM) ***

The operation failed.
Bind result: hr = 0x80004005. Unspecified error

Assembly manager loaded from:  E:\Windows\Microsoft.NET\Framework64\v2.0.50727\mscorwks.dll
Running under executable  E:\test\Application101622.exe
--- A detailed error log follows.

LOG: Start binding of native image Application101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
LOG: IL assembly loaded from E:\test\Application101622.exe.
LOG: Start validating native image Application101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
LOG: Start validating all the dependencies.
LOG: [Level 1]Start validating native image dependency mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089.
LOG: Dependency evaluation succeeded.
LOG: [Level 1]Start validating IL dependency Dependency101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
LOG: Dependency evaluation succeeded.
LOG: Validation of dependencies succeeded.
LOG: Start loading all the dependencies into load context.
LOG: Loading of dependencies succeeded.
LOG: Bind to native image succeeded.
Native image has correct version information.
Attempting to use native image E:\Windows\assembly\NativeImages_v2.0.50727_64\Application101622\1ac7fadabec4f72575d807501e9fdc72\Application101622.ni.exe.
Rejecting native image because it failed the security check. The assembly's permissions must have changed since the time it was ngenned, or it is running with a different security context.
Discarding native image.
```

## <a name="the-log-settings-dialog"></a>Диалоговое окно "Параметры журнала"

В диалоговом окне **Параметры журнала** можно выполнить следующие действия.

### <a name="to-disable-logging"></a>Отключение ведения журнала

- Выберите **Журнал отключен**.  Обратите внимание, что этот параметр выбран по умолчанию.

### <a name="to-log-assembly-binds-in-exceptions"></a>Запись привязок сборок в исключения

- Выберите **Запись текста исключения в журнал**. В тексте исключения указываются наиболее краткие сведения fusion-журнала. Чтобы просмотреть все сведения, используйте один из других параметров.

  См. важное примечание о сборках, которые загружаются как нейтральные к домену.

### <a name="to-log-assembly-bind-failures"></a>Запись в журнал ошибок привязки сборок

- Выберите **Запись ошибок привязки на диск**.

  См. важное примечание о сборках, которые загружаются как нейтральные к домену.

### <a name="to-log-all-assembly-binds"></a>Запись в журнал всех привязок сборок

- Выберите **Запись всех привязок на диск**.

  См. важное примечание о сборках, которые загружаются как нейтральные к домену.

> [!IMPORTANT]
> Если сборка загружается как нейтральная к домену, например если свойству <xref:System.AppDomainSetup.LoaderOptimization%2A> задано значение <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType> или <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType>, в некоторых случаях ведение журнала может привести к утечке памяти. Это возможно, если запись вносится в журнал при загрузке нейтрального к домену модуля в домен приложения с последующей выгрузкой домена приложения. Запись журнала может не освобождаться до завершения данного процесса. Некоторые отладчики включают ведение журналов автоматически.

### <a name="to-enable-a-custom-log-path"></a>Разрешение пользовательского пути к журналу

1. Выберите **Разрешить пользовательский путь к журналу**.

2. Введите путь в текстовом поле **Пользовательский путь к журналу**.

> [!NOTE]
> [Средство просмотра журнала привязки сборок (Fuslogvw.exe)](fuslogvw-exe-assembly-binding-log-viewer.md) сохраняет журнал привязок в кэше Internet Explorer. Из-за возможных повреждений кэша Internet Explorer в окне [средства просмотра журнала привязок сборки (Fuslogvw.exe)](fuslogvw-exe-assembly-binding-log-viewer.md) перестают отображаться новые журналы привязок. В результате таких сбоев инфраструктура привязки в платформе .NET (fusion) не может выполнять запись в журнал привязки и считывание из него. (Эта проблема не возникает при выборе пользовательского пути к журналу).  Чтобы fusion-журнал снова отображал привязки, очистите кэш IE. Для этого удалите временные файлы Интернета в диалоговом окне "Свойства обозревателя".
>
> Если неуправляемое приложение размещает среду CLR посредством реализации интерфейсов `IHostAssemblyManager` и `IHostAssemblyStore`, хранение записей журнала в кэше WinINet невозможно. Чтобы просматривать записи журнала основных пользовательских приложений, которые реализуют эти интерфейсы, необходимо задать альтернативный путь к журналу.

### <a name="to-enable-logging-for-apps-running-in-the-windows-app-container"></a>Ведение журнала для приложений, выполняемых в контейнере приложений Windows

1. Укажите пользовательский путь к журналу, как описано в предыдущей процедуре. По умолчанию у приложений, выполняемых в контейнере приложений Windows, ограничен доступ к жесткому диску. Все приложения в контейнере приложений будут иметь право на чтение и запись в указанном каталоге.

2. Установите флажок **Включить иммерсивное ведение журнала**.

    > [!NOTE]
    > Это поле активно только в Windows 8 или более поздней версии.

## <a name="see-also"></a>См. также

- <xref:System.TypeLoadException>
- [Инструменты](index.md)
- [Глобальный кэш сборок](../app-domains/gac.md)
- [Обнаружение сборок в среде выполнения](../deployment/how-the-runtime-locates-assemblies.md)
- [Оболочки командной строки для разработчиков](/visualstudio/ide/reference/command-prompt-powershell)
