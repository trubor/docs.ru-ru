---
description: Дополнительные сведения о функции CorBindToRuntime
title: Функция CorBindToRuntime
ms.date: 03/30/2017
api_name:
- CorBindToRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntime
helpviewer_keywords:
- CorBindToRuntime function [.NET Framework hosting]
ms.assetid: 799740aa-46ec-4532-95da-6444565b4971
topic_type:
- apiref
ms.openlocfilehash: 727abdccd692a431960d293404025cf9ccc1d7ee
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790091"
---
# <a name="corbindtoruntime-function"></a><span data-ttu-id="0734a-103">Функция CorBindToRuntime</span><span class="sxs-lookup"><span data-stu-id="0734a-103">CorBindToRuntime Function</span></span>

<span data-ttu-id="0734a-104">Позволяет неуправляемым узлам загружать среду CLR в процесс.</span><span class="sxs-lookup"><span data-stu-id="0734a-104">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="0734a-105">Эта функция является устаревшей в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="0734a-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0734a-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0734a-106">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,
    [in]  LPCWSTR     pwszBuildFlavor,
    [in]  REFCLSID    rclsid,
    [in]  REFIID      riid,
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0734a-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="0734a-107">Parameters</span></span>  

 `pwszVersion`  
 <span data-ttu-id="0734a-108">окне Строка, описывающая версию среды CLR, которую требуется загрузить.</span><span class="sxs-lookup"><span data-stu-id="0734a-108">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="0734a-109">Номер версии в платформа .NET Framework состоит из четырех частей, разделенных точками: *основной. дополнительный. сборка. Редакция*.</span><span class="sxs-lookup"><span data-stu-id="0734a-109">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="0734a-110">Строка, передаваемая как, `pwszVersion` должна начинаться с символа "v", за которым следуют первые три части номера версии (например, "v 1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="0734a-110">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="0734a-111">Некоторые версии среды CLR устанавливаются с инструкцией политики, которая определяет совместимость с предыдущими версиями среды CLR.</span><span class="sxs-lookup"><span data-stu-id="0734a-111">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="0734a-112">По умолчанию оболочка запуска выполняет проверку на `pwszVersion` соответствие инструкциям политики и загружает последнюю версию среды выполнения, совместимую с запрашиваемой версией.</span><span class="sxs-lookup"><span data-stu-id="0734a-112">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="0734a-113">Узел может заставить оболочку пропускать вычисление политики и загружать точную версию, указанную в `pwszVersion` , передав значение  `STARTUP_LOADER_SAFEMODE` для `flags` параметра, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="0734a-113">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `flags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="0734a-114">Если вызывающий объект задает значение NULL для `pwszVersion` , загружается последняя версия среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="0734a-114">If the caller specifies null for `pwszVersion`, the latest version of the runtime is loaded.</span></span> <span data-ttu-id="0734a-115">Передача значения NULL позволяет узлу не контролировать, какая версия среды выполнения загружена.</span><span class="sxs-lookup"><span data-stu-id="0734a-115">Passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="0734a-116">Хотя такой подход может быть приемлемым в некоторых сценариях, настоятельно рекомендуется, чтобы узел предоставил определенную версию для загрузки.</span><span class="sxs-lookup"><span data-stu-id="0734a-116">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="0734a-117">окне Строка, указывающая, загружать ли сервер или рабочую станцию сборку среды CLR.</span><span class="sxs-lookup"><span data-stu-id="0734a-117">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="0734a-118">Допустимые значения: `svr` и `wks`.</span><span class="sxs-lookup"><span data-stu-id="0734a-118">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="0734a-119">Сборка сервера оптимизирована для использования нескольких процессоров для сборок мусора, а сборка рабочей станции оптимизирована для клиентских приложений, работающих на однопроцессорном компьютере.</span><span class="sxs-lookup"><span data-stu-id="0734a-119">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="0734a-120">Если параметр `pwszBuildFlavor` имеет значение null, загружается сборка рабочей станции.</span><span class="sxs-lookup"><span data-stu-id="0734a-120">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="0734a-121">При запуске на однопроцессорном компьютере сборка рабочей станции всегда загружается, даже если параметр `pwszBuildFlavor` имеет значение `svr` .</span><span class="sxs-lookup"><span data-stu-id="0734a-121">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="0734a-122">Однако если задано `pwszBuildFlavor` значение `svr` и задана параллельная сборка мусора (см `flags` . Описание параметра), то загружается серверная сборка.</span><span class="sxs-lookup"><span data-stu-id="0734a-122">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `flags` parameter), the server build is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="0734a-123">окне Объект `CLSID` coclass, реализующий интерфейс [ICorRuntimeHost](icorruntimehost-interface.md) или [ICLRRuntimeHost](iclrruntimehost-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="0734a-123">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="0734a-124">Поддерживаемые значения: CLSID_CorRuntimeHost или CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="0734a-124">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="0734a-125">окне Объект `IID` запрашиваемого интерфейса из `rclsid` .</span><span class="sxs-lookup"><span data-stu-id="0734a-125">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="0734a-126">Поддерживаемые значения: IID_ICorRuntimeHost или IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="0734a-126">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="0734a-127">заполняет Возвращаемый указатель интерфейса в `riid` .</span><span class="sxs-lookup"><span data-stu-id="0734a-127">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0734a-128">Remarks</span><span class="sxs-lookup"><span data-stu-id="0734a-128">Remarks</span></span>  

 <span data-ttu-id="0734a-129">Если `pwszVersion` указывает несуществующую версию среды выполнения, `CorBindToRuntimeEx` ВОЗВРАЩАЕТ значение HRESULT, равное CLR_E_SHIM_RUNTIMELOAD.</span><span class="sxs-lookup"><span data-stu-id="0734a-129">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="0734a-130">Контекст выполнения и поток удостоверения Windows</span><span class="sxs-lookup"><span data-stu-id="0734a-130">Execution Context and Flow of Windows Identity</span></span>  

 <span data-ttu-id="0734a-131">В версии 1 среды CLR <xref:System.Security.Principal.WindowsIdentity> объект не перетекает через асинхронные точки, такие как новые потоки, пулы потоков или обратные вызовы таймера.</span><span class="sxs-lookup"><span data-stu-id="0734a-131">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="0734a-132">В версии 2,0 среды CLR <xref:System.Threading.ExecutionContext> объект заключает некоторые сведения о выполняемом в данный момент потоке и передает его через любую асинхронную точку, но не через границы домена приложения.</span><span class="sxs-lookup"><span data-stu-id="0734a-132">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="0734a-133">Аналогичным образом <xref:System.Security.Principal.WindowsIdentity> объект также проходит через любую асинхронную точку.</span><span class="sxs-lookup"><span data-stu-id="0734a-133">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="0734a-134">Таким образом, текущее олицетворение в потоке, если таковое имеется, также проходит.</span><span class="sxs-lookup"><span data-stu-id="0734a-134">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="0734a-135">Изменить последовательность можно двумя способами:</span><span class="sxs-lookup"><span data-stu-id="0734a-135">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="0734a-136">Путем изменения <xref:System.Threading.ExecutionContext> параметров для подавления потока на основе потока (см <xref:System.Threading.ExecutionContext.SuppressFlow%2A> <xref:System.Security.SecurityContext.SuppressFlow%2A> <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> . методы, и).</span><span class="sxs-lookup"><span data-stu-id="0734a-136">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="0734a-137">Изменив режим обработки по умолчанию на режим совместимости версии 1, где <xref:System.Security.Principal.WindowsIdentity> объект не пополняется по какой бы то ни было асинхронной точке, независимо от <xref:System.Threading.ExecutionContext> параметров в текущем потоке.</span><span class="sxs-lookup"><span data-stu-id="0734a-137">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="0734a-138">Изменение режима по умолчанию зависит от того, используется ли управляемый исполняемый файл или неуправляемый интерфейс размещения для загрузки среды CLR:</span><span class="sxs-lookup"><span data-stu-id="0734a-138">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="0734a-139">Для управляемых исполняемых файлов необходимо задать `enabled` атрибуту [\<legacyImpersonationPolicy>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) элемента значение `true` .</span><span class="sxs-lookup"><span data-stu-id="0734a-139">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="0734a-140">Для неуправляемых интерфейсов размещения установите `STARTUP_LEGACY_IMPERSONATION` флаг в `flags` параметре при вызове `CorBindToRuntimeEx` функции.</span><span class="sxs-lookup"><span data-stu-id="0734a-140">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `flags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="0734a-141">Режим совместимости версии 1 применяется ко всему процессу и всем доменам приложения в процессе.</span><span class="sxs-lookup"><span data-stu-id="0734a-141">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0734a-142">Remarks</span><span class="sxs-lookup"><span data-stu-id="0734a-142">Remarks</span></span>  

 <span data-ttu-id="0734a-143">[CorBindToRuntimeEx](corbindtoruntimeex-function.md) и `CorBindToRuntime` выполните ту же операцию, но `CorBindToRuntimeEx` функция позволяет устанавливать флаги для указания поведения среды CLR.</span><span class="sxs-lookup"><span data-stu-id="0734a-143">[CorBindToRuntimeEx](corbindtoruntimeex-function.md) and `CorBindToRuntime` perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0734a-144">Требования</span><span class="sxs-lookup"><span data-stu-id="0734a-144">Requirements</span></span>  

 <span data-ttu-id="0734a-145">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0734a-145">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0734a-146">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0734a-146">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0734a-147">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0734a-147">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0734a-148">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0734a-148">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0734a-149">См. также</span><span class="sxs-lookup"><span data-stu-id="0734a-149">See also</span></span>

- [<span data-ttu-id="0734a-150">Функция CorBindToCurrentRuntime</span><span class="sxs-lookup"><span data-stu-id="0734a-150">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="0734a-151">Функция CorBindToRuntimeByCfg</span><span class="sxs-lookup"><span data-stu-id="0734a-151">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="0734a-152">Функция CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="0734a-152">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="0734a-153">Функция CorBindToRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="0734a-153">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)
- [<span data-ttu-id="0734a-154">Интерфейс ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="0734a-154">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="0734a-155">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="0734a-155">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
