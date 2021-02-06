---
description: 'Дополнительные сведения о методе ICorDebugThread:: Креативал'
title: Метод ICorDebugThread::CreateEval
ms.date: 03/30/2017
api_name:
- ICorDebugThread.CreateEval
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateEval
helpviewer_keywords:
- CreateEval method [.NET Framework debugging]
- ICorDebugThread::CreateEval method [.NET Framework debugging]
ms.assetid: 36605067-33d3-4579-9c72-fb0e551ab0f1
topic_type:
- apiref
ms.openlocfilehash: a789840e099a14b584e5713bee12f5c4b0717fe7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659391"
---
# <a name="icordebugthreadcreateeval-method"></a><span data-ttu-id="f41d0-103">Метод ICorDebugThread::CreateEval</span><span class="sxs-lookup"><span data-stu-id="f41d0-103">ICorDebugThread::CreateEval Method</span></span>

<span data-ttu-id="f41d0-104">Создает объект ICorDebugEval, который собирает и предоставляет функциональные возможности этого ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="f41d0-104">Creates an ICorDebugEval object that collects and exposes the functionality of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f41d0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f41d0-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f41d0-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f41d0-106">Parameters</span></span>  

 `ppEval`  
 <span data-ttu-id="f41d0-107">заполняет Указатель на адрес `ICorDebugEval` объекта, который собирает и предоставляет функциональные возможности этого потока.</span><span class="sxs-lookup"><span data-stu-id="f41d0-107">[out] A pointer to the address of an `ICorDebugEval` object that collects and exposes the functionality of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f41d0-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="f41d0-108">Remarks</span></span>  

 <span data-ttu-id="f41d0-109">Объект вычисления перед выполнением вычислений выдаст новую цепочку в потоке.</span><span class="sxs-lookup"><span data-stu-id="f41d0-109">The evaluation object will push a new chain on the thread before doing its computation.</span></span> <span data-ttu-id="f41d0-110">Это прерывает вычисления, выполняемые в данный момент в потоке до завершения оценки.</span><span class="sxs-lookup"><span data-stu-id="f41d0-110">This interrupts the computation currently being performed on the thread until the evaluation completes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f41d0-111">Требования</span><span class="sxs-lookup"><span data-stu-id="f41d0-111">Requirements</span></span>  

 <span data-ttu-id="f41d0-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f41d0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f41d0-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f41d0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f41d0-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f41d0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f41d0-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f41d0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
