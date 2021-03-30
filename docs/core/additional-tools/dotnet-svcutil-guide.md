---
title: Обзор средства WCF svcutil
description: Обзор инструмента Microsoft WCF dotnet-svcutil, который расширяет функциональные возможности проектов .NET Core и ASP.NET Core аналогично инструменту WCF svcutil для проектов .NET Framework.
author: honggit
ms.date: 02/22/2019
ms.openlocfilehash: 6af04c4fb5e824ffce594b6e21b720246c67bf66
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873033"
---
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a>Средство WCF dotnet-svcutil для .NET Core

WCF (Windows Communication Foundation) **dotnet-svcutil** — это средство .NET, которое извлекает метаданные из веб-службы в сетевом расположении или WSDL-файла, а затем создает класс WCF, который содержит клиентские методы прокси-сервера и используется для доступа к операциям веб-службы.

Как и [**Service Model Metadata — svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) для проектов .NET Framework, **dotnet-svcutil** является программой командной строки для создания ссылки на веб-службу, совместимой с проектами .NET Core и .NET Standard.

Средство **dotnet-svcutil** служит альтернативой для поставщика подключенной службы Visual Studio [**WCF Web Service Reference**](wcf-web-service-reference-guide.md), впервые представленного в Visual Studio 2017 версии 15.5. Как и .NET, средство **dotnet-svcutil** доступно на платформах Linux, macOS и Windows.

> [!IMPORTANT]
> Ссылаться на службы следует только из надежного источника. Добавление ссылок из ненадежного источника может нарушить безопасность.

## <a name="prerequisites"></a>Предварительные требования

<!-- markdownlint-disable MD025 -->

# <a name="dotnet-svcutil-2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

- [пакет SDK для .NET Core 2.1](https://dotnet.microsoft.com/download) или более поздней версии;
- Любой редактор кода

# <a name="dotnet-svcutil-1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

- [пакет SDK для .NET Core 1.0.4](https://dotnet.microsoft.com/download) или более поздней версии;
- Любой редактор кода

---

## <a name="getting-started"></a>Начало работы

В следующем примере описаны шаги, необходимые для добавления ссылки на веб-службу в веб-проект .NET Core и вызова службы. Вы создадите веб-приложение .NET Core с именем *HelloSvcutil* и добавите ссылку на веб-службу, которая реализует следующий контракт:

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

В этом примере предполагается, что веб-служба размещена по следующему адресу: `http://contoso.com/SayHello.svc`

В окне командной строки Windows, macOS или Linux выполните следующие действия:

1. Создайте для проекта каталог с именем _HelloSvcutil_ и сделайте его текущим каталогом, как показано в следующем примере:

    ```console
    mkdir HelloSvcutil
    cd HelloSvcutil
    ```

2. Создайте в этом каталоге веб-проект C# с помощью команды [`dotnet new`](../tools/dotnet-new.md), как показано ниже:

    ```dotnetcli
    dotnet new web
    ```

3. Установите [`dotnet-svcutil` (пакет NuGet)](https://nuget.org/packages/dotnet-svcutil) в качестве средства CLI:  <!-- markdownlint-disable MD023 -->
    # <a name="dotnet-svcutil-2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet tool install --global dotnet-svcutil
    ```

    # <a name="dotnet-svcutil-1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

    Откройте в редакторе файл проекта `HelloSvcutil.csproj`, измените элемент `Project` и добавьте [пакет NuGet `dotnet-svcutil`](https://nuget.org/packages/dotnet-svcutil) в виде ссылки на средство командной строки, используя следующий код:

    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
    </ItemGroup>
    ```

    Затем восстановите пакет _dotnet-svcutil_ с помощью команды [`dotnet restore`](../tools/dotnet-restore.md), как показано ниже:

    ```dotnetcli
    dotnet restore
    ```

    ---

4. Выполните команду _dotnet-svcutil_, чтобы создать файл со ссылкой на веб-службу, как показано ниже:

    # <a name="dotnet-svcutil-2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet-svcutil http://contoso.com/SayHello.svc
    ```

    # <a name="dotnet-svcutil-1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

    ```dotnetcli
    dotnet svcutil http://contoso.com/SayHello.svc
    ```

    ---

Созданный файл сохраняется с именем _HelloSvcutil/ServiceReference/Reference.cs_. Средство _dotnet-svcutil_ также добавляет в проект необходимые пакеты WCF, которые указаны в коде прокси-сервера как ссылки на пакеты.

## <a name="using-the-service-reference"></a>Использование ссылки на службу

1. Восстановите пакеты WCF с помощью команды [`dotnet restore`](../tools/dotnet-restore.md), как показано ниже:

    ```dotnetcli
    dotnet restore
    ```

2. Определите имена класса клиента и операций, которые хотите использовать. Файл `Reference.cs` будет содержать класс, наследующий свойства от `System.ServiceModel.ClientBase`, с методами, которые можно использовать для вызова операций из службы. В этом примере вызовите из службы _SayHello_ операцию _Hello_. `ServiceReference.SayHelloClient` — это имя класса клиента с методом `HelloAsync`, который можно использовать для вызова операции.

3. Откройте файл `Startup.cs` в редакторе и добавьте директиву `using` для пространства имен ссылки на службу вверху:

    ```csharp
    using ServiceReference;
    ```

4. Измените метод `Configure` для вызова веб-службы. Для этого создайте экземпляр класса, который наследует свойства от класса `ClientBase`, и вызовите метод для объекта клиента:

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }

        app.Run(async (context) =>
        {
            var client = new SayHelloClient();
            var response = await client.HelloAsync();
            await context.Response.WriteAsync(response);
        });
    }

    ```

5. Запустите приложение с помощью команды [`dotnet run`](../tools/dotnet-run.md), как показано ниже:

    ```dotnetcli
    dotnet run
    ```

6. Перейдите по указанному в консоли URL-адресу (например, `http://localhost:5000`) в веб-браузере.

Должны выводиться следующие данные: "Hello dotnet-svcutil!"

Подробное описание параметров средства `dotnet-svcutil` можно получить, вызвав это средство с параметром help, как показано ниже:

# <a name="dotnet-svcutil-2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

```dotnetcli
dotnet-svcutil --help
```

# <a name="dotnet-svcutil-1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

```dotnetcli
dotnet svcutil --help
```

---

## <a name="feedback--questions"></a>Отзывы и вопросы

Если у вас появились вопросы или отзывы, [сообщите об этом на сайте GitHub](https://github.com/dotnet/wcf/issues/new). Вы также можете просмотреть имеющиеся вопросы или проблемы [в репозитории WCF на сайте GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).

## <a name="release-notes"></a>заметки о выпуске;

- Актуальные сведения о выпуске, включая описание известных проблем, см. в [заметках о выпуске](https://github.com/dotnet/wcf/blob/main/release-notes/dotnet-svcutil-notes.md).

## <a name="information"></a>Сведения

- [Пакет NuGet dotnet-svcutil](https://nuget.org/packages/dotnet-svcutil)
