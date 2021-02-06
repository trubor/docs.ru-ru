---
description: 'Дополнительные сведения о методе: ICLRMetaHost:: Runtime'
title: Метод ICLRMetaHost::GetRuntime
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetRuntime
helpviewer_keywords:
- GetRuntime method [.NET Framework hosting]
- ICLRMetaHost::GetRuntime method [.NET Framework hosting]
ms.assetid: a10749f1-ab91-47cf-982f-d8ccd2e81bd2
topic_type:
- apiref
ms.openlocfilehash: 8a2ada652dbb139337150cb8ed20986ebf8ae7f4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637525"
---
# <a name="iclrmetahostgetruntime-method"></a><span data-ttu-id="09873-103">Метод ICLRMetaHost::GetRuntime</span><span class="sxs-lookup"><span data-stu-id="09873-103">ICLRMetaHost::GetRuntime Method</span></span>

<span data-ttu-id="09873-104">Возвращает интерфейс [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , соответствующий определенной версии среды CLR.</span><span class="sxs-lookup"><span data-stu-id="09873-104">Gets the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that corresponds to a particular version of the common language runtime (CLR).</span></span> <span data-ttu-id="09873-105">Этот метод заменяет функцию [CorBindToRuntimeEx](corbindtoruntimeex-function.md) , используемую с флагом [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="09873-105">This method supersedes the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) flag.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09873-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="09873-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in] REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09873-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="09873-107">Parameters</span></span>  

 `pwzVersion`  
 <span data-ttu-id="09873-108">окне Версия компиляции платформа .NET Framework, хранящаяся в метаданных, в формате "v *A*. *B*[.*X*] ".</span><span class="sxs-lookup"><span data-stu-id="09873-108">[in] The .NET Framework compilation version stored in the metadata, in the format "v *A*.*B*[.*X*]".</span></span> <span data-ttu-id="09873-109">*A*, *B* и *X* — это десятичные числа, соответствующие основной версии, дополнительной версии и номеру сборки.</span><span class="sxs-lookup"><span data-stu-id="09873-109">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="09873-110">Этот параметр должен соответствовать имени каталога для платформа .NET Framework версии, так как она отображается в разделе К:\виндовс\микрософт.нет\фрамеворк или C:\Windows\Microsoft.NET\Framework64.</span><span class="sxs-lookup"><span data-stu-id="09873-110">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework or C:\Windows\Microsoft.NET\Framework64.</span></span>  
  
 <span data-ttu-id="09873-111">Примеры значений: "v 1.0.3705", "v 1.1.4322", "v 2.0.50727" и "v 4.0. *X*", где *X* зависит от установленного номера сборки.</span><span class="sxs-lookup"><span data-stu-id="09873-111">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="09873-112">Требуется префикс "v".</span><span class="sxs-lookup"><span data-stu-id="09873-112">The "v" prefix is required.</span></span>  
  
 `riid`  
 <span data-ttu-id="09873-113">окне Идентификатор требуемого интерфейса.</span><span class="sxs-lookup"><span data-stu-id="09873-113">[in] The identifier for the desired interface.</span></span> <span data-ttu-id="09873-114">В настоящее время единственным допустимым значением для этого параметра является IID_ICLRRuntimeInfo.</span><span class="sxs-lookup"><span data-stu-id="09873-114">Currently, the only valid value for this parameter is IID_ICLRRuntimeInfo.</span></span>  
  
 `ppRuntime`  
 <span data-ttu-id="09873-115">заполняет Указатель на интерфейс [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , соответствующий запрошенной среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="09873-115">[out] A pointer to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that corresponds to the requested runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09873-116">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="09873-116">Return Value</span></span>  

 <span data-ttu-id="09873-117">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="09873-117">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="09873-118">HRESULT</span><span class="sxs-lookup"><span data-stu-id="09873-118">HRESULT</span></span>|<span data-ttu-id="09873-119">Описание:</span><span class="sxs-lookup"><span data-stu-id="09873-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="09873-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="09873-120">S_OK</span></span>|<span data-ttu-id="09873-121">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="09873-121">The method completed successfully.</span></span>|  
|<span data-ttu-id="09873-122">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="09873-122">E_POINTER</span></span>|<span data-ttu-id="09873-123">`pwzVersion` или `ppRuntime` равно null.</span><span class="sxs-lookup"><span data-stu-id="09873-123">`pwzVersion` or `ppRuntime` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09873-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="09873-124">Remarks</span></span>  

 <span data-ttu-id="09873-125">Этот метод взаимодействует согласованно с устаревшими интерфейсами, такими как интерфейс [ICorRuntimeHost](icorruntimehost-interface.md) , и устаревшими функциями, такими как устаревшие `CorBindTo*` функции (см. статью [устаревшие функции размещения CLR](deprecated-clr-hosting-functions.md) в API размещения платформа .NET Framework 2,0).</span><span class="sxs-lookup"><span data-stu-id="09873-125">This method interacts consistently with legacy interfaces such as the [ICorRuntimeHost](icorruntimehost-interface.md) interface and legacy functions such as the deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span> <span data-ttu-id="09873-126">То есть среды выполнения, загруженные с помощью API прежних версий, видимы для нового API, а среды выполнения, которые загружаются с новым API, видимы для API прежних версий.</span><span class="sxs-lookup"><span data-stu-id="09873-126">That is, runtimes that are loaded with the legacy API are visible to the new API, and runtimes that are loaded with the new API are visible to the legacy API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09873-127">Требования</span><span class="sxs-lookup"><span data-stu-id="09873-127">Requirements</span></span>  

 <span data-ttu-id="09873-128">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09873-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09873-129">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="09873-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="09873-130">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="09873-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="09873-131">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09873-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09873-132">См. также</span><span class="sxs-lookup"><span data-stu-id="09873-132">See also</span></span>

- [<span data-ttu-id="09873-133">Интерфейс ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="09873-133">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="09873-134">Устаревшие интерфейсы размещения CLR и CoClasses</span><span class="sxs-lookup"><span data-stu-id="09873-134">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)
- [<span data-ttu-id="09873-135">Интерфейсы размещения CLR</span><span class="sxs-lookup"><span data-stu-id="09873-135">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="09873-136">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="09873-136">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="09873-137">Размещение</span><span class="sxs-lookup"><span data-stu-id="09873-137">Hosting</span></span>](index.md)
