---
title: Предоставление доступа к компонентам .NET Core для COM
description: В этом руководстве демонстрируется, как предоставить доступ к классу .NET Core для COM. Вы создаете COM-сервер и параллельный манифест сервера для модели COM без поддержки реестра.
ms.date: 07/12/2019
helpviewer_keywords:
- exposing .NET Core components to COM
- interoperation with unmanaged code, exposing .NET Core components
- COM interop, exposing COM components
ms.assetid: 21271167-fe7f-46ba-a81f-a6812ea649d4
author: jkoritzinsky
ms.author: jekoritz
ms.openlocfilehash: 30323113520f3bd148a0f1a6fab9801381a332b3
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875152"
---
# <a name="exposing-net-core-components-to-com"></a>Предоставление доступа к компонентам .NET Core для COM

В .NET Core процесс предоставления объектов .NET для модели COM значительно упрощен по сравнению с .NET Framework. Ниже описывается, как предоставить класс для модели COM. В этом учебнике демонстрируется выполнение следующих действий:

- Предоставление класса для модели COM из .NET Core.
- Создайте сервер COM в процессе сборки библиотеки .NET Core.
- Автоматически создайте параллельный манифест сервера для модели COM без поддержки реестра.

## <a name="prerequisites"></a>Предварительные требования

- Установите [пакет SDK для .NET Core 3.0](https://dotnet.microsoft.com/download) или более новой версии.

## <a name="create-the-library"></a>Создание библиотеки

Сначала нужно создать библиотеку.

1. Создайте новую папку и в этой папке выполните следующую команду.

    ```dotnetcli
    dotnet new classlib
    ```

2. Откройте `Class1.cs`.
3. Добавьте `using System.Runtime.InteropServices;` в начало файла.
4. Создайте интерфейс с именем `IServer`. Пример:

   ```csharp
   using System;
   using System.Runtime.InteropServices;

   [ComVisible(true)]
   [Guid(ContractGuids.ServerInterface)]
   [InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
   public interface IServer
   {
       /// <summary>
       /// Compute the value of the constant Pi.
       /// </summary>
       double ComputePi();
   }
   ```

5. Добавьте в интерфейс атрибут `[Guid("<IID>")]` с идентификатором GUID реализуемого интерфейса COM. Например, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`. Обратите внимание, что этот идентификатор GUID должен быть уникальным, так как он является единственным идентификатором данного интерфейса для модели COM. Чтобы создать идентификатор GUID в Visual Studio, выберите "Сервис" > "Создать GUID". Откроется средство создания идентификатора GUID.
6. Добавьте в интерфейс атрибут `[InterfaceType]` и укажите, какие базовые COM-интерфейсы должен реализовывать ваш интерфейс.
7. Создайте класс `Server`, реализующий `IServer`.
8. Добавьте в класс атрибут `[Guid("<CLSID>")]` с идентификатором GUID реализуемого класса COM. Например, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`. Так же как и в случае с идентификатором GUID интерфейса, этот идентификатор GUID должен быть уникальным, так как он является единственным идентификатором данного класса для модели COM.
9. Добавьте атрибут `[ComVisible(true)]` как в интерфейс, так и в класс.

> [!IMPORTANT]
> В отличие от .NET Framework, .NET Core требует указывать идентификатор CLSID любого класса, который должен активироваться через модель COM.

## <a name="generate-the-com-host"></a>Создание узла COM

1. Откройте файл проекта `.csproj` и добавьте элемент `<EnableComHosting>true</EnableComHosting>` внутри тега `<PropertyGroup></PropertyGroup>`.
2. Выполните построение проекта.

В результате будут получены файлы `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` и `ProjectName.comhost.dll`.

## <a name="register-the-com-host-for-com"></a>Регистрация узла COM для модели COM

Откройте командную строку с повышенными привилегиями и запустите `regsvr32 ProjectName.comhost.dll`. Это приведет к регистрации всех предоставленных объектов .NET в модели COM.

## <a name="enabling-regfree-com"></a>Реализация модели COM без поддержки реестра

1. Откройте файл проекта `.csproj` и добавьте элемент `<EnableRegFreeCom>true</EnableRegFreeCom>` внутри тега `<PropertyGroup></PropertyGroup>`.
2. Выполните построение проекта.

В результате будет также получен файл `ProjectName.X.manifest`. Это параллельный манифест для использования с моделью COM без поддержки реестра.

## <a name="sample"></a>Пример

В репозитории dotnet/samples на сайте GitHub есть полнофункциональный [пример сервера COM](https://github.com/dotnet/samples/tree/main/core/extensions/COMServerDemo).

## <a name="additional-notes"></a>Дополнительные сведения

В отличие от .NET Framework, в .NET Core создание библиотеки типов COM (TLB) из сборки .NET Core не поддерживается. Нужно вручную написать файл IDL или заголовок C/C++ для собственных объявлений COM-интерфейсов.

> [!IMPORTANT]
> В .NET Framework сборка "Любой ЦП" может использоваться как с 32-разрядными, так и с 64-разрядными клиентами. По умолчанию в .NET Core, .NET 5 и более поздних версий вместе со сборками "Любой ЦП" поставляется 64-разрядная библиотека *\*.comhost.dll*. По этой причине они могут использоваться только в 64-разрядных клиентах. Это настроено по умолчанию, поскольку это то, что предоставляет пакет SDK. Такое поведение аналогично публикации "автономного" компонента: по умолчанию он использует то, что предоставляет пакет SDK. Свойство MSBuild `NETCoreSdkRuntimeIdentifier` определяет разрядность библиотеки *\*.comhost.dll*. Управляемая часть на самом деле не зависит от ожидаемой разрядности, однако разрядность сопутствующего ресурса по умолчанию совпадает с разрядностью целевого пакета SDK.

[Автономные развертывания](../deploying/index.md#publish-self-contained) COM-компонентов не поддерживаются. Поддерживаются только [зависящие от платформы развертывания](../deploying/index.md#publish-framework-dependent) COM-компонентов.

Кроме того, загрузка как .NET Framework, так и .NET Core в один и тот же процесс имеет ограничения диагностического характера. Основное ограничение — отладка управляемых компонентов, так как невозможно одновременно выполнить отладку .NET Framework и .NET Core. Кроме того, два экземпляра среды выполнения не используют управляемые сборки совместно. Это означает, что невозможно совместно использовать фактические типы .NET в двух средах выполнения, вместо этого все взаимодействия должны быть ограничены предоставленными контрактами COM-интерфейса.
