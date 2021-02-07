---
description: 'Дополнительные сведения: структура COR_TYPEID'
title: Структура COR_TYPEID
ms.date: 03/30/2017
api_name:
- COR_TYPEID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPEID
helpviewer_keywords:
- COR_TYPEID structure [.NET Framework debugging]
ms.assetid: 1e172b14-ee22-4943-b3b8-3740e7bdcd2e
topic_type:
- apiref
ms.openlocfilehash: fe246d544697275ffc4ea3ab6ed21c0f33863881
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712218"
---
# <a name="cor_typeid-structure"></a><span data-ttu-id="0a329-103">Структура COR_TYPEID</span><span class="sxs-lookup"><span data-stu-id="0a329-103">COR_TYPEID Structure</span></span>

<span data-ttu-id="0a329-104">Содержит идентификатор типа.</span><span class="sxs-lookup"><span data-stu-id="0a329-104">Contains a type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a329-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0a329-105">Syntax</span></span>  
  
```cpp  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a><span data-ttu-id="0a329-106">Члены</span><span class="sxs-lookup"><span data-stu-id="0a329-106">Members</span></span>  
  
|<span data-ttu-id="0a329-107">Член</span><span class="sxs-lookup"><span data-stu-id="0a329-107">Member</span></span>|<span data-ttu-id="0a329-108">Описание</span><span class="sxs-lookup"><span data-stu-id="0a329-108">Description</span></span>|  
|------------|-----------------|  
|`token1`|<span data-ttu-id="0a329-109">Первый токен.</span><span class="sxs-lookup"><span data-stu-id="0a329-109">The first token.</span></span>|  
|`token2`|<span data-ttu-id="0a329-110">Второй токен.</span><span class="sxs-lookup"><span data-stu-id="0a329-110">The second token.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a329-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="0a329-111">Remarks</span></span>  

 <span data-ttu-id="0a329-112">`COR_TYPEID`Структура возвращается несколькими методами отладки, которые предоставляют сведения об объектах, которые должны быть собраны в мусор.</span><span class="sxs-lookup"><span data-stu-id="0a329-112">The `COR_TYPEID` structure is returned by a number of debugging methods that provide information about objects to be garbage-collected.</span></span> <span data-ttu-id="0a329-113">Затем его можно передать в качестве аргумента другим методам отладки, которые предоставляют дополнительные сведения об этом элементе.</span><span class="sxs-lookup"><span data-stu-id="0a329-113">It can then be passed as an argument to other debugging methods that provide additional information about that item.</span></span> <span data-ttu-id="0a329-114">Например, при перечислении объекта [икордебугхеапенум](icordebugheapenum-interface.md) можно получить отдельные объекты [COR_HEAPOBJECT](cor-heapobject-structure.md) , представляющие отдельные объекты в управляемой куче.</span><span class="sxs-lookup"><span data-stu-id="0a329-114">For example, by enumerating an [ICorDebugHeapEnum](icordebugheapenum-interface.md) object, you can retrieve individual [COR_HEAPOBJECT](cor-heapobject-structure.md) objects that represent individual objects on the managed heap.</span></span> <span data-ttu-id="0a329-115">Затем можно передать `COR_TYPEID` значение из `COR_HEAPOBJECT.type` поля в метод [метод ICorDebugProcess5:: жеттипефортипеид](icordebugprocess5-gettypefortypeid-method.md) , чтобы получить объект ICorDebugType, предоставляющий сведения о типе объекта.</span><span class="sxs-lookup"><span data-stu-id="0a329-115">You can then pass the `COR_TYPEID` value from the `COR_HEAPOBJECT.type` field to the [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) method to retrieve an ICorDebugType object that provides type information about the object.</span></span>  
  
 <span data-ttu-id="0a329-116">`COR_TYPEID`Объект должен быть непрозрачным.</span><span class="sxs-lookup"><span data-stu-id="0a329-116">A `COR_TYPEID` object is intended to be opaque.</span></span> <span data-ttu-id="0a329-117">Доступ к отдельным полям не должен осуществляться или манипулировать им.</span><span class="sxs-lookup"><span data-stu-id="0a329-117">Its individual fields should not be accessed or manipulated.</span></span> <span data-ttu-id="0a329-118">Его единственное использование — это идентификатор, предоставляемый как `out` параметр в вызове метода, который, в свою очередь, может быть передан другим методам для предоставления дополнительных сведений.</span><span class="sxs-lookup"><span data-stu-id="0a329-118">Its sole use is as an identifier that is provided as an `out` parameter in a method call and that can, in turn, be passed to other methods to provide additional information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a329-119">Требования</span><span class="sxs-lookup"><span data-stu-id="0a329-119">Requirements</span></span>  

 <span data-ttu-id="0a329-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a329-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a329-121">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0a329-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0a329-122">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a329-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a329-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a329-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a329-124">См. также</span><span class="sxs-lookup"><span data-stu-id="0a329-124">See also</span></span>

- [<span data-ttu-id="0a329-125">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="0a329-125">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="0a329-126">Отладка</span><span class="sxs-lookup"><span data-stu-id="0a329-126">Debugging</span></span>](index.md)
