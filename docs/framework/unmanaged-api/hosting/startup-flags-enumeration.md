---
description: 'Дополнительные сведения: перечисление STARTUP_FLAGS'
title: Перечисление STARTUP_FLAGS
ms.date: 03/30/2017
api_name:
- STARTUP_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- STARTUP_FLAGS
helpviewer_keywords:
- STARTUP_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 4f043594-0c45-4bc6-988e-a6793f0d8d06
topic_type:
- apiref
ms.openlocfilehash: 2136f1c43545342f2cdc7cde884999a2f2c11bdd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679346"
---
# <a name="startup_flags-enumeration"></a><span data-ttu-id="4474d-103">Перечисление STARTUP_FLAGS</span><span class="sxs-lookup"><span data-stu-id="4474d-103">STARTUP_FLAGS Enumeration</span></span>

<span data-ttu-id="4474d-104">Содержит значения, которые указывают на поведение среды CLR при запуске.</span><span class="sxs-lookup"><span data-stu-id="4474d-104">Contains values that indicate the startup behavior of the common language runtime (CLR).</span></span> <span data-ttu-id="4474d-105">По умолчанию сборка мусора не параллельна, и в область, нейтральную к домену, загружается только Библиотека базовых классов.</span><span class="sxs-lookup"><span data-stu-id="4474d-105">By default, garbage collection is non-concurrent, and only the base class library is loaded into the domain-neutral area.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4474d-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4474d-106">Syntax</span></span>  
  
