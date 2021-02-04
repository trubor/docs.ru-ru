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
ms.openlocfilehash: 13c91e5cb6728c5669642d1b5f7bb461efdd44f8
ms.sourcegitcommit: 78eb25647b0c750cd80354ebd6ce83a60668e22c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/29/2021
ms.locfileid: "99065055"
---
# <a name="exposing-net-core-components-to-com"></a><span data-ttu-id="b5f6d-104">Предоставление доступа к компонентам .NET Core для COM</span><span class="sxs-lookup"><span data-stu-id="b5f6d-104">Exposing .NET Core components to COM</span></span>

<span data-ttu-id="b5f6d-105">В .NET Core процесс предоставления объектов .NET для модели COM значительно упрощен по сравнению с .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-105">In .NET Core, the process for exposing your .NET objects to COM has been significantly streamlined in comparison to .NET Framework.</span></span> <span data-ttu-id="b5f6d-106">Ниже описывается, как предоставить класс для модели COM.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-106">The following process will walk you through how to expose a class to COM.</span></span> <span data-ttu-id="b5f6d-107">В этом учебнике демонстрируется выполнение следующих действий:</span><span class="sxs-lookup"><span data-stu-id="b5f6d-107">This tutorial shows you how to:</span></span>

- <span data-ttu-id="b5f6d-108">Предоставление класса для модели COM из .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-108">Expose a class to COM from .NET Core.</span></span>
- <span data-ttu-id="b5f6d-109">Создайте сервер COM в процессе сборки библиотеки .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-109">Generate a COM server as part of building your .NET Core library.</span></span>
- <span data-ttu-id="b5f6d-110">Автоматически создайте параллельный манифест сервера для модели COM без поддержки реестра.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-110">Automatically generate a side-by-side server manifest for Registry-Free COM.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b5f6d-111">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="b5f6d-111">Prerequisites</span></span>

