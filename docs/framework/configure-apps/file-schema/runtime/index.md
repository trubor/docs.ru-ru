---
description: 'Подробнее: схема параметров времени выполнения'
title: Схема параметров среды выполнения
ms.date: 03/30/2017
helpviewer_keywords:
- schema runtime settings
- configuration schema [.NET Framework], runtime settings
- runtime settings schema
ms.assetid: f04816ab-110d-4e28-9283-845d6d9a4a68
ms.openlocfilehash: ee9c209866eb8c505130327d78a18482f5a282e5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726134"
---
# <a name="run-time-settings-schema"></a><span data-ttu-id="a0ded-103">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="a0ded-103">Run-time settings schema</span></span>

<span data-ttu-id="a0ded-104">Параметры времени выполнения используются средой CLR для настройки приложений, предназначенных для платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a0ded-104">Run-time settings are used by the common language runtime to configure applications that target the .NET Framework.</span></span>

## <a name="the-runtime-section-and-its-parent-and-child-elements"></a><span data-ttu-id="a0ded-105">\<runtime>Раздел и его родительские и дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="a0ded-105">The \<runtime> section and its parent and child elements</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<alwaysFlowImpersonationPolicy>](alwaysflowimpersonationpolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<AppContextSwitchOverrides>](appcontextswitchoverrides-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<appDomainManagerType>](appdomainmanagertype-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<appDomainResourceMonitoring>](appdomainresourcemonitoring-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<assemblyBinding>](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<dependentAssembly>](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<assemblyIdentity>](assemblyidentity-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<bindingRedirect>](bindingredirect-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<codeBase>](codebase-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<publisherPolicy>](publisherpolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<probing>](probing-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<qualifyAssembly>](qualifyassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<supportPortability>](supportportability-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<bypassTrustedAppStrongNames>](bypasstrustedappstrongnames-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<CompatSortNLSVersion>](compatsortnlsversion-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<developmentMode>](developmentmode-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<disableCachingBindingFailures>](disablecachingbindingfailures-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<disableCommitThreadStack>](disablecommitthreadstack-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<disableFusionUpdatesFromADManager>](disablefusionupdatesfromadmanager-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<EnableAmPmParseAdjustment>](enableampmparseadjustment-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<enforceFIPSPolicy>](enforcefipspolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<etwEnable>](etwenable-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<forcePerformanceCounterUniqueSharedMemoryReads>](forceperformancecounteruniquesharedmemoryreads-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<gcAllowVeryLargeObjects>](gcallowverylargeobjects-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<gcConcurrent>](gcconcurrent-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<GCCpuGroup>](gccpugroup-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<GCHeapAffinitizeMask>](gcheapaffinitizemask-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<GCHeapCount>](gcheapcount-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<GCLOHThreshold>](gclohthreshold-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<GCNoAffinitize>](gcnoaffinitize-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<gcServer>](gcserver-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<generatePublisherEvidence>](generatepublisherevidence-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<legacyCorruptedStateExceptionsPolicy>](legacycorruptedstateexceptionspolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<legacyImpersonationPolicy>](legacyimpersonationpolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<loadfromRemoteSources>](loadfromremotesources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<NetFx40_LegacySecurityPolicy>](netfx40-legacysecuritypolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<NetFx40_PInvokeStackResilience>](netfx40-pinvokestackresilience-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](netfx45-cultureawarecomparergethashcode-longstrings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<PreferComInsteadOfManagedRemoting>](prefercominsteadofmanagedremoting-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<relativeBindForResources>](relativebindforresources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<shadowCopyVerifyByTimeStamp>](shadowcopyverifybytimestamp-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<ThrowUnobservedTaskExceptions>](throwunobservedtaskexceptions-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<TimeSpan_LegacyFormatMode>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<useLegacyJit>](uselegacyjit-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<UseRandomizedStringHashAlgorithm>](userandomizedstringhashalgorithm-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<UseSmallInternalThreadStacks>](usesmallinternalthreadstacks-element.md)\
&nbsp;&nbsp;[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<memoryCache>](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<namedCaches>](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<add>](add-element-for-namedcaches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<clear>](clear-element-for-namedcaches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<remove>](remove-element-for-namedcaches.md)

