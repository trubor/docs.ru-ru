---
description: 'Дополнительные сведения о методе: ICLRAssemblyIdentityManager:: Жетбиндингидентитифромстреам'
title: Метод ICLRAssemblyIdentityManager::GetBindingIdentityFromStream
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetBindingIdentityFromStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetBindingIdentityFromStream
helpviewer_keywords:
- GetBindingIdentityFromStream method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentityFromStream method [.NET Framework hosting]
ms.assetid: 40123b30-a589-46b3-95d3-af7b2b0baa05
topic_type:
- apiref
ms.openlocfilehash: aed5968a5f5c22a2f5cbea66a350dbe452368325
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716895"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromstream-method"></a><span data-ttu-id="6db13-103">Метод ICLRAssemblyIdentityManager::GetBindingIdentityFromStream</span><span class="sxs-lookup"><span data-stu-id="6db13-103">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Method</span></span>

<span data-ttu-id="6db13-104">Возвращает канонические данные удостоверений сборки для сборки в указанном потоке.</span><span class="sxs-lookup"><span data-stu-id="6db13-104">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6db13-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6db13-105">Syntax</span></span>  
  
```cpp  
HRESULT GetBindingIdentityFromStream (  
    [in] IStream    *pStream,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6db13-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6db13-106">Parameters</span></span>  

 `pStream`  
 <span data-ttu-id="6db13-107">окне Оцениваемый поток сборки.</span><span class="sxs-lookup"><span data-stu-id="6db13-107">[in] The assembly stream to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="6db13-108">окне Предоставляется для будущего расширения.</span><span class="sxs-lookup"><span data-stu-id="6db13-108">[in] Provided for future extensibility.</span></span> <span data-ttu-id="6db13-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT является единственным значением, которое поддерживает Текущая версия среды CLR.</span><span class="sxs-lookup"><span data-stu-id="6db13-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="6db13-110">заполняет Буфер, содержащий непрозрачные данные идентификации сборки.</span><span class="sxs-lookup"><span data-stu-id="6db13-110">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="6db13-111">[вход, выход] Размер `pwzBuffer` .</span><span class="sxs-lookup"><span data-stu-id="6db13-111">[in, out] The size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6db13-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="6db13-112">Return Value</span></span>  
  
|<span data-ttu-id="6db13-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6db13-113">HRESULT</span></span>|<span data-ttu-id="6db13-114">Описание:</span><span class="sxs-lookup"><span data-stu-id="6db13-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6db13-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="6db13-115">S_OK</span></span>|<span data-ttu-id="6db13-116">Метод возвратился успешно.</span><span class="sxs-lookup"><span data-stu-id="6db13-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="6db13-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="6db13-117">E_INVALIDARG</span></span>|<span data-ttu-id="6db13-118">Переданный параметр `pStream` имеет значение null.</span><span class="sxs-lookup"><span data-stu-id="6db13-118">The supplied `pStream` is null.</span></span>|  
|<span data-ttu-id="6db13-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="6db13-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="6db13-120">Размер `pwzBuffer` слишком мал.</span><span class="sxs-lookup"><span data-stu-id="6db13-120">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="6db13-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6db13-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6db13-122">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="6db13-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6db13-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6db13-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6db13-124">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="6db13-124">The call timed out.</span></span>|  
|<span data-ttu-id="6db13-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6db13-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6db13-126">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="6db13-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6db13-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6db13-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6db13-128">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="6db13-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6db13-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6db13-129">E_FAIL</span></span>|<span data-ttu-id="6db13-130">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="6db13-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6db13-131">Если метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="6db13-131">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6db13-132">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6db13-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6db13-133">Требования</span><span class="sxs-lookup"><span data-stu-id="6db13-133">Requirements</span></span>  

 <span data-ttu-id="6db13-134">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6db13-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6db13-135">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6db13-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6db13-136">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6db13-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6db13-137">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6db13-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6db13-138">См. также</span><span class="sxs-lookup"><span data-stu-id="6db13-138">See also</span></span>

- [<span data-ttu-id="6db13-139">Интерфейс ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="6db13-139">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="6db13-140">Интерфейс ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="6db13-140">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
