---
description: 'Дополнительные сведения о: интерфейс Икордебугмодулебреакпоинт'
title: Интерфейс ICorDebugModuleBreakpoint
ms.date: 03/30/2017
api_name:
- ICorDebugModuleBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleBreakpoint
helpviewer_keywords:
- ICorDebugModuleBreakpoint interface [.NET Framework debugging]
ms.assetid: 34667162-f314-475f-ae1b-ce9cb0fcbb83
topic_type:
- apiref
ms.openlocfilehash: c864850400471c9a3580de9bb94262c62656edf0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790754"
---
# <a name="icordebugmodulebreakpoint-interface"></a><span data-ttu-id="f8dce-103">Интерфейс ICorDebugModuleBreakpoint</span><span class="sxs-lookup"><span data-stu-id="f8dce-103">ICorDebugModuleBreakpoint Interface</span></span>

<span data-ttu-id="f8dce-104">Предоставляет доступ к конкретным модулям.</span><span class="sxs-lookup"><span data-stu-id="f8dce-104">Provides access to specific modules.</span></span> <span data-ttu-id="f8dce-105">Этот интерфейс является подклассом интерфейса Икордебугбреакпоинт.</span><span class="sxs-lookup"><span data-stu-id="f8dce-105">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f8dce-106">Методы</span><span class="sxs-lookup"><span data-stu-id="f8dce-106">Methods</span></span>  
  
|<span data-ttu-id="f8dce-107">Метод</span><span class="sxs-lookup"><span data-stu-id="f8dce-107">Method</span></span>|<span data-ttu-id="f8dce-108">Описание</span><span class="sxs-lookup"><span data-stu-id="f8dce-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f8dce-109">Метод GetModule</span><span class="sxs-lookup"><span data-stu-id="f8dce-109">GetModule Method</span></span>](icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="f8dce-110">Возвращает указатель интерфейса на объект ICorDebugModule, который ссылается на модуль, в котором задана эта точка останова.</span><span class="sxs-lookup"><span data-stu-id="f8dce-110">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8dce-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="f8dce-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8dce-112">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="f8dce-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8dce-113">Требования</span><span class="sxs-lookup"><span data-stu-id="f8dce-113">Requirements</span></span>  

 <span data-ttu-id="f8dce-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8dce-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8dce-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f8dce-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8dce-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8dce-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8dce-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8dce-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8dce-118">См. также</span><span class="sxs-lookup"><span data-stu-id="f8dce-118">See also</span></span>

- [<span data-ttu-id="f8dce-119">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="f8dce-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
