---
description: 'Дополнительные сведения о: интерфейс Икордебугкомобжектвалуе'
title: Интерфейс ICorDebugComObjectValue Interface
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugComObjectValue
helpviewer_keywords:
- ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 505a7f6c-d92b-42b4-b539-433f5102ea9b
topic_type:
- apiref
ms.openlocfilehash: 3c071c371ae6e330431630cfb1934b538d62efe6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710820"
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="b3f72-103">Интерфейс ICorDebugComObjectValue Interface</span><span class="sxs-lookup"><span data-stu-id="b3f72-103">ICorDebugComObjectValue Interface</span></span>

<span data-ttu-id="b3f72-104">Предоставляет методы для получения сведений, связанных с вызываемой оболочкой времени выполнения (RCW).</span><span class="sxs-lookup"><span data-stu-id="b3f72-104">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b3f72-105">Методы</span><span class="sxs-lookup"><span data-stu-id="b3f72-105">Methods</span></span>  
  
|<span data-ttu-id="b3f72-106">Метод</span><span class="sxs-lookup"><span data-stu-id="b3f72-106">Method</span></span>|<span data-ttu-id="b3f72-107">Описание</span><span class="sxs-lookup"><span data-stu-id="b3f72-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b3f72-108">Метод GetCachedInterfacePointers</span><span class="sxs-lookup"><span data-stu-id="b3f72-108">GetCachedInterfacePointers Method</span></span>](icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="b3f72-109">Возвращает необработанные указатели интерфейса, кэшированные в текущей RCW.</span><span class="sxs-lookup"><span data-stu-id="b3f72-109">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="b3f72-110">Метод GetCachedInterfaceTypes</span><span class="sxs-lookup"><span data-stu-id="b3f72-110">GetCachedInterfaceTypes Method</span></span>](icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="b3f72-111">Предоставляет перечислитель для типов интерфейса, к которым был применен регистр текущего объекта или использован в качестве.</span><span class="sxs-lookup"><span data-stu-id="b3f72-111">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3f72-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="b3f72-112">Remarks</span></span>  

 <span data-ttu-id="b3f72-113">Чтобы проверить, представляет ли экземпляр интерфейса "ICorDebugValue" RCW, отладчик вызывает метод `QueryInterface` "ICorDebugValue" с `IID_ICorDebugComObjectValue` .</span><span class="sxs-lookup"><span data-stu-id="b3f72-113">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3f72-114">Требования</span><span class="sxs-lookup"><span data-stu-id="b3f72-114">Requirements</span></span>  

 <span data-ttu-id="b3f72-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3f72-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3f72-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b3f72-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b3f72-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3f72-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3f72-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3f72-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3f72-119">См. также</span><span class="sxs-lookup"><span data-stu-id="b3f72-119">See also</span></span>

- [<span data-ttu-id="b3f72-120">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="b3f72-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b3f72-121">Отладка</span><span class="sxs-lookup"><span data-stu-id="b3f72-121">Debugging</span></span>](index.md)