## <a name="alphabetical-list-of-runtime-elements"></a><span data-ttu-id="a0ded-106">Алфавитный список \<runtime> элементов</span><span class="sxs-lookup"><span data-stu-id="a0ded-106">Alphabetical list of \<runtime> elements</span></span>

|<span data-ttu-id="a0ded-107">Элемент</span><span class="sxs-lookup"><span data-stu-id="a0ded-107">Element</span></span>|<span data-ttu-id="a0ded-108">Описание</span><span class="sxs-lookup"><span data-stu-id="a0ded-108">Description</span></span>|
|-------------|-----------------|
|[\<add>](add-element-for-namedcaches.md)|<span data-ttu-id="a0ded-109">Добавляет именованный кэш к коллекции `namedCaches` для кэша памяти.</span><span class="sxs-lookup"><span data-stu-id="a0ded-109">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|
|[\<alwaysFlowImpersonationPolicy>](alwaysflowimpersonationpolicy-element.md)|<span data-ttu-id="a0ded-110">Указывает, что удостоверение Windows всегда проходит через асинхронные точки, независимо от того, как было выполнено олицетворение.</span><span class="sxs-lookup"><span data-stu-id="a0ded-110">Specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>|
|[\<AppContextSwitchOverrides>](appcontextswitchoverrides-element.md)|<span data-ttu-id="a0ded-111">Определяет один или несколько коммутаторов, используемых классом <xref:System.AppContext> для предоставления механизма отказа от новых функциональных возможностей.</span><span class="sxs-lookup"><span data-stu-id="a0ded-111">Defines one or more switches used by the <xref:System.AppContext> class to provide an opt-out mechanism for new functionality.</span></span>|
|[\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md)|<span data-ttu-id="a0ded-112">Указывает сборку, предоставляющую диспетчер домена приложения для домена приложения, по умолчанию используемого в процессе.</span><span class="sxs-lookup"><span data-stu-id="a0ded-112">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>|
|[\<appDomainManagerType>](appdomainmanagertype-element.md)|<span data-ttu-id="a0ded-113">Указывает тип, который служит диспетчером домена приложения для домена приложения, используемого по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="a0ded-113">Specifies the type that serves as the application domain manager for the default application domain.</span></span>|
|[\<appDomainResourceMonitoring>](appdomainresourcemonitoring-element.md)|<span data-ttu-id="a0ded-114">Указывает среде собирать статистику для всех доменов приложений в процессе за весь период его существования.</span><span class="sxs-lookup"><span data-stu-id="a0ded-114">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>|
|[\<assemblyBinding>](assemblybinding-element-for-runtime.md)|<span data-ttu-id="a0ded-115">Содержит сведения о перенаправлении версии сборки и о расположениях сборок.</span><span class="sxs-lookup"><span data-stu-id="a0ded-115">Contains information about assembly version redirection and the locations of assemblies.</span></span>|
|[\<assemblyIdentity>](assemblyidentity-element-for-runtime.md)|<span data-ttu-id="a0ded-116">Содержит идентификационные сведения о сборке.</span><span class="sxs-lookup"><span data-stu-id="a0ded-116">Contains identifying information about an assembly.</span></span>|
|[\<bindingRedirect>](bindingredirect-element.md)|<span data-ttu-id="a0ded-117">Перенаправляет одну версию сборки на другую.</span><span class="sxs-lookup"><span data-stu-id="a0ded-117">Redirects one assembly version to another.</span></span>|
|[\<bypassTrustedAppStrongNames>](bypasstrustedappstrongnames-element.md)|<span data-ttu-id="a0ded-118">Указывает, следует ли обходить проверку строгих имен для доверенных сборок.</span><span class="sxs-lookup"><span data-stu-id="a0ded-118">Specifies whether strong name verification for trusted assemblies should be bypassed.</span></span>|
|[\<clear>](clear-element-for-namedcaches.md)|<span data-ttu-id="a0ded-119">Очищает коллекцию `namedCaches` для кэша памяти.</span><span class="sxs-lookup"><span data-stu-id="a0ded-119">Clears the `namedCaches` collection for a memory cache.</span></span>|
|[\<codeBase>](codebase-element.md)|<span data-ttu-id="a0ded-120">Указывает, где среда выполнения может найти сборку.</span><span class="sxs-lookup"><span data-stu-id="a0ded-120">Specifies where the runtime can find an assembly.</span></span>|
|[\<CompatSortNLSVersion>](compatsortnlsversion-element.md)|<span data-ttu-id="a0ded-121">Указывает, что при операциях сравнения строк среда выполнения должна использовать устаревший режим сортировки.</span><span class="sxs-lookup"><span data-stu-id="a0ded-121">Specifies that the runtime should use legacy sorting behavior when performing string comparisons</span></span>|
|[\<dependentAssembly>](dependentassembly-element.md)|<span data-ttu-id="a0ded-122">Инкапсулирует политику привязки и расположение каждой сборки.</span><span class="sxs-lookup"><span data-stu-id="a0ded-122">Encapsulates binding policy and assembly location for each assembly.</span></span>|
|[\<developmentMode>](developmentmode-element.md)|<span data-ttu-id="a0ded-123">Указывает, выполняет ли среда поиск сборок в каталогах, указанных в переменной среды DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="a0ded-123">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|
|[\<disableCachingBindingFailures>](disablecachingbindingfailures-element.md)|<span data-ttu-id="a0ded-124">Указывает, отключено ли кэширование ошибок привязки, что является поведением по умолчанию в платформа .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="a0ded-124">Specifies whether the caching of binding failures, which is the default behavior in the .NET Framework 2.0, is disabled.</span></span>|
|[\<disableCommitThreadStack>](disablecommitthreadstack-element.md)|<span data-ttu-id="a0ded-125">Указывает, фиксируется ли весь стек потоков при запуске потока.</span><span class="sxs-lookup"><span data-stu-id="a0ded-125">Specifies whether the full thread stack is committed when a thread starts.</span></span>|
|[\<disableFusionUpdatesFromADManager>](disablefusionupdatesfromadmanager-element.md)|<span data-ttu-id="a0ded-126">Указывает, отключено ли поведение по умолчанию, которое разрешает хост-приложению среды выполнения переопределять параметры конфигурации для домена приложения.</span><span class="sxs-lookup"><span data-stu-id="a0ded-126">Specifies whether the default behavior, which is to allow the runtime host to override configuration settings for an application domain, is disabled.</span></span>|
|[\<EnableAmPmParseAdjustment>](enableampmparseadjustment-element.md)|<span data-ttu-id="a0ded-127">Определяет, используют ли методы анализа даты и времени скорректированной набор правил для анализа строк даты, содержащих только день, месяц, час и указатель AM/PM.</span><span class="sxs-lookup"><span data-stu-id="a0ded-127">Determines whether date and time parsing methods use an adjusted set of rules to parse date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|
|[\<enforceFIPSPolicy>](enforcefipspolicy-element.md)|<span data-ttu-id="a0ded-128">Указывает, нужно ли принудительно обеспечивать соблюдение требования конфигурации компьютера о том, что криптографические алгоритмы должны соответствовать стандартам FIPS.</span><span class="sxs-lookup"><span data-stu-id="a0ded-128">Specifies whether to enforce a computer configuration requirement that cryptographic algorithms must comply with the Federal Information Processing Standards (FIPS).</span></span>|
|[\<etwEnable>](etwenable-element.md)|<span data-ttu-id="a0ded-129">Указывает, следует ли включить трассировку событий Windows для событий среды CLR.</span><span class="sxs-lookup"><span data-stu-id="a0ded-129">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>|
|[\<forcePerformanceCounterUniqueSharedMemoryReads>](forceperformancecounteruniquesharedmemoryreads-element.md)|<span data-ttu-id="a0ded-130">Указывает, использует ли файл PerfCounter.dll параметр реестра CategoryOptions в приложении .NET Framework версии 1.1, чтобы определить, следует ли загружать данные счетчиков производительности из общей памяти конкретной категории или глобальной памяти.</span><span class="sxs-lookup"><span data-stu-id="a0ded-130">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|
|[\<gcAllowVeryLargeObjects>](gcallowverylargeobjects-element.md)|<span data-ttu-id="a0ded-131">На 64 разрядных платформах позволяет использовать массивы, размер которых превышает 2 гигабайта (ГБ).</span><span class="sxs-lookup"><span data-stu-id="a0ded-131">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>|
|[\<gcConcurrent>](gcconcurrent-element.md)|<span data-ttu-id="a0ded-132">Указывает, выполняет ли среда выполнения сборку мусора параллельно.</span><span class="sxs-lookup"><span data-stu-id="a0ded-132">Specifies whether the runtime runs garbage collection concurrently.</span></span>|
|[\<GCCpuGroup>](gccpugroup-element.md)|<span data-ttu-id="a0ded-133">Определяет, поддерживает ли сборка мусора несколько групп ЦП.</span><span class="sxs-lookup"><span data-stu-id="a0ded-133">Specifies whether garbage collection supports multiple CPU groups.</span></span>|
|[\<GCHeapAffinitizeMask>](gcheapaffinitizemask-element.md)|<span data-ttu-id="a0ded-134">Определяет сходство между кучами сборщика мусора и отдельными процессорами.</span><span class="sxs-lookup"><span data-stu-id="a0ded-134">Defines the affinity between GC heaps and individual processors.</span></span>|
|[\<GCHeapCount>](gcheapcount-element.md)|<span data-ttu-id="a0ded-135">Указывает число куч/потоков, используемых для сборки мусора сервера.</span><span class="sxs-lookup"><span data-stu-id="a0ded-135">Specifies the number of heaps/threads to use for server garbage collection.</span></span>  |
|[\<GCLOHThreshold>](gclohthreshold-element.md)|<span data-ttu-id="a0ded-136">Указывает пороговый размер, который приводит к тому, что объекты попадают в кучу больших объектов (LOH).</span><span class="sxs-lookup"><span data-stu-id="a0ded-136">Specifies the threshold size that causes objects to go on the large object heap (LOH).</span></span>|
|[\<GCNoAffinitize>](gcnoaffinitize-element.md)|<span data-ttu-id="a0ded-137">Указывает, следует ли привязать потоки сервера GC с ЦП.</span><span class="sxs-lookup"><span data-stu-id="a0ded-137">Specifies whether or not to affinitize server GC threads with CPUs.</span></span>|
|[\<gcServer>](gcserver-element.md)|<span data-ttu-id="a0ded-138">Указывает, выполняет ли среда CLR сборку мусора сервера.</span><span class="sxs-lookup"><span data-stu-id="a0ded-138">Specifies whether the common language runtime runs server garbage collection.</span></span>|
|[\<generatePublisherEvidence>](generatepublisherevidence-element.md)|<span data-ttu-id="a0ded-139">Указывает, использует ли среда выполнения политику разграничения доступа кода, используемую издателем.</span><span class="sxs-lookup"><span data-stu-id="a0ded-139">Specifies whether the runtime uses code access security (CAS) publisher policy.</span></span>|
|[\<legacyCorruptedStateExceptionsPolicy>](legacycorruptedstateexceptionspolicy-element.md)|<span data-ttu-id="a0ded-140">Указывает, позволяет ли среда выполнения управляемому коду перехватывать нарушения прав доступа и другие исключения поврежденного состояния.</span><span class="sxs-lookup"><span data-stu-id="a0ded-140">Specifies whether the runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>|
|[\<legacyImpersonationPolicy>](legacyimpersonationpolicy-element.md)|<span data-ttu-id="a0ded-141">Указывает, что удостоверение Windows не проходит через асинхронные точки, независимо от параметров потока для контекста выполнения в текущем потоке.</span><span class="sxs-lookup"><span data-stu-id="a0ded-141">Specifies that the Windows identity does not flow across asynchronous points, regardless of the flow settings for the execution context on the current thread.</span></span>|
|[\<loadfromRemoteSources>](loadfromremotesources-element.md)|<span data-ttu-id="a0ded-142">Указывает, загружены ли сборки из удаленных источников как полностью доверенные.</span><span class="sxs-lookup"><span data-stu-id="a0ded-142">Specifies whether assemblies from remote sources are loaded as full trust.</span></span>|
|[\<memoryCache>](memorycache-element-cache-settings.md)|<span data-ttu-id="a0ded-143">Определяет элемент, используемый для настройки кэша, который основан на классе <xref:System.Runtime.Caching.MemoryCache> .</span><span class="sxs-lookup"><span data-stu-id="a0ded-143">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="a0ded-144">Содержит коллекцию параметров конфигурации для экземпляра `namedCache` .</span><span class="sxs-lookup"><span data-stu-id="a0ded-144">Contains a collection of configuration settings for the `namedCache` instance.</span></span>|
|[\<NetFx40_LegacySecurityPolicy>](netfx40-legacysecuritypolicy-element.md)|<span data-ttu-id="a0ded-145">Указывает, использует ли среда выполнения устаревшую политику разграничения доступа кода.</span><span class="sxs-lookup"><span data-stu-id="a0ded-145">Specifies whether the runtime uses legacy code access security (CAS) policy.</span></span>|
|[\<NetFx40_PInvokeStackResilience>](netfx40-pinvokestackresilience-element.md)|<span data-ttu-id="a0ded-146">Указывает, исправляет ли автоматически среда выполнения неправильные объявления вызова неуправляемого кода во время выполнения за счет скорости перехода между управляемыми и неуправляемым кодом.</span><span class="sxs-lookup"><span data-stu-id="a0ded-146">Specifies whether the runtime automatically fixes incorrect platform invoke declarations at run time, at the cost of slower transitions between managed and unmanaged code.</span></span>|
|[\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](netfx45-cultureawarecomparergethashcode-longstrings-element.md)|<span data-ttu-id="a0ded-147">Определяет, использует ли среда выполнения постоянный объем памяти для вычисления хэш-кодов методом <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="a0ded-147">Specifies whether the runtime uses a fixed amount of memory to calculate hash codes for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method.</span></span>|
|[\<PreferComInsteadOfManagedRemoting>](prefercominsteadofmanagedremoting-element.md)|<span data-ttu-id="a0ded-148">Указывает, что среда выполнения должна использовать COM-взаимодействие вместо удаленного взаимодействия через границы домена приложения.</span><span class="sxs-lookup"><span data-stu-id="a0ded-148">Specifies that the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|
|[\<probing>](probing-element.md)|<span data-ttu-id="a0ded-149">Задает вложенные папки, в которых среда выполняет поиск при загрузке сборок.</span><span class="sxs-lookup"><span data-stu-id="a0ded-149">Specifies subdirectories that the runtime searches when loading assemblies.</span></span>|
|[\<publisherPolicy>](publisherpolicy-element.md)|<span data-ttu-id="a0ded-150">Указывает, применяет ли среда выполнения политику издателя.</span><span class="sxs-lookup"><span data-stu-id="a0ded-150">Specifies whether the runtime applies publisher policy.</span></span>|
|[\<qualifyAssembly>](qualifyassembly-element.md)|<span data-ttu-id="a0ded-151">Задает полное имя сборки, которая должна загружаться динамически в случае использования неполного имени.</span><span class="sxs-lookup"><span data-stu-id="a0ded-151">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>|
|[\<relativeBindForResources>](relativebindforresources-element.md)|<span data-ttu-id="a0ded-152">Оптимизирует поиск вспомогательных сборок.</span><span class="sxs-lookup"><span data-stu-id="a0ded-152">Optimizes the probe for satellite assemblies.</span></span>|
|[\<remove>](remove-element-for-namedcaches.md)|<span data-ttu-id="a0ded-153">Удаляет элемент именованного кэша из коллекции `namedCaches` для кэша памяти.</span><span class="sxs-lookup"><span data-stu-id="a0ded-153">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|
|[\<runtime>](runtime-element.md)|<span data-ttu-id="a0ded-154">Содержит сведения о привязке сборок и поведении при сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="a0ded-154">Contains information about assembly binding and the behavior of garbage collection.</span></span>|
|[\<shadowCopyTimeStampVerification>](shadowcopyverifybytimestamp-element.md)|<span data-ttu-id="a0ded-155">Указывает, использует ли теневое копирование поведение при запуске по умолчанию, представленное в платформа .NET Framework 4, или возвращается к поведению при запуске более ранних версий платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a0ded-155">Specifies whether shadow copying uses the default startup behavior introduced in the .NET Framework 4, or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>|
|[\<supportPortability>](supportportability-element.md)|<span data-ttu-id="a0ded-156">Указывает, что приложение может ссылаться на ту же сборку в двух различных реализациях .NET Framework, отключая поведение по умолчанию, которое рассматривает сборки как эквивалент для переносимости приложения.</span><span class="sxs-lookup"><span data-stu-id="a0ded-156">Specifies that an application can reference the same assembly in two different implementations of the .NET Framework, by disabling the default behavior that treats the assemblies as equivalent for application portability purposes.</span></span>|
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="a0ded-157">Указывает сведения о конфигурации кэша объектов в памяти, используемого по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="a0ded-157">Provides configuration information for the default in-memory object cache.</span></span>|
|[\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md)|<span data-ttu-id="a0ded-158">Указывает, распределяет ли среда выполнения управляемые потоки во всех группах ЦП.</span><span class="sxs-lookup"><span data-stu-id="a0ded-158">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|
|[\<ThrowUnobservedTaskExceptions>](throwunobservedtaskexceptions-element.md)|<span data-ttu-id="a0ded-159">Определяет, будут ли необработанные исключения задачи завершать выполняющийся процесс.</span><span class="sxs-lookup"><span data-stu-id="a0ded-159">Specifies whether unhandled task exceptions should terminate a running process.</span></span>|
|[\<TimeSpan_LegacyFormatMode>](runtime-element.md)|<span data-ttu-id="a0ded-160">Указывает, использует ли среда выполнения устаревшее форматирование для значений <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="a0ded-160">Specifies whether the runtime uses legacy formatting for <xref:System.TimeSpan> values.</span></span>|
|[\<useLegacyJit>](uselegacyjit-element.md)|<span data-ttu-id="a0ded-161">Определяет, использует ли среда CLR устаревший 64-разрядный JIT-компилятор для JIT-компиляции.</span><span class="sxs-lookup"><span data-stu-id="a0ded-161">Determines whether the common language runtime uses the legacy 64-bit JIT compiler for just-in-time compilation.</span></span>|
|[\<UseRandomizedStringHashAlgorithm>](userandomizedstringhashalgorithm-element.md)|<span data-ttu-id="a0ded-162">Указывает, вычисляет ли среда выполнения хэш-коды для строк для каждого домена приложения.</span><span class="sxs-lookup"><span data-stu-id="a0ded-162">Specifies whether the runtime calculates hash codes for strings on a per application domain basis.</span></span>|
|[\<UseSmallInternalThreadStacks>](usesmallinternalthreadstacks-element.md)|<span data-ttu-id="a0ded-163">Запрашивает использование средой выполнения явных размеров стека при создании определенных потоков, используемых для внутренних целей, вместо размер стека по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="a0ded-163">Requests that the runtime use explicit stack sizes when it creates certain threads that it uses internally, instead of the default stack size.</span></span>|

## <a name="see-also"></a><span data-ttu-id="a0ded-164">См. также</span><span class="sxs-lookup"><span data-stu-id="a0ded-164">See also</span></span>

- [<span data-ttu-id="a0ded-165">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="a0ded-165">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a0ded-166">Отключение параллельной сборки мусора</span><span class="sxs-lookup"><span data-stu-id="a0ded-166">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="a0ded-167">Перенаправление версий сборки</span><span class="sxs-lookup"><span data-stu-id="a0ded-167">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
