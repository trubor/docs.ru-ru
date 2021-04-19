---
title: Использование внедрения зависимостей в .NET
description: Узнайте, как использовать внедрение зависимостей в приложениях .NET.
author: IEvangelist
ms.author: dapine
ms.date: 04/12/2021
ms.topic: tutorial
no-loc:
- Transient
- Scoped
- Singleton
- Example
ms.openlocfilehash: 03828496dfa3487ad70fac8cf32ff81844eca6fd
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494276"
---
# <a name="tutorial-use-dependency-injection-in-net"></a><span data-ttu-id="70d57-103">Руководство. Использование внедрения зависимостей в .NET</span><span class="sxs-lookup"><span data-stu-id="70d57-103">Tutorial: Use dependency injection in .NET</span></span>

<span data-ttu-id="70d57-104">В этом руководстве показано, как использовать [внедрение зависимостей в .NET](dependency-injection.md).</span><span class="sxs-lookup"><span data-stu-id="70d57-104">This tutorial shows how to use [dependency injection (DI) in .NET](dependency-injection.md).</span></span> <span data-ttu-id="70d57-105">Наряду с *расширениями Майкрософт* внедрение зависимостей является объектом первого класса, в котором службы добавляются и настраиваются в <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span><span class="sxs-lookup"><span data-stu-id="70d57-105">With *Microsoft Extensions*, DI is a first-class citizen where services are added and configured in an <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span></span> <span data-ttu-id="70d57-106">Интерфейс <xref:Microsoft.Extensions.Hosting.IHost> предоставляет собой экземпляр <xref:System.IServiceProvider>, который выступает в качестве контейнера всех зарегистрированных служб.</span><span class="sxs-lookup"><span data-stu-id="70d57-106">The <xref:Microsoft.Extensions.Hosting.IHost> interface exposes the <xref:System.IServiceProvider> instance, which acts as a container of all the registered services.</span></span>

<span data-ttu-id="70d57-107">В этом руководстве описано следующее:</span><span class="sxs-lookup"><span data-stu-id="70d57-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="70d57-108">Создание консольного приложения .NET, использующего внедрение зависимостей</span><span class="sxs-lookup"><span data-stu-id="70d57-108">Create a .NET console app that uses dependency injection</span></span>
> - <span data-ttu-id="70d57-109">Создание и настройка [универсального узла](generic-host.md)</span><span class="sxs-lookup"><span data-stu-id="70d57-109">Build and configure a [Generic Host](generic-host.md)</span></span>
> - <span data-ttu-id="70d57-110">Написание нескольких интерфейсов и соответствующих реализаций</span><span class="sxs-lookup"><span data-stu-id="70d57-110">Write several interfaces and corresponding implementations</span></span>
> - <span data-ttu-id="70d57-111">Использование времени существования службы и области для внедрения зависимостей</span><span class="sxs-lookup"><span data-stu-id="70d57-111">Use service lifetime and scoping for DI</span></span>

## <a name="prerequisites"></a><span data-ttu-id="70d57-112">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="70d57-112">Prerequisites</span></span>

- <span data-ttu-id="70d57-113">[Пакет SDK для .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet) или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="70d57-113">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet) or later.</span></span>
- <span data-ttu-id="70d57-114">Знакомство с созданием новых приложений .NET и установкой пакетов NuGet.</span><span class="sxs-lookup"><span data-stu-id="70d57-114">Familiarity with creating new .NET applications and installing NuGet packages.</span></span>

## <a name="create-a-new-console-application"></a><span data-ttu-id="70d57-115">Создание нового консольного приложения</span><span class="sxs-lookup"><span data-stu-id="70d57-115">Create a new console application</span></span>

<span data-ttu-id="70d57-116">С помощью команды [dotnet new](../tools/dotnet-new.md) или мастера создания проектов в среде разработки создайте новое консольное приложение .NET с именем **ConsoleDI.Example** .</span><span class="sxs-lookup"><span data-stu-id="70d57-116">Using either the [dotnet new](../tools/dotnet-new.md) command or an IDE new project wizard, create a new .NET console application named **ConsoleDI.Example**.</span></span> <span data-ttu-id="70d57-117">Добавьте в проект пакет NuGet [Microsoft.Extensions.Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting).</span><span class="sxs-lookup"><span data-stu-id="70d57-117">Add the [Microsoft.Extensions.Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) NuGet package to the project.</span></span>

