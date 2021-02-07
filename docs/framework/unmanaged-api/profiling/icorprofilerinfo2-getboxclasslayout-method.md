---
description: 'Дополнительные сведения о методе: ICorProfilerInfo2:: Жетбокскласслайаут'
title: Метод ICorProfilerInfo2::GetBoxClassLayout
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetBoxClassLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetBoxClassLayout
helpviewer_keywords:
- GetBoxClassLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetBoxClassLayout method [.NET Framework profiling]
ms.assetid: 624672b5-1189-488a-85d2-3e12b49617c1
topic_type:
- apiref
ms.openlocfilehash: 0bc9ccc80da8bcc89cfe73eaa240310c01e6ca8f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760522"
---
# <a name="icorprofilerinfo2getboxclasslayout-method"></a><span data-ttu-id="1553c-103">Метод ICorProfilerInfo2::GetBoxClassLayout</span><span class="sxs-lookup"><span data-stu-id="1553c-103">ICorProfilerInfo2::GetBoxClassLayout Method</span></span>

<span data-ttu-id="1553c-104">Возвращает сведения о расположении указанного типа значения при его упаковке.</span><span class="sxs-lookup"><span data-stu-id="1553c-104">Gets information about where the specified value type is located when it is boxed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1553c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1553c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetBoxClassLayout(  
    [in] ClassID classId,  
    [out] ULONG32 *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1553c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1553c-106">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="1553c-107">окне Идентификатор класса, который описывает упакованный тип значения.</span><span class="sxs-lookup"><span data-stu-id="1553c-107">[in] The ID of the class that describes the value type that is boxed.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="1553c-108">заполняет Целое число, которое является смещением относительно указателя на идентификатор упакованного объекта для типа значения.</span><span class="sxs-lookup"><span data-stu-id="1553c-108">[out] An integer that is the offset, relative to the boxed object ID pointer, of the value type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1553c-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="1553c-109">Remarks</span></span>  

 <span data-ttu-id="1553c-110">`pBufferOffset`Значение — это расположение типа значения в поле.</span><span class="sxs-lookup"><span data-stu-id="1553c-110">The `pBufferOffset` value is the location of the value type within a box.</span></span> <span data-ttu-id="1553c-111">После `pBufferOffset` применения к упакованному объекту можно использовать макет класса типа значения для интерпретации значения объекта.</span><span class="sxs-lookup"><span data-stu-id="1553c-111">After `pBufferOffset` is applied to a boxed object, the value type's class layout can be used to interpret the object's value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1553c-112">Требования</span><span class="sxs-lookup"><span data-stu-id="1553c-112">Requirements</span></span>  

 <span data-ttu-id="1553c-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1553c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1553c-114">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1553c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1553c-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1553c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1553c-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1553c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1553c-117">См. также</span><span class="sxs-lookup"><span data-stu-id="1553c-117">See also</span></span>

- [<span data-ttu-id="1553c-118">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="1553c-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="1553c-119">Интерфейс ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="1553c-119">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
