---
description: 'Дополнительные сведения о: интерфейс ICorDebugDebugEvent'
title: Интерфейс ICorDebugDebugEvent
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
ms.openlocfilehash: 5735be22b76e9f74847bb5138c00130f28dbfc96
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764311"
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="bdff7-103">Интерфейс ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="bdff7-103">ICorDebugDebugEvent Interface</span></span>

<span data-ttu-id="bdff7-104">Определяет базовый интерфейс, из которого возникают все события отладки `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="bdff7-104">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bdff7-105">Методы</span><span class="sxs-lookup"><span data-stu-id="bdff7-105">Methods</span></span>  
  
|<span data-ttu-id="bdff7-106">Метод</span><span class="sxs-lookup"><span data-stu-id="bdff7-106">Method</span></span>|<span data-ttu-id="bdff7-107">Описание</span><span class="sxs-lookup"><span data-stu-id="bdff7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bdff7-108">Метод GetEventKind</span><span class="sxs-lookup"><span data-stu-id="bdff7-108">GetEventKind Method</span></span>](icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="bdff7-109">Указывает тип события, который представляет этот объект `ICorDebugDebugEvent`.</span><span class="sxs-lookup"><span data-stu-id="bdff7-109">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="bdff7-110">Метод GetThread</span><span class="sxs-lookup"><span data-stu-id="bdff7-110">GetThread Method</span></span>](icordebugdebugevent-getthread-method.md)|<span data-ttu-id="bdff7-111">Получает поток, в котором произошло событие.</span><span class="sxs-lookup"><span data-stu-id="bdff7-111">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bdff7-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="bdff7-112">Remarks</span></span>  

 <span data-ttu-id="bdff7-113">Следующие интерфейсы являются производными от интерфейса `ICorDebugDebugEvent`.</span><span class="sxs-lookup"><span data-stu-id="bdff7-113">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
- [<span data-ttu-id="bdff7-114">ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="bdff7-114">ICorDebugExceptionDebugEvent</span></span>](icordebugexceptiondebugevent-interface.md)  
  
- [<span data-ttu-id="bdff7-115">ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="bdff7-115">ICorDebugModuleDebugEvent</span></span>](icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="bdff7-116">Этот интерфейс доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="bdff7-116">The interface is available with .NET Native only.</span></span> <span data-ttu-id="bdff7-117">Попытка вызова метода `QueryInterface` для получения указателя интерфейса возвращает `E_NOINTERFACE` для сценариев ICorDebug вне .NET Native.</span><span class="sxs-lookup"><span data-stu-id="bdff7-117">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdff7-118">Требования</span><span class="sxs-lookup"><span data-stu-id="bdff7-118">Requirements</span></span>  

 <span data-ttu-id="bdff7-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdff7-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdff7-120">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bdff7-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bdff7-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bdff7-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bdff7-122">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdff7-122">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdff7-123">См. также</span><span class="sxs-lookup"><span data-stu-id="bdff7-123">See also</span></span>

- [<span data-ttu-id="bdff7-124">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="bdff7-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="bdff7-125">Отладка</span><span class="sxs-lookup"><span data-stu-id="bdff7-125">Debugging</span></span>](index.md)