## <a name="add-interfaces"></a><span data-ttu-id="70d57-118">Добавление интерфейсов</span><span class="sxs-lookup"><span data-stu-id="70d57-118">Add interfaces</span></span>

<span data-ttu-id="70d57-119">Добавьте следующие интерфейсы в корень проекта:</span><span class="sxs-lookup"><span data-stu-id="70d57-119">Add the following interfaces to the project root directory:</span></span>

<span data-ttu-id="70d57-120">*IOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="70d57-120">*IOperation.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/IOperation.cs":::

<span data-ttu-id="70d57-121">Интерфейс `IOperation` определяет одно свойство `OperationId`.</span><span class="sxs-lookup"><span data-stu-id="70d57-121">The `IOperation` interface defines a single `OperationId` property.</span></span>

<span data-ttu-id="70d57-122">*ITransientOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="70d57-122">*ITransientOperation.cs*</span></span>

<span data-ttu-id="70d57-123">:::code language="csharp" source="snippets/configuration/console-di/ITransientOperation.cs":::</span><span class="sxs-lookup"><span data-stu-id="70d57-123">:::code language="csharp" source="snippets/configuration/console-di/ITransientOperation.cs":::</span></span>

<span data-ttu-id="70d57-124">*IScopedOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="70d57-124">*IScopedOperation.cs*</span></span>

<span data-ttu-id="70d57-125">:::code language="csharp" source="snippets/configuration/console-di/IScopedOperation.cs":::</span><span class="sxs-lookup"><span data-stu-id="70d57-125">:::code language="csharp" source="snippets/configuration/console-di/IScopedOperation.cs":::</span></span>

<span data-ttu-id="70d57-126">*ISingletonOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="70d57-126">*ISingletonOperation.cs*</span></span>

<span data-ttu-id="70d57-127">:::code language="csharp" source="snippets/configuration/console-di/ISingletonOperation.cs":::</span><span class="sxs-lookup"><span data-stu-id="70d57-127">:::code language="csharp" source="snippets/configuration/console-di/ISingletonOperation.cs":::</span></span>

<span data-ttu-id="70d57-128">Все подынтерфейсы `IOperation` названы в соответствии с предполагаемым временем существования службы.</span><span class="sxs-lookup"><span data-stu-id="70d57-128">All of the subinterfaces of `IOperation` name their intended service lifetime.</span></span> <span data-ttu-id="70d57-129">Например, "Transient" или "Singleton".</span><span class="sxs-lookup"><span data-stu-id="70d57-129">For example, "Transient" or "Singleton".</span></span>

## <a name="add-default-implementation"></a><span data-ttu-id="70d57-130">Добавление реализации по умолчанию</span><span class="sxs-lookup"><span data-stu-id="70d57-130">Add default implementation</span></span>

<span data-ttu-id="70d57-131">Добавьте следующую реализацию по умолчанию для различных операций:</span><span class="sxs-lookup"><span data-stu-id="70d57-131">Add the following default implementation for the various operations:</span></span>

<span data-ttu-id="70d57-132">*DefaultOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="70d57-132">*DefaultOperation.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/DefaultOperation.cs":::

<span data-ttu-id="70d57-133">`DefaultOperation` реализует все интерфейсы именованной метки и инициализирует свойство `OperationId` последними четырьмя символами нового глобального уникального идентификатора (GUID).</span><span class="sxs-lookup"><span data-stu-id="70d57-133">The `DefaultOperation` implements all of the named marker interfaces and initializes the `OperationId` property to the last four characters of a new globally unique identifier (GUID).</span></span>

## <a name="add-service-that-requires-di"></a><span data-ttu-id="70d57-134">Добавление службы, требующей внедрения зависимостей</span><span class="sxs-lookup"><span data-stu-id="70d57-134">Add service that requires DI</span></span>

