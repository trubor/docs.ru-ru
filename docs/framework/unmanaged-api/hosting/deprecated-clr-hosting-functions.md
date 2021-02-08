---
description: 'Дополнительные сведения: устаревшие функции размещения CLR'
title: Устаревшие функции размещения CLR
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
ms.openlocfilehash: 3d16b5829e29c5c963f4790bbb3be7adcaeedbfc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785670"
---
# <a name="deprecated-clr-hosting-functions"></a><span data-ttu-id="44701-103">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="44701-103">Deprecated CLR Hosting Functions</span></span>

<span data-ttu-id="44701-104">В этом разделе описаны неуправляемые глобальные статические функции, которые использовались в предыдущих версиях API размещения.</span><span class="sxs-lookup"><span data-stu-id="44701-104">This section describes the unmanaged global static functions that earlier versions of the hosting API used.</span></span>  
  
 <span data-ttu-id="44701-105">За исключением функций инфраструктуры ( `_Cor*` функций), которые используются только платформа .NET Framework, эти функции являются устаревшими в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="44701-105">With the exception of the infrastructure functions (`_Cor*` functions), which are used only by the .NET Framework, these functions have been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="activation-functions"></a><span data-ttu-id="44701-106">Функции активации</span><span class="sxs-lookup"><span data-stu-id="44701-106">Activation functions</span></span>  

 [<span data-ttu-id="44701-107">Функция ClrCreateManagedInstance</span><span class="sxs-lookup"><span data-stu-id="44701-107">ClrCreateManagedInstance Function</span></span>](clrcreatemanagedinstance-function.md)  
 <span data-ttu-id="44701-108">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-108">Deprecated.</span></span> <span data-ttu-id="44701-109">Создает экземпляр указанного управляемого типа.</span><span class="sxs-lookup"><span data-stu-id="44701-109">Creates an instance of the specified managed type.</span></span>  
  
 [<span data-ttu-id="44701-110">Функция CoInitializeCor</span><span class="sxs-lookup"><span data-stu-id="44701-110">CoInitializeCor Function</span></span>](coinitializecor-function.md)  
 <span data-ttu-id="44701-111">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="44701-111">Obsolete.</span></span> <span data-ttu-id="44701-112">Чтобы инициализировать среду CLR, используйте либо [CorBindToRuntimeEx](corbindtoruntimeex-function.md) , либо [корбиндтокуррентрунтиме](corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="44701-112">To initialize the common language runtime (CLR), use either [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span>  
  
 [<span data-ttu-id="44701-113">Функция CoInitializeEE</span><span class="sxs-lookup"><span data-stu-id="44701-113">CoInitializeEE Function</span></span>](coinitializeee-function.md)  
 <span data-ttu-id="44701-114">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-114">Deprecated.</span></span> <span data-ttu-id="44701-115">Гарантирует, что подсистема выполнения среды CLR загружается в процесс.</span><span class="sxs-lookup"><span data-stu-id="44701-115">Ensures that the CLR execution engine is loaded into a process.</span></span> <span data-ttu-id="44701-116">Используйте вместо этого метод [ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md) .</span><span class="sxs-lookup"><span data-stu-id="44701-116">Use the [ICLRRuntimeHost::Start](iclrruntimehost-start-method.md) method instead.</span></span>  
  
 [<span data-ttu-id="44701-117">Функция CorBindToCurrentRuntime</span><span class="sxs-lookup"><span data-stu-id="44701-117">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)  
 <span data-ttu-id="44701-118">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-118">Deprecated.</span></span> <span data-ttu-id="44701-119">Загружает среду CLR в процесс с использованием сведений о версии, хранящихся в XML-файле.</span><span class="sxs-lookup"><span data-stu-id="44701-119">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span>  
  
 [<span data-ttu-id="44701-120">Функция CorBindToRuntime</span><span class="sxs-lookup"><span data-stu-id="44701-120">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)  
 <span data-ttu-id="44701-121">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-121">Deprecated.</span></span> <span data-ttu-id="44701-122">Позволяет неуправляемым узлам загружать среду CLR в процесс.</span><span class="sxs-lookup"><span data-stu-id="44701-122">Enables unmanaged hosts to load the CLR into a process.</span></span>  
  
 [<span data-ttu-id="44701-123">Функция CorBindToRuntimeByCfg</span><span class="sxs-lookup"><span data-stu-id="44701-123">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)  
 <span data-ttu-id="44701-124">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-124">Deprecated.</span></span> <span data-ttu-id="44701-125">Загружает среду CLR в процесс с использованием сведений о версии, считываемых из XML-файла.</span><span class="sxs-lookup"><span data-stu-id="44701-125">Loads the CLR into a process by using version information that is read from an XML file.</span></span>  
  
 [<span data-ttu-id="44701-126">Функция CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="44701-126">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)  
 <span data-ttu-id="44701-127">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-127">Deprecated.</span></span> <span data-ttu-id="44701-128">Позволяет неуправляемым узлам загружать среду CLR в процесс и устанавливать флаги для указания поведения среды CLR.</span><span class="sxs-lookup"><span data-stu-id="44701-128">Enables unmanaged hosts to load the CLR into a process, and allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 [<span data-ttu-id="44701-129">Функция CorBindToRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="44701-129">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)  
 <span data-ttu-id="44701-130">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-130">Deprecated.</span></span> <span data-ttu-id="44701-131">Позволяет узлам загружать указанную версию среды CLR в процесс.</span><span class="sxs-lookup"><span data-stu-id="44701-131">Enables hosts to load a specified version of the CLR into a process.</span></span>  
  
 [<span data-ttu-id="44701-132">Функция GetCORRequiredVersion</span><span class="sxs-lookup"><span data-stu-id="44701-132">GetCORRequiredVersion Function</span></span>](getcorrequiredversion-function.md)  
 <span data-ttu-id="44701-133">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-133">Deprecated.</span></span> <span data-ttu-id="44701-134">Возвращает требуемый номер версии среды CLR.</span><span class="sxs-lookup"><span data-stu-id="44701-134">Gets the required CLR version number.</span></span>  
  
 [<span data-ttu-id="44701-135">Функция GetCORSystemDirectory</span><span class="sxs-lookup"><span data-stu-id="44701-135">GetCORSystemDirectory Function</span></span>](getcorsystemdirectory-function.md)  
 <span data-ttu-id="44701-136">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-136">Deprecated.</span></span> <span data-ttu-id="44701-137">Возвращает каталог установки CLR, который загружается в процесс.</span><span class="sxs-lookup"><span data-stu-id="44701-137">Returns the installation directory of the CLR that is loaded into the process.</span></span>  
  
 [<span data-ttu-id="44701-138">Функция GetRealProcAddress</span><span class="sxs-lookup"><span data-stu-id="44701-138">GetRealProcAddress Function</span></span>](getrealprocaddress-function.md)  
 <span data-ttu-id="44701-139">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-139">Deprecated.</span></span> <span data-ttu-id="44701-140">Возвращает адрес указанной функции, которая экспортируется из последней установленной версии среды CLR.</span><span class="sxs-lookup"><span data-stu-id="44701-140">Gets the address of the specified function that is exported from the latest installed version of the CLR.</span></span>  
  
 [<span data-ttu-id="44701-141">Функция GetRequestedRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="44701-141">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)  
 <span data-ttu-id="44701-142">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-142">Deprecated.</span></span> <span data-ttu-id="44701-143">Возвращает сведения о версии и каталоге о среде CLR, запрошенной приложением.</span><span class="sxs-lookup"><span data-stu-id="44701-143">Gets version and directory information about the CLR requested by an application.</span></span>  
  
## <a name="clr-version-functions"></a><span data-ttu-id="44701-144">Функции версий среды CLR</span><span class="sxs-lookup"><span data-stu-id="44701-144">CLR version functions</span></span>  

 <span data-ttu-id="44701-145">Функции в этом разделе возвращают версию среды CLR. они не активируют среду CLR.</span><span class="sxs-lookup"><span data-stu-id="44701-145">The functions in this section return a CLR version; they do not activate the CLR.</span></span>  
  
 [<span data-ttu-id="44701-146">Функция GetCORVersion</span><span class="sxs-lookup"><span data-stu-id="44701-146">GetCORVersion Function</span></span>](getcorversion-function.md)  
 <span data-ttu-id="44701-147">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-147">Deprecated.</span></span> <span data-ttu-id="44701-148">Возвращает номер версии среды CLR, которая выполняется в текущем процессе.</span><span class="sxs-lookup"><span data-stu-id="44701-148">Returns the version number of the CLR that is running in the current process.</span></span>  
  
 [<span data-ttu-id="44701-149">Функция GetFileVersion</span><span class="sxs-lookup"><span data-stu-id="44701-149">GetFileVersion Function</span></span>](getfileversion-function.md)  
 <span data-ttu-id="44701-150">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-150">Deprecated.</span></span> <span data-ttu-id="44701-151">Возвращает сведения о версии среды CLR указанного файла, используя указанный буфер.</span><span class="sxs-lookup"><span data-stu-id="44701-151">Gets the CLR version information of the specified file, using the specified buffer.</span></span>  
  
 [<span data-ttu-id="44701-152">Функция GetRequestedRuntimeVersion</span><span class="sxs-lookup"><span data-stu-id="44701-152">GetRequestedRuntimeVersion Function</span></span>](getrequestedruntimeversion-function.md)  
 <span data-ttu-id="44701-153">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-153">Deprecated.</span></span> <span data-ttu-id="44701-154">Возвращает номер версии среды CLR, запрошенной указанным приложением.</span><span class="sxs-lookup"><span data-stu-id="44701-154">Gets the version number of the CLR requested by the specified application.</span></span> <span data-ttu-id="44701-155">Если эта версия не установлена, возвращает последнюю версию, установленную до запрошенной версии.</span><span class="sxs-lookup"><span data-stu-id="44701-155">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 [<span data-ttu-id="44701-156">Функция GetRequestedRuntimeVersionForCLSID</span><span class="sxs-lookup"><span data-stu-id="44701-156">GetRequestedRuntimeVersionForCLSID Function</span></span>](getrequestedruntimeversionforclsid-function.md)  
 <span data-ttu-id="44701-157">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-157">Deprecated.</span></span> <span data-ttu-id="44701-158">Возвращает соответствующую информацию о версии среды CLR для класса с указанным идентификатором CLSID.</span><span class="sxs-lookup"><span data-stu-id="44701-158">Gets the appropriate CLR version information for the class with the specified CLSID.</span></span>  
  
 [<span data-ttu-id="44701-159">Функция GetVersionFromProcess</span><span class="sxs-lookup"><span data-stu-id="44701-159">GetVersionFromProcess Function</span></span>](getversionfromprocess-function.md)  
 <span data-ttu-id="44701-160">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-160">Deprecated.</span></span> <span data-ttu-id="44701-161">Возвращает номер версии среды CLR, связанной с указанным обработчиком процесса.</span><span class="sxs-lookup"><span data-stu-id="44701-161">Gets the version number of the CLR that is associated with the specified process handle.</span></span>  
  
 [<span data-ttu-id="44701-162">Функция LockClrVersion</span><span class="sxs-lookup"><span data-stu-id="44701-162">LockClrVersion Function</span></span>](lockclrversion-function.md)  
 <span data-ttu-id="44701-163">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-163">Deprecated.</span></span> <span data-ttu-id="44701-164">Позволяет узлу определить версию среды CLR, которая будет использоваться в процессе перед явной инициализацией среды CLR.</span><span class="sxs-lookup"><span data-stu-id="44701-164">Allows the host to determine which version of the CLR will be used within the process before explicitly initializing the CLR.</span></span>  
  
## <a name="hosting-functions"></a><span data-ttu-id="44701-165">Функции размещения</span><span class="sxs-lookup"><span data-stu-id="44701-165">Hosting functions</span></span>  

 [<span data-ttu-id="44701-166">Функция CallFunctionShim</span><span class="sxs-lookup"><span data-stu-id="44701-166">CallFunctionShim Function</span></span>](callfunctionshim-function.md)  
 <span data-ttu-id="44701-167">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-167">Deprecated.</span></span> <span data-ttu-id="44701-168">Вызывает функцию с указанным именем и параметрами в указанной библиотеке.</span><span class="sxs-lookup"><span data-stu-id="44701-168">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 [<span data-ttu-id="44701-169">Функция CoEEShutDownCOM</span><span class="sxs-lookup"><span data-stu-id="44701-169">CoEEShutDownCOM Function</span></span>](coeeshutdowncom-function.md)  
 <span data-ttu-id="44701-170">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-170">Deprecated.</span></span> <span data-ttu-id="44701-171">Выгружает сборку COM из процесса.</span><span class="sxs-lookup"><span data-stu-id="44701-171">Unloads a COM assembly from the process.</span></span>  
  
 [<span data-ttu-id="44701-172">Функция CorExitProcess</span><span class="sxs-lookup"><span data-stu-id="44701-172">CorExitProcess Function</span></span>](corexitprocess-function.md)  
 <span data-ttu-id="44701-173">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-173">Deprecated.</span></span> <span data-ttu-id="44701-174">Завершает текущий неуправляемый процесс.</span><span class="sxs-lookup"><span data-stu-id="44701-174">Shuts down the current unmanaged process.</span></span>  
  
 [<span data-ttu-id="44701-175">Функция CorLaunchApplication</span><span class="sxs-lookup"><span data-stu-id="44701-175">CorLaunchApplication Function</span></span>](corlaunchapplication-function.md)  
 <span data-ttu-id="44701-176">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-176">Deprecated.</span></span> <span data-ttu-id="44701-177">Запускает приложение по указанному сетевому пути, используя указанные манифесты и другие данные приложения.</span><span class="sxs-lookup"><span data-stu-id="44701-177">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 [<span data-ttu-id="44701-178">Функция CorMarkThreadInThreadPool</span><span class="sxs-lookup"><span data-stu-id="44701-178">CorMarkThreadInThreadPool Function</span></span>](cormarkthreadinthreadpool-function.md)  
 <span data-ttu-id="44701-179">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-179">Deprecated.</span></span> <span data-ttu-id="44701-180">Помечает выполняющийся в данный момент поток пула потоков для выполнения управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="44701-180">Marks the currently executing thread-pool thread for the execution of managed code.</span></span> <span data-ttu-id="44701-181">Начиная с версии платформа .NET Framework 2,0 эта функция не действует.</span><span class="sxs-lookup"><span data-stu-id="44701-181">Starting with the .NET Framework version 2.0, this function has no effect.</span></span> <span data-ttu-id="44701-182">Он не является обязательным и может быть удален из кода.</span><span class="sxs-lookup"><span data-stu-id="44701-182">It is not required, and can be removed from your code.</span></span>  
  
 [<span data-ttu-id="44701-183">Функция CoUninitializeCor</span><span class="sxs-lookup"><span data-stu-id="44701-183">CoUninitializeCor Function</span></span>](couninitializecor-function.md)  
 <span data-ttu-id="44701-184">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="44701-184">Obsolete.</span></span> <span data-ttu-id="44701-185">Среду CLR нельзя выгрузить из процесса.</span><span class="sxs-lookup"><span data-stu-id="44701-185">The CLR cannot be unloaded from a process.</span></span>  
  
 [<span data-ttu-id="44701-186">Функция CoUninitializeEE</span><span class="sxs-lookup"><span data-stu-id="44701-186">CoUninitializeEE Function</span></span>](couninitializeee-function.md)  
 <span data-ttu-id="44701-187">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="44701-187">Obsolete.</span></span>  
  
 [<span data-ttu-id="44701-188">Функция CreateDebuggingInterfaceFromVersion</span><span class="sxs-lookup"><span data-stu-id="44701-188">CreateDebuggingInterfaceFromVersion Function</span></span>](createdebugginginterfacefromversion-function.md)  
 <span data-ttu-id="44701-189">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-189">Deprecated.</span></span> <span data-ttu-id="44701-190">Создает объект [ICorDebug](../debugging/icordebug-interface.md) на основе указанных сведений о версии.</span><span class="sxs-lookup"><span data-stu-id="44701-190">Creates an [ICorDebug](../debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 [<span data-ttu-id="44701-191">Функция CreateICeeFileGen</span><span class="sxs-lookup"><span data-stu-id="44701-191">CreateICeeFileGen Function</span></span>](createiceefilegen-function.md)  
 <span data-ttu-id="44701-192">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-192">Deprecated.</span></span> <span data-ttu-id="44701-193">Создает объект [ицеефилежен](iceefilegen-class.md) .</span><span class="sxs-lookup"><span data-stu-id="44701-193">Creates an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="44701-194">Функция DestroyICeeFileGen</span><span class="sxs-lookup"><span data-stu-id="44701-194">DestroyICeeFileGen Function</span></span>](destroyiceefilegen-function.md)  
 <span data-ttu-id="44701-195">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-195">Deprecated.</span></span> <span data-ttu-id="44701-196">Уничтожает объект [ицеефилежен](iceefilegen-class.md) .</span><span class="sxs-lookup"><span data-stu-id="44701-196">Destroys an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="44701-197">Указатель функции FExecuteInAppDomainCallback</span><span class="sxs-lookup"><span data-stu-id="44701-197">FExecuteInAppDomainCallback Function Pointer</span></span>](fexecuteinappdomaincallback-function-pointer.md)  
 <span data-ttu-id="44701-198">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-198">Deprecated.</span></span> <span data-ttu-id="44701-199">Указывает на функцию, которую CLR вызывает для выполнения управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="44701-199">Points to a function that the CLR calls to execute managed code.</span></span>  
  
 [<span data-ttu-id="44701-200">Указатель функции FLockClrVersionCallback</span><span class="sxs-lookup"><span data-stu-id="44701-200">FLockClrVersionCallback Function Pointer</span></span>](flockclrversioncallback-function-pointer.md)  
 <span data-ttu-id="44701-201">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-201">Deprecated.</span></span> <span data-ttu-id="44701-202">Указывает на функцию, которая вызывается средой CLR для уведомления узла о том, что инициализация запущена или завершена.</span><span class="sxs-lookup"><span data-stu-id="44701-202">Points to a function that the CLR calls to notify the host that initialization has either started or completed.</span></span>  
  
 [<span data-ttu-id="44701-203">Функция GetCLRIdentityManager</span><span class="sxs-lookup"><span data-stu-id="44701-203">GetCLRIdentityManager Function</span></span>](getclridentitymanager-function.md)  
 <span data-ttu-id="44701-204">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-204">Deprecated.</span></span> <span data-ttu-id="44701-205">Возвращает указатель на интерфейс, который позволяет среде CLR управлять удостоверениями.</span><span class="sxs-lookup"><span data-stu-id="44701-205">Gets a pointer to an interface that allows the CLR to manage identities.</span></span>  
  
 [<span data-ttu-id="44701-206">Функция LoadLibraryShim</span><span class="sxs-lookup"><span data-stu-id="44701-206">LoadLibraryShim Function</span></span>](loadlibraryshim-function.md)  
 <span data-ttu-id="44701-207">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-207">Deprecated.</span></span> <span data-ttu-id="44701-208">Загружает указанную версию платформа .NET Framework DLL.</span><span class="sxs-lookup"><span data-stu-id="44701-208">Loads a specified version of a .NET Framework DLL.</span></span>  
  
 [<span data-ttu-id="44701-209">Функция LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="44701-209">LoadStringRC Function</span></span>](loadstringrc-function.md)  
 <span data-ttu-id="44701-210">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-210">Deprecated.</span></span> <span data-ttu-id="44701-211">Преобразует значение HRESULT в сообщение об ошибке с помощью языка и региональных параметров по умолчанию текущего потока.</span><span class="sxs-lookup"><span data-stu-id="44701-211">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 [<span data-ttu-id="44701-212">Функция LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="44701-212">LoadStringRCEx Function</span></span>](loadstringrcex-function.md)  
 <span data-ttu-id="44701-213">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-213">Deprecated.</span></span> <span data-ttu-id="44701-214">Преобразует значение HRESULT в соответствующее сообщение об ошибке для указанного языка и региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="44701-214">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 [<span data-ttu-id="44701-215">Указатель функции LPOVERLAPPED_COMPLETION_ROUTINE</span><span class="sxs-lookup"><span data-stu-id="44701-215">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>](lpoverlapped-completion-routine-function-pointer.md)  
 <span data-ttu-id="44701-216">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-216">Deprecated.</span></span> <span data-ttu-id="44701-217">Указывает на функцию, которая уведомляет узел при завершении перекрытия (асинхронного) ввода-вывода на устройство.</span><span class="sxs-lookup"><span data-stu-id="44701-217">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 [<span data-ttu-id="44701-218">Указатель функции LPTHREAD_START_ROUTINE</span><span class="sxs-lookup"><span data-stu-id="44701-218">LPTHREAD_START_ROUTINE Function Pointer</span></span>](lpthread-start-routine-function-pointer.md)  
 <span data-ttu-id="44701-219">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-219">Deprecated.</span></span> <span data-ttu-id="44701-220">Указывает на функцию, которая уведомляет узел о начале выполнения потока.</span><span class="sxs-lookup"><span data-stu-id="44701-220">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 [<span data-ttu-id="44701-221">Функция RunDll32ShimW</span><span class="sxs-lookup"><span data-stu-id="44701-221">RunDll32ShimW Function</span></span>](rundll32shimw-function.md)  
 <span data-ttu-id="44701-222">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-222">Deprecated.</span></span> <span data-ttu-id="44701-223">Выполняет указанную команду.</span><span class="sxs-lookup"><span data-stu-id="44701-223">Executes the specified command.</span></span>  
  
 [<span data-ttu-id="44701-224">Указатель функции WAITORTIMERCALLBACK</span><span class="sxs-lookup"><span data-stu-id="44701-224">WAITORTIMERCALLBACK Function Pointer</span></span>](waitortimercallback-function-pointer.md)  
 <span data-ttu-id="44701-225">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="44701-225">Deprecated.</span></span> <span data-ttu-id="44701-226">Указывает на функцию, которая уведомляет узел о том, что дескриптор ожидания имеет сигнал или время ожидания истекло.</span><span class="sxs-lookup"><span data-stu-id="44701-226">Points to a function that notifies the host that a wait handle has either been signaled or timed out.</span></span>  
  
## <a name="infrastructure-functions"></a><span data-ttu-id="44701-227">Функции инфраструктуры</span><span class="sxs-lookup"><span data-stu-id="44701-227">Infrastructure functions</span></span>  

 <span data-ttu-id="44701-228">Функции в этом разделе предназначены для использования только платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="44701-228">The functions in this section are for use by the .NET Framework only.</span></span>  
  
 [<span data-ttu-id="44701-229">Функция _CorDllMain</span><span class="sxs-lookup"><span data-stu-id="44701-229">_CorDllMain Function</span></span>](cordllmain-function.md)  
 <span data-ttu-id="44701-230">Инициализирует среду CLR, находит управляемую точку входа в заголовке CLR сборки DLL и начинает выполнение.</span><span class="sxs-lookup"><span data-stu-id="44701-230">Initializes the CLR, locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="44701-231">Функция _CorExeMain</span><span class="sxs-lookup"><span data-stu-id="44701-231">_CorExeMain Function</span></span>](corexemain-function.md)  
 <span data-ttu-id="44701-232">Инициализирует среду CLR, находит управляемую точку входа в заголовке CLR исполняемой сборки и начинает выполнение.</span><span class="sxs-lookup"><span data-stu-id="44701-232">Initializes the CLR, locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="44701-233">Функция _CorExeMain2</span><span class="sxs-lookup"><span data-stu-id="44701-233">_CorExeMain2 Function</span></span>](corexemain2-function.md)  
 <span data-ttu-id="44701-234">Выполняет точку входа в указанном коде, сопоставленном с памятью.</span><span class="sxs-lookup"><span data-stu-id="44701-234">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="44701-235">Эта функция вызывается загрузчиком операционной системы.</span><span class="sxs-lookup"><span data-stu-id="44701-235">This function is called by the operating system loader.</span></span>  
  
 [<span data-ttu-id="44701-236">Функция _CorImageUnloading</span><span class="sxs-lookup"><span data-stu-id="44701-236">_CorImageUnloading Function</span></span>](corimageunloading-function.md)  
 <span data-ttu-id="44701-237">Уведомляет загрузчик об выгрузке образов управляемого модуля.</span><span class="sxs-lookup"><span data-stu-id="44701-237">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 [<span data-ttu-id="44701-238">Функция _CorValidateImage</span><span class="sxs-lookup"><span data-stu-id="44701-238">_CorValidateImage Function</span></span>](corvalidateimage-function.md)  
 <span data-ttu-id="44701-239">Проверяет образы управляемого модуля и уведомляет загрузчик операционной системы после их загрузки.</span><span class="sxs-lookup"><span data-stu-id="44701-239">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44701-240">См. также</span><span class="sxs-lookup"><span data-stu-id="44701-240">See also</span></span>

- [<span data-ttu-id="44701-241">Глобальные статические функции размещения платформы .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="44701-241">.NET Framework 4 Hosting Global Static Functions</span></span>](net-framework-4-hosting-global-static-functions.md)
