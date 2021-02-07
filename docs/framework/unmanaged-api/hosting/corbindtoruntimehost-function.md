---
description: Дополнительные сведения о функции Корбиндторунтимехост
title: Функция CorBindToRuntimeHost
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeHost
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeHost
helpviewer_keywords:
- CorBindToRuntimeHost function [.NET Framework hosting]
ms.assetid: 5c826ba3-8258-49bc-a417-78807915fcaf
topic_type:
- apiref
ms.openlocfilehash: 1921eece4c6fa7f1a8fc851f17ce8f9708bc49d1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717164"
---
# <a name="corbindtoruntimehost-function"></a><span data-ttu-id="e885d-103">Функция CorBindToRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="e885d-103">CorBindToRuntimeHost Function</span></span>

<span data-ttu-id="e885d-104">Позволяет узлам загружать в процесс указанную версию среды CLR.</span><span class="sxs-lookup"><span data-stu-id="e885d-104">Enables hosts to load a specified version of the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="e885d-105">Эта функция является устаревшей в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="e885d-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e885d-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e885d-106">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntimeHost (  
    [in] LPCWSTR       pwszVersion,
    [in] LPCWSTR       pwszBuildFlavor,
    [in] LPCWSTR       pwszHostConfigFile,
    [in] VOID*         pReserved,
    [in] DWORD         startupFlags,
    [in] REFCLSID      rclsid,
    [in] REFIID        riid,
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e885d-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="e885d-107">Parameters</span></span>  

 `pwszVersion`  
 <span data-ttu-id="e885d-108">окне Строка, описывающая версию среды CLR, которую требуется загрузить.</span><span class="sxs-lookup"><span data-stu-id="e885d-108">[in] A string that describes the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="e885d-109">Номер версии в платформа .NET Framework состоит из четырех частей, разделенных точками: *основной. дополнительный. сборка. Редакция*.</span><span class="sxs-lookup"><span data-stu-id="e885d-109">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="e885d-110">Строка, передаваемая как, `pwszVersion` должна начинаться с символа "v", за которым следуют первые три части номера версии (например, "v 1.0.1529").</span><span class="sxs-lookup"><span data-stu-id="e885d-110">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="e885d-111">Некоторые версии среды CLR устанавливаются с инструкцией политики, которая определяет совместимость с предыдущими версиями среды CLR.</span><span class="sxs-lookup"><span data-stu-id="e885d-111">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="e885d-112">По умолчанию оболочка запуска выполняет проверку на `pwszVersion` соответствие инструкциям политики и загружает последнюю версию среды выполнения, совместимую с запрашиваемой версией.</span><span class="sxs-lookup"><span data-stu-id="e885d-112">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="e885d-113">Узел может заставить оболочку пропускать вычисление политики и загружать точную версию, указанную в `pwszVersion` , передав значение STARTUP_LOADER_SAFEMODE для `startupFlags` параметра.</span><span class="sxs-lookup"><span data-stu-id="e885d-113">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of STARTUP_LOADER_SAFEMODE for the `startupFlags` parameter.</span></span>  
  
 <span data-ttu-id="e885d-114">Если `pwszVersion` — `null,` метод не загружает ни одной версии среды CLR.</span><span class="sxs-lookup"><span data-stu-id="e885d-114">If `pwszVersion` is `null,` the method does not load any version of the CLR.</span></span> <span data-ttu-id="e885d-115">Вместо этого он возвращает CLR_E_SHIM_RUNTIMELOAD, который указывает, что ему не удалось загрузить среду выполнения.</span><span class="sxs-lookup"><span data-stu-id="e885d-115">Instead, it returns CLR_E_SHIM_RUNTIMELOAD, which indicates that it failed to load the runtime.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="e885d-116">окне Строка, указывающая, загружать ли сервер или рабочую станцию сборку среды CLR.</span><span class="sxs-lookup"><span data-stu-id="e885d-116">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="e885d-117">Допустимые значения: `svr` и `wks`.</span><span class="sxs-lookup"><span data-stu-id="e885d-117">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="e885d-118">Сборка сервера оптимизирована для использования нескольких процессоров для сборок мусора, а сборка рабочей станции оптимизирована для клиентских приложений, работающих на однопроцессорном компьютере.</span><span class="sxs-lookup"><span data-stu-id="e885d-118">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="e885d-119">Если параметр `pwszBuildFlavor` имеет значение null, загружается сборка рабочей станции.</span><span class="sxs-lookup"><span data-stu-id="e885d-119">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="e885d-120">При запуске на однопроцессорном компьютере сборка рабочей станции всегда загружается, даже если параметр `pwszBuildFlavor` имеет значение `svr` .</span><span class="sxs-lookup"><span data-stu-id="e885d-120">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="e885d-121">Однако если задано `pwszBuildFlavor` значение `svr` и задана параллельная сборка мусора (см `startupFlags` . Описание параметра), то загружается серверная сборка.</span><span class="sxs-lookup"><span data-stu-id="e885d-121">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e885d-122">Параллельная сборка мусора не поддерживается в приложениях, использующих Эмулятор WOW64 x86 в 64-разрядных системах, которые реализуют архитектуру Intel Itanium (прежнее название — IA-64).</span><span class="sxs-lookup"><span data-stu-id="e885d-122">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="e885d-123">Дополнительные сведения об использовании WOW64 в 64-разрядных системах Windows см. в разделе [выполнение 32-разрядных приложений](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="e885d-123">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>  
  
 `pwszHostConfigFile`  
 <span data-ttu-id="e885d-124">окне Имя файла конфигурации узла, указывающего версию среды CLR для загрузки.</span><span class="sxs-lookup"><span data-stu-id="e885d-124">[in] The name of a host configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="e885d-125">Если имя файла не содержит полного пути, предполагается, что файл находится в том же каталоге, что и исполняемый файл, выполняющий вызов.</span><span class="sxs-lookup"><span data-stu-id="e885d-125">If the file name does not include a fully qualified path, the file is assumed to be in the same directory as the executable that is making the call.</span></span>  
  
 `pReserved`  
 <span data-ttu-id="e885d-126">окне Зарезервировано для будущего расширения.</span><span class="sxs-lookup"><span data-stu-id="e885d-126">[in] Reserved for future extensibility.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="e885d-127">окне Набор флагов, управляющих параллельной сборкой мусора, нейтральным к домену кодом и поведением `pwszVersion` параметра.</span><span class="sxs-lookup"><span data-stu-id="e885d-127">[in] A set of flags that controls concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="e885d-128">Значение по умолчанию — один домен, если флаг не установлен.</span><span class="sxs-lookup"><span data-stu-id="e885d-128">The default is single domain if no flag is set.</span></span> <span data-ttu-id="e885d-129">Список поддерживаемых значений см. в разделе [перечисление STARTUP_FLAGS](startup-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="e885d-129">For a list of supported values, see the [STARTUP_FLAGS enumeration](startup-flags-enumeration.md).</span></span>  
  
 `rclsid`  
 <span data-ttu-id="e885d-130">окне Объект `CLSID` coclass, реализующий интерфейс [ICorRuntimeHost](icorruntimehost-interface.md) или [ICLRRuntimeHost](iclrruntimehost-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="e885d-130">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="e885d-131">Поддерживаемые значения: CLSID_CorRuntimeHost или CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="e885d-131">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="e885d-132">окне `IID` Запрашиваемый интерфейс.</span><span class="sxs-lookup"><span data-stu-id="e885d-132">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="e885d-133">Поддерживаемые значения: IID_ICorRuntimeHost или IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="e885d-133">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="e885d-134">заполняет Указатель интерфейса на версию загруженной среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="e885d-134">[out] An interface pointer to the version of the runtime that was loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e885d-135">Требования</span><span class="sxs-lookup"><span data-stu-id="e885d-135">Requirements</span></span>  

 <span data-ttu-id="e885d-136">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e885d-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e885d-137">**Заголовок:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="e885d-137">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="e885d-138">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e885d-138">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e885d-139">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e885d-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e885d-140">См. также</span><span class="sxs-lookup"><span data-stu-id="e885d-140">See also</span></span>

- [<span data-ttu-id="e885d-141">Функция CorBindToCurrentRuntime</span><span class="sxs-lookup"><span data-stu-id="e885d-141">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="e885d-142">Функция CorBindToRuntime</span><span class="sxs-lookup"><span data-stu-id="e885d-142">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)
- [<span data-ttu-id="e885d-143">Функция CorBindToRuntimeByCfg</span><span class="sxs-lookup"><span data-stu-id="e885d-143">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="e885d-144">Функция CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="e885d-144">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="e885d-145">Интерфейс ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="e885d-145">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="e885d-146">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="e885d-146">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
