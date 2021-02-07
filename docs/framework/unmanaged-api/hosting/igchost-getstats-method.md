---
description: 'Дополнительные сведения о методе: IGCHost:: stats'
title: Метод IGCHost::GetStats
ms.date: 03/30/2017
api_name:
- IGCHost.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetStats
helpviewer_keywords:
- GetStats method, IGCHost interface [.NET Framework hosting]
- IGCHost::GetStats method [.NET Framework hosting]
ms.assetid: c4ae022c-46ac-4f19-9ddd-09b955f19412
topic_type:
- apiref
ms.openlocfilehash: 564224d01e23c8ac1fe81025ee87dabc41ed5166
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709698"
---
# <a name="igchostgetstats-method"></a><span data-ttu-id="8d944-103">Метод IGCHost::GetStats</span><span class="sxs-lookup"><span data-stu-id="8d944-103">IGCHost::GetStats Method</span></span>

<span data-ttu-id="8d944-104">Возвращает статистику текущего состояния системы сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="8d944-104">Gets the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d944-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8d944-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d944-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8d944-106">Parameters</span></span>  

 `pStats`  
 <span data-ttu-id="8d944-107">[вход, выход] Указатель на структуру [COR_GC_STATS](cor-gc-stats-structure.md) , которая содержит статистику для текущего состояния системы сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="8d944-107">[in, out] A pointer to a [COR_GC_STATS](cor-gc-stats-structure.md) structure that contains the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d944-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="8d944-108">Remarks</span></span>  

 <span data-ttu-id="8d944-109">Статистика может использоваться системой интеллектуального распределения, чтобы помочь системе сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="8d944-109">The statistics can be used by a smart allocation system to help the garbage collection system operate.</span></span> <span data-ttu-id="8d944-110">Например, система распределения может определить, что после проверки статистики потребуется добавить память или принудительно выполнить сбор.</span><span class="sxs-lookup"><span data-stu-id="8d944-110">For example, the allocation system may determine, after reviewing the statistics, that it needs to add more memory or force a collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d944-111">Требования</span><span class="sxs-lookup"><span data-stu-id="8d944-111">Requirements</span></span>  

 <span data-ttu-id="8d944-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d944-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d944-113">**Заголовок:** Гчост. idl, Гчост. h</span><span class="sxs-lookup"><span data-stu-id="8d944-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="8d944-114">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8d944-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8d944-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d944-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d944-116">См. также</span><span class="sxs-lookup"><span data-stu-id="8d944-116">See also</span></span>

- [<span data-ttu-id="8d944-117">Интерфейс IGCHost</span><span class="sxs-lookup"><span data-stu-id="8d944-117">IGCHost Interface</span></span>](igchost-interface.md)
