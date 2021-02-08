---
description: 'Дополнительные сведения о методе: ICLRMetaHostPolicy:: GetRequestedRuntime'
title: Метод ICLRMetaHostPolicy::GetRequestedRuntime
ms.date: 03/30/2017
api_name:
- ICLRMetaHostPolicy.GetRequestedRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHostPolicy::GetRequestedRuntime
helpviewer_keywords:
- GetRequestedRuntime method [.NET Framework hosting]
- ICLRMetaHostPolicy::GetRequestedRuntime method [.NET Framework hosting]
ms.assetid: 59ec1832-9cc1-4b5c-983d-03407e51de56
topic_type:
- apiref
ms.openlocfilehash: 0e11694b0cb66ad7fc28abf7bb9f7fc8c6931a19
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789844"
---
# <a name="iclrmetahostpolicygetrequestedruntime-method"></a><span data-ttu-id="2592e-103">Метод ICLRMetaHostPolicy::GetRequestedRuntime</span><span class="sxs-lookup"><span data-stu-id="2592e-103">ICLRMetaHostPolicy::GetRequestedRuntime Method</span></span>

<span data-ttu-id="2592e-104">Предоставляет интерфейс для предпочитаемой версии общеязыковой среды выполнения (CLR) на основе политики размещения, управляемой сборки, строки версии и потока конфигурации.</span><span class="sxs-lookup"><span data-stu-id="2592e-104">Provides an interface to a preferred version of the common language runtime (CLR) based on a hosting policy, managed assembly, version string, and configuration stream.</span></span> <span data-ttu-id="2592e-105">Этот метод не выполняет фактическую загрузку или активацию среды CLR, но просто возвращает интерфейс [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , представляющий результат политики.</span><span class="sxs-lookup"><span data-stu-id="2592e-105">This method does not actually load or activate the CLR, but simply returns the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that represents the policy result.</span></span> <span data-ttu-id="2592e-106">Этот метод заменяет методы [GetRequestedRuntimeInfo](getrequestedruntimeinfo-function.md), [жетрекуестедрунтимеверсион](getrequestedruntimeversion-function.md), [корбиндторунтимехост](corbindtoruntimehost-function.md), [корбиндторунтимебикфг](corbindtoruntimebycfg-function.md)и [жеткоррекуиредверсион](getcorrequiredversion-function.md) .</span><span class="sxs-lookup"><span data-stu-id="2592e-106">This method supersedes the [GetRequestedRuntimeInfo](getrequestedruntimeinfo-function.md), [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md), [CorBindToRuntimeHost](corbindtoruntimehost-function.md), [CorBindToRuntimeByCfg](corbindtoruntimebycfg-function.md), and [GetCORRequiredVersion](getcorrequiredversion-function.md) methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="2592e-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2592e-107">Syntax</span></span>

```cpp
HRESULT GetRequestedRuntime(
    [in]  METAHOST_POLICY_FLAGS dwPolicyFlags,
    [in]  LPCWSTR pwzBinary,
    [in]  IStream *pCfgStream,
    [in, out, size_is(*pcchVersion)] LPWSTR pwzVersion,
    [in, out]  DWORD *pcchVersion,
    [out, size_is(*pcchImageVersion)] LPWSTR pwzImageVersion,
    [in, out]  DWORD *pcchImageVersion,
    [out] DWORD *pdwConfigFlags,
    [in]  REFIID  riid
    [out, iid_is(riid), retval] LPVOID *ppRuntime);
```

## <a name="parameters"></a><span data-ttu-id="2592e-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="2592e-108">Parameters</span></span>

|<span data-ttu-id="2592e-109">Имя</span><span class="sxs-lookup"><span data-stu-id="2592e-109">Name</span></span>|<span data-ttu-id="2592e-110">Описание</span><span class="sxs-lookup"><span data-stu-id="2592e-110">Description</span></span>|
|----------|-----------------|
|`dwPolicyFlags`|<span data-ttu-id="2592e-111">[in] Обязательный.</span><span class="sxs-lookup"><span data-stu-id="2592e-111">[in] Required.</span></span> <span data-ttu-id="2592e-112">Указывает элемент перечисления [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) , представляющий политику привязки, и любое количество модификаторов.</span><span class="sxs-lookup"><span data-stu-id="2592e-112">Specifies a member of the [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) enumeration, representing a binding policy, and any number of modifiers.</span></span> <span data-ttu-id="2592e-113">Единственной доступной в данный момент политикой является [METAHOST_POLICY_HIGHCOMPAT](metahost-policy-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="2592e-113">The only policy that is currently available is [METAHOST_POLICY_HIGHCOMPAT](metahost-policy-flags-enumeration.md).</span></span><br /><br /> <span data-ttu-id="2592e-114">К модификаторам относятся [METAHOST_POLICY_EMULATE_EXE_LAUNCH](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](metahost-policy-flags-enumeration.md)и [METAHOST_POLICY_ENSURE_SKU_SUPPORTED](metahost-policy-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="2592e-114">Modifiers include [METAHOST_POLICY_EMULATE_EXE_LAUNCH](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](metahost-policy-flags-enumeration.md), and [METAHOST_POLICY_ENSURE_SKU_SUPPORTED](metahost-policy-flags-enumeration.md).</span></span>|
|`pwzBinary`|<span data-ttu-id="2592e-115">[в] Необязательно.</span><span class="sxs-lookup"><span data-stu-id="2592e-115">[in] Optional.</span></span> <span data-ttu-id="2592e-116">Задает путь к файлу сборки.</span><span class="sxs-lookup"><span data-stu-id="2592e-116">Specifies the assembly file path.</span></span>|
|`pCfgStream`|<span data-ttu-id="2592e-117">[в] Необязательно.</span><span class="sxs-lookup"><span data-stu-id="2592e-117">[in] Optional.</span></span> <span data-ttu-id="2592e-118">Задает файл конфигурации в виде <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2592e-118">Specifies the configuration file as a <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType>.</span></span>|
|`pwzVersion`|<span data-ttu-id="2592e-119">[in, out] Необязательный.</span><span class="sxs-lookup"><span data-stu-id="2592e-119">[in, out] Optional.</span></span> <span data-ttu-id="2592e-120">Задает или возвращает предпочтительную версию среды CLR для загрузки.</span><span class="sxs-lookup"><span data-stu-id="2592e-120">Specifies or returns the preferred CLR version to be loaded.</span></span>|
|`pcchVersion`|<span data-ttu-id="2592e-121">[in, out] Обязательный.</span><span class="sxs-lookup"><span data-stu-id="2592e-121">[in, out] Required.</span></span> <span data-ttu-id="2592e-122">Указывает ожидаемый размер `pwzVersion` в качестве входных данных для предотвращения переполнения буфера.</span><span class="sxs-lookup"><span data-stu-id="2592e-122">Specifies the expected size of `pwzVersion` as input, to avoid buffer overruns.</span></span> <span data-ttu-id="2592e-123">Если `pwzVersion` имеет значение NULL, `pcchVersion` содержит ожидаемый размер `pwzVersion` при возвращении значения `GetRequestedRuntime`, чтобы разрешить предварительное выделение; в противном случае `pcchVersion` содержит число символов, записанных в `pwzVersion`.</span><span class="sxs-lookup"><span data-stu-id="2592e-123">If `pwzVersion` is null, `pcchVersion` contains the expected size of `pwzVersion` when `GetRequestedRuntime` returns, to allow pre-allocation; otherwise, `pcchVersion` contains the number of characters written to `pwzVersion`.</span></span>|
|`pwzImageVersion`|<span data-ttu-id="2592e-124">[out] Необязательный.</span><span class="sxs-lookup"><span data-stu-id="2592e-124">[out] Optional.</span></span> <span data-ttu-id="2592e-125">При `GetRequestedRuntime` возврате содержит версию среды CLR, соответствующую возвращаемому интерфейсу [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="2592e-125">When `GetRequestedRuntime` returns, contains the CLR version corresponding to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that is returned.</span></span>|
|`pcchImageVersion`|<span data-ttu-id="2592e-126">[in, out] Необязательный.</span><span class="sxs-lookup"><span data-stu-id="2592e-126">[in, out] Optional.</span></span> <span data-ttu-id="2592e-127">Указывает размер `pwzImageVersion` в качестве входных данных для предотвращения переполнения буфера.</span><span class="sxs-lookup"><span data-stu-id="2592e-127">Specifies the size of `pwzImageVersion` as input to avoid buffer overruns.</span></span> <span data-ttu-id="2592e-128">Если `pwzImageVersion` имеет значение NULL, `pcchImageVersion` содержит требуемый размер `pwzImageVersion` при возвращении значения `GetRequestedRuntime`, чтобы разрешить предварительное выделение.</span><span class="sxs-lookup"><span data-stu-id="2592e-128">If `pwzImageVersion` is null, `pcchImageVersion` contains the required size of `pwzImageVersion` when `GetRequestedRuntime` returns, to allow pre-allocation.</span></span>|
|`pdwConfigFlags`|<span data-ttu-id="2592e-129">[out] Необязательный.</span><span class="sxs-lookup"><span data-stu-id="2592e-129">[out] Optional.</span></span> <span data-ttu-id="2592e-130">Если в процессе `GetRequestedRuntime` привязки использует файл конфигурации, то при возвращении `pdwConfigFlags` содержит значение [METAHOST_CONFIG_FLAGS](metahost-config-flags-enumeration.md) , указывающее, задан ли атрибут для [\<startup>](../../configure-apps/file-schema/startup/startup-element.md) элемента `useLegacyV2RuntimeActivationPolicy` , и значение атрибута.</span><span class="sxs-lookup"><span data-stu-id="2592e-130">If `GetRequestedRuntime` uses a configuration file during the binding process, when it returns, `pdwConfigFlags` contains a [METAHOST_CONFIG_FLAGS](metahost-config-flags-enumeration.md) value that indicates whether the [\<startup>](../../configure-apps/file-schema/startup/startup-element.md) element has the `useLegacyV2RuntimeActivationPolicy` attribute set, and the value of the attribute.</span></span> <span data-ttu-id="2592e-131">Примените маску [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](metahost-config-flags-enumeration.md) к, чтобы `pdwConfigFlags` получить значения, относящиеся к `useLegacyV2RuntimeActivationPolicy` .</span><span class="sxs-lookup"><span data-stu-id="2592e-131">Apply the [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](metahost-config-flags-enumeration.md) mask to `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|
|`riid`|<span data-ttu-id="2592e-132">окне Указывает идентификатор интерфейса IID_ICLRRuntimeInfo для запрошенного интерфейса [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="2592e-132">[in] Specifies the interface identifier IID_ICLRRuntimeInfo for the requested [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>|
|`ppRuntime`|<span data-ttu-id="2592e-133">заполняет При `GetRequestedRuntime` возврате содержит указатель на соответствующий интерфейс [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="2592e-133">[out] When `GetRequestedRuntime` returns, contains a pointer to the corresponding [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2592e-134">Remarks</span><span class="sxs-lookup"><span data-stu-id="2592e-134">Remarks</span></span>

<span data-ttu-id="2592e-135">После успешного завершения этого метода имеет место его побочный эффект в виде объединения дополнительных флагов с текущими флагами запуска по умолчанию из возвращенного интерфейса среды выполнения тогда и только тогда, когда один или несколько из следующих элементов существуют в потоке конфигурации в разделе `<configuration><runtime>`.</span><span class="sxs-lookup"><span data-stu-id="2592e-135">When this method succeeds, it has the side effect of combining additional flags with the current default startup flags of the returned runtime interface, if and only if one or more of the following elements exist in the configuration stream within the `<configuration><runtime>` section:</span></span>

- <span data-ttu-id="2592e-136">`<gcServer enabled="true"/>` приводит к заданию `STARTUP_SERVER_GC`.</span><span class="sxs-lookup"><span data-stu-id="2592e-136">`<gcServer enabled="true"/>` causes `STARTUP_SERVER_GC` to be set.</span></span>

- <span data-ttu-id="2592e-137">`<etwEnable enabled="true"/>` приводит к заданию `STARTUP_ETW`.</span><span class="sxs-lookup"><span data-stu-id="2592e-137">`<etwEnable enabled="true"/>` causes `STARTUP_ETW` to be set.</span></span>

- <span data-ttu-id="2592e-138">`<appDomainResourceMonitoring enabled="true"/>` приводит к заданию `STARTUP_ARM`.</span><span class="sxs-lookup"><span data-stu-id="2592e-138">`<appDomainResourceMonitoring enabled="true"/>` causes `STARTUP_ARM` to be set.</span></span>

<span data-ttu-id="2592e-139">По умолчанию результирующее значение`STARTUP_FLAGS` является побитовым или сочетанием заданных значений из предыдущего списка с флагами запуска по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="2592e-139">The resulting default `STARTUP_FLAGS` value is the bitwise OR combination of the values that are set from the preceding list with the default startup flags.</span></span>

## <a name="return-value"></a><span data-ttu-id="2592e-140">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="2592e-140">Return Value</span></span>

<span data-ttu-id="2592e-141">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="2592e-141">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>

|<span data-ttu-id="2592e-142">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2592e-142">HRESULT</span></span>|<span data-ttu-id="2592e-143">Описание:</span><span class="sxs-lookup"><span data-stu-id="2592e-143">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="2592e-144">S_OK</span><span class="sxs-lookup"><span data-stu-id="2592e-144">S_OK</span></span>|<span data-ttu-id="2592e-145">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="2592e-145">The method completed successfully.</span></span>|
|<span data-ttu-id="2592e-146">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="2592e-146">E_POINTER</span></span>|<span data-ttu-id="2592e-147">`pwzVersion` не равен NULL, а `pcchVersion` равен NULL.</span><span class="sxs-lookup"><span data-stu-id="2592e-147">`pwzVersion` is not null and `pcchVersion` is null.</span></span><br /><br /> <span data-ttu-id="2592e-148">-или-</span><span class="sxs-lookup"><span data-stu-id="2592e-148">-or-</span></span><br /><br /> <span data-ttu-id="2592e-149">`pwzImageVersion` не равен NULL, а `pcchImageVersion` равен NULL.</span><span class="sxs-lookup"><span data-stu-id="2592e-149">`pwzImageVersion` is not null and `pcchImageVersion` is null.</span></span>|
|<span data-ttu-id="2592e-150">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="2592e-150">E_INVALIDARG</span></span>|<span data-ttu-id="2592e-151">`dwPolicyFlags` не указывает `METAHOST_POLICY_HIGHCOMPAT`.</span><span class="sxs-lookup"><span data-stu-id="2592e-151">`dwPolicyFlags` does not specify `METAHOST_POLICY_HIGHCOMPAT`.</span></span>|
|<span data-ttu-id="2592e-152">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="2592e-152">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="2592e-153">Памяти, выделенной для `pwzVersion`, недостаточно.</span><span class="sxs-lookup"><span data-stu-id="2592e-153">The memory allocated to `pwzVersion` is inadequate.</span></span><br /><br /> <span data-ttu-id="2592e-154">-или-</span><span class="sxs-lookup"><span data-stu-id="2592e-154">-or-</span></span><br /><br /> <span data-ttu-id="2592e-155">Памяти, выделенной для `pwzImageVersion`, недостаточно.</span><span class="sxs-lookup"><span data-stu-id="2592e-155">The memory allocated to `pwzImageVersion` is inadequate.</span></span>|
|<span data-ttu-id="2592e-156">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="2592e-156">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="2592e-157">`dwPolicyFlags` включает в себя METAHOST_POLICY_APPLY_UPGRADE_POLICY, а как `pwzVersion`, так и `pcchVersion` имеют значение NULL.</span><span class="sxs-lookup"><span data-stu-id="2592e-157">`dwPolicyFlags` includes METAHOST_POLICY_APPLY_UPGRADE_POLICY, and both `pwzVersion` and `pcchVersion` are null.</span></span>|

## <a name="requirements"></a><span data-ttu-id="2592e-158">Требования</span><span class="sxs-lookup"><span data-stu-id="2592e-158">Requirements</span></span>

<span data-ttu-id="2592e-159">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2592e-159">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="2592e-160">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="2592e-160">**Header:** MetaHost.h</span></span>

<span data-ttu-id="2592e-161">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2592e-161">**Library:** Included as a resource in MSCorEE.dll</span></span>

<span data-ttu-id="2592e-162">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2592e-162">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="2592e-163">См. также</span><span class="sxs-lookup"><span data-stu-id="2592e-163">See also</span></span>

- [<span data-ttu-id="2592e-164">Интерфейс ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="2592e-164">ICLRMetaHostPolicy Interface</span></span>](iclrmetahostpolicy-interface.md)
- [<span data-ttu-id="2592e-165">Интерфейсы размещения CLR, добавленные в версиях .NET Framework 4 и 4.5</span><span class="sxs-lookup"><span data-stu-id="2592e-165">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="2592e-166">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="2592e-166">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="2592e-167">Размещение</span><span class="sxs-lookup"><span data-stu-id="2592e-167">Hosting</span></span>](index.md)
