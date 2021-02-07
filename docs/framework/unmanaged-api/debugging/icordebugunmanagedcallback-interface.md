---
description: 'Дополнительные сведения о: интерфейс Икордебугунманажедкаллбакк'
title: Интерфейс ICorDebugUnmanagedCallback
ms.date: 03/30/2017
api_name:
- ICorDebugUnmanagedCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnmanagedCallback
helpviewer_keywords:
- ICorDebugUnmanagedCallback interface [.NET Framework debugging]
ms.assetid: bc71cbca-7d73-40e5-84dd-2109fade3c2a
topic_type:
- apiref
ms.openlocfilehash: 6d8aa398ff7121e360c3da66671781cd169b6228
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690552"
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="c6fce-103">Интерфейс ICorDebugUnmanagedCallback</span><span class="sxs-lookup"><span data-stu-id="c6fce-103">ICorDebugUnmanagedCallback Interface</span></span>

<span data-ttu-id="c6fce-104">Предоставляет уведомления о событиях машинного кода, которые не связаны напрямую с общеязыковой средой выполнения (CLR).</span><span class="sxs-lookup"><span data-stu-id="c6fce-104">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c6fce-105">Методы</span><span class="sxs-lookup"><span data-stu-id="c6fce-105">Methods</span></span>  
  
|<span data-ttu-id="c6fce-106">Метод</span><span class="sxs-lookup"><span data-stu-id="c6fce-106">Method</span></span>|<span data-ttu-id="c6fce-107">Описание</span><span class="sxs-lookup"><span data-stu-id="c6fce-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c6fce-108">Метод DebugEvent</span><span class="sxs-lookup"><span data-stu-id="c6fce-108">DebugEvent Method</span></span>](icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="c6fce-109">Уведомляет отладчик о срабатывании собственного события.</span><span class="sxs-lookup"><span data-stu-id="c6fce-109">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6fce-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="c6fce-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c6fce-111">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="c6fce-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6fce-112">Требования</span><span class="sxs-lookup"><span data-stu-id="c6fce-112">Requirements</span></span>  

 <span data-ttu-id="c6fce-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6fce-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6fce-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c6fce-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6fce-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6fce-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6fce-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6fce-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6fce-117">См. также</span><span class="sxs-lookup"><span data-stu-id="c6fce-117">See also</span></span>

- [<span data-ttu-id="c6fce-118">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="c6fce-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
