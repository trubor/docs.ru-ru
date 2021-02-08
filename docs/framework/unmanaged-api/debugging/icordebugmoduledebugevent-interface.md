---
description: 'Дополнительные сведения о: интерфейс Икордебугмодуледебужевент'
title: Интерфейс ICorDebugModuleDebugEvent
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
ms.openlocfilehash: 0c2d43d7b04caeea0407ede23f0df6e278d60c92
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801037"
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="ab997-103">Интерфейс ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="ab997-103">ICorDebugModuleDebugEvent Interface</span></span>

<span data-ttu-id="ab997-104">Расширяет интерфейс [ICorDebugDebugEvent](icordebugdebugevent-interface.md) для поддержки событий уровня модуля.</span><span class="sxs-lookup"><span data-stu-id="ab997-104">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ab997-105">Методы</span><span class="sxs-lookup"><span data-stu-id="ab997-105">Methods</span></span>  
  
|<span data-ttu-id="ab997-106">Метод</span><span class="sxs-lookup"><span data-stu-id="ab997-106">Method</span></span>|<span data-ttu-id="ab997-107">Описание</span><span class="sxs-lookup"><span data-stu-id="ab997-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ab997-108">Метод GetModule</span><span class="sxs-lookup"><span data-stu-id="ab997-108">GetModule Method</span></span>](icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="ab997-109">Возвращает объединенный модуль, который только что был загружен или выгружен.</span><span class="sxs-lookup"><span data-stu-id="ab997-109">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab997-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="ab997-110">Remarks</span></span>  

 <span data-ttu-id="ab997-111">Типы событий [MODULE_LOADED](cordebugdebugeventkind-enumeration.md) и [MODULE_UNLOADED](cordebugdebugeventkind-enumeration.md) реализуют этот интерфейс.</span><span class="sxs-lookup"><span data-stu-id="ab997-111">The [MODULE_LOADED](cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ab997-112">Этот интерфейс доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="ab997-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="ab997-113">Попытка вызова метода `QueryInterface` для получения указателя интерфейса возвращает `E_NOINTERFACE` для сценариев ICorDebug вне .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ab997-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab997-114">Требования</span><span class="sxs-lookup"><span data-stu-id="ab997-114">Requirements</span></span>  

 <span data-ttu-id="ab997-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab997-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab997-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ab997-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab997-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab997-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab997-118">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab997-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab997-119">См. также</span><span class="sxs-lookup"><span data-stu-id="ab997-119">See also</span></span>

- [<span data-ttu-id="ab997-120">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="ab997-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ab997-121">Отладка</span><span class="sxs-lookup"><span data-stu-id="ab997-121">Debugging</span></span>](index.md)
