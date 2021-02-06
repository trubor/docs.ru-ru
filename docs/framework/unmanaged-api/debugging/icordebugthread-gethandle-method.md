---
description: 'Дополнительные сведения о методе ICorDebugThread:: getHandler'
title: Метод ICorDebugThread::GetHandle
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetHandle method [.NET Framework debugging]
ms.assetid: 172ef8c4-2ead-4cfc-bd2e-dee4fb7191cd
topic_type:
- apiref
ms.openlocfilehash: 378bb395e56f0fc287a480d67d2047e082d0796f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659105"
---
# <a name="icordebugthreadgethandle-method"></a><span data-ttu-id="9eede-103">Метод ICorDebugThread::GetHandle</span><span class="sxs-lookup"><span data-stu-id="9eede-103">ICorDebugThread::GetHandle Method</span></span>

<span data-ttu-id="9eede-104">Возвращает текущий маркер для активной части этого ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="9eede-104">Gets the current handle for the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9eede-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9eede-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9eede-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="9eede-106">Parameters</span></span>  

 `phThreadHandle`  
 <span data-ttu-id="9eede-107">заполняет Указатель на ХСРЕАД, который является маркером активной части этого потока.</span><span class="sxs-lookup"><span data-stu-id="9eede-107">[out] A pointer to an HTHREAD that is the handle of the active part of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9eede-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="9eede-108">Remarks</span></span>  

 <span data-ttu-id="9eede-109">Этот маркер может измениться при выполнении процесса и может отличаться для разных частей потока.</span><span class="sxs-lookup"><span data-stu-id="9eede-109">The handle may change as the process executes, and may be different for different parts of the thread.</span></span>  
  
 <span data-ttu-id="9eede-110">Этот обработчик принадлежит API отладки.</span><span class="sxs-lookup"><span data-stu-id="9eede-110">This handle is owned by the debugging API.</span></span> <span data-ttu-id="9eede-111">Отладчик должен дублировать его перед использованием.</span><span class="sxs-lookup"><span data-stu-id="9eede-111">The debugger should duplicate it before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9eede-112">Требования</span><span class="sxs-lookup"><span data-stu-id="9eede-112">Requirements</span></span>  

 <span data-ttu-id="9eede-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9eede-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9eede-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9eede-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9eede-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9eede-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9eede-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9eede-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
