---
description: 'Дополнительные сведения о методе: ICorDebugManagedCallback:: Controlctrap-'
title: Метод ICorDebugManagedCallback::ControlCTrap
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ControlCTrap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ControlCTrap
helpviewer_keywords:
- ICorDebugManagedCallback::ControlCTrap method [.NET Framework debugging]
- ControlCTrap method [.NET Framework debugging]
ms.assetid: 0500854e-2121-43d9-a028-64312da35258
topic_type:
- apiref
ms.openlocfilehash: 9fa71dacb20ff6df21d8aabb687c2601f27643c7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791074"
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a><span data-ttu-id="60e71-103">Метод ICorDebugManagedCallback::ControlCTrap</span><span class="sxs-lookup"><span data-stu-id="60e71-103">ICorDebugManagedCallback::ControlCTrap Method</span></span>

<span data-ttu-id="60e71-104">Уведомляет отладчик о том, что в отлаживаемом процессе выполняется перехват CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="60e71-104">Notifies the debugger that a CTRL+C is trapped in the process that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60e71-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="60e71-105">Syntax</span></span>  
  
```cpp  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60e71-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="60e71-106">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="60e71-107">окне Указатель на объект ICorDebugProcess, представляющий процесс, в котором выполняется перехват CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="60e71-107">[in] A pointer to an ICorDebugProcess object that represents the process in which the CTRL+C is trapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="60e71-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="60e71-108">Return Value</span></span>  
  
|<span data-ttu-id="60e71-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="60e71-109">HRESULT</span></span>|<span data-ttu-id="60e71-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="60e71-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="60e71-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="60e71-111">S_OK</span></span>|<span data-ttu-id="60e71-112">Отладчик будет выполнять обработку ловушек CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="60e71-112">The debugger will handle the CTRL+C trap.</span></span>|  
|<span data-ttu-id="60e71-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="60e71-113">S_FALSE</span></span>|<span data-ttu-id="60e71-114">Отладчик не будет выполнять обработку ловушек CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="60e71-114">The debugger will not handle the CTRL+C trap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60e71-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="60e71-115">Remarks</span></span>  

 <span data-ttu-id="60e71-116">Все домены приложений в рамках процесса останавливаются для этого обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="60e71-116">All application domains within the process are stopped for this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60e71-117">Требования</span><span class="sxs-lookup"><span data-stu-id="60e71-117">Requirements</span></span>  

 <span data-ttu-id="60e71-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60e71-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60e71-119">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="60e71-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="60e71-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60e71-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60e71-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60e71-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60e71-122">См. также</span><span class="sxs-lookup"><span data-stu-id="60e71-122">See also</span></span>

- [<span data-ttu-id="60e71-123">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="60e71-123">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
