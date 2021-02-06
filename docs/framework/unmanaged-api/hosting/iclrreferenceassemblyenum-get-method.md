---
description: 'Дополнительные сведения о методе: ICLRReferenceAssemblyEnum:: Get'
title: Метод ICLRReferenceAssemblyEnum::Get
ms.date: 03/30/2017
api_name:
- ICLRReferenceAssemblyEnum.Get
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRReferenceAssemblyEnum::Get
helpviewer_keywords:
- ICLRReferenceAssemblyEnum::Get method [.NET Framework hosting]
- Get method, ICLRReferenceAssemblyEnum interface [.NET Framework hosting]
ms.assetid: f21c1612-9c5d-4abc-a337-577086d29c17
topic_type:
- apiref
ms.openlocfilehash: ea4e71631a9ebb381f721b78f17507603891a032
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637304"
---
# <a name="iclrreferenceassemblyenumget-method"></a><span data-ttu-id="7fe6b-103">Метод ICLRReferenceAssemblyEnum::Get</span><span class="sxs-lookup"><span data-stu-id="7fe6b-103">ICLRReferenceAssemblyEnum::Get Method</span></span>

<span data-ttu-id="7fe6b-104">Возвращает удостоверение сборки по заданному индексу.</span><span class="sxs-lookup"><span data-stu-id="7fe6b-104">Gets the assembly identity at the supplied index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fe6b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7fe6b-105">Syntax</span></span>  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7fe6b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7fe6b-106">Parameters</span></span>  

 `dwIndex`  
 <span data-ttu-id="7fe6b-107">окне Отсчитываемый от нуля индекс возвращаемого удостоверения сборки.</span><span class="sxs-lookup"><span data-stu-id="7fe6b-107">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="7fe6b-108">заполняет Буфер, содержащий данные удостоверения сборки.</span><span class="sxs-lookup"><span data-stu-id="7fe6b-108">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="7fe6b-109">[вход, выход] Размер `pwzBuffer` буфера.</span><span class="sxs-lookup"><span data-stu-id="7fe6b-109">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7fe6b-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="7fe6b-110">Return Value</span></span>  
  
|<span data-ttu-id="7fe6b-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7fe6b-111">HRESULT</span></span>|<span data-ttu-id="7fe6b-112">Описание:</span><span class="sxs-lookup"><span data-stu-id="7fe6b-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7fe6b-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="7fe6b-113">S_OK</span></span>|<span data-ttu-id="7fe6b-114">`Get` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="7fe6b-114">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="7fe6b-115">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="7fe6b-115">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="7fe6b-116">`pwzBuffer` слишком мал.</span><span class="sxs-lookup"><span data-stu-id="7fe6b-116">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="7fe6b-117">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="7fe6b-117">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="7fe6b-118">Перечисление не содержит больше элементов.</span><span class="sxs-lookup"><span data-stu-id="7fe6b-118">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="7fe6b-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7fe6b-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7fe6b-120">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="7fe6b-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7fe6b-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7fe6b-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7fe6b-122">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="7fe6b-122">The call timed out.</span></span>|  
|<span data-ttu-id="7fe6b-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7fe6b-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7fe6b-124">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="7fe6b-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7fe6b-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7fe6b-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7fe6b-126">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="7fe6b-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7fe6b-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7fe6b-127">E_FAIL</span></span>|<span data-ttu-id="7fe6b-128">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="7fe6b-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7fe6b-129">Если метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="7fe6b-129">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7fe6b-130">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7fe6b-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7fe6b-131">Remarks</span><span class="sxs-lookup"><span data-stu-id="7fe6b-131">Remarks</span></span>  

 <span data-ttu-id="7fe6b-132">`Get` обычно вызывается дважды.</span><span class="sxs-lookup"><span data-stu-id="7fe6b-132">`Get` is typically called twice.</span></span> <span data-ttu-id="7fe6b-133">Первый вызов предоставляет значение NULL для `pwzBuffer` , а устанавливает `pcchBufferSize` в качестве размера, соответствующего `pwzBuffer` .</span><span class="sxs-lookup"><span data-stu-id="7fe6b-133">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="7fe6b-134">Второй вызов предоставляет соответствующий размер `pwzBuffer` и содержит канонические данные удостоверений сборки после завершения.</span><span class="sxs-lookup"><span data-stu-id="7fe6b-134">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fe6b-135">Требования</span><span class="sxs-lookup"><span data-stu-id="7fe6b-135">Requirements</span></span>  

 <span data-ttu-id="7fe6b-136">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fe6b-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fe6b-137">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7fe6b-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7fe6b-138">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7fe6b-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7fe6b-139">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fe6b-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fe6b-140">См. также</span><span class="sxs-lookup"><span data-stu-id="7fe6b-140">See also</span></span>

- [<span data-ttu-id="7fe6b-141">Интерфейс ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="7fe6b-141">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="7fe6b-142">Интерфейс ICLRReferenceAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="7fe6b-142">ICLRReferenceAssemblyEnum Interface</span></span>](iclrreferenceassemblyenum-interface.md)
