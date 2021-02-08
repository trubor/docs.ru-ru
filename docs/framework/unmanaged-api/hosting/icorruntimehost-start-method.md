---
description: 'Дополнительные сведения о методе: ICorRuntimeHost:: Start'
title: Метод ICorRuntimeHost::Start
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Start
helpviewer_keywords:
- Start method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Start method [.NET Framework hosting]
ms.assetid: c66f3ac5-6489-484a-9bed-c31b711cee01
topic_type:
- apiref
ms.openlocfilehash: d07c0144c7192bc2f57927c294ea472cd6b47f9f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789610"
---
# <a name="icorruntimehoststart-method"></a><span data-ttu-id="6b7d4-103">Метод ICorRuntimeHost::Start</span><span class="sxs-lookup"><span data-stu-id="6b7d4-103">ICorRuntimeHost::Start Method</span></span>

<span data-ttu-id="6b7d4-104">Запускает среду CLR.</span><span class="sxs-lookup"><span data-stu-id="6b7d4-104">Starts the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b7d4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6b7d4-105">Syntax</span></span>  
  
```cpp  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="6b7d4-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="6b7d4-106">Return Value</span></span>  
  
|<span data-ttu-id="6b7d4-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6b7d4-107">HRESULT</span></span>|<span data-ttu-id="6b7d4-108">Описание:</span><span class="sxs-lookup"><span data-stu-id="6b7d4-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6b7d4-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="6b7d4-109">S_OK</span></span>|<span data-ttu-id="6b7d4-110">Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6b7d4-110">The operation was successful.</span></span>|  
|<span data-ttu-id="6b7d4-111">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="6b7d4-111">S_FALSE</span></span>|<span data-ttu-id="6b7d4-112">Не удалось завершить операцию.</span><span class="sxs-lookup"><span data-stu-id="6b7d4-112">The operation failed to complete.</span></span>|  
|<span data-ttu-id="6b7d4-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6b7d4-113">E_FAIL</span></span>|<span data-ttu-id="6b7d4-114">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="6b7d4-114">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="6b7d4-115">Если метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="6b7d4-115">If a method returns E_FAIL, the CLR is no longer usable in the process.</span></span> <span data-ttu-id="6b7d4-116">Последующие вызовы любых API размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6b7d4-116">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6b7d4-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6b7d4-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6b7d4-118">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="6b7d4-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b7d4-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="6b7d4-119">Remarks</span></span>  

 <span data-ttu-id="6b7d4-120">Как правило, вызов метода не требуется `Start` , поскольку среда CLR запускается автоматически при первом запросе на выполнение управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="6b7d4-120">It is typically not necessary to call the `Start` method, because the CLR starts automatically upon the first request to run managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b7d4-121">Требования</span><span class="sxs-lookup"><span data-stu-id="6b7d4-121">Requirements</span></span>  

 <span data-ttu-id="6b7d4-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b7d4-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b7d4-123">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6b7d4-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6b7d4-124">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6b7d4-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b7d4-125">**Платформа .NET Framework версии:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="6b7d4-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b7d4-126">См. также</span><span class="sxs-lookup"><span data-stu-id="6b7d4-126">See also</span></span>

- [<span data-ttu-id="6b7d4-127">Интерфейс ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="6b7d4-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
