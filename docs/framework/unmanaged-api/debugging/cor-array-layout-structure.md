---
description: 'Дополнительные сведения: структура COR_ARRAY_LAYOUT'
title: Структура COR_ARRAY_LAYOUT
ms.date: 03/30/2017
api_name:
- COR_ARRAY_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ARRAY_LAYOUT
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: aa20ac3d-6f60-4aa2-91c5-f3a86f82eba8
topic_type:
- apiref
ms.openlocfilehash: dfd9f503356b65d0a85cb3a8f108409dc6aea011
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801830"
---
# <a name="cor_array_layout-structure"></a><span data-ttu-id="960c2-103">Структура COR_ARRAY_LAYOUT</span><span class="sxs-lookup"><span data-stu-id="960c2-103">COR_ARRAY_LAYOUT Structure</span></span>

<span data-ttu-id="960c2-104">Предоставляет сведения о расположении объекта массива в памяти.</span><span class="sxs-lookup"><span data-stu-id="960c2-104">Provides information about the layout of an array object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="960c2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="960c2-105">Syntax</span></span>  
  
```cpp  
typedef struct COR_ARRAY_LAYOUT {  
    COR_TYPEID componentID;  
    CorElementType componentType;  
    ULONG32 firstElementOffset;  
    ULONG32 elementSize;  
    ULONG32 countOffset;
    ULONG32 rankSize;
    ULONG32 numRanks;
    ULONG32 rankOffset;
} COR_ARRAY_LAYOUT;  
```  
  
## <a name="members"></a><span data-ttu-id="960c2-106">Члены</span><span class="sxs-lookup"><span data-stu-id="960c2-106">Members</span></span>  
  
|<span data-ttu-id="960c2-107">Член</span><span class="sxs-lookup"><span data-stu-id="960c2-107">Member</span></span>|<span data-ttu-id="960c2-108">Описание</span><span class="sxs-lookup"><span data-stu-id="960c2-108">Description</span></span>|  
|------------|-----------------|  
|`componentID`|<span data-ttu-id="960c2-109">Идентификатор типа объектов, содержащихся в массиве.</span><span class="sxs-lookup"><span data-stu-id="960c2-109">The identifier of the type of objects that the array contains.</span></span>|  
|`componentType`|<span data-ttu-id="960c2-110">Значение перечисления Корелементтипе, указывающее, является ли компонент ссылкой для сборки мусора, классом значения или примитивом.</span><span class="sxs-lookup"><span data-stu-id="960c2-110">A CorElementType enumeration value that indicates whether the component is a garbage collection reference, a value class, or a primitive.</span></span>|  
|`firstElementOffset`|<span data-ttu-id="960c2-111">Смещение к первому элементу в массиве.</span><span class="sxs-lookup"><span data-stu-id="960c2-111">The offset to the first element in the array.</span></span>|  
|`elementSize`|<span data-ttu-id="960c2-112">Размер каждого элемента.</span><span class="sxs-lookup"><span data-stu-id="960c2-112">The size of each element.</span></span>|  
|`countOffset`|<span data-ttu-id="960c2-113">Смещение к числу элементов в массиве.</span><span class="sxs-lookup"><span data-stu-id="960c2-113">The offset to the number of elements in the array.</span></span>|  
|`rankSize`|<span data-ttu-id="960c2-114">Размер ранга в байтах.</span><span class="sxs-lookup"><span data-stu-id="960c2-114">The size of the rank, in bytes.</span></span>|  
|`numRanks`|<span data-ttu-id="960c2-115">Число рангов в массиве.</span><span class="sxs-lookup"><span data-stu-id="960c2-115">The number of ranks in the array.</span></span>|  
|`rankOffset`|<span data-ttu-id="960c2-116">Смещение, с которого начинается ранжирование.</span><span class="sxs-lookup"><span data-stu-id="960c2-116">The offset at which the ranks start.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="960c2-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="960c2-117">Remarks</span></span>  

 <span data-ttu-id="960c2-118">`rankSize`Поле задает размер ранга в многомерном массиве.</span><span class="sxs-lookup"><span data-stu-id="960c2-118">The `rankSize` field specifies the size of a rank in a multi-dimensional array.</span></span> <span data-ttu-id="960c2-119">Точны также для одномерных массивов.</span><span class="sxs-lookup"><span data-stu-id="960c2-119">It is accurate for single-dimensional arrays as well.</span></span>  
  
 <span data-ttu-id="960c2-120">Значение `numRanks` равно 1 для одномерного массива и `N` многомерного массива `N` измерений.</span><span class="sxs-lookup"><span data-stu-id="960c2-120">The value of `numRanks` is 1 for a single-dimensional array and `N` for a multi-dimensional array of `N` dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="960c2-121">Требования</span><span class="sxs-lookup"><span data-stu-id="960c2-121">Requirements</span></span>  

 <span data-ttu-id="960c2-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="960c2-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="960c2-123">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="960c2-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="960c2-124">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="960c2-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="960c2-125">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="960c2-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="960c2-126">См. также</span><span class="sxs-lookup"><span data-stu-id="960c2-126">See also</span></span>

- [<span data-ttu-id="960c2-127">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="960c2-127">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="960c2-128">Отладка</span><span class="sxs-lookup"><span data-stu-id="960c2-128">Debugging</span></span>](index.md)
