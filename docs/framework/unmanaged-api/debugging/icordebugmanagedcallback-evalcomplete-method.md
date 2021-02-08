---
description: 'Дополнительные сведения о методе: ICorDebugManagedCallback:: Евалкомплете'
title: Метод ICorDebugManagedCallback::EvalComplete
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EvalComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EvalComplete
helpviewer_keywords:
- ICorDebugManagedCallback::EvalComplete method [.NET Framework debugging]
- EvalComplete method [.NET Framework debugging]
ms.assetid: f74ab4eb-cd1b-407c-a66d-8ec0d85647f3
topic_type:
- apiref
ms.openlocfilehash: 729b00bc630ef5d6e508b75bd6483580f1dd75b5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791038"
---
# <a name="icordebugmanagedcallbackevalcomplete-method"></a><span data-ttu-id="e1214-103">Метод ICorDebugManagedCallback::EvalComplete</span><span class="sxs-lookup"><span data-stu-id="e1214-103">ICorDebugManagedCallback::EvalComplete Method</span></span>

<span data-ttu-id="e1214-104">Уведомляет отладчик о завершении оценки.</span><span class="sxs-lookup"><span data-stu-id="e1214-104">Notifies the debugger that an evaluation has been completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1214-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e1214-105">Syntax</span></span>  
  
```cpp  
HRESULT EvalComplete (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1214-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e1214-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="e1214-107">окне Указатель на объект ICorDebugAppDomain, представляющий домен приложения, в котором была выполнена оценка.</span><span class="sxs-lookup"><span data-stu-id="e1214-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation was performed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="e1214-108">окне Указатель на объект ICorDebugThread, представляющий поток, в котором выполнялась оценка.</span><span class="sxs-lookup"><span data-stu-id="e1214-108">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation was performed.</span></span>  
  
 `pEval`  
 <span data-ttu-id="e1214-109">окне Указатель на объект ICorDebugEval, представляющий код, который выполнил вычисление.</span><span class="sxs-lookup"><span data-stu-id="e1214-109">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1214-110">Требования</span><span class="sxs-lookup"><span data-stu-id="e1214-110">Requirements</span></span>  

 <span data-ttu-id="e1214-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1214-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1214-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e1214-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1214-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1214-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1214-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1214-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1214-115">См. также</span><span class="sxs-lookup"><span data-stu-id="e1214-115">See also</span></span>

- [<span data-ttu-id="e1214-116">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="e1214-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
