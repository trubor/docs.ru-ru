---
description: 'Дополнительные сведения о методе: IHostCrst:: Enter'
title: Метод IHostCrst::Enter
ms.date: 03/30/2017
api_name:
- IHostCrst.Enter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::Enter
helpviewer_keywords:
- Enter method [.NET Framework hosting]
- IHostCrst::Enter method [.NET Framework hosting]
ms.assetid: 100dd7eb-7053-4295-9bb3-32ba47f6ec79
topic_type:
- apiref
ms.openlocfilehash: ef8e4ce71cde75fe6b834802b08d22aedbd6fab9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789454"
---
# <a name="ihostcrstenter-method"></a><span data-ttu-id="57855-103">Метод IHostCrst::Enter</span><span class="sxs-lookup"><span data-stu-id="57855-103">IHostCrst::Enter Method</span></span>

<span data-ttu-id="57855-104">Вводит критическую секцию, представленную текущим экземпляром [IHostCrst](ihostcrst-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="57855-104">Enters the critical section that is represented by the current [IHostCrst](ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57855-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="57855-105">Syntax</span></span>  
  
```cpp  
HRESULT Enter (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57855-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="57855-106">Parameters</span></span>  

 `option`  
 <span data-ttu-id="57855-107">окне Одно из значений [WAIT_OPTION](wait-option-enumeration.md) , указывающее, какое действие должно предпринять узел при блокировке операции.</span><span class="sxs-lookup"><span data-stu-id="57855-107">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57855-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="57855-108">Return Value</span></span>  
  
|<span data-ttu-id="57855-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="57855-109">HRESULT</span></span>|<span data-ttu-id="57855-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="57855-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="57855-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="57855-111">S_OK</span></span>|<span data-ttu-id="57855-112">`Enter` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="57855-112">`Enter` returned successfully.</span></span>|  
|<span data-ttu-id="57855-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="57855-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="57855-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="57855-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="57855-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="57855-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="57855-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="57855-116">The call timed out.</span></span>|  
|<span data-ttu-id="57855-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="57855-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="57855-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="57855-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="57855-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="57855-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="57855-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="57855-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="57855-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="57855-121">E_FAIL</span></span>|<span data-ttu-id="57855-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="57855-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="57855-123">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="57855-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="57855-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="57855-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57855-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="57855-125">Remarks</span></span>  

 <span data-ttu-id="57855-126">`Enter` отражает функцию Win32 `EnterCriticalSection` .</span><span class="sxs-lookup"><span data-stu-id="57855-126">`Enter` mirrors the Win32 `EnterCriticalSection` function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="57855-127">Этот метод не возвращает значение до тех пор, пока не будет указан критический раздел.</span><span class="sxs-lookup"><span data-stu-id="57855-127">This method does not return until the critical section is entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57855-128">Требования</span><span class="sxs-lookup"><span data-stu-id="57855-128">Requirements</span></span>  

 <span data-ttu-id="57855-129">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57855-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57855-130">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="57855-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="57855-131">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="57855-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57855-132">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57855-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57855-133">См. также</span><span class="sxs-lookup"><span data-stu-id="57855-133">See also</span></span>

- [<span data-ttu-id="57855-134">Интерфейс ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="57855-134">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="57855-135">Интерфейс IHostCrst</span><span class="sxs-lookup"><span data-stu-id="57855-135">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="57855-136">Интерфейс IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="57855-136">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