<span data-ttu-id="70d57-135">Добавьте следующий объект средства ведения журнала операций, который выступает в качестве службы для консольного приложения:</span><span class="sxs-lookup"><span data-stu-id="70d57-135">Add the following operation logger object, which acts as a service to the console app:</span></span>

<span data-ttu-id="70d57-136">*OperationLogger.cs*</span><span class="sxs-lookup"><span data-stu-id="70d57-136">*OperationLogger.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/OperationLogger.cs":::

<span data-ttu-id="70d57-137">`OperationLogger` определяет конструктор, которому требуется каждый из вышеупомянутых интерфейсов метки, то есть `ITransientOperation`, `IScopedOperation` и `ISingletonOperation`.</span><span class="sxs-lookup"><span data-stu-id="70d57-137">The `OperationLogger` defines a constructor that requires each of the aforementioned marker interfaces, that is; `ITransientOperation`, `IScopedOperation`, and `ISingletonOperation`.</span></span> <span data-ttu-id="70d57-138">Объект предоставляет единственный метод, позволяющий потребителю записывать в журнал операции с заданным параметром `scope`.</span><span class="sxs-lookup"><span data-stu-id="70d57-138">The object exposes a single method that allows the consumer to log the operations with a given `scope` parameter.</span></span> <span data-ttu-id="70d57-139">При вызове метод `LogOperations` записывает уникальный идентификатор каждой операции в строку и сообщение области.</span><span class="sxs-lookup"><span data-stu-id="70d57-139">When invoked, the `LogOperations` method logs each operation's unique identifier with the scope string and message.</span></span>

## <a name="register-services-for-di"></a><span data-ttu-id="70d57-140">Регистрация служб для внедрения зависимостей</span><span class="sxs-lookup"><span data-stu-id="70d57-140">Register services for DI</span></span>

<span data-ttu-id="70d57-141">Обновите файл *Program.cs*, используя следующий код:</span><span class="sxs-lookup"><span data-stu-id="70d57-141">Update *Program.cs* with the following code:</span></span>

:::code language="csharp" source="snippets/configuration/console-di/Program.cs" range="1-18,35-60" highlight="22-26":::

<span data-ttu-id="70d57-142">Каждый метод расширения `services.Add{SERVICE_NAME}` добавляет (а потенциально и настраивает) службы.</span><span class="sxs-lookup"><span data-stu-id="70d57-142">Each `services.Add{SERVICE_NAME}` extension method adds (and potentially configures) services.</span></span> <span data-ttu-id="70d57-143">Рекомендуем придерживаться такого подхода в приложениях.</span><span class="sxs-lookup"><span data-stu-id="70d57-143">We recommended that apps follow this convention.</span></span> <span data-ttu-id="70d57-144">Поместите методы расширения в пространство имен <xref:Microsoft.Extensions.DependencyInjection?displayProperty=fullName>, чтобы инкапсулировать группы зарегистрированных служб.</span><span class="sxs-lookup"><span data-stu-id="70d57-144">Place extension methods in the <xref:Microsoft.Extensions.DependencyInjection?displayProperty=fullName> namespace to encapsulate groups of service registrations.</span></span> <span data-ttu-id="70d57-145">Включение части `Microsoft.Extensions.DependencyInjection` пространства имен для методов расширения внедрения зависимостей также:</span><span class="sxs-lookup"><span data-stu-id="70d57-145">Including the namespace portion `Microsoft.Extensions.DependencyInjection` for DI extension methods also:</span></span>

- <span data-ttu-id="70d57-146">позволяет отображать их в [IntelliSense](/visualstudio/ide/using-intellisense) без добавления дополнительных блоков `using`;</span><span class="sxs-lookup"><span data-stu-id="70d57-146">Allows them to be displayed in [IntelliSense](/visualstudio/ide/using-intellisense) without adding additional `using` blocks.</span></span>
- <span data-ttu-id="70d57-147">позволяет избежать чрезмерного количества инструкций `using` в классе `Program` или `Startup`, из которого обычно вызываются эти методы расширения.</span><span class="sxs-lookup"><span data-stu-id="70d57-147">Prevents excessive `using` statements in the `Program` or `Startup` classes where these extension methods are typically called.</span></span>

