---
description: 'Дополнительные сведения о методе: ICorRuntimeHost:: останавливаться'
title: Метод ICorRuntimeHost::Stop
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.Stop
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Stop
helpviewer_keywords:
- Stop method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Stop method [.NET Framework hosting]
ms.assetid: 46a0d450-b516-4bef-8b71-8d3bf265cbed
topic_type:
- apiref
ms.openlocfilehash: b44c77b7d0fe3a078efa11756f5fac7ba400ca5e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789597"
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="fd719-103">Метод ICorRuntimeHost::Stop</span><span class="sxs-lookup"><span data-stu-id="fd719-103">ICorRuntimeHost::Stop Method</span></span>

<span data-ttu-id="fd719-104">Останавливает выполнение кода в среде выполнения для текущего процесса.</span><span class="sxs-lookup"><span data-stu-id="fd719-104">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd719-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fd719-105">Syntax</span></span>  
  
```cpp  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="fd719-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="fd719-106">Return Value</span></span>  
  
|<span data-ttu-id="fd719-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fd719-107">HRESULT</span></span>|<span data-ttu-id="fd719-108">Описание:</span><span class="sxs-lookup"><span data-stu-id="fd719-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fd719-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="fd719-109">S_OK</span></span>|<span data-ttu-id="fd719-110">Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="fd719-110">The operation was successful.</span></span>|  
|<span data-ttu-id="fd719-111">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="fd719-111">S_FALSE</span></span>|<span data-ttu-id="fd719-112">Не удалось завершить операцию.</span><span class="sxs-lookup"><span data-stu-id="fd719-112">The operation failed to complete.</span></span>|  
|<span data-ttu-id="fd719-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fd719-113">E_FAIL</span></span>|<span data-ttu-id="fd719-114">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="fd719-114">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="fd719-115">Если метод возвращает E_FAIL, общеязыковая среда выполнения (CLR) больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="fd719-115">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="fd719-116">Последующие вызовы любых API размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fd719-116">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fd719-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fd719-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fd719-118">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="fd719-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd719-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="fd719-119">Remarks</span></span>  

 <span data-ttu-id="fd719-120">Как правило, вызов метода не требуется `Stop` , поскольку код прекращает выполнение при завершении процесса.</span><span class="sxs-lookup"><span data-stu-id="fd719-120">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fd719-121">После вызова `Stop` Среда CLR не может быть инициализирована в том же процессе.</span><span class="sxs-lookup"><span data-stu-id="fd719-121">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd719-122">Требования</span><span class="sxs-lookup"><span data-stu-id="fd719-122">Requirements</span></span>  

 <span data-ttu-id="fd719-123">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd719-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd719-124">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fd719-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fd719-125">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fd719-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fd719-126">**Платформа .NET Framework версии:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="fd719-126">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd719-127">См. также</span><span class="sxs-lookup"><span data-stu-id="fd719-127">See also</span></span>

- [<span data-ttu-id="fd719-128">Интерфейс ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="fd719-128">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
