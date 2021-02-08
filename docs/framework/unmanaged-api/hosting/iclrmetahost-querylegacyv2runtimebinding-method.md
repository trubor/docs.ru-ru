---
description: 'Дополнительные сведения о методе: ICLRMetaHost:: QueryLegacyV2RuntimeBinding'
title: Метод ICLRMetaHost::QueryLegacyV2RuntimeBinding
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::QueryLegacyV2RuntimeBinding
helpviewer_keywords:
- QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
- ICLRMetaHost::QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
ms.assetid: 9929817e-acc9-40b7-960c-598664e04b60
topic_type:
- apiref
ms.openlocfilehash: ae825c2b2dfe2ce5b75ac9b82511215704fa357f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789857"
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a><span data-ttu-id="b49ea-103">Метод ICLRMetaHost::QueryLegacyV2RuntimeBinding</span><span class="sxs-lookup"><span data-stu-id="b49ea-103">ICLRMetaHost::QueryLegacyV2RuntimeBinding Method</span></span>

<span data-ttu-id="b49ea-104">Возвращает интерфейс, представляющий среду выполнения, к которой привязана политика устаревшей активации, например, с помощью `useLegacyV2RuntimeActivationPolicy` атрибута в записи файла конфигурации [ \<startup> элемента](../../configure-apps/file-schema/startup/startup-element.md) , путем непосредственного использования устаревших API-интерфейсов активации или путем вызова метода [ICLRRuntimeInfo:: BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b49ea-104">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b49ea-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b49ea-105">Syntax</span></span>  
  
```cpp  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b49ea-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b49ea-106">Parameters</span></span>  

 `riid`  
 <span data-ttu-id="b49ea-107">окне Обязательно. в настоящее время единственным допустимым значением для этого параметра является `IID_ICLRRuntimeInfo` .</span><span class="sxs-lookup"><span data-stu-id="b49ea-107">[in] Required.Currently the only valid value for this parameter is `IID_ICLRRuntimeInfo`.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="b49ea-108">[out] Обязательный.</span><span class="sxs-lookup"><span data-stu-id="b49ea-108">[out] Required.</span></span> <span data-ttu-id="b49ea-109">При возврате из этого метода содержит указатель на интерфейс [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , представляющий среду выполнения, привязанную к устаревшей политике активации.</span><span class="sxs-lookup"><span data-stu-id="b49ea-109">When this method returns, contains a pointer to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that represents a runtime that has been bound to legacy activation policy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b49ea-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="b49ea-110">Return Value</span></span>  

 <span data-ttu-id="b49ea-111">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="b49ea-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b49ea-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b49ea-112">HRESULT</span></span>|<span data-ttu-id="b49ea-113">Описание:</span><span class="sxs-lookup"><span data-stu-id="b49ea-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b49ea-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="b49ea-114">S_OK</span></span>|<span data-ttu-id="b49ea-115">Метод успешно выполнен, и возвращена среда выполнения, которая была привязана к устаревшей политике активации.</span><span class="sxs-lookup"><span data-stu-id="b49ea-115">The method completed successfully and returned a runtime that was bound to legacy activation policy.</span></span>|  
|<span data-ttu-id="b49ea-116">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b49ea-116">S_FALSE</span></span>|<span data-ttu-id="b49ea-117">Метод успешно выполнен, но устаревшая среда выполнения еще не привязана.</span><span class="sxs-lookup"><span data-stu-id="b49ea-117">The method completed successfully, but a legacy runtime has not yet been bound.</span></span>|  
|<span data-ttu-id="b49ea-118">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="b49ea-118">E_NOINTERFACE</span></span>|<span data-ttu-id="b49ea-119">Метод обнаружил среду выполнения, которая была привязана к устаревшей политике активации, но параметр `riid` не поддерживается этой средой.</span><span class="sxs-lookup"><span data-stu-id="b49ea-119">The method found a runtime that was bound to legacy activation policy, but `riid` is not supported by that runtime.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b49ea-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="b49ea-120">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b49ea-121">Требования</span><span class="sxs-lookup"><span data-stu-id="b49ea-121">Requirements</span></span>  

 <span data-ttu-id="b49ea-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b49ea-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b49ea-123">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="b49ea-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b49ea-124">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b49ea-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b49ea-125">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b49ea-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b49ea-126">См. также</span><span class="sxs-lookup"><span data-stu-id="b49ea-126">See also</span></span>

- [<span data-ttu-id="b49ea-127">Интерфейс ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="b49ea-127">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="b49ea-128">Размещение</span><span class="sxs-lookup"><span data-stu-id="b49ea-128">Hosting</span></span>](index.md)
