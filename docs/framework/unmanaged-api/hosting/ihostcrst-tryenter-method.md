---
description: 'Дополнительные сведения о методе: IHostCrst:: TryEnter'
title: Метод IHostCrst::TryEnter
ms.date: 03/30/2017
api_name:
- IHostCrst.TryEnter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::TryEnter
helpviewer_keywords:
- IHostCrst::TryEnter method [.NET Framework hosting]
- TryEnter method [.NET Framework hosting]
ms.assetid: a922fa98-beab-4f09-a342-cc94fc65687f
topic_type:
- apiref
ms.openlocfilehash: 59c632b7c9edd422e2ceee1e0526a7bb077759a4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708727"
---
# <a name="ihostcrsttryenter-method"></a><span data-ttu-id="a19fc-103">Метод IHostCrst::TryEnter</span><span class="sxs-lookup"><span data-stu-id="a19fc-103">IHostCrst::TryEnter Method</span></span>

<span data-ttu-id="a19fc-104">Пытается ввести критическую секцию, представленную текущим экземпляром [IHostCrst](ihostcrst-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a19fc-104">Attempts to enter the critical section represented by the current [IHostCrst](ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a19fc-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a19fc-105">Syntax</span></span>  
  
```cpp  
HRESULT TryEnter (  
    [in]  DWORD  option,  
    [out] BOOL   *pbSucceeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a19fc-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a19fc-106">Parameters</span></span>  

 `option`  
 <span data-ttu-id="a19fc-107">окне Одно из значений [WAIT_OPTION](wait-option-enumeration.md) , указывающее, какое действие должно предпринять узел при блокировке операции.</span><span class="sxs-lookup"><span data-stu-id="a19fc-107">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
 `pbSucceeded`  
 <span data-ttu-id="a19fc-108">[out] `true` значение, если можно указать критический раздел; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="a19fc-108">[out] `true` if the critical section can be entered; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a19fc-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="a19fc-109">Return Value</span></span>  
  
|<span data-ttu-id="a19fc-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a19fc-110">HRESULT</span></span>|<span data-ttu-id="a19fc-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="a19fc-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a19fc-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="a19fc-112">S_OK</span></span>|<span data-ttu-id="a19fc-113">`TryEnter` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="a19fc-113">`TryEnter` returned successfully.</span></span>|  
|<span data-ttu-id="a19fc-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a19fc-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a19fc-115">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="a19fc-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a19fc-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a19fc-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a19fc-117">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="a19fc-117">The call timed out.</span></span>|  
|<span data-ttu-id="a19fc-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a19fc-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a19fc-119">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="a19fc-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a19fc-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a19fc-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a19fc-121">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="a19fc-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a19fc-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a19fc-122">E_FAIL</span></span>|<span data-ttu-id="a19fc-123">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="a19fc-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a19fc-124">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="a19fc-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a19fc-125">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a19fc-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a19fc-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="a19fc-126">Remarks</span></span>  

 <span data-ttu-id="a19fc-127">`TryEnter` Возвращает значение немедленно и указывает, вошел ли вызывающий поток в критическую секцию.</span><span class="sxs-lookup"><span data-stu-id="a19fc-127">`TryEnter` returns immediately and indicates whether the calling thread entered the critical section.</span></span> <span data-ttu-id="a19fc-128">Этот метод отражает функцию Wind32 `TryEnterCriticalSection` .</span><span class="sxs-lookup"><span data-stu-id="a19fc-128">This method mirrors the Wind32 `TryEnterCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a19fc-129">Требования</span><span class="sxs-lookup"><span data-stu-id="a19fc-129">Requirements</span></span>  

 <span data-ttu-id="a19fc-130">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a19fc-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a19fc-131">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a19fc-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a19fc-132">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a19fc-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a19fc-133">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a19fc-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a19fc-134">См. также</span><span class="sxs-lookup"><span data-stu-id="a19fc-134">See also</span></span>

- [<span data-ttu-id="a19fc-135">Интерфейс ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="a19fc-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="a19fc-136">Интерфейс IHostCrst</span><span class="sxs-lookup"><span data-stu-id="a19fc-136">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="a19fc-137">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="a19fc-137">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
