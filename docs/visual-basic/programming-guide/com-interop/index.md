---
description: 'Дополнительные сведения: COM Interop (Visual Basic)'
title: COM-взаимодействие
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, COM interop
- COM interop [Visual Basic], in Visual Basic
ms.assetid: 3ffd1bdf-1b8d-47f5-87eb-75b659f64294
ms.openlocfilehash: 02ce21c6175f76bca17ae6ab57aa1569800167f4
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100460713"
---
# <a name="com-interop-visual-basic"></a><span data-ttu-id="a988e-103">COM-взаимодействие (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a988e-103">COM Interop (Visual Basic)</span></span>

<span data-ttu-id="a988e-104">Объектная модель компонентов (модель COM) позволяет объекту предоставлять свою функциональность другим компонентам и ведущим приложениям.</span><span class="sxs-lookup"><span data-stu-id="a988e-104">The Component Object Model (COM) allows an object to expose its functionality to other components and to host applications.</span></span> <span data-ttu-id="a988e-105">COM-объекты входят в состав большей части современного программного обеспечения.</span><span class="sxs-lookup"><span data-stu-id="a988e-105">Most of today's software includes COM objects.</span></span> <span data-ttu-id="a988e-106">Хотя сборки .NET являются наилучшим решением для новых приложений, в некоторых случаях необходимо использование COM-объектов.</span><span class="sxs-lookup"><span data-stu-id="a988e-106">Although .NET assemblies are the best choice for new applications, you may at times need to employ COM objects.</span></span> <span data-ttu-id="a988e-107">В этом разделе рассматриваются некоторые проблемы, связанные с созданием и использованием COM-объектов с Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a988e-107">This section covers some of the issues associated with creating and using COM objects with Visual Basic.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a988e-108">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="a988e-108">In This Section</span></span>  

 [<span data-ttu-id="a988e-109">Знакомство с COM-взаимодействием</span><span class="sxs-lookup"><span data-stu-id="a988e-109">Introduction to COM Interop</span></span>](introduction-to-com-interop.md)  
 <span data-ttu-id="a988e-110">Общие сведения о COM-взаимодействии.</span><span class="sxs-lookup"><span data-stu-id="a988e-110">Provides an overview of COM interoperability.</span></span>  
  
 [<span data-ttu-id="a988e-111">Практическое руководство. Ссылки на COM-объекты в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a988e-111">How to: Reference COM Objects from Visual Basic</span></span>](how-to-reference-com-objects.md)  
 <span data-ttu-id="a988e-112">Описывает, как добавлять ссылки на COM-объекты, имеющие библиотеки типов.</span><span class="sxs-lookup"><span data-stu-id="a988e-112">Covers how to add references to COM objects that have type libraries.</span></span>  
  
 [<span data-ttu-id="a988e-113">Практическое руководство. Работа с элементами управления ActiveX</span><span class="sxs-lookup"><span data-stu-id="a988e-113">How to: Work with ActiveX Controls</span></span>](how-to-work-with-activex-controls.md)  
 <span data-ttu-id="a988e-114">Демонстрирует использование существующих элементов управления ActiveX для добавления компонентов в панель элементов Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a988e-114">Demonstrates how to use existing ActiveX controls to add features to the Visual Studio Toolbox.</span></span>  
  
 [<span data-ttu-id="a988e-115">Пошаговое руководство. Вызов API Windows</span><span class="sxs-lookup"><span data-stu-id="a988e-115">Walkthrough: Calling Windows APIs</span></span>](walkthrough-calling-windows-apis.md)  
 <span data-ttu-id="a988e-116">Пошаговое описание процесса вызова API-интерфейсов, входящих в операционную систему Windows.</span><span class="sxs-lookup"><span data-stu-id="a988e-116">Steps you through the process of calling the APIs that are part of the Windows operating system.</span></span>  
  
 [<span data-ttu-id="a988e-117">Практическое руководство. Вызов API Windows</span><span class="sxs-lookup"><span data-stu-id="a988e-117">How to: Call Windows APIs</span></span>](how-to-call-windows-apis.md)  
 <span data-ttu-id="a988e-118">Демонстрация определения и вызова функции `MessageBox` в библиотеке User32.dll.</span><span class="sxs-lookup"><span data-stu-id="a988e-118">Demonstrates how to define and call the `MessageBox` function in User32.dll.</span></span>  
  
 [<span data-ttu-id="a988e-119">Практическое руководство. Вызов функции Windows, принимающей значение беззнакового типа</span><span class="sxs-lookup"><span data-stu-id="a988e-119">How to: Call a Windows Function that Takes Unsigned Types</span></span>](how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 <span data-ttu-id="a988e-120">Демонстрация вызова функции Windows, которая имеет параметр с типом без знака.</span><span class="sxs-lookup"><span data-stu-id="a988e-120">Demonstrates how to call a Windows function that has a parameter of an unsigned type.</span></span>  
  
 [<span data-ttu-id="a988e-121">Пошаговое руководство. Создание объектов COM с помощью Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a988e-121">Walkthrough: Creating COM Objects with Visual Basic</span></span>](walkthrough-creating-com-objects.md)  
 <span data-ttu-id="a988e-122">Пошаговое описание создания COM-объектов с использованием шаблона класса COM и без него.</span><span class="sxs-lookup"><span data-stu-id="a988e-122">Steps you through the process of creating COM objects with and without the COM class template.</span></span>  
  
 [<span data-ttu-id="a988e-123">Устранение неполадок взаимодействия</span><span class="sxs-lookup"><span data-stu-id="a988e-123">Troubleshooting Interoperability</span></span>](troubleshooting-interoperability.md)  
 <span data-ttu-id="a988e-124">Описание некоторых проблем, которые могут возникнуть при использовании модели COM.</span><span class="sxs-lookup"><span data-stu-id="a988e-124">Covers some of the problems you may encounter when using COM.</span></span>  
  
 [<span data-ttu-id="a988e-125">COM-взаимодействие в приложениях .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a988e-125">COM Interoperability in .NET Framework Applications</span></span>](com-interoperability-in-net-framework-applications.md)  
 <span data-ttu-id="a988e-126">Общие сведения об использовании объектов .NET Framework и COM в одном приложении.</span><span class="sxs-lookup"><span data-stu-id="a988e-126">Provides an overview of how to use COM objects and .NET Framework objects in the same application.</span></span>  
  
 [<span data-ttu-id="a988e-127">Пошаговое руководство. Реализация наследования с использованием COM-объектов</span><span class="sxs-lookup"><span data-stu-id="a988e-127">Walkthrough: Implementing Inheritance with COM Objects</span></span>](walkthrough-implementing-inheritance-with-com-objects.md)  
 <span data-ttu-id="a988e-128">Описание использования существующих COM-объектов в качестве основы для новых объектов.</span><span class="sxs-lookup"><span data-stu-id="a988e-128">Describes using existing COM objects as the basis for new objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a988e-129">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="a988e-129">Related Sections</span></span>  

 [<span data-ttu-id="a988e-130">Взаимодействие с неуправляемым кодом</span><span class="sxs-lookup"><span data-stu-id="a988e-130">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)  
 <span data-ttu-id="a988e-131">Описываются службы взаимодействия, предоставляемые средой CLR.</span><span class="sxs-lookup"><span data-stu-id="a988e-131">Describes interoperability services provided by the common language runtime.</span></span>  
  
 [<span data-ttu-id="a988e-132">Предоставление COM-компонентов платформе .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a988e-132">Exposing COM Components to the .NET Framework</span></span>](../../../framework/interop/exposing-com-components.md)  
 <span data-ttu-id="a988e-133">Описание процесса вызова типов COM через COM-взаимодействие.</span><span class="sxs-lookup"><span data-stu-id="a988e-133">Describes the process of calling COM types through COM interop.</span></span>  
  
 [<span data-ttu-id="a988e-134">Предоставление компонентов .NET Framework клиентам COM</span><span class="sxs-lookup"><span data-stu-id="a988e-134">Exposing .NET Framework Components to COM</span></span>](../../../framework/interop/exposing-dotnet-components-to-com.md)  
 <span data-ttu-id="a988e-135">Описание подготовки и использования управляемых типов из COM.</span><span class="sxs-lookup"><span data-stu-id="a988e-135">Describes the preparation and use of managed types from COM.</span></span>  
  
 [<span data-ttu-id="a988e-136">Применение атрибутов взаимодействия</span><span class="sxs-lookup"><span data-stu-id="a988e-136">Applying Interop Attributes</span></span>](../../../standard/native-interop/apply-interop-attributes.md)  
 <span data-ttu-id="a988e-137">Описание атрибутов, которые можно использовать при работе с неуправляемым кодом.</span><span class="sxs-lookup"><span data-stu-id="a988e-137">Covers attributes you can use when working with unmanaged code.</span></span>
