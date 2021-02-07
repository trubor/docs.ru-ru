---
description: 'Дополнительные сведения: структура COR_FIELD'
title: Структура COR_FIELD
ms.date: 03/30/2017
api_name:
- COR_FIELD
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_FIELD
helpviewer_keywords:
- COR_FIELD structure [.NET Framework debugging]
ms.assetid: c0822423-a9df-4961-950d-50dcc152f863
topic_type:
- apiref
ms.openlocfilehash: a3e9dcc2a5c3bb2abae42dab4292c1d285df5ad7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747116"
---
# <a name="cor_field-structure"></a><span data-ttu-id="e8a50-103">Структура COR_FIELD</span><span class="sxs-lookup"><span data-stu-id="e8a50-103">COR_FIELD Structure</span></span>

<span data-ttu-id="e8a50-104">Предоставляет сведения о поле в объекте.</span><span class="sxs-lookup"><span data-stu-id="e8a50-104">Provides information about a field in an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8a50-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e8a50-105">Syntax</span></span>  
  
```cpp  
typedef struct COR_FIELD{  
    mdFieldDef token;  
    ULONG32 offset;  
    COR_TYPEID id;  
    CorElementType fieldType;  
} COR_FIELD;  
```  
  
## <a name="members"></a><span data-ttu-id="e8a50-106">Члены</span><span class="sxs-lookup"><span data-stu-id="e8a50-106">Members</span></span>  
  
|<span data-ttu-id="e8a50-107">Член</span><span class="sxs-lookup"><span data-stu-id="e8a50-107">Member</span></span>|<span data-ttu-id="e8a50-108">Описание</span><span class="sxs-lookup"><span data-stu-id="e8a50-108">Description</span></span>|  
|------------|-----------------|  
|`token`|<span data-ttu-id="e8a50-109">`mdFieldDef`Токен, который можно использовать для получения сведений о полях.</span><span class="sxs-lookup"><span data-stu-id="e8a50-109">An `mdFieldDef` token that can be used to get field information.</span></span>|  
|`offset`|<span data-ttu-id="e8a50-110">Смещение в байтах для данных поля в объекте.</span><span class="sxs-lookup"><span data-stu-id="e8a50-110">The offset, in bytes, to the field data in the object.</span></span>|  
|`id`|<span data-ttu-id="e8a50-111">Значение [COR_TYPEID](cor-typeid-structure.md) , определяющее тип этого поля.</span><span class="sxs-lookup"><span data-stu-id="e8a50-111">A [COR_TYPEID](cor-typeid-structure.md) value that identifies the type of this field.</span></span>|  
|`fieldType`|<span data-ttu-id="e8a50-112">Значение перечисления Корелементтипе, указывающее тип поля.</span><span class="sxs-lookup"><span data-stu-id="e8a50-112">A CorElementType enumeration value that indicates the type of the field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8a50-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="e8a50-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8a50-114">Требования</span><span class="sxs-lookup"><span data-stu-id="e8a50-114">Requirements</span></span>  

 <span data-ttu-id="e8a50-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8a50-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8a50-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e8a50-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e8a50-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8a50-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8a50-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8a50-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8a50-119">См. также</span><span class="sxs-lookup"><span data-stu-id="e8a50-119">See also</span></span>

- [<span data-ttu-id="e8a50-120">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="e8a50-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="e8a50-121">Отладка</span><span class="sxs-lookup"><span data-stu-id="e8a50-121">Debugging</span></span>](index.md)
