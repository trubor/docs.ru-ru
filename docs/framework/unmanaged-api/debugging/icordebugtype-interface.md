---
description: Дополнительные сведения о интерфейсе ICorDebugType
title: Интерфейс ICorDebugType
ms.date: 03/30/2017
api_name:
- ICorDebugType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType
helpviewer_keywords:
- ICorDebugType interface [.NET Framework debugging]
ms.assetid: 94e02e31-67ea-4b00-8148-a46740a4571d
topic_type:
- apiref
ms.openlocfilehash: 4cd668263906ef21e1bb665795425ca3a239c2bd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800894"
---
# <a name="icordebugtype-interface"></a><span data-ttu-id="4cbb5-103">Интерфейс ICorDebugType</span><span class="sxs-lookup"><span data-stu-id="4cbb5-103">ICorDebugType Interface</span></span>

<span data-ttu-id="4cbb5-104">Представляет тип — базовый или сложный (то есть определяемый пользователем).</span><span class="sxs-lookup"><span data-stu-id="4cbb5-104">Represents a type, either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="4cbb5-105">Если тип универсален, интерфейс `ICorDebugType` представляет универсальный тип с экземплярами.</span><span class="sxs-lookup"><span data-stu-id="4cbb5-105">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4cbb5-106">Методы</span><span class="sxs-lookup"><span data-stu-id="4cbb5-106">Methods</span></span>  
  
|<span data-ttu-id="4cbb5-107">Метод</span><span class="sxs-lookup"><span data-stu-id="4cbb5-107">Method</span></span>|<span data-ttu-id="4cbb5-108">Описание</span><span class="sxs-lookup"><span data-stu-id="4cbb5-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4cbb5-109">Метод EnumerateTypeParameters</span><span class="sxs-lookup"><span data-stu-id="4cbb5-109">EnumerateTypeParameters Method</span></span>](icordebugtype-enumeratetypeparameters-method.md)|<span data-ttu-id="4cbb5-110">Возвращает указатель интерфейса на ICorDebugTypeEnum, который ссылается на универсальные <xref:System.Type> Параметры класса, на который ссылается this `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="4cbb5-110">Gets an interface pointer to an ICorDebugTypeEnum that references the generic <xref:System.Type> parameters of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="4cbb5-111">Метод GetBase</span><span class="sxs-lookup"><span data-stu-id="4cbb5-111">GetBase Method</span></span>](icordebugtype-getbase-method.md)|<span data-ttu-id="4cbb5-112">Возвращает указатель интерфейса на объект `ICorDebugType` , который ссылается на базовый класс класса, на который ссылается этот класс `ICorDebugType` , если он существует.</span><span class="sxs-lookup"><span data-stu-id="4cbb5-112">Gets an interface pointer to an `ICorDebugType` that references the base class of the class referenced by this `ICorDebugType`, if one exists.</span></span>|  
|[<span data-ttu-id="4cbb5-113">Метод GetClass</span><span class="sxs-lookup"><span data-stu-id="4cbb5-113">GetClass Method</span></span>](icordebugtype-getclass-method.md)|<span data-ttu-id="4cbb5-114">Возвращает указатель интерфейса на объект ICorDebugClass, который ссылается на типизированный конструктор этого объекта `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="4cbb5-114">Gets an interface pointer to an ICorDebugClass that references the typed constructor of this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="4cbb5-115">Метод GetFirstTypeParameter</span><span class="sxs-lookup"><span data-stu-id="4cbb5-115">GetFirstTypeParameter Method</span></span>](icordebugtype-getfirsttypeparameter-method.md)|<span data-ttu-id="4cbb5-116">Возвращает указатель интерфейса на объект `ICorDebugType` , который ссылается на первый универсальный <xref:System.Type> параметр для конструктора класса, на который ссылается this `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="4cbb5-116">Gets an interface pointer to an `ICorDebugType` that references the first generic <xref:System.Type> parameter for the constructor of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="4cbb5-117">Метод GetRank</span><span class="sxs-lookup"><span data-stu-id="4cbb5-117">GetRank Method</span></span>](icordebugtype-getrank-method.md)|<span data-ttu-id="4cbb5-118">Возвращает число измерений в типе массива.</span><span class="sxs-lookup"><span data-stu-id="4cbb5-118">Gets the number of dimensions in an array type.</span></span>|  
|[<span data-ttu-id="4cbb5-119">Метод GetStaticFieldValue</span><span class="sxs-lookup"><span data-stu-id="4cbb5-119">GetStaticFieldValue Method</span></span>](icordebugtype-getstaticfieldvalue-method.md)|<span data-ttu-id="4cbb5-120">Возвращает указатель интерфейса на объект ICorDebugValue, содержащий значение статического поля, на которое ссылается заданный токен поля в указанном кадре стека.</span><span class="sxs-lookup"><span data-stu-id="4cbb5-120">Gets an interface pointer to an ICorDebugValue that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>|  
|[<span data-ttu-id="4cbb5-121">Метод GetType</span><span class="sxs-lookup"><span data-stu-id="4cbb5-121">GetType Method</span></span>](icordebugtype-gettype-method.md)|<span data-ttu-id="4cbb5-122">Возвращает значение Корелементтипе, описывающее собственный тип среды CLR, <xref:System.Type> на который ссылается this `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="4cbb5-122">Gets a CorElementType value that describes the native type of the common language runtime <xref:System.Type> referenced by this `ICorDebugType`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4cbb5-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="4cbb5-123">Remarks</span></span>  

 <span data-ttu-id="4cbb5-124">Если тип является универсальным, `ICorDebugClass` представляет тип, не являющийся экземпляром.</span><span class="sxs-lookup"><span data-stu-id="4cbb5-124">If the type is generic, `ICorDebugClass` represents the uninstantiated type.</span></span> <span data-ttu-id="4cbb5-125">`ICorDebugType`Интерфейс представляет экземпляр универсального типа.</span><span class="sxs-lookup"><span data-stu-id="4cbb5-125">The `ICorDebugType` interface represents an instantiated generic type.</span></span> <span data-ttu-id="4cbb5-126">Например, таблица Hashtable будет \<K, V> представлена с помощью `ICorDebugClass` , тогда как Hashtable будет \<Int32, String> представлена `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="4cbb5-126">For example, Hashtable\<K, V> would be represented by `ICorDebugClass`, whereas Hashtable\<Int32, String> would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="4cbb5-127">Типы, не являющиеся универсальными, представлены как, так `ICorDebugClass` и `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="4cbb5-127">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="4cbb5-128">Последний интерфейс появился в платформа .NET Framework версии 2,0 для обработки создания экземпляра типа.</span><span class="sxs-lookup"><span data-stu-id="4cbb5-128">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4cbb5-129">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="4cbb5-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cbb5-130">Требования</span><span class="sxs-lookup"><span data-stu-id="4cbb5-130">Requirements</span></span>  

 <span data-ttu-id="4cbb5-131">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4cbb5-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cbb5-132">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4cbb5-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4cbb5-133">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4cbb5-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4cbb5-134">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cbb5-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cbb5-135">См. также</span><span class="sxs-lookup"><span data-stu-id="4cbb5-135">See also</span></span>

- [<span data-ttu-id="4cbb5-136">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="4cbb5-136">Debugging Interfaces</span></span>](debugging-interfaces.md)
