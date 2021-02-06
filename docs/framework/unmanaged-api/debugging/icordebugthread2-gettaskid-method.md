---
description: 'Дополнительные сведения о методе: ICorDebugThread2:: GetTaskID'
title: Метод ICorDebugThread2::GetTaskID
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetTaskID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetTaskID
helpviewer_keywords:
- ICorDebugThread2::GetTaskID method [.NET Framework debugging]
- GetTaskID method [.NET Framework debugging]
ms.assetid: 6ba3c6ee-4ba1-4c98-bf1e-8531acd3da09
topic_type:
- apiref
ms.openlocfilehash: 5429daee9150d63834c747dd5ebb763dd6f0da6c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658689"
---
# <a name="icordebugthread2gettaskid-method"></a><span data-ttu-id="bfbee-103">Метод ICorDebugThread2::GetTaskID</span><span class="sxs-lookup"><span data-stu-id="bfbee-103">ICorDebugThread2::GetTaskID Method</span></span>

<span data-ttu-id="bfbee-104">Возвращает идентификатор задачи, выполняющейся в этом потоке.</span><span class="sxs-lookup"><span data-stu-id="bfbee-104">Gets the identifier of the task running on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfbee-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bfbee-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bfbee-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="bfbee-106">Parameters</span></span>  

 `pTaskId`  
 <span data-ttu-id="bfbee-107">заполняет Указатель на идентификатор задачи, выполняемой в потоке, представленном этим объектом ICorDebugThread2.</span><span class="sxs-lookup"><span data-stu-id="bfbee-107">[out] A pointer to the identifier of the task running on the thread represented by this ICorDebugThread2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bfbee-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="bfbee-108">Remarks</span></span>  

 <span data-ttu-id="bfbee-109">Задача может выполняться только в потоке, если поток связан с соединением.</span><span class="sxs-lookup"><span data-stu-id="bfbee-109">A task can only be running on the thread if the thread is associated with a connection.</span></span> <span data-ttu-id="bfbee-110">`GetTaskID` Возвращает ноль в `pTaskId` , если поток не связан с соединением.</span><span class="sxs-lookup"><span data-stu-id="bfbee-110">`GetTaskID` returns zero in `pTaskId` if the thread is not associated with a connection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfbee-111">Требования</span><span class="sxs-lookup"><span data-stu-id="bfbee-111">Requirements</span></span>  

 <span data-ttu-id="bfbee-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bfbee-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfbee-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bfbee-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bfbee-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bfbee-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bfbee-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfbee-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
