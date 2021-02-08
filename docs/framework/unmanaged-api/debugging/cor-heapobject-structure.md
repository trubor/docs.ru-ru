---
description: 'Дополнительные сведения: структура COR_HEAPOBJECT'
title: Структура COR_HEAPOBJECT
ms.date: 03/30/2017
api_name:
- COR_HEAPOBJECT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPOBJECT
helpviewer_keywords:
- COR_HEAPOBJECT structure [.NET Framework debugging]
ms.assetid: a92fdf95-492b-49ae-a741-2186e5c1d7c5
topic_type:
- apiref
ms.openlocfilehash: f41e02e7c528063f4b7ed485cbadbabb4d3e5ca7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801804"
---
# <a name="cor_heapobject-structure"></a><span data-ttu-id="00509-103">Структура COR_HEAPOBJECT</span><span class="sxs-lookup"><span data-stu-id="00509-103">COR_HEAPOBJECT Structure</span></span>

<span data-ttu-id="00509-104">Предоставляет сведения об объекте, находящемся в управляемой куче.</span><span class="sxs-lookup"><span data-stu-id="00509-104">Provides information about an object on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00509-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="00509-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;
    ULONG64 size;
    COR_TYPEID type;
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a><span data-ttu-id="00509-106">Члены</span><span class="sxs-lookup"><span data-stu-id="00509-106">Members</span></span>  
  
|<span data-ttu-id="00509-107">Член</span><span class="sxs-lookup"><span data-stu-id="00509-107">Member</span></span>|<span data-ttu-id="00509-108">Описание</span><span class="sxs-lookup"><span data-stu-id="00509-108">Description</span></span>|  
|------------|-----------------|  
|`address`|<span data-ttu-id="00509-109">Адрес объекта в памяти.</span><span class="sxs-lookup"><span data-stu-id="00509-109">The address of the object in memory.</span></span>|  
|`size`|<span data-ttu-id="00509-110">Общий размер объекта в байтах.</span><span class="sxs-lookup"><span data-stu-id="00509-110">The total size of the object, in bytes.</span></span>|  
|`type`|<span data-ttu-id="00509-111">Токен [COR_TYPEID](cor-typeid-structure.md) , представляющий тип объекта.</span><span class="sxs-lookup"><span data-stu-id="00509-111">A [COR_TYPEID](cor-typeid-structure.md) token that represents the type of the object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00509-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="00509-112">Remarks</span></span>  

 <span data-ttu-id="00509-113">`COR_HEAPOBJECT` экземпляры можно получить, перечисляя объект интерфейса [икордебугхеапенум](icordebugheapenum-interface.md) , который заполняется путем вызова метода [метод ICorDebugProcess5:: енумератехеап](icordebugprocess5-enumerateheap-method.md) .</span><span class="sxs-lookup"><span data-stu-id="00509-113">`COR_HEAPOBJECT` instances can be retrieved by enumerating an [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object that is populated by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span>  
  
 <span data-ttu-id="00509-114">`COR_HEAPOBJECT`Экземпляр предоставляет сведения об активном объекте в управляемой куче или об объекте, который не является корневым для какого-либо объекта, но еще не был собран сборщиком мусора.</span><span class="sxs-lookup"><span data-stu-id="00509-114">A `COR_HEAPOBJECT` instance provides information either about a live object on the managed heap, or about an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span>  
  
 <span data-ttu-id="00509-115">Для повышения производительности `COR_HEAPOBJECT.address` поле является `CORDB_ADDRESS` значением, а не значением интерфейса ICorDebugValue, которое используется в большинстве API отладки.</span><span class="sxs-lookup"><span data-stu-id="00509-115">For better performance, the `COR_HEAPOBJECT.address` field is a `CORDB_ADDRESS` value rather than the ICorDebugValue interface value used in much of the debugging API.</span></span> <span data-ttu-id="00509-116">Чтобы получить объект ICorDebugValue для заданного адреса объекта, можно передать `CORDB_ADDRESS` значение в метод [метод ICorDebugProcess5:: GetObject](icordebugprocess5-getobject-method.md) .</span><span class="sxs-lookup"><span data-stu-id="00509-116">To obtain an ICorDebugValue object for a given object address, you can pass the `CORDB_ADDRESS` value to the [ICorDebugProcess5::GetObject](icordebugprocess5-getobject-method.md) method.</span></span>  
  
 <span data-ttu-id="00509-117">Для повышения производительности `COR_HEAPOBJECT.type` поле является `COR_TYPEID` значением, а не значением интерфейса ICorDebugType, которое используется в большинстве API отладки.</span><span class="sxs-lookup"><span data-stu-id="00509-117">For better performance, the `COR_HEAPOBJECT.type` field is a `COR_TYPEID` value rather than the ICorDebugType interface value used in much of the debugging API.</span></span> <span data-ttu-id="00509-118">Чтобы получить объект ICorDebugType для заданного идентификатора типа, можно передать `COR_TYPEID` значение в метод [метод ICorDebugProcess5:: жеттипефортипеид](icordebugprocess5-gettypefortypeid-method.md) .</span><span class="sxs-lookup"><span data-stu-id="00509-118">To obtain an ICorDebugType object for a given type ID, you can pass the `COR_TYPEID` value to the [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) method.</span></span>  
  
 <span data-ttu-id="00509-119">`COR_HEAPOBJECT`Структура включает в себя COM-интерфейс, подсчитанный по ссылке.</span><span class="sxs-lookup"><span data-stu-id="00509-119">The `COR_HEAPOBJECT` structure includes a reference-counted COM interface.</span></span> <span data-ttu-id="00509-120">При извлечении `COR_HEAPOBJECT` экземпляра из перечислителя путем вызова метода [икордебугхеапенум:: Next](icordebugheapenum-next-method.md) необходимо впоследствии освободить ссылку.</span><span class="sxs-lookup"><span data-stu-id="00509-120">If you retrieve a `COR_HEAPOBJECT` instance from the enumerator by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method, you must subsequently release the reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00509-121">Требования</span><span class="sxs-lookup"><span data-stu-id="00509-121">Requirements</span></span>  

 <span data-ttu-id="00509-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00509-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00509-123">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="00509-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="00509-124">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00509-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00509-125">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00509-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00509-126">См. также</span><span class="sxs-lookup"><span data-stu-id="00509-126">See also</span></span>

- [<span data-ttu-id="00509-127">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="00509-127">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="00509-128">Отладка</span><span class="sxs-lookup"><span data-stu-id="00509-128">Debugging</span></span>](index.md)
