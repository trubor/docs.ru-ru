---
description: 'Узнайте подробнее о: Справочник по неуправляемым API'
title: Справочник по неуправляемым API
ms.date: 11/06/2017
helpviewer_keywords:
- runtime, unmanaged APIs
- common language runtime, unmanaged APIs
- native API reference [.NET Framework]
- unmanaged API reference [.NET Framework]
ms.assetid: 9aa000ee-c04c-492c-ae4f-83ecdf4fdbbe
ms.openlocfilehash: 3c9c485d8dced9641d0d1af850de190318902aa9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678995"
---
# <a name="unmanaged-api-reference"></a><span data-ttu-id="d4a63-103">Справочник по неуправляемым API</span><span class="sxs-lookup"><span data-stu-id="d4a63-103">Unmanaged API Reference</span></span>

<span data-ttu-id="d4a63-104">В данном разделе содержатся сведения о неуправляемых API, которые могут использоваться приложениями, связанными с управляемым кодом, например хост-приложениями среды выполнения, компиляторами, дизассемблерами, средствами запутывания, отладчиками и профилировщиками.</span><span class="sxs-lookup"><span data-stu-id="d4a63-104">This section includes information on unmanaged APIs that can be used by managed-code-related applications, such as runtime hosts, compilers, disassemblers, obfuscators, debuggers, and profilers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d4a63-105">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="d4a63-105">In This Section</span></span>  

 [<span data-ttu-id="d4a63-106">Общие типы данных</span><span class="sxs-lookup"><span data-stu-id="d4a63-106">Common Data Types</span></span>](common-data-types-unmanaged-api-reference.md)  
 <span data-ttu-id="d4a63-107">Содержит список используемых общих типы данных, в частности в неуправляемых API профилирования и отладки.</span><span class="sxs-lookup"><span data-stu-id="d4a63-107">Lists the common data types that are used, particularly in the unmanaged profiling and debugging APIs.</span></span>  
  
 [<span data-ttu-id="d4a63-108">ALink</span><span class="sxs-lookup"><span data-stu-id="d4a63-108">ALink</span></span>](./alink/index.md)  
 <span data-ttu-id="d4a63-109">Описывает API ALink, поддерживающий создание сборок платформы .NET Framework и несвязанных модулей.</span><span class="sxs-lookup"><span data-stu-id="d4a63-109">Describes the ALink API, which supports the creation of .NET Framework assemblies and unbound modules.</span></span>  
  
 [<span data-ttu-id="d4a63-110">Authenticode</span><span class="sxs-lookup"><span data-stu-id="d4a63-110">Authenticode</span></span>](./authenticode/index.md)  
 <span data-ttu-id="d4a63-111">Поддерживает модуль создания и проверки лицензий Authenticode XrML.</span><span class="sxs-lookup"><span data-stu-id="d4a63-111">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
 [<span data-ttu-id="d4a63-112">Константы</span><span class="sxs-lookup"><span data-stu-id="d4a63-112">Constants</span></span>](constants-unmanaged-api-reference.md)  
 <span data-ttu-id="d4a63-113">Описывает константы, определяемые в CorSym.idl.</span><span class="sxs-lookup"><span data-stu-id="d4a63-113">Describes the constants that are defined in CorSym.idl.</span></span>  
  
 <span data-ttu-id="d4a63-114">[Пользовательские атрибуты интерфейса](/previous-versions/dotnet/netframework-4.0/ms231946(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d4a63-114">[Custom Interface Attributes](/previous-versions/dotnet/netframework-4.0/ms231946(v=vs.100))</span></span>  
 <span data-ttu-id="d4a63-115">Описывает атрибуты пользовательского интерфейса COM.</span><span class="sxs-lookup"><span data-stu-id="d4a63-115">Describes component object model (COM) custom interface attributes.</span></span>  
  
 [<span data-ttu-id="d4a63-116">Отладка</span><span class="sxs-lookup"><span data-stu-id="d4a63-116">Debugging</span></span>](./debugging/index.md)  
 <span data-ttu-id="d4a63-117">Описывает API отладки, позволяющий отладчику производить отладку кода, который выполняется в среде CLR.</span><span class="sxs-lookup"><span data-stu-id="d4a63-117">Describes the debugging API, which enables a debugger to debug code that runs in the common language runtime (CLR) environment.</span></span>  
  
 [<span data-ttu-id="d4a63-118">Хранилище символов диагностики</span><span class="sxs-lookup"><span data-stu-id="d4a63-118">Diagnostics Symbol Store</span></span>](./diagnostics/index.md)  
 <span data-ttu-id="d4a63-119">Описывает API хранилища диагностических символов, который позволяет компилятору генерировать символьную информацию для ее использования отладчиком.</span><span class="sxs-lookup"><span data-stu-id="d4a63-119">Describes the diagnostics symbol store API, which enables a compiler to generate symbol information for use by a debugger.</span></span>  
  
 [<span data-ttu-id="d4a63-120">Fusion</span><span class="sxs-lookup"><span data-stu-id="d4a63-120">Fusion</span></span>](./fusion/index.md)  
 <span data-ttu-id="d4a63-121">Описывает API переопределения, который позволяет хост-приложению среды выполнения получать доступ к свойствам ресурсов приложения для того, чтобы найти правильные версии этих ресурсов для их применения.</span><span class="sxs-lookup"><span data-stu-id="d4a63-121">Describes the fusion API, which enables a runtime host to access the properties of an application's resources in order to locate the correct versions of those resources for the application.</span></span>  
  
 [<span data-ttu-id="d4a63-122">Размещение</span><span class="sxs-lookup"><span data-stu-id="d4a63-122">Hosting</span></span>](./hosting/index.md)  
 <span data-ttu-id="d4a63-123">Описывает API размещения, который позволяет неуправляемым узлам интегрировать среду CLR в свои приложения.</span><span class="sxs-lookup"><span data-stu-id="d4a63-123">Describes the hosting API, which enables unmanaged hosts to integrate the CLR into their applications.</span></span>  
  
 [<span data-ttu-id="d4a63-124">Метаданные</span><span class="sxs-lookup"><span data-stu-id="d4a63-124">Metadata</span></span>](./metadata/index.md)  
 <span data-ttu-id="d4a63-125">Описывает API метаданных, который позволяет клиенту, например компилятору, генерировать метаданные компонента или получать к ним доступ без загрузки типов средой CLR.</span><span class="sxs-lookup"><span data-stu-id="d4a63-125">Describes the metadata API, which enables a client such as a compiler to generate or access a component's metadata without the types being loaded by the CLR.</span></span>  
  
 [<span data-ttu-id="d4a63-126">Профилирование</span><span class="sxs-lookup"><span data-stu-id="d4a63-126">Profiling</span></span>](./profiling/index.md)  
 <span data-ttu-id="d4a63-127">Описывает API профилирования, который позволяет профилировщику отслеживать выполнение программы с помощью среды CLR.</span><span class="sxs-lookup"><span data-stu-id="d4a63-127">Describes the profiling API, which enables a profiler to monitor a program's execution by the CLR.</span></span>  
  
 [<span data-ttu-id="d4a63-128">Строгое именование</span><span class="sxs-lookup"><span data-stu-id="d4a63-128">Strong Naming</span></span>](./strong-naming/index.md)  
 <span data-ttu-id="d4a63-129">Описывает API строгого именования, который позволяет клиенту администрировать подписание строгого именования для сборки.</span><span class="sxs-lookup"><span data-stu-id="d4a63-129">Describes the strong naming API, which enables a client to administer strong name signing for assemblies.</span></span>  

 [<span data-ttu-id="d4a63-130">WMI и счетчики производительности</span><span class="sxs-lookup"><span data-stu-id="d4a63-130">WMI and Performance Counters</span></span>](wmi/index.md)  
 <span data-ttu-id="d4a63-131">Описывает интерфейсы API, которые упаковывают вызовы библиотек инструментария управления Windows (WMI).</span><span class="sxs-lookup"><span data-stu-id="d4a63-131">Describes the APIs that wrap calls to Windows Management Instrumentation (WMI) libraries.</span></span>
  
 [<span data-ttu-id="d4a63-132">Вспомогательные функции Tlbexp</span><span class="sxs-lookup"><span data-stu-id="d4a63-132">Tlbexp Helper Functions</span></span>](./tlbexp/index.md)  
 <span data-ttu-id="d4a63-133">Описывает две вспомогательные функции и интерфейс, используемые модулем экспорта библиотек (Tlbexp.exe) в процессе преобразования сборки в библиотеку типов.</span><span class="sxs-lookup"><span data-stu-id="d4a63-133">Describes the two helper functions and interface used by the Type Library Exporter (Tlbexp.exe) during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d4a63-134">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="d4a63-134">Related Sections</span></span>  

 [<span data-ttu-id="d4a63-135">Руководство по разработке</span><span class="sxs-lookup"><span data-stu-id="d4a63-135">Development Guide</span></span>](../development-guide.md)
