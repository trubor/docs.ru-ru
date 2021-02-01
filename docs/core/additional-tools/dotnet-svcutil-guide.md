---
title: Обзор средства WCF svcutil
description: Обзор инструмента Microsoft WCF dotnet-svcutil, который расширяет функциональные возможности проектов .NET Core и ASP.NET Core аналогично инструменту WCF svcutil для проектов .NET Framework.
author: honggit
ms.date: 02/22/2019
ms.openlocfilehash: 9468a881fe3850b53d48945340127ac2c2d4c6c8
ms.sourcegitcommit: 7e42488c2f8f63f6d499b5f8fb1dec5bac9ad254
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/28/2021
ms.locfileid: "98957927"
---
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a><span data-ttu-id="b0927-103">Средство WCF dotnet-svcutil для .NET Core</span><span class="sxs-lookup"><span data-stu-id="b0927-103">WCF dotnet-svcutil tool for .NET Core</span></span>

<span data-ttu-id="b0927-104">WCF (Windows Communication Foundation) **dotnet-svcutil** — это средство .NET, которое извлекает метаданные из веб-службы в сетевом расположении или WSDL-файла, а затем создает класс WCF, который содержит клиентские методы прокси-сервера и используется для доступа к операциям веб-службы.</span><span class="sxs-lookup"><span data-stu-id="b0927-104">The Windows Communication Foundation (WCF) **dotnet-svcutil** tool is a .NET tool that retrieves metadata from a web service on a network location or from a WSDL file, and generates a WCF class containing client proxy methods that access the web service operations.</span></span>

