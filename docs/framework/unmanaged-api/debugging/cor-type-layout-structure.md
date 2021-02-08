---
description: 'Дополнительные сведения: структура COR_TYPE_LAYOUT'
title: Структура COR_TYPE_LAYOUT
ms.date: 03/30/2017
api_name:
- COR_TYPE_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPE_LAYOUT
helpviewer_keywords:
- COR_TYPE_LAYOUT structure [.NET Framework debugging]
ms.assetid: 43a7addd-f25a-4049-9907-abec3eb17af2
topic_type:
- apiref
ms.openlocfilehash: 07bed0c526aae38cb380b57da505a3f02bdf4aae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801769"
---
# <a name="cor_type_layout-structure"></a><span data-ttu-id="a114f-103">Структура COR_TYPE_LAYOUT</span><span class="sxs-lookup"><span data-stu-id="a114f-103">COR_TYPE_LAYOUT Structure</span></span>

<span data-ttu-id="a114f-104">Предоставляет сведения о расположении объекта в памяти.</span><span class="sxs-lookup"><span data-stu-id="a114f-104">Provides information about the layout of an object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a114f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a114f-105">Syntax</span></span>  
  
```cpp  
typedef struct COR_TYPE_LAYOUT {  
    COR_TYPEID parentID;  
    ULONG32 objectSize;  
    ULONG32 numFields;  
    ULONG32 boxOffset;  
    CorElementType type;  
} COR_TYPE_LAYOUT;  
```  
  
## <a name="members"></a><span data-ttu-id="a114f-106">Члены</span><span class="sxs-lookup"><span data-stu-id="a114f-106">Members</span></span>  
  
|<span data-ttu-id="a114f-107">Член</span><span class="sxs-lookup"><span data-stu-id="a114f-107">Member</span></span>|<span data-ttu-id="a114f-108">Описание</span><span class="sxs-lookup"><span data-stu-id="a114f-108">Description</span></span>|  
|------------|-----------------|  
|`parentID`|<span data-ttu-id="a114f-109">Идентификатор родительского типа для этого типа.</span><span class="sxs-lookup"><span data-stu-id="a114f-109">The identifier of the parent type to this type.</span></span> <span data-ttu-id="a114f-110">Это будет идентификатор типа NULL (токен1 = 0, токен2 = 0), если идентификатор типа соответствует <xref:System.Object?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="a114f-110">This will be the NULL type id (token1= 0, token2 = 0) if the type id corresponds to <xref:System.Object?displayProperty=nameWithType>.</span></span>|  
|`objectSize`|<span data-ttu-id="a114f-111">Базовый размер объекта этого типа.</span><span class="sxs-lookup"><span data-stu-id="a114f-111">The base size of an object of this type.</span></span> <span data-ttu-id="a114f-112">Это общий размер для объектов, не имеющих переменного размера.</span><span class="sxs-lookup"><span data-stu-id="a114f-112">This is the total size for non-variable sized objects.</span></span>|  
|`numFields`|<span data-ttu-id="a114f-113">Число полей, включаемых в объекты этого типа.</span><span class="sxs-lookup"><span data-stu-id="a114f-113">The number of fields included in objects of this type.</span></span>|  
|`boxOffset`|<span data-ttu-id="a114f-114">Если этот тип упакован, начальное смещение полей объекта.</span><span class="sxs-lookup"><span data-stu-id="a114f-114">If this type is boxed, the beginning offset of an object's fields.</span></span> <span data-ttu-id="a114f-115">Это поле допустимо только для типов значений, таких как примитивы и структуры.</span><span class="sxs-lookup"><span data-stu-id="a114f-115">This field is valid only for value types such as primitives and structures.</span></span>|  
|`type`|<span data-ttu-id="a114f-116">Корелементтипе, к которому принадлежит этот тип.</span><span class="sxs-lookup"><span data-stu-id="a114f-116">The CorElementType to which this type belongs.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a114f-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="a114f-117">Remarks</span></span>  

 <span data-ttu-id="a114f-118">Если `numFields` значение больше нуля, можно вызвать метод [метод ICorDebugProcess5:: жеттипефиелдс](icordebugprocess5-gettypefields-method.md) для получения сведений о полях этого типа.</span><span class="sxs-lookup"><span data-stu-id="a114f-118">If `numFields` is greater than zero, you can call the [ICorDebugProcess5::GetTypeFields](icordebugprocess5-gettypefields-method.md) method to obtain information about the fields in this type.</span></span> <span data-ttu-id="a114f-119">Если `type` имеет значение `ELEMENT_TYPE_STRING` , `ELEMENT_TYPE_ARRAY` или `ELEMENT_TYPE_SZARRAY` , то размер объектов этого типа является переменным, и можно передать структуру [COR_TYPEID](cor-typeid-structure.md) в метод [метод ICorDebugProcess5:: жетаррайлайаут](icordebugprocess5-getarraylayout-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a114f-119">If `type` is `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, or `ELEMENT_TYPE_SZARRAY`, the size of objects of this type is variable, and you can pass the [COR_TYPEID](cor-typeid-structure.md) structure to the [ICorDebugProcess5::GetArrayLayout](icordebugprocess5-getarraylayout-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a114f-120">Требования</span><span class="sxs-lookup"><span data-stu-id="a114f-120">Requirements</span></span>  

 <span data-ttu-id="a114f-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a114f-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a114f-122">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a114f-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a114f-123">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a114f-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a114f-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a114f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a114f-125">См. также</span><span class="sxs-lookup"><span data-stu-id="a114f-125">See also</span></span>

- [<span data-ttu-id="a114f-126">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="a114f-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="a114f-127">Отладка</span><span class="sxs-lookup"><span data-stu-id="a114f-127">Debugging</span></span>](index.md)
