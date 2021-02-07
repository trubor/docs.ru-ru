---
description: 'Дополнительные сведения: структура COR_HEAPINFO'
title: Структура COR_HEAPINFO
ms.date: 03/30/2017
api_name:
- COR_HEAPINFO
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPINFO
helpviewer_keywords:
- COR_HEAPINFO structure [.NET Framework debugging]
ms.assetid: bfb2cd39-3e0b-4d51-ba0c-f009755c1456
topic_type:
- apiref
ms.openlocfilehash: 0841739172b3eaf807813af28e0b20fbb54608b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712319"
---
# <a name="cor_heapinfo-structure"></a><span data-ttu-id="83409-103">Структура COR_HEAPINFO</span><span class="sxs-lookup"><span data-stu-id="83409-103">COR_HEAPINFO Structure</span></span>

<span data-ttu-id="83409-104">Содержит общие сведения о куче для сборки мусора и указывает, является ли она перечислимой.</span><span class="sxs-lookup"><span data-stu-id="83409-104">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83409-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="83409-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;
    DWORD pointerSize;
    DWORD numHeaps;  
    BOOL concurrent;
    CorDebugGCType gcType;
} COR_HEAPINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="83409-106">Члены</span><span class="sxs-lookup"><span data-stu-id="83409-106">Members</span></span>  
  
|<span data-ttu-id="83409-107">Член</span><span class="sxs-lookup"><span data-stu-id="83409-107">Member</span></span>|<span data-ttu-id="83409-108">Описание</span><span class="sxs-lookup"><span data-stu-id="83409-108">Description</span></span>|  
|------------|-----------------|  
|`areGCStructuresValid`|<span data-ttu-id="83409-109">`true` значение, если структуры сборки мусора являются допустимыми и можно перечислить в куче. в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="83409-109">`true` if garbage collection structures are valid and the heap can be enumerated; otherwise, `false`.</span></span>|  
|`pointerSize`|<span data-ttu-id="83409-110">Размер указателей в байтах в целевой архитектуре.</span><span class="sxs-lookup"><span data-stu-id="83409-110">The size, in bytes, of pointers on the target architecture.</span></span>|  
|`numHeaps`|<span data-ttu-id="83409-111">Количество куч логической сборки мусора в процессе.</span><span class="sxs-lookup"><span data-stu-id="83409-111">The number of logical garbage collection heaps in the process.</span></span>|  
|`concurrent`|<span data-ttu-id="83409-112">`TRUE` Если включена одновременная (фоновая) сборка мусора; в противном случае — `FALSE` .</span><span class="sxs-lookup"><span data-stu-id="83409-112">`TRUE` if concurrent (background) garbage collection is enabled; otherwise, `FALSE`.</span></span>|  
|`gcType`|<span data-ttu-id="83409-113">Член перечисления [CorDebugGCType](cordebuggctype-enumeration.md) , указывающий, работает ли сборщик мусора на рабочей станции или сервере.</span><span class="sxs-lookup"><span data-stu-id="83409-113">A member of the [CorDebugGCType](cordebuggctype-enumeration.md) enumeration that indicates whether the garbage collector is running on a workstation or a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83409-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="83409-114">Remarks</span></span>  

 <span data-ttu-id="83409-115">Экземпляр `COR_HEAPINFO` структуры возвращается путем вызова метода [метод ICorDebugProcess5:: GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) .</span><span class="sxs-lookup"><span data-stu-id="83409-115">An instance of the `COR_HEAPINFO` structure is returned by calling the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
 <span data-ttu-id="83409-116">Перед перечислением объектов в куче сборки мусора необходимо всегда проверять `areGCStructuresValid` поле, чтобы убедиться в том, что куча находится в перечислимом состоянии.</span><span class="sxs-lookup"><span data-stu-id="83409-116">Before enumerating objects on the garbage collection heap, you must always check the `areGCStructuresValid` field to ensure that the heap is in an enumerable state.</span></span> <span data-ttu-id="83409-117">Дополнительные сведения см. в описании метода [метод ICorDebugProcess5:: GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) .</span><span class="sxs-lookup"><span data-stu-id="83409-117">For more information, see the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83409-118">Требования</span><span class="sxs-lookup"><span data-stu-id="83409-118">Requirements</span></span>  

 <span data-ttu-id="83409-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83409-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83409-120">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="83409-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83409-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83409-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83409-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83409-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83409-123">См. также</span><span class="sxs-lookup"><span data-stu-id="83409-123">See also</span></span>

- [<span data-ttu-id="83409-124">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="83409-124">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="83409-125">Отладка</span><span class="sxs-lookup"><span data-stu-id="83409-125">Debugging</span></span>](index.md)
