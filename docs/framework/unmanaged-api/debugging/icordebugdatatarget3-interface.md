---
description: 'Дополнительные сведения о: интерфейс ICorDebugDataTarget3'
title: Интерфейс ICorDebugDataTarget3
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
ms.openlocfilehash: fa786b920d1a2e72dc2a7918e0514773862a0e85
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710443"
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="faee4-103">Интерфейс ICorDebugDataTarget3</span><span class="sxs-lookup"><span data-stu-id="faee4-103">ICorDebugDataTarget3 Interface</span></span>

<span data-ttu-id="faee4-104">Логически расширяет интерфейс [ICorDebugDataTarget](icordebugdatatarget-interface.md) , чтобы предоставить сведения о загруженных модулях.</span><span class="sxs-lookup"><span data-stu-id="faee4-104">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="faee4-105">Метод</span><span class="sxs-lookup"><span data-stu-id="faee4-105">Method</span></span>  
  
|<span data-ttu-id="faee4-106">Метод</span><span class="sxs-lookup"><span data-stu-id="faee4-106">Method</span></span>|<span data-ttu-id="faee4-107">Описание</span><span class="sxs-lookup"><span data-stu-id="faee4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="faee4-108">Метод GetLoadedModules</span><span class="sxs-lookup"><span data-stu-id="faee4-108">GetLoadedModules Method</span></span>](icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="faee4-109">Возвращает список модулей, загруженных на данный момент.</span><span class="sxs-lookup"><span data-stu-id="faee4-109">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="faee4-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="faee4-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="faee4-111">Этот интерфейс доступен только в .NET Native.</span><span class="sxs-lookup"><span data-stu-id="faee4-111">This interface is available with .NET Native only.</span></span> <span data-ttu-id="faee4-112">При реализации этого интерфейса для сценариев ICorDebug вне .NET Native среда CLR будет игнорировать этот интерфейс.</span><span class="sxs-lookup"><span data-stu-id="faee4-112">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="faee4-113">Требования</span><span class="sxs-lookup"><span data-stu-id="faee4-113">Requirements</span></span>  

 <span data-ttu-id="faee4-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="faee4-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="faee4-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="faee4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="faee4-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="faee4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="faee4-117">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="faee4-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faee4-118">См. также</span><span class="sxs-lookup"><span data-stu-id="faee4-118">See also</span></span>

- [<span data-ttu-id="faee4-119">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="faee4-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="faee4-120">Отладка</span><span class="sxs-lookup"><span data-stu-id="faee4-120">Debugging</span></span>](index.md)
