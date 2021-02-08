---
description: 'Дополнительные сведения о методе: ICorProfilerObjectEnum:: Next'
title: Метод ICorProfilerObjectEnum::Next
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Next
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Next
helpviewer_keywords:
- Next method, ICorProfilerObjectEnum interface [.NET Framework profiling]
- ICorProfilerObjectEnum::Next method [.NET Framework profiling]
ms.assetid: b420433c-5ebe-4986-bba1-97902e6db819
topic_type:
- apiref
ms.openlocfilehash: 7f61fa1d4e28043bf5eda95f67dde0d8e87d8c0d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781419"
---
# <a name="icorprofilerobjectenumnext-method"></a><span data-ttu-id="1c410-103">Метод ICorProfilerObjectEnum::Next</span><span class="sxs-lookup"><span data-stu-id="1c410-103">ICorProfilerObjectEnum::Next Method</span></span>

<span data-ttu-id="1c410-104">Возвращает указанное количество смежных объектов из последовательной коллекции объектов, начиная с текущей позиции перечислителя в последовательности.</span><span class="sxs-lookup"><span data-stu-id="1c410-104">Gets the specified number of contiguous objects from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c410-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1c410-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG                    celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        ObjectID                  objects[],  
    [out] ULONG                   *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c410-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1c410-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="1c410-107">[in] Количество объектов, которые должны быть получены.</span><span class="sxs-lookup"><span data-stu-id="1c410-107">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="1c410-108">заполняет Массив `ObjectID` значений, каждый из которых представляет извлеченный объект.</span><span class="sxs-lookup"><span data-stu-id="1c410-108">[out] An array of `ObjectID` values, each of which represents a retrieved object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="1c410-109">[out] Указатель на число элементов, фактически извлеченных в массив `objects`.</span><span class="sxs-lookup"><span data-stu-id="1c410-109">[out] A pointer to the number of elements actually returned in the `objects` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c410-110">Требования</span><span class="sxs-lookup"><span data-stu-id="1c410-110">Requirements</span></span>  

 <span data-ttu-id="1c410-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c410-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c410-112">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1c410-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1c410-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c410-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c410-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c410-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c410-115">См. также</span><span class="sxs-lookup"><span data-stu-id="1c410-115">See also</span></span>

- [<span data-ttu-id="1c410-116">Интерфейс ICorProfilerObjectEnum</span><span class="sxs-lookup"><span data-stu-id="1c410-116">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
