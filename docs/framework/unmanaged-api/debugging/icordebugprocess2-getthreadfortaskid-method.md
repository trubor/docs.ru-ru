---
description: 'Дополнительные сведения о методе: ICorDebugProcess2:: Жетсреадфортаскид'
title: Метод ICorDebugProcess2::GetThreadForTaskID
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetThreadForTaskID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetThreadForTaskID
helpviewer_keywords:
- ICorDebugProcess2::GetThreadForTaskId method [.NET Framework debugging]
- GetThreadForTaskID method [.NET Framework debugging]
ms.assetid: 32d54a5b-8ad3-405b-a1b9-0936a3b49d1e
topic_type:
- apiref
ms.openlocfilehash: aafb1223f6e2e73aae600fd482c76b84c57dae52
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650135"
---
# <a name="icordebugprocess2getthreadfortaskid-method"></a><span data-ttu-id="1ee24-103">Метод ICorDebugProcess2::GetThreadForTaskID</span><span class="sxs-lookup"><span data-stu-id="1ee24-103">ICorDebugProcess2::GetThreadForTaskID Method</span></span>

<span data-ttu-id="1ee24-104">Возвращает поток, в котором выполняются задачи с указанным идентификатором.</span><span class="sxs-lookup"><span data-stu-id="1ee24-104">Gets the thread on which the task with the specified identifier is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ee24-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1ee24-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadForTaskID (  
    [in]  TASKID            taskid,  
    [out] ICorDebugThread2  **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ee24-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ee24-106">Parameters</span></span>  

 `taskid`  
 <span data-ttu-id="1ee24-107">окне Идентификатор задачи.</span><span class="sxs-lookup"><span data-stu-id="1ee24-107">[in] The identifier of the task.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="1ee24-108">заполняет Указатель на адрес объекта ICorDebugThread2, который представляет поток для извлечения.</span><span class="sxs-lookup"><span data-stu-id="1ee24-108">[out] A pointer to the address of an ICorDebugThread2 object that represents the thread to be retrieved.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ee24-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="1ee24-109">Remarks</span></span>  

 <span data-ttu-id="1ee24-110">Узел может задать идентификатор задачи с помощью метода [ICLRTask:: SetTaskIdentifier](../hosting/iclrtask-settaskidentifier-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1ee24-110">The host can set the task identifier by using the [ICLRTask::SetTaskIdentifier](../hosting/iclrtask-settaskidentifier-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ee24-111">Требования</span><span class="sxs-lookup"><span data-stu-id="1ee24-111">Requirements</span></span>  

 <span data-ttu-id="1ee24-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ee24-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ee24-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ee24-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ee24-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ee24-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ee24-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ee24-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
