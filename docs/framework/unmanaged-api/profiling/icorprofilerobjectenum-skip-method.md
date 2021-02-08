---
description: 'Дополнительные сведения о методе: ICorProfilerObjectEnum:: Skip'
title: Метод ICorProfilerObjectEnum::Skip
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Skip
helpviewer_keywords:
- ICorProfilerObjectEnum::Skip method [.NET Framework profiling]
- Skip method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: f8e498f8-f93a-4b82-bd22-55bdbf5e8d45
topic_type:
- apiref
ms.openlocfilehash: 8a2aa5dd2b905931b97fafa4db6709aab16aacc4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781263"
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="daf52-103">Метод ICorProfilerObjectEnum::Skip</span><span class="sxs-lookup"><span data-stu-id="daf52-103">ICorProfilerObjectEnum::Skip Method</span></span>

<span data-ttu-id="daf52-104">Перемещает курсор этого перечислителя из текущей позиции, чтобы было пропущено указанное число элементов.</span><span class="sxs-lookup"><span data-stu-id="daf52-104">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daf52-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="daf52-105">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="daf52-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="daf52-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="daf52-107">окне Число пропущенных элементов.</span><span class="sxs-lookup"><span data-stu-id="daf52-107">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="daf52-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="daf52-108">Remarks</span></span>  

 <span data-ttu-id="daf52-109">Новая позиции курсора перечислителя: (Текущая позиции) + `celt` .</span><span class="sxs-lookup"><span data-stu-id="daf52-109">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="daf52-110">Требования</span><span class="sxs-lookup"><span data-stu-id="daf52-110">Requirements</span></span>  

 <span data-ttu-id="daf52-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="daf52-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="daf52-112">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="daf52-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="daf52-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="daf52-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="daf52-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="daf52-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daf52-115">См. также</span><span class="sxs-lookup"><span data-stu-id="daf52-115">See also</span></span>

- [<span data-ttu-id="daf52-116">Интерфейс ICorProfilerObjectEnum</span><span class="sxs-lookup"><span data-stu-id="daf52-116">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
