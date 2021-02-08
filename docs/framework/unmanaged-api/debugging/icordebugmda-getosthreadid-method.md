---
description: 'Дополнительные сведения о методе: ICorDebugMDA:: Жетоссреадид'
title: Метод ICorDebugMDA::GetOSThreadId
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetOSThreadId
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetOSThreadId
helpviewer_keywords:
- ICorDebugMDA::GetOSThreadId method [.NET Framework debugging]
- GetOSThreadId method [.NET Framework debugging]
ms.assetid: 7ca7c364-ade4-4219-b434-9f6ae2359be6
topic_type:
- apiref
ms.openlocfilehash: f965585a6e6060a14f0cbc2a80b46124b2751e0e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801154"
---
# <a name="icordebugmdagetosthreadid-method"></a><span data-ttu-id="f7b93-103">Метод ICorDebugMDA::GetOSThreadId</span><span class="sxs-lookup"><span data-stu-id="f7b93-103">ICorDebugMDA::GetOSThreadId Method</span></span>

<span data-ttu-id="f7b93-104">Возвращает идентификатор потока операционной системы (ОС), по которому выполняется управляемый помощник по отладке (MDA), представленный [ICorDebugMDA](icordebugmda-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="f7b93-104">Gets the operating system (OS) thread identifier upon which the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md) is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7b93-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f7b93-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOSThreadId (  
    [out] DWORD    *pOsTid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7b93-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f7b93-106">Parameters</span></span>  

 `pOsTid`  
 <span data-ttu-id="f7b93-107">заполняет Указатель на идентификатор потока операционной системы.</span><span class="sxs-lookup"><span data-stu-id="f7b93-107">[out] A pointer to the OS thread identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7b93-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="f7b93-108">Remarks</span></span>  

 <span data-ttu-id="f7b93-109">Поток операционной системы используется вместо ICorDebugThread, чтобы разрешить ситуации, в которых MDA срабатывает либо в собственном потоке, либо в управляемом потоке, который еще не вошел в управляемый код.</span><span class="sxs-lookup"><span data-stu-id="f7b93-109">The OS thread is used instead of an ICorDebugThread to allow for situations in which an MDA is fired either on a native thread or on a managed thread that has not yet entered managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7b93-110">Требования</span><span class="sxs-lookup"><span data-stu-id="f7b93-110">Requirements</span></span>  

 <span data-ttu-id="f7b93-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7b93-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7b93-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7b93-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7b93-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7b93-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7b93-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7b93-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7b93-115">См. также</span><span class="sxs-lookup"><span data-stu-id="f7b93-115">See also</span></span>

- [<span data-ttu-id="f7b93-116">Интерфейс ICorDebugMDA</span><span class="sxs-lookup"><span data-stu-id="f7b93-116">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="f7b93-117">Диагностика ошибок посредством управляемых помощников по отладке</span><span class="sxs-lookup"><span data-stu-id="f7b93-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
