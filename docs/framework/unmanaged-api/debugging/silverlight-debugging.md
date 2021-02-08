---
description: 'Дополнительные сведения: отладка Silverlight'
title: Отладка в Silverlight
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
ms.openlocfilehash: 54a3f7f4b2de867509ff94dafa25c067a78b3ee6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800543"
---
# <a name="silverlight-debugging"></a><span data-ttu-id="6ce6e-103">Отладка в Silverlight</span><span class="sxs-lookup"><span data-stu-id="6ce6e-103">Silverlight Debugging</span></span>

<span data-ttu-id="6ce6e-104">В этом разделе описываются среда и интерфейсы, предоставляемые средой CLR для поддержки отладки приложений на основе Silverlight, работающих в ОС Windows или на платформе Macintosh.</span><span class="sxs-lookup"><span data-stu-id="6ce6e-104">The topics in this section describe the environment and interfaces that the common language runtime (CLR) provides to support debugging Silverlight-based applications that are running on the Windows operating system, or on the Macintosh platform.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6ce6e-105">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="6ce6e-105">In This Section</span></span>  

 [<span data-ttu-id="6ce6e-106">Функция EnumerateCLRs</span><span class="sxs-lookup"><span data-stu-id="6ce6e-106">EnumerateCLRs Function</span></span>](enumerateclrs-function.md)  
 <span data-ttu-id="6ce6e-107">Предоставляет механизм для перечисления сред CLR в процессе.</span><span class="sxs-lookup"><span data-stu-id="6ce6e-107">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
 [<span data-ttu-id="6ce6e-108">Функция CloseCLREnumeration</span><span class="sxs-lookup"><span data-stu-id="6ce6e-108">CloseCLREnumeration Function</span></span>](closeclrenumeration-function.md)  
 <span data-ttu-id="6ce6e-109">Закрывает все допустимые события продолжения запуска среды CLR, расположенные в массиве дескрипторов, возвращенных [функцией EnumerateCLRs](enumerateclrs-function.md), и освобождает память для массивов дескрипторов и строк.</span><span class="sxs-lookup"><span data-stu-id="6ce6e-109">Closes any valid CLR continue-startup events located in an array of handles returned by the [EnumerateCLRs Function](enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
 [<span data-ttu-id="6ce6e-110">Функция CreateCoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="6ce6e-110">CreateCoreClrDebugTarget Function</span></span>](createcoreclrdebugtarget-function.md)  
 <span data-ttu-id="6ce6e-111">Создает подключение к удаленному целевому объекту для процесса и перечисления среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="6ce6e-111">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="6ce6e-112">Функция CreateCordbObject</span><span class="sxs-lookup"><span data-stu-id="6ce6e-112">CreateCordbObject Function</span></span>](createcordbobject-function.md)  
 <span data-ttu-id="6ce6e-113">Создает интерфейс отладчика, обеспечивающий функциональность для создания управляемого сеанса отладки в удаленном процессе.</span><span class="sxs-lookup"><span data-stu-id="6ce6e-113">Creates a debugger interface that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
 [<span data-ttu-id="6ce6e-114">Функция CreateVersionStringFromModule</span><span class="sxs-lookup"><span data-stu-id="6ce6e-114">CreateVersionStringFromModule Function</span></span>](createversionstringfrommodule-function.md)  
 <span data-ttu-id="6ce6e-115">Создает строку версии из пути среды CLR в целевом процессе.</span><span class="sxs-lookup"><span data-stu-id="6ce6e-115">Creates a version string from a CLR path in a target process.</span></span>  
  
 [<span data-ttu-id="6ce6e-116">Функция CreateDebuggingInterfaceFromVersion</span><span class="sxs-lookup"><span data-stu-id="6ce6e-116">CreateDebuggingInterfaceFromVersion Function</span></span>](createdebugginginterfacefromversion-function-for-silverlight.md)  
 <span data-ttu-id="6ce6e-117">Принимает строку версии среды CLR, возвращаемую функцией [CreateVersionStringFromModule Function](createversionstringfrommodule-function.md), и возвращает соответствующий интерфейс отладчика.</span><span class="sxs-lookup"><span data-stu-id="6ce6e-117">Accepts a CLR version string returned from [CreateVersionStringFromModule Function](createversionstringfrommodule-function.md)function, and returns a corresponding debugger interface.</span></span>  
  
 [<span data-ttu-id="6ce6e-118">Структура CoreClrDebugProcInfo</span><span class="sxs-lookup"><span data-stu-id="6ce6e-118">CoreClrDebugProcInfo Structure</span></span>](coreclrdebugprocinfo-structure.md)  
 <span data-ttu-id="6ce6e-119">Представляет процесс, который выполняется на удаленном компьютере.</span><span class="sxs-lookup"><span data-stu-id="6ce6e-119">Represents a process that is running on a remote machine.</span></span>  
  
 [<span data-ttu-id="6ce6e-120">Структура CoreClrDebugRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="6ce6e-120">CoreClrDebugRuntimeInfo Structure</span></span>](coreclrdebugruntimeinfo-structure.md)  
 <span data-ttu-id="6ce6e-121">Представляет экземпляр среды CLR, который загружается в процессе на удаленном компьютере.</span><span class="sxs-lookup"><span data-stu-id="6ce6e-121">Represents a CLR instance that is loaded in a process on a remote machine.</span></span>  
  
 [<span data-ttu-id="6ce6e-122">Функция GetStartupNotificationEvent</span><span class="sxs-lookup"><span data-stu-id="6ce6e-122">GetStartupNotificationEvent Function</span></span>](getstartupnotificationevent-function.md)  
 <span data-ttu-id="6ce6e-123">Создает или открывает обработчик событий, который будет информироваться любой средой CLR, загружаемой в указанный целевой процесс.</span><span class="sxs-lookup"><span data-stu-id="6ce6e-123">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
 [<span data-ttu-id="6ce6e-124">Интерфейс ICoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="6ce6e-124">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)  
 <span data-ttu-id="6ce6e-125">Создает подключение к удаленному целевому объекту для процесса и перечисления среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="6ce6e-125">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="6ce6e-126">Функция InitDbgTransportManager</span><span class="sxs-lookup"><span data-stu-id="6ce6e-126">InitDbgTransportManager Function</span></span>](initdbgtransportmanager-function.md)  
 <span data-ttu-id="6ce6e-127">Инициализирует диспетчер транспорта для подключения к удаленному целевому объекту для процесса и перечисления среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="6ce6e-127">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="6ce6e-128">Функция ShutdownDbgTransportManager</span><span class="sxs-lookup"><span data-stu-id="6ce6e-128">ShutdownDbgTransportManager Function</span></span>](shutdowndbgtransportmanager-function.md)  
 <span data-ttu-id="6ce6e-129">Завершает работу диспетчера транспорта для подключения к удаленному целевому компьютеру.</span><span class="sxs-lookup"><span data-stu-id="6ce6e-129">Shuts down the transport manager for a connection to a remote target machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ce6e-130">См. также</span><span class="sxs-lookup"><span data-stu-id="6ce6e-130">See also</span></span>

- [<span data-ttu-id="6ce6e-131">Компонентные классы отладки</span><span class="sxs-lookup"><span data-stu-id="6ce6e-131">Debugging Coclasses</span></span>](debugging-coclasses.md)
- [<span data-ttu-id="6ce6e-132">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="6ce6e-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="6ce6e-133">Глобальные статические функции отладки</span><span class="sxs-lookup"><span data-stu-id="6ce6e-133">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
- [<span data-ttu-id="6ce6e-134">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="6ce6e-134">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="6ce6e-135">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="6ce6e-135">Debugging Structures</span></span>](debugging-structures.md)