<span data-ttu-id="b0927-105">Как и [**Service Model Metadata — svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) для проектов .NET Framework, **dotnet-svcutil** является программой командной строки для создания ссылки на веб-службу, совместимой с проектами .NET Core и .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="b0927-105">Similar to the [**Service Model Metadata - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool for .NET Framework projects, the **dotnet-svcutil** is a command-line tool for generating a web service reference compatible with .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="b0927-106">Средство **dotnet-svcutil** служит альтернативой для поставщика подключенной службы Visual Studio [**WCF Web Service Reference**](wcf-web-service-reference-guide.md), впервые представленного в Visual Studio 2017 версии 15.5.</span><span class="sxs-lookup"><span data-stu-id="b0927-106">The **dotnet-svcutil** tool is an alternative option to the [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio connected service provider that first shipped with Visual Studio 2017 version 15.5.</span></span> <span data-ttu-id="b0927-107">Как и .NET, средство **dotnet-svcutil** доступно на платформах Linux, macOS и Windows.</span><span class="sxs-lookup"><span data-stu-id="b0927-107">The **dotnet-svcutil** tool as a .NET tool, is available cross-platform on Linux, macOS, and Windows.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b0927-108">Ссылаться на службы следует только из надежного источника.</span><span class="sxs-lookup"><span data-stu-id="b0927-108">You should only reference services from a trusted source.</span></span> <span data-ttu-id="b0927-109">Добавление ссылок из ненадежного источника может нарушить безопасность.</span><span class="sxs-lookup"><span data-stu-id="b0927-109">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b0927-110">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="b0927-110">Prerequisites</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="dotnet-svcutil-2x"></a>[<span data-ttu-id="b0927-111">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="b0927-111">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

- <span data-ttu-id="b0927-112">[пакет SDK для .NET Core 2.1](https://dotnet.microsoft.com/download) или более поздней версии;</span><span class="sxs-lookup"><span data-stu-id="b0927-112">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions</span></span>
- <span data-ttu-id="b0927-113">Любой редактор кода</span><span class="sxs-lookup"><span data-stu-id="b0927-113">Your favorite code editor</span></span>

# <a name="dotnet-svcutil-1x"></a>[<span data-ttu-id="b0927-114">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="b0927-114">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

- <span data-ttu-id="b0927-115">[пакет SDK для .NET Core 1.0.4](https://dotnet.microsoft.com/download) или более поздней версии;</span><span class="sxs-lookup"><span data-stu-id="b0927-115">[.NET Core 1.0.4 SDK](https://dotnet.microsoft.com/download) or later versions</span></span>
- <span data-ttu-id="b0927-116">Любой редактор кода</span><span class="sxs-lookup"><span data-stu-id="b0927-116">Your favorite code editor</span></span>

---

## <a name="getting-started"></a><span data-ttu-id="b0927-117">Начало работы</span><span class="sxs-lookup"><span data-stu-id="b0927-117">Getting started</span></span>

<span data-ttu-id="b0927-118">В следующем примере описаны шаги, необходимые для добавления ссылки на веб-службу в веб-проект .NET Core и вызова службы.</span><span class="sxs-lookup"><span data-stu-id="b0927-118">The following example walks you through the steps required to add a web service reference to a .NET Core web project and invoke the service.</span></span> <span data-ttu-id="b0927-119">Вы создадите веб-приложение .NET Core с именем *HelloSvcutil* и добавите ссылку на веб-службу, которая реализует следующий контракт:</span><span class="sxs-lookup"><span data-stu-id="b0927-119">You'll create a .NET Core web application named *HelloSvcutil* and add a reference to a web service that implements the following contract:</span></span>

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

<span data-ttu-id="b0927-120">В этом примере предполагается, что веб-служба размещена по следующему адресу: `http://contoso.com/SayHello.svc`</span><span class="sxs-lookup"><span data-stu-id="b0927-120">For this example, let's assume the web service will be hosted at the following address: `http://contoso.com/SayHello.svc`</span></span>

<span data-ttu-id="b0927-121">В окне командной строки Windows, macOS или Linux выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="b0927-121">From a Windows, macOS, or Linux command window perform the following steps:</span></span>

1. <span data-ttu-id="b0927-122">Создайте для проекта каталог с именем _HelloSvcutil_ и сделайте его текущим каталогом, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="b0927-122">Create a directory named _HelloSvcutil_ for your project and make it your current directory, as in the following example:</span></span>

    ```console
    mkdir HelloSvcutil
    cd HelloSvcutil
    ```

2. <span data-ttu-id="b0927-123">Создайте в этом каталоге веб-проект C# с помощью команды [`dotnet new`](../tools/dotnet-new.md), как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="b0927-123">Create a new C# web project in that directory using the [`dotnet new`](../tools/dotnet-new.md) command as follows:</span></span>

    ```dotnetcli
    dotnet new web
    ```

3. <span data-ttu-id="b0927-124">Установите [`dotnet-svcutil` (пакет NuGet)](https://nuget.org/packages/dotnet-svcutil) в качестве средства CLI:  </span><span class="sxs-lookup"><span data-stu-id="b0927-124">Install the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool:  </span></span><!-- markdownlint-disable MD023 -->
    # <a name="dotnet-svcutil-2x"></a>[<span data-ttu-id="b0927-125">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="b0927-125">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet tool install --global dotnet-svcutil
    ```

    # <a name="dotnet-svcutil-1x"></a>[<span data-ttu-id="b0927-126">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="b0927-126">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

    <span data-ttu-id="b0927-127">Откройте в редакторе файл проекта `HelloSvcutil.csproj`, измените элемент `Project` и добавьте [пакет NuGet `dotnet-svcutil`](https://nuget.org/packages/dotnet-svcutil) в виде ссылки на средство командной строки, используя следующий код:</span><span class="sxs-lookup"><span data-stu-id="b0927-127">Open the `HelloSvcutil.csproj` project file in your editor, edit the `Project` element, and add the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool reference, using the following code:</span></span>

    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
    </ItemGroup>
    ```

    <span data-ttu-id="b0927-128">Затем восстановите пакет _dotnet-svcutil_ с помощью команды [`dotnet restore`](../tools/dotnet-restore.md), как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="b0927-128">Then restore the _dotnet-svcutil_ package using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

    ```dotnetcli
    dotnet restore
    ```

    ---

4. <span data-ttu-id="b0927-129">Выполните команду _dotnet-svcutil_, чтобы создать файл со ссылкой на веб-службу, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="b0927-129">Run the _dotnet-svcutil_ command to generate the web service reference file as follows:</span></span>

    # <a name="dotnet-svcutil-2x"></a>[<span data-ttu-id="b0927-130">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="b0927-130">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet-svcutil http://contoso.com/SayHello.svc
    ```

    # <a name="dotnet-svcutil-1x"></a>[<span data-ttu-id="b0927-131">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="b0927-131">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

    ```dotnetcli
    dotnet svcutil http://contoso.com/SayHello.svc
    ```

    ---

<span data-ttu-id="b0927-132">Созданный файл сохраняется с именем _HelloSvcutil/ServiceReference/Reference.cs_.</span><span class="sxs-lookup"><span data-stu-id="b0927-132">The generated file is saved as _HelloSvcutil/ServiceReference/Reference.cs_.</span></span> <span data-ttu-id="b0927-133">Средство _dotnet-svcutil_ также добавляет в проект необходимые пакеты WCF, которые указаны в коде прокси-сервера как ссылки на пакеты.</span><span class="sxs-lookup"><span data-stu-id="b0927-133">The _dotnet-svcutil_ tool also adds to the project the appropriate WCF packages required by the proxy code as package references.</span></span>

## <a name="using-the-service-reference"></a><span data-ttu-id="b0927-134">Использование ссылки на службу</span><span class="sxs-lookup"><span data-stu-id="b0927-134">Using the Service Reference</span></span>

1. <span data-ttu-id="b0927-135">Восстановите пакеты WCF с помощью команды [`dotnet restore`](../tools/dotnet-restore.md), как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="b0927-135">Restore the WCF packages using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

    ```dotnetcli
    dotnet restore
    ```

2. <span data-ttu-id="b0927-136">Определите имена класса клиента и операций, которые хотите использовать.</span><span class="sxs-lookup"><span data-stu-id="b0927-136">Find the name of the client class and operation you want to use.</span></span> <span data-ttu-id="b0927-137">Файл `Reference.cs` будет содержать класс, наследующий свойства от `System.ServiceModel.ClientBase`, с методами, которые можно использовать для вызова операций из службы.</span><span class="sxs-lookup"><span data-stu-id="b0927-137">`Reference.cs` will contain a class that inherits from `System.ServiceModel.ClientBase`, with methods that can be used to call operations on the service.</span></span> <span data-ttu-id="b0927-138">В этом примере вызовите из службы _SayHello_ операцию _Hello_.</span><span class="sxs-lookup"><span data-stu-id="b0927-138">In this example, you want to call the _SayHello_ service's _Hello_ operation.</span></span> <span data-ttu-id="b0927-139">`ServiceReference.SayHelloClient` — это имя класса клиента с методом `HelloAsync`, который можно использовать для вызова операции.</span><span class="sxs-lookup"><span data-stu-id="b0927-139">`ServiceReference.SayHelloClient` is the name of the client class, and has a method called `HelloAsync` that can be used to call the operation.</span></span>

3. <span data-ttu-id="b0927-140">Откройте файл `Startup.cs` в редакторе и добавьте директиву `using` для пространства имен ссылки на службу вверху:</span><span class="sxs-lookup"><span data-stu-id="b0927-140">Open the `Startup.cs` file in your editor, and add a `using` directive for the service reference namespace at the top:</span></span>

    ```csharp
    using ServiceReference;
    ```

4. <span data-ttu-id="b0927-141">Измените метод `Configure` для вызова веб-службы.</span><span class="sxs-lookup"><span data-stu-id="b0927-141">Edit the `Configure` method to invoke the web service.</span></span> <span data-ttu-id="b0927-142">Для этого создайте экземпляр класса, который наследует свойства от класса `ClientBase`, и вызовите метод для объекта клиента:</span><span class="sxs-lookup"><span data-stu-id="b0927-142">You do this by creating an instance of the class that inherits from `ClientBase` and calling the method on the client object:</span></span>

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

5. <span data-ttu-id="b0927-143">Запустите приложение с помощью команды [`dotnet run`](../tools/dotnet-run.md), как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="b0927-143">Run the application using the [`dotnet run`](../tools/dotnet-run.md) command as follows:</span></span>

    ```dotnetcli
    dotnet run
    ```

6. <span data-ttu-id="b0927-144">Перейдите по указанному в консоли URL-адресу (например, `http://localhost:5000`) в веб-браузере.</span><span class="sxs-lookup"><span data-stu-id="b0927-144">Navigate to the URL listed in the console (for example, `http://localhost:5000`) in your web browser.</span></span>

<span data-ttu-id="b0927-145">Должны выводиться следующие данные: "Hello dotnet-svcutil!"</span><span class="sxs-lookup"><span data-stu-id="b0927-145">You should see the following output: "Hello dotnet-svcutil!"</span></span>

<span data-ttu-id="b0927-146">Подробное описание параметров средства `dotnet-svcutil` можно получить, вызвав это средство с параметром help, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="b0927-146">For a detailed description of the `dotnet-svcutil` tool parameters, invoke the tool passing the help parameter as follows:</span></span>

# <a name="dotnet-svcutil-2x"></a>[<span data-ttu-id="b0927-147">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="b0927-147">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

```dotnetcli
dotnet-svcutil --help
```

# <a name="dotnet-svcutil-1x"></a>[<span data-ttu-id="b0927-148">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="b0927-148">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

```dotnetcli
dotnet svcutil --help
```

---

## <a name="feedback--questions"></a><span data-ttu-id="b0927-149">Отзывы и вопросы</span><span class="sxs-lookup"><span data-stu-id="b0927-149">Feedback & questions</span></span>

<span data-ttu-id="b0927-150">Если у вас появились вопросы или отзывы, [сообщите об этом на сайте GitHub](https://github.com/dotnet/wcf/issues/new).</span><span class="sxs-lookup"><span data-stu-id="b0927-150">If you have any questions or feedback, [open an issue on GitHub](https://github.com/dotnet/wcf/issues/new).</span></span> <span data-ttu-id="b0927-151">Вы также можете просмотреть имеющиеся вопросы или проблемы [в репозитории WCF на сайте GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span><span class="sxs-lookup"><span data-stu-id="b0927-151">You can also review any existing questions or issues [at the WCF repo on GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span></span>

## <a name="release-notes"></a><span data-ttu-id="b0927-152">заметки о выпуске;</span><span class="sxs-lookup"><span data-stu-id="b0927-152">Release notes</span></span>

- <span data-ttu-id="b0927-153">Актуальные сведения о выпуске, включая описание известных проблем, см. в [заметках о выпуске](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md).</span><span class="sxs-lookup"><span data-stu-id="b0927-153">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) for updated release information, including known issues.</span></span>

## <a name="information"></a><span data-ttu-id="b0927-154">Сведения</span><span class="sxs-lookup"><span data-stu-id="b0927-154">Information</span></span>

- [<span data-ttu-id="b0927-155">Пакет NuGet dotnet-svcutil</span><span class="sxs-lookup"><span data-stu-id="b0927-155">dotnet-svcutil NuGet Package</span></span>](https://nuget.org/packages/dotnet-svcutil)
