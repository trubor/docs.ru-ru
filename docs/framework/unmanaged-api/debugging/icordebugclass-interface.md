---
description: 'Дополнительные сведения о: интерфейс ICorDebugClass'
title: Интерфейс ICorDebugClass
ms.date: 03/30/2017
api_name:
- ICorDebugClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass
helpviewer_keywords:
- ICorDebugClass interface [.NET Framework debugging]
ms.assetid: 03a6facb-f12f-49be-9839-e73b9c791cd5
topic_type:
- apiref
ms.openlocfilehash: 5ded26a8b3a98bd273bbfe1bfa9efd1bb70d5595
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711509"
---
# <a name="icordebugclass-interface"></a><span data-ttu-id="64291-103">Интерфейс ICorDebugClass</span><span class="sxs-lookup"><span data-stu-id="64291-103">ICorDebugClass Interface</span></span>

<span data-ttu-id="64291-104">Представляет тип, который может быть базовым или сложным (иными словами, пользовательским).</span><span class="sxs-lookup"><span data-stu-id="64291-104">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="64291-105">Если тип универсальный, `ICorDebugClass` представляет универсальный тип, у которого отсутствуют экземпляры.</span><span class="sxs-lookup"><span data-stu-id="64291-105">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="64291-106">Методы</span><span class="sxs-lookup"><span data-stu-id="64291-106">Methods</span></span>  
  
|<span data-ttu-id="64291-107">Метод</span><span class="sxs-lookup"><span data-stu-id="64291-107">Method</span></span>|<span data-ttu-id="64291-108">Описание</span><span class="sxs-lookup"><span data-stu-id="64291-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="64291-109">Метод GetModule</span><span class="sxs-lookup"><span data-stu-id="64291-109">GetModule Method</span></span>](icordebugclass-getmodule-method.md)|<span data-ttu-id="64291-110">Возвращает модуль, который определяет этот класс.</span><span class="sxs-lookup"><span data-stu-id="64291-110">Gets the module that defines this class.</span></span>|  
|[<span data-ttu-id="64291-111">Метод GetStaticFieldValue</span><span class="sxs-lookup"><span data-stu-id="64291-111">GetStaticFieldValue Method</span></span>](icordebugclass-getstaticfieldvalue-method.md)|<span data-ttu-id="64291-112">Возвращает значение указанного статического поля.</span><span class="sxs-lookup"><span data-stu-id="64291-112">Gets the value of the specified static field.</span></span>|  
|[<span data-ttu-id="64291-113">Метод GetToken</span><span class="sxs-lookup"><span data-stu-id="64291-113">GetToken Method</span></span>](icordebugclass-gettoken-method.md)|<span data-ttu-id="64291-114">Возвращает `TypeDef` маркер метаданных для этого класса.</span><span class="sxs-lookup"><span data-stu-id="64291-114">Gets the `TypeDef` metadata token for this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64291-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="64291-115">Remarks</span></span>  

 <span data-ttu-id="64291-116">`ICorDebugClass`Интерфейс представляет универсальный тип, экземпляр которого не был создан.</span><span class="sxs-lookup"><span data-stu-id="64291-116">The `ICorDebugClass` interface represents an uninstantiated generic type.</span></span> <span data-ttu-id="64291-117">Интерфейс ICorDebugType представляет экземпляр универсального типа.</span><span class="sxs-lookup"><span data-stu-id="64291-117">The ICorDebugType interface represents an instantiated generic type.</span></span> <span data-ttu-id="64291-118">Например, будет `Hashtable<K, V>` представлено `ICorDebugClass` , а будет `Hashtable<Int32, String>` представлено `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="64291-118">For example, `Hashtable<K, V>` would be represented by `ICorDebugClass`, whereas `Hashtable<Int32, String>` would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="64291-119">Типы, не являющиеся универсальными, представлены как, так `ICorDebugClass` и `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="64291-119">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="64291-120">Последний интерфейс появился в платформа .NET Framework версии 2,0 для обработки создания экземпляра типа.</span><span class="sxs-lookup"><span data-stu-id="64291-120">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="64291-121">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="64291-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64291-122">Требования</span><span class="sxs-lookup"><span data-stu-id="64291-122">Requirements</span></span>  

 <span data-ttu-id="64291-123">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64291-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64291-124">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="64291-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64291-125">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64291-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64291-126">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64291-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64291-127">См. также</span><span class="sxs-lookup"><span data-stu-id="64291-127">See also</span></span>

- [<span data-ttu-id="64291-128">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="64291-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