- <span data-ttu-id="b5f6d-112">Установите [пакет SDK для .NET Core 3.0](https://dotnet.microsoft.com/download) или более новой версии.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-112">Install [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download) or a newer version.</span></span>

## <a name="create-the-library"></a><span data-ttu-id="b5f6d-113">Создание библиотеки</span><span class="sxs-lookup"><span data-stu-id="b5f6d-113">Create the library</span></span>

<span data-ttu-id="b5f6d-114">Сначала нужно создать библиотеку.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-114">The first step is to create the library.</span></span>

1. <span data-ttu-id="b5f6d-115">Создайте новую папку и в этой папке выполните следующую команду.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-115">Create a new folder, and in that folder run the following command:</span></span>

    ```dotnetcli
    dotnet new classlib
    ```

2. <span data-ttu-id="b5f6d-116">Откройте `Class1.cs`.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-116">Open `Class1.cs`.</span></span>
3. <span data-ttu-id="b5f6d-117">Добавьте `using System.Runtime.InteropServices;` в начало файла.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-117">Add `using System.Runtime.InteropServices;` to the top of the file.</span></span>
4. <span data-ttu-id="b5f6d-118">Создайте интерфейс с именем `IServer`.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-118">Create an interface named `IServer`.</span></span> <span data-ttu-id="b5f6d-119">Пример:</span><span class="sxs-lookup"><span data-stu-id="b5f6d-119">For example:</span></span>

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

5. <span data-ttu-id="b5f6d-120">Добавьте в интерфейс атрибут `[Guid("<IID>")]` с идентификатором GUID реализуемого интерфейса COM.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-120">Add the `[Guid("<IID>")]` attribute to the interface, with the interface GUID for the COM interface you're implementing.</span></span> <span data-ttu-id="b5f6d-121">Например, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-121">For example, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`.</span></span> <span data-ttu-id="b5f6d-122">Обратите внимание, что этот идентификатор GUID должен быть уникальным, так как он является единственным идентификатором данного интерфейса для модели COM.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-122">Note that this GUID needs to be unique since it is the only identifier of this interface for COM.</span></span> <span data-ttu-id="b5f6d-123">Чтобы создать идентификатор GUID в Visual Studio, выберите "Сервис" > "Создать GUID". Откроется средство создания идентификатора GUID.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-123">In Visual Studio, you can generate a GUID by going to Tools > Create GUID to open the Create GUID tool.</span></span>
6. <span data-ttu-id="b5f6d-124">Добавьте в интерфейс атрибут `[InterfaceType]` и укажите, какие базовые COM-интерфейсы должен реализовывать ваш интерфейс.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-124">Add the `[InterfaceType]` attribute to the interface and specify what base COM interfaces your interface should implement.</span></span>
7. <span data-ttu-id="b5f6d-125">Создайте класс `Server`, реализующий `IServer`.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-125">Create a class named `Server` that implements `IServer`.</span></span>
8. <span data-ttu-id="b5f6d-126">Добавьте в класс атрибут `[Guid("<CLSID>")]` с идентификатором GUID реализуемого класса COM.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-126">Add the `[Guid("<CLSID>")]` attribute to the class, with the class identifier GUID for the COM class you're implementing.</span></span> <span data-ttu-id="b5f6d-127">Например, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-127">For example, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`.</span></span> <span data-ttu-id="b5f6d-128">Так же как и в случае с идентификатором GUID интерфейса, этот идентификатор GUID должен быть уникальным, так как он является единственным идентификатором данного класса для модели COM.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-128">As with the interface GUID, this GUID must be unique since it is the only identifier of this interface to COM.</span></span>
9. <span data-ttu-id="b5f6d-129">Добавьте атрибут `[ComVisible(true)]` как в интерфейс, так и в класс.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-129">Add the `[ComVisible(true)]` attribute to both the interface and the class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b5f6d-130">В отличие от .NET Framework, .NET Core требует указывать идентификатор CLSID любого класса, который должен активироваться через модель COM.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-130">Unlike in .NET Framework, .NET Core requires you to specify the CLSID of any class you want to be activatable via COM.</span></span>

## <a name="generate-the-com-host"></a><span data-ttu-id="b5f6d-131">Создание узла COM</span><span class="sxs-lookup"><span data-stu-id="b5f6d-131">Generate the COM host</span></span>

1. <span data-ttu-id="b5f6d-132">Откройте файл проекта `.csproj` и добавьте элемент `<EnableComHosting>true</EnableComHosting>` внутри тега `<PropertyGroup></PropertyGroup>`.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-132">Open the `.csproj` project file and add `<EnableComHosting>true</EnableComHosting>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="b5f6d-133">Выполните построение проекта.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-133">Build the project.</span></span>

<span data-ttu-id="b5f6d-134">В результате будут получены файлы `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` и `ProjectName.comhost.dll`.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-134">The resulting output will have a `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` and `ProjectName.comhost.dll` file.</span></span>

## <a name="register-the-com-host-for-com"></a><span data-ttu-id="b5f6d-135">Регистрация узла COM для модели COM</span><span class="sxs-lookup"><span data-stu-id="b5f6d-135">Register the COM host for COM</span></span>

<span data-ttu-id="b5f6d-136">Откройте командную строку с повышенными привилегиями и запустите `regsvr32 ProjectName.comhost.dll`.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-136">Open an elevated command prompt and run `regsvr32 ProjectName.comhost.dll`.</span></span> <span data-ttu-id="b5f6d-137">Это приведет к регистрации всех предоставленных объектов .NET в модели COM.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-137">That will register all of your exposed .NET objects with COM.</span></span>

## <a name="enabling-regfree-com"></a><span data-ttu-id="b5f6d-138">Реализация модели COM без поддержки реестра</span><span class="sxs-lookup"><span data-stu-id="b5f6d-138">Enabling RegFree COM</span></span>

1. <span data-ttu-id="b5f6d-139">Откройте файл проекта `.csproj` и добавьте элемент `<EnableRegFreeCom>true</EnableRegFreeCom>` внутри тега `<PropertyGroup></PropertyGroup>`.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-139">Open the `.csproj` project file and add `<EnableRegFreeCom>true</EnableRegFreeCom>` inside a `<PropertyGroup></PropertyGroup>` tag.</span></span>
2. <span data-ttu-id="b5f6d-140">Выполните построение проекта.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-140">Build the project.</span></span>

<span data-ttu-id="b5f6d-141">В результате будет также получен файл `ProjectName.X.manifest`.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-141">The resulting output will now also have a `ProjectName.X.manifest` file.</span></span> <span data-ttu-id="b5f6d-142">Это параллельный манифест для использования с моделью COM без поддержки реестра.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-142">This file is the side-by-side manifest for use with Registry-Free COM.</span></span>

## <a name="sample"></a><span data-ttu-id="b5f6d-143">Пример</span><span class="sxs-lookup"><span data-stu-id="b5f6d-143">Sample</span></span>

<span data-ttu-id="b5f6d-144">В репозитории dotnet/samples на сайте GitHub есть полнофункциональный [пример сервера COM](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span><span class="sxs-lookup"><span data-stu-id="b5f6d-144">There is a fully functional [COM server sample](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) in the dotnet/samples repository on GitHub.</span></span>

## <a name="additional-notes"></a><span data-ttu-id="b5f6d-145">Дополнительные сведения</span><span class="sxs-lookup"><span data-stu-id="b5f6d-145">Additional notes</span></span>

<span data-ttu-id="b5f6d-146">В отличие от .NET Framework, в .NET Core создание библиотеки типов COM (TLB) из сборки .NET Core не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-146">Unlike in .NET Framework, there is no support in .NET Core for generating a COM Type Library (TLB) from a .NET Core assembly.</span></span> <span data-ttu-id="b5f6d-147">Нужно вручную написать файл IDL или заголовок C/C++ для собственных объявлений COM-интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-147">The guidance is to either manually write an IDL file or a C/C++ header for the native declarations of the COM interfaces.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b5f6d-148">В .NET Framework сборка "Любой ЦП" может использоваться как с 32-разрядными, так и с 64-разрядными клиентами.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-148">In .NET Framework, an "Any CPU" assembly can be consumed by both 32-bit and 64-bit clients.</span></span> <span data-ttu-id="b5f6d-149">По умолчанию в .NET Core, .NET 5 и более поздних версий вместе со сборками "Любой ЦП" поставляется 64-разрядная библиотека *\*.comhost.dll*.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-149">By default, in .NET Core, .NET 5, and later versions, "Any CPU" assemblies are accompanied by a 64-bit *\*.comhost.dll*.</span></span> <span data-ttu-id="b5f6d-150">По этой причине они могут использоваться только в 64-разрядных клиентах.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-150">Because of this, they can only be consumed by 64-bit clients.</span></span> <span data-ttu-id="b5f6d-151">Это настроено по умолчанию, поскольку это то, что предоставляет пакет SDK.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-151">That is the default because that is what the SDK represents.</span></span> <span data-ttu-id="b5f6d-152">Такое поведение аналогично публикации "автономного" компонента: по умолчанию он использует то, что предоставляет пакет SDK.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-152">This behavior is identical to how the "self-contained" feature is published: by default it uses what the SDK provides.</span></span> <span data-ttu-id="b5f6d-153">Свойство MSBuild `NETCoreSdkRuntimeIdentifier` определяет разрядность библиотеки *\*.comhost.dll*.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-153">The `NETCoreSdkRuntimeIdentifier` MSBuild property determines the bitness of *\*.comhost.dll*.</span></span> <span data-ttu-id="b5f6d-154">Управляемая часть на самом деле не зависит от ожидаемой разрядности, однако разрядность сопутствующего ресурса по умолчанию совпадает с разрядностью целевого пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-154">The managed part is actually bitness agnostic as expected, but the accompanying native asset defaults to the targeted SDK.</span></span>

<span data-ttu-id="b5f6d-155">[Автономные развертывания](../deploying/index.md#publish-self-contained) COM-компонентов не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-155">[Self-contained deployments](../deploying/index.md#publish-self-contained) of COM components are not supported.</span></span> <span data-ttu-id="b5f6d-156">Поддерживаются только [зависящие от платформы развертывания](../deploying/index.md#publish-framework-dependent) COM-компонентов.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-156">Only [framework-dependent deployments](../deploying/index.md#publish-framework-dependent) of COM components are supported.</span></span>

<span data-ttu-id="b5f6d-157">Кроме того, загрузка как .NET Framework, так и .NET Core в один и тот же процесс имеет ограничения диагностического характера.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-157">Additionally, loading both .NET Framework and .NET Core into the same process does have diagnostic limitations.</span></span> <span data-ttu-id="b5f6d-158">Основное ограничение — отладка управляемых компонентов, так как невозможно одновременно выполнить отладку .NET Framework и .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-158">The primary limitation is the debugging of managed components as it is not possible to debug both .NET Framework and .NET Core at the same time.</span></span> <span data-ttu-id="b5f6d-159">Кроме того, два экземпляра среды выполнения не используют управляемые сборки совместно.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-159">In addition, the two runtime instances don't share managed assemblies.</span></span> <span data-ttu-id="b5f6d-160">Это означает, что невозможно совместно использовать фактические типы .NET в двух средах выполнения, вместо этого все взаимодействия должны быть ограничены предоставленными контрактами COM-интерфейса.</span><span class="sxs-lookup"><span data-stu-id="b5f6d-160">This means that it isn't possible to share actual .NET types across the two runtimes and instead all interactions must be restricted to the exposed COM interface contracts.</span></span>