<span data-ttu-id="70d57-148">Приложение:</span><span class="sxs-lookup"><span data-stu-id="70d57-148">The app:</span></span>

- <span data-ttu-id="70d57-149">создает экземпляр <xref:Microsoft.Extensions.Hosting.IHostBuilder> с [настройками привязки по умолчанию](generic-host.md#default-builder-settings);</span><span class="sxs-lookup"><span data-stu-id="70d57-149">Creates an <xref:Microsoft.Extensions.Hosting.IHostBuilder> instance with the [default binder settings](generic-host.md#default-builder-settings).</span></span>
- <span data-ttu-id="70d57-150">настраивает службы и добавляет их с соответствующим временем существования службы;</span><span class="sxs-lookup"><span data-stu-id="70d57-150">Configures services and adds them with their corresponding service lifetime.</span></span>
- <span data-ttu-id="70d57-151">вызывает метод <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> и назначает экземпляр <xref:Microsoft.Extensions.Hosting.IHost>;</span><span class="sxs-lookup"><span data-stu-id="70d57-151">Calls <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> and assigns an instance of <xref:Microsoft.Extensions.Hosting.IHost>.</span></span>
- <span data-ttu-id="70d57-152">вызывает `ExemplifyScoping`, передавая <xref:Microsoft.Extensions.Hosting.IHost.Services?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="70d57-152">Calls `ExemplifyScoping`, passing in the <xref:Microsoft.Extensions.Hosting.IHost.Services?displayProperty=nameWithType>.</span></span>

## <a name="conclusion"></a><span data-ttu-id="70d57-153">Заключение</span><span class="sxs-lookup"><span data-stu-id="70d57-153">Conclusion</span></span>

<span data-ttu-id="70d57-154">Приложение отобразит выходные данные, аналогичные следующему примеру:</span><span class="sxs-lookup"><span data-stu-id="70d57-154">The app displays output similar to the following example:</span></span>

```console
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): ITransientOperation [ 80f4...Always different        ]
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): IScopedOperation    [ c878...Changes only with scope ]
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]
...
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): ITransientOperation [ f3c0...Always different        ]
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): IScopedOperation    [ c878...Changes only with scope ]
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]

Scope 2-Call 1 .GetRequiredService<OperationLogger>(): ITransientOperation [ f9af...Always different        ]
Scope 2-Call 1 .GetRequiredService<OperationLogger>(): IScopedOperation    [ 2bd0...Changes only with scope ]
Scope 2-Call 1 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]
...
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): ITransientOperation [ fa65...Always different        ]
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): IScopedOperation    [ 2bd0...Changes only with scope ]
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]
```

<span data-ttu-id="70d57-155">Из выходных данных приложения можно понять следующее.</span><span class="sxs-lookup"><span data-stu-id="70d57-155">From the app output, you can see that:</span></span>

- <span data-ttu-id="70d57-156">Операции Transient всегда различаются, при каждом извлечении службы создается новый экземпляр.</span><span class="sxs-lookup"><span data-stu-id="70d57-156">Transient operations are always different, a new instance is created with every retrieval of the service.</span></span>
- <span data-ttu-id="70d57-157">Операции Scoped изменяются только с новой областью, но являются одним и тем же экземпляром в пределах области.</span><span class="sxs-lookup"><span data-stu-id="70d57-157">Scoped operations change only with a new scope, but are the same instance within a scope.</span></span>
- <span data-ttu-id="70d57-158">Операции Singleton всегда одинаковы, новый экземпляр создается только один раз.</span><span class="sxs-lookup"><span data-stu-id="70d57-158">Singleton operations are always the same, a new instance is only created once.</span></span>

## <a name="see-also"></a><span data-ttu-id="70d57-159">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="70d57-159">See also</span></span>

* [<span data-ttu-id="70d57-160">Рекомендации по внедрению зависимостей</span><span class="sxs-lookup"><span data-stu-id="70d57-160">Dependency injection guidelines</span></span>](dependency-injection-guidelines.md)
* [<span data-ttu-id="70d57-161">Использование внедрения зависимостей в ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="70d57-161">Dependency injection in ASP.NET Core</span></span>](/aspnet/core/fundamentals/dependency-injection)
