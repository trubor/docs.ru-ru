---
description: 'Дополнительные сведения о методе ICLRRuntimeInfo:: interface'
title: Метод ICLRRuntimeInfo::GetInterface
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetInterface
helpviewer_keywords:
- GetInterface method [.NET Framework hosting]
- ICLRRuntimeInfo::GetInterface method [.NET Framework hosting]
ms.assetid: cc7b0e5b-48c3-4509-8ebb-611ddb1f7ec2
topic_type:
- apiref
ms.openlocfilehash: 5a5c55823ff9954735a712423d8aaab1256c947d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637135"
---
# <a name="iclrruntimeinfogetinterface-method"></a><span data-ttu-id="9333b-103">Метод ICLRRuntimeInfo::GetInterface</span><span class="sxs-lookup"><span data-stu-id="9333b-103">ICLRRuntimeInfo::GetInterface Method</span></span>

<span data-ttu-id="9333b-104">Загружает среду CLR в текущий процесс и возвращает указатели на интерфейсы среды выполнения, такие как [ICLRRuntimeHost](iclrruntimehost-interface.md), [метод iclrstrongname](iclrstrongname-interface.md)и [IMetaDataDispenserEx](../metadata/imetadatadispenser-interface.md).</span><span class="sxs-lookup"><span data-stu-id="9333b-104">Loads the CLR into the current process and returns runtime interface pointers, such as [ICLRRuntimeHost](iclrruntimehost-interface.md), [ICLRStrongName](iclrstrongname-interface.md), and [IMetaDataDispenserEx](../metadata/imetadatadispenser-interface.md).</span></span>  
  
 <span data-ttu-id="9333b-105">Этот метод заменяет все `CorBindTo` функции \* в разделе [устаревшие функции размещения CLR](deprecated-clr-hosting-functions.md) .</span><span class="sxs-lookup"><span data-stu-id="9333b-105">This method supersedes all the `CorBindTo`\* functions in the [Deprecated CLR Hosting Functions](deprecated-clr-hosting-functions.md) section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9333b-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9333b-106">Syntax</span></span>  
  
```cpp  
HRESULT GetInterface(  
[in]  REFCLSID rclsid,  
[in]  REFIID   riid,  
[out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9333b-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="9333b-107">Parameters</span></span>  

 `rclsid`  
 <span data-ttu-id="9333b-108">окне Интерфейс CLSID для компонентного класса.</span><span class="sxs-lookup"><span data-stu-id="9333b-108">[in] The CLSID interface for the coclass.</span></span>  
  
 `riid`  
 <span data-ttu-id="9333b-109">окне IID запрашиваемого `rclsid` интерфейса.</span><span class="sxs-lookup"><span data-stu-id="9333b-109">[in] The IID of the requested `rclsid` interface.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="9333b-110">заполняет Указатель на запрашиваемый интерфейс.</span><span class="sxs-lookup"><span data-stu-id="9333b-110">[out] A pointer to the queried interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9333b-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="9333b-111">Return Value</span></span>  

 <span data-ttu-id="9333b-112">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="9333b-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9333b-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9333b-113">HRESULT</span></span>|<span data-ttu-id="9333b-114">Описание:</span><span class="sxs-lookup"><span data-stu-id="9333b-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9333b-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="9333b-115">S_OK</span></span>|<span data-ttu-id="9333b-116">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="9333b-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="9333b-117">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="9333b-117">E_POINTER</span></span>|<span data-ttu-id="9333b-118">Параметр `ppUnk` имеет значение null.</span><span class="sxs-lookup"><span data-stu-id="9333b-118">`ppUnk` is null.</span></span>|  
|<span data-ttu-id="9333b-119">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="9333b-119">E_OUTOFMEMORY</span></span>|<span data-ttu-id="9333b-120">Недостаточно памяти для выполнения запроса.</span><span class="sxs-lookup"><span data-stu-id="9333b-120">Not enough memory is available to handle the request.</span></span>|  
|<span data-ttu-id="9333b-121">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="9333b-121">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="9333b-122">Другая среда выполнения уже привязана к устаревшей политике активации CLR версии 2.</span><span class="sxs-lookup"><span data-stu-id="9333b-122">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9333b-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="9333b-123">Remarks</span></span>  

 <span data-ttu-id="9333b-124">Этот метод приводит к тому, что среда CLR загружается, но не инициализируется.</span><span class="sxs-lookup"><span data-stu-id="9333b-124">This method causes the CLR to be loaded but not initialized.</span></span>  
  
 <span data-ttu-id="9333b-125">В следующей таблице приведены поддерживаемые сочетания для `rclsid` и `riid` .</span><span class="sxs-lookup"><span data-stu-id="9333b-125">The following table shows the supported combinations for `rclsid` and `riid`.</span></span>  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="9333b-126">CLSID_CorMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="9333b-126">CLSID_CorMetaDataDispenser</span></span>|<span data-ttu-id="9333b-127">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="9333b-127">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="9333b-128">CLSID_CorMetaDataDispenserRuntime</span><span class="sxs-lookup"><span data-stu-id="9333b-128">CLSID_CorMetaDataDispenserRuntime</span></span>|<span data-ttu-id="9333b-129">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="9333b-129">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="9333b-130">CLSID_CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="9333b-130">CLSID_CorRuntimeHost</span></span>|<span data-ttu-id="9333b-131">IID_ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="9333b-131">IID_ICorRuntimeHost</span></span>|  
|<span data-ttu-id="9333b-132">CLSID_CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="9333b-132">CLSID_CLRRuntimeHost</span></span>|<span data-ttu-id="9333b-133">IID_ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="9333b-133">IID_ICLRRuntimeHost</span></span>|  
|<span data-ttu-id="9333b-134">CLSID_TypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="9333b-134">CLSID_TypeNameFactory</span></span>|<span data-ttu-id="9333b-135">IID_ITypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="9333b-135">IID_ITypeNameFactory</span></span>|  
|<span data-ttu-id="9333b-136">CLSID_CLRDebuggingLegacy</span><span class="sxs-lookup"><span data-stu-id="9333b-136">CLSID_CLRDebuggingLegacy</span></span>|<span data-ttu-id="9333b-137">IID_ICorDebug</span><span class="sxs-lookup"><span data-stu-id="9333b-137">IID_ICorDebug</span></span>|  
|||  
|<span data-ttu-id="9333b-138">CLSID_CLRStrongName</span><span class="sxs-lookup"><span data-stu-id="9333b-138">CLSID_CLRStrongName</span></span>|<span data-ttu-id="9333b-139">IID_ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="9333b-139">IID_ICLRStrongName</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9333b-140">Требования</span><span class="sxs-lookup"><span data-stu-id="9333b-140">Requirements</span></span>  

 <span data-ttu-id="9333b-141">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9333b-141">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9333b-142">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="9333b-142">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9333b-143">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9333b-143">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9333b-144">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9333b-144">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9333b-145">См. также</span><span class="sxs-lookup"><span data-stu-id="9333b-145">See also</span></span>

- [<span data-ttu-id="9333b-146">Интерфейс ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="9333b-146">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="9333b-147">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="9333b-147">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="9333b-148">Размещение</span><span class="sxs-lookup"><span data-stu-id="9333b-148">Hosting</span></span>](index.md)
