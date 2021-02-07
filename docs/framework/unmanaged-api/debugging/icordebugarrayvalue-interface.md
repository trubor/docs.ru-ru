---
description: 'Дополнительные сведения о: интерфейс ICorDebugArrayValue'
title: Интерфейс ICorDebugArrayValue
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue interface
helpviewer_keywords:
- ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: dc437751-7093-44e2-bfdc-191d9ce3c192
topic_type:
- apiref
ms.openlocfilehash: 2b91c910b9444b061b4a6bea715667bca6a4629c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722897"
---
# <a name="icordebugarrayvalue-interface"></a><span data-ttu-id="cd731-103">Интерфейс ICorDebugArrayValue</span><span class="sxs-lookup"><span data-stu-id="cd731-103">ICorDebugArrayValue Interface</span></span>

<span data-ttu-id="cd731-104">Подкласс ICorDebugHeapValue, представляющий одномерный или многомерный массив.</span><span class="sxs-lookup"><span data-stu-id="cd731-104">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cd731-105">Методы</span><span class="sxs-lookup"><span data-stu-id="cd731-105">Methods</span></span>  
  
|<span data-ttu-id="cd731-106">Метод</span><span class="sxs-lookup"><span data-stu-id="cd731-106">Method</span></span>|<span data-ttu-id="cd731-107">Описание</span><span class="sxs-lookup"><span data-stu-id="cd731-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cd731-108">Метод GetBaseIndicies</span><span class="sxs-lookup"><span data-stu-id="cd731-108">GetBaseIndicies Method</span></span>](icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="cd731-109">Возвращает базовый индекс каждого измерения в массиве.</span><span class="sxs-lookup"><span data-stu-id="cd731-109">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="cd731-110">Метод GetCount</span><span class="sxs-lookup"><span data-stu-id="cd731-110">GetCount Method</span></span>](icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="cd731-111">Возвращает общее число элементов в массиве.</span><span class="sxs-lookup"><span data-stu-id="cd731-111">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="cd731-112">Метод GetDimensions</span><span class="sxs-lookup"><span data-stu-id="cd731-112">GetDimensions Method</span></span>](icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="cd731-113">Возвращает размеры массива.</span><span class="sxs-lookup"><span data-stu-id="cd731-113">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="cd731-114">Метод GetElement</span><span class="sxs-lookup"><span data-stu-id="cd731-114">GetElement Method</span></span>](icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="cd731-115">Возвращает значение, представляющее заданный элемент в массиве.</span><span class="sxs-lookup"><span data-stu-id="cd731-115">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="cd731-116">Метод GetElementAtPosition</span><span class="sxs-lookup"><span data-stu-id="cd731-116">GetElementAtPosition Method</span></span>](icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="cd731-117">Возвращает элемент в заданной позиции, рассматривая массив как одномерный массив с отсчетом от нуля.</span><span class="sxs-lookup"><span data-stu-id="cd731-117">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="cd731-118">Метод GetElementType</span><span class="sxs-lookup"><span data-stu-id="cd731-118">GetElementType Method</span></span>](icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="cd731-119">Возвращает простой тип элементов в массиве.</span><span class="sxs-lookup"><span data-stu-id="cd731-119">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="cd731-120">Метод GetRank</span><span class="sxs-lookup"><span data-stu-id="cd731-120">GetRank Method</span></span>](icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="cd731-121">Получает число измерений в массиве.</span><span class="sxs-lookup"><span data-stu-id="cd731-121">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="cd731-122">Метод HasBaseIndicies</span><span class="sxs-lookup"><span data-stu-id="cd731-122">HasBaseIndicies Method</span></span>](icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="cd731-123">Определяет, имеет ли массив базовые индексы.</span><span class="sxs-lookup"><span data-stu-id="cd731-123">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd731-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="cd731-124">Remarks</span></span>  

 <span data-ttu-id="cd731-125">`ICorDebugArrayValue` поддерживает одномерный и многомерный массивы.</span><span class="sxs-lookup"><span data-stu-id="cd731-125">`ICorDebugArrayValue` supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cd731-126">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="cd731-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd731-127">Требования</span><span class="sxs-lookup"><span data-stu-id="cd731-127">Requirements</span></span>  

 <span data-ttu-id="cd731-128">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd731-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd731-129">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cd731-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cd731-130">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd731-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd731-131">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd731-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd731-132">См. также</span><span class="sxs-lookup"><span data-stu-id="cd731-132">See also</span></span>

- [<span data-ttu-id="cd731-133">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="cd731-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
