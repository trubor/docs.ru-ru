---
description: 'Дополнительные сведения о методе: ICorRuntimeHost:: CloseEnum'
title: Метод ICorRuntimeHost::CloseEnum
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CloseEnum
helpviewer_keywords:
- CloseEnum method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::CloseEnum method [.NET Framework hosting]
ms.assetid: f7ce7e8c-0a3e-4587-a180-063e2b85940e
topic_type:
- apiref
ms.openlocfilehash: 1fc18ff3e00f85a4f047417f880ec2b0e06496b7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789727"
---
# <a name="icorruntimehostcloseenum-method"></a><span data-ttu-id="6b9a6-103">Метод ICorRuntimeHost::CloseEnum</span><span class="sxs-lookup"><span data-stu-id="6b9a6-103">ICorRuntimeHost::CloseEnum Method</span></span>

<span data-ttu-id="6b9a6-104">Сбрасывает перечислитель домена обратно в начало списка доменов.</span><span class="sxs-lookup"><span data-stu-id="6b9a6-104">Resets a domain enumerator back to the beginning of the domain list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b9a6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6b9a6-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum (  
    [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b9a6-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6b9a6-106">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="6b9a6-107">окне Перечислитель для сброса.</span><span class="sxs-lookup"><span data-stu-id="6b9a6-107">[in] The enumerator to reset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b9a6-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="6b9a6-108">Return Value</span></span>  
  
|<span data-ttu-id="6b9a6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6b9a6-109">HRESULT</span></span>|<span data-ttu-id="6b9a6-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="6b9a6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6b9a6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6b9a6-111">S_OK</span></span>|<span data-ttu-id="6b9a6-112">Операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="6b9a6-112">The operation was successful.</span></span>|  
|<span data-ttu-id="6b9a6-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="6b9a6-113">S_FALSE</span></span>|<span data-ttu-id="6b9a6-114">Не удалось завершить операцию.</span><span class="sxs-lookup"><span data-stu-id="6b9a6-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="6b9a6-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6b9a6-115">E_FAIL</span></span>|<span data-ttu-id="6b9a6-116">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="6b9a6-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="6b9a6-117">Если метод возвращает E_FAIL, общеязыковая среда выполнения (CLR) больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="6b9a6-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="6b9a6-118">Последующие вызовы любых API размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6b9a6-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6b9a6-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6b9a6-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6b9a6-120">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="6b9a6-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6b9a6-121">Требования</span><span class="sxs-lookup"><span data-stu-id="6b9a6-121">Requirements</span></span>  

 <span data-ttu-id="6b9a6-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b9a6-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b9a6-123">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6b9a6-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6b9a6-124">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6b9a6-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b9a6-125">**Платформа .NET Framework версии:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="6b9a6-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b9a6-126">См. также</span><span class="sxs-lookup"><span data-stu-id="6b9a6-126">See also</span></span>

- [<span data-ttu-id="6b9a6-127">Функция CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="6b9a6-127">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="6b9a6-128">Интерфейс ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="6b9a6-128">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
