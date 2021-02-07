---
description: 'Дополнительные сведения о методе: ICorDebugEval:: NewArray'
title: Метод ICorDebugEval::NewArray
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewArray
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewArray
helpviewer_keywords:
- NewArray method [.NET Framework debugging]
- ICorDebugEval::NewArray method [.NET Framework debugging]
ms.assetid: cc79a67d-5368-434d-a943-209db90491b9
topic_type:
- apiref
ms.openlocfilehash: 1344a99450974369533b1c54b641c036fc64e3ea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693984"
---
# <a name="icordebugevalnewarray-method"></a><span data-ttu-id="10839-103">Метод ICorDebugEval::NewArray</span><span class="sxs-lookup"><span data-stu-id="10839-103">ICorDebugEval::NewArray Method</span></span>

<span data-ttu-id="10839-104">Выделяет новый массив указанного типа элемента и измерений.</span><span class="sxs-lookup"><span data-stu-id="10839-104">Allocates a new array of the specified element type and dimensions.</span></span>  
  
 <span data-ttu-id="10839-105">Этот метод является устаревшим в платформа .NET Framework версии 2,0.</span><span class="sxs-lookup"><span data-stu-id="10839-105">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="10839-106">Вместо этого используйте [ICorDebugEval2:: NewParameterizedArray](icordebugeval2-newparameterizedarray-method.md) .</span><span class="sxs-lookup"><span data-stu-id="10839-106">Use [ICorDebugEval2::NewParameterizedArray](icordebugeval2-newparameterizedarray-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10839-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="10839-107">Syntax</span></span>  
  
```cpp  
HRESULT NewArray (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [in] ULONG32            rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10839-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="10839-108">Parameters</span></span>  

 `elementType`  
 <span data-ttu-id="10839-109">окне Значение перечисления Корелементтипе, указывающее тип элемента массива.</span><span class="sxs-lookup"><span data-stu-id="10839-109">[in] A value of the CorElementType enumeration that specifies the element type of the array.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="10839-110">окне Указатель на объект ICorDebugClass, указывающий класс элемента.</span><span class="sxs-lookup"><span data-stu-id="10839-110">[in] A pointer to a ICorDebugClass object that specifies the class of the element.</span></span> <span data-ttu-id="10839-111">Это значение может быть равно null, если тип элемента является типом-примитивом.</span><span class="sxs-lookup"><span data-stu-id="10839-111">This value may be null if the element type is a primitive type.</span></span>  
  
 `rank`  
 <span data-ttu-id="10839-112">окне Число измерений массива.</span><span class="sxs-lookup"><span data-stu-id="10839-112">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="10839-113">В платформа .NET Framework 2,0 это значение должно быть равно 1.</span><span class="sxs-lookup"><span data-stu-id="10839-113">In the .NET Framework 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="10839-114">окне Размер каждого измерения массива в байтах.</span><span class="sxs-lookup"><span data-stu-id="10839-114">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="10839-115">[в] Необязательно.</span><span class="sxs-lookup"><span data-stu-id="10839-115">[in] Optional.</span></span> <span data-ttu-id="10839-116">Нижняя граница каждого измерения массива.</span><span class="sxs-lookup"><span data-stu-id="10839-116">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="10839-117">Если это значение пропущено, для каждого измерения предполагается Нижняя граница, равная нулю.</span><span class="sxs-lookup"><span data-stu-id="10839-117">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10839-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="10839-118">Remarks</span></span>  

 <span data-ttu-id="10839-119">Массив всегда создается в домене приложения, в котором в данный момент выполняется поток.</span><span class="sxs-lookup"><span data-stu-id="10839-119">The array is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10839-120">Требования</span><span class="sxs-lookup"><span data-stu-id="10839-120">Requirements</span></span>  

 <span data-ttu-id="10839-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10839-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10839-122">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="10839-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10839-123">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10839-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10839-124">**Платформа .NET Framework версии:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="10839-124">**.NET Framework Versions:** 1.1, 1.0</span></span>