```cpp  
typedef enum {  
    STARTUP_CONCURRENT_GC                         = 0x1,  
    STARTUP_LOADER_OPTIMIZATION_MASK              = 0x3<<1,  
    STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN     = 0x1<<1,  
    STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN      = 0x2<<1,  
    STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST = 0x3<<1,  
  
    STARTUP_LOADER_SAFEMODE                       = 0x10,  
    STARTUP_LOADER_SETPREFERENCE                  = 0x100,  
  
    STARTUP_SERVER_GC                             = 0x1000,  
    STARTUP_HOARD_GC_VM                           = 0x2000,  
  
    STARTUP_SINGLE_VERSION_HOSTING_INTERFACE      = 0x4000,  
    STARTUP_LEGACY_IMPERSONATION                  = 0x10000,  
    STARTUP_DISABLE_COMMITTHREADSTACK             = 0x20000,  
    STARTUP_ALWAYSFLOW_IMPERSONATION              = 0x40000,  
    STARTUP_TRIM_GC_COMMIT                        = 0x80000,  
  
    STARTUP_ETW                                   = 0x100000,  
    STARTUP_ARM                                   = 0x400000  
} STARTUP_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="4474d-107">Члены</span><span class="sxs-lookup"><span data-stu-id="4474d-107">Members</span></span>  
  
|<span data-ttu-id="4474d-108">Член</span><span class="sxs-lookup"><span data-stu-id="4474d-108">Member</span></span>|<span data-ttu-id="4474d-109">Описание</span><span class="sxs-lookup"><span data-stu-id="4474d-109">Description</span></span>|  
|------------|-----------------|  
|`STARTUP_CONCURRENT_GC`|<span data-ttu-id="4474d-110">Указывает, что следует использовать параллельную сборку мусора.</span><span class="sxs-lookup"><span data-stu-id="4474d-110">Specifies that concurrent garbage collection should be used.</span></span> <span data-ttu-id="4474d-111">Если вызывающий объект запрашивает сборку сервера и параллельную сборку мусора на однопроцессорном компьютере, то выполняется сборка рабочей станции и непараллельная сборка мусора.</span><span class="sxs-lookup"><span data-stu-id="4474d-111">If the caller asks for the server build and concurrent garbage collection on a single-processor machine, the workstation build and non-concurrent garbage collection are run instead.</span></span> <span data-ttu-id="4474d-112">**Примечание.**  Параллельная сборка мусора не поддерживается в приложениях, работающих под управлением эмулятора x86 WOW64 в 64-разрядных системах, которые реализуют архитектуру Intel Itanium (прежнее название — IA-64).</span><span class="sxs-lookup"><span data-stu-id="4474d-112">**Note:**  Concurrent garbage collection is not supported in applications that are running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="4474d-113">Дополнительные сведения об использовании WOW64 в 64-разрядных системах Windows см. в разделе [выполнение 32-разрядных приложений](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="4474d-113">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|<span data-ttu-id="4474d-114">Указывает, что должна выполняться оптимизация загрузчика.</span><span class="sxs-lookup"><span data-stu-id="4474d-114">Specifies that loader optimization shall occur.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|<span data-ttu-id="4474d-115">Указывает, что ни одна сборка не загружается как нейтральная к домену.</span><span class="sxs-lookup"><span data-stu-id="4474d-115">Specifies that no assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|<span data-ttu-id="4474d-116">Указывает, что все сборки загружаются как нейтральные к домену.</span><span class="sxs-lookup"><span data-stu-id="4474d-116">Specifies that all assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|<span data-ttu-id="4474d-117">Указывает, что все сборки со строгими именами загружаются как нейтральные к домену.</span><span class="sxs-lookup"><span data-stu-id="4474d-117">Specifies that all strong-named assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_SAFEMODE`|<span data-ttu-id="4474d-118">Указывает, что политика версий среды CLR не будет применена к переданной версии.</span><span class="sxs-lookup"><span data-stu-id="4474d-118">Specifies that CLR version policy will not be applied to the version passed in.</span></span> <span data-ttu-id="4474d-119">Будет загружена точная версия, указанная для CLR.</span><span class="sxs-lookup"><span data-stu-id="4474d-119">The exact version specified of the CLR will be loaded.</span></span> <span data-ttu-id="4474d-120">Оболочка совместимости не выполняет оценку политики для определения последней совместимой версии.</span><span class="sxs-lookup"><span data-stu-id="4474d-120">The shim does not evaluate policy to determine the latest compatible version.</span></span>|  
|`STARTUP_LOADER_SETPREFERENCE`|<span data-ttu-id="4474d-121">Указывает, что предпочтительная среда выполнения будет установлена, но фактически не запущена.</span><span class="sxs-lookup"><span data-stu-id="4474d-121">Specifies that the preferred runtime will be set, but not actually started.</span></span>|  
|`STARTUP_SERVER_GC`|<span data-ttu-id="4474d-122">Указывает, что будет использоваться сборка мусора сервера.</span><span class="sxs-lookup"><span data-stu-id="4474d-122">Specifies that the server garbage collection will be used.</span></span>|  
|`STARTUP_HOARD_GC_VM`|<span data-ttu-id="4474d-123">Указывает, что виртуальный адрес будет использоваться при сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="4474d-123">Specifies that garbage collection will keep the virtual address used.</span></span>|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|<span data-ttu-id="4474d-124">Указывает, что смешивание интерфейса размещения не будет разрешено.</span><span class="sxs-lookup"><span data-stu-id="4474d-124">Specifies that mixing a hosting interface will not be allowed.</span></span>|  
|`STARTUP_LEGACY_IMPERSONATION`|<span data-ttu-id="4474d-125">Указывает, что олицетворение не должно проходить через асинхронные точки по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="4474d-125">Specifies that impersonation should not flow across asynchronous points by default.</span></span>|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|<span data-ttu-id="4474d-126">Указывает, что весь стек потоков не должен зафиксироваться при запуске потока.</span><span class="sxs-lookup"><span data-stu-id="4474d-126">Specifies that the full thread stack should not be committed when the thread starts running.</span></span>|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|<span data-ttu-id="4474d-127">Указывает, что управляемые олицетворения и олицетворения, полученные через вызов неуправляемого кода, будут передаваться через асинхронные точки.</span><span class="sxs-lookup"><span data-stu-id="4474d-127">Specifies that managed impersonations and impersonations achieved through platform invoke will flow across asynchronous points.</span></span> <span data-ttu-id="4474d-128">По умолчанию только управляемые олицетворения будут проходить через асинхронные точки.</span><span class="sxs-lookup"><span data-stu-id="4474d-128">By default, only managed impersonations will flow across asynchronous points.</span></span>|  
|`STARTUP_TRIM_GC_COMMIT`|<span data-ttu-id="4474d-129">Указывает, что при нехватке системной памяти сборка мусора будет использовать меньше зафиксированного пространства.</span><span class="sxs-lookup"><span data-stu-id="4474d-129">Specifies that garbage collection will use less committed space when system memory is low.</span></span> <span data-ttu-id="4474d-130">См `gcTrimCommitOnLowMemory` . раздел [Оптимизация для размещения общих веб-](../../../standard/garbage-collection/optimization-for-shared-web-hosting.md)сайтов.</span><span class="sxs-lookup"><span data-stu-id="4474d-130">See `gcTrimCommitOnLowMemory` in [Optimization for Shared Web Hosting](../../../standard/garbage-collection/optimization-for-shared-web-hosting.md).</span></span>|  
|`STARTUP_ETW`|<span data-ttu-id="4474d-131">Указывает, что трассировка событий для Windows (ETW) включена для событий общеязыковой среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="4474d-131">Specifies that event tracing for Windows (ETW) is enabled for common language runtime events.</span></span> <span data-ttu-id="4474d-132">Начиная с Windows Vista, трассировка событий всегда включена, поэтому этот флаг не действует.</span><span class="sxs-lookup"><span data-stu-id="4474d-132">Beginning with Windows Vista, event tracing is always enabled, so this flag has no effect.</span></span> <span data-ttu-id="4474d-133">См. раздел [Управление ведением журнала платформа .NET Framework](../../performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="4474d-133">See [Controlling .NET Framework Logging](../../performance/controlling-logging.md).</span></span>|  
|`STARTUP_ARM`|<span data-ttu-id="4474d-134">Указывает, что отслеживание ресурсов домена приложения включено.</span><span class="sxs-lookup"><span data-stu-id="4474d-134">Specifies that application domain resource monitoring is enabled.</span></span> <span data-ttu-id="4474d-135">См <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> . свойство и [ \<appDomainResourceMonitoring> элемент](../../configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).</span><span class="sxs-lookup"><span data-stu-id="4474d-135">See the <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> property and [\<appDomainResourceMonitoring> Element](../../configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4474d-136">Требования</span><span class="sxs-lookup"><span data-stu-id="4474d-136">Requirements</span></span>  

 <span data-ttu-id="4474d-137">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4474d-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4474d-138">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4474d-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4474d-139">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4474d-139">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4474d-140">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4474d-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4474d-141">См. также</span><span class="sxs-lookup"><span data-stu-id="4474d-141">See also</span></span>

- [<span data-ttu-id="4474d-142">Размещение перечислений</span><span class="sxs-lookup"><span data-stu-id="4474d-142">Hosting Enumerations</span></span>](hosting-enumerations.md)
