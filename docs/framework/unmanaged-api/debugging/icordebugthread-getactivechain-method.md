---
description: 'Дополнительные сведения о методе ICorDebugThread:: Жетактивечаин'
title: Метод ICorDebugThread::GetActiveChain
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetActiveChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetActiveChain
helpviewer_keywords:
- ICorDebugThread::GetActiveChain method [.NET Framework debugging]
- GetActiveChain method [.NET Framework debugging]
ms.assetid: f50de1f7-40ef-4949-b542-1d9a61f7bfef
topic_type:
- apiref
ms.openlocfilehash: d9aff80801fa72a227a84b3b5216e3ffa72b0e24
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659287"
---
# <a name="icordebugthreadgetactivechain-method"></a><span data-ttu-id="f9e7e-103">Метод ICorDebugThread::GetActiveChain</span><span class="sxs-lookup"><span data-stu-id="f9e7e-103">ICorDebugThread::GetActiveChain Method</span></span>

<span data-ttu-id="f9e7e-104">Возвращает указатель интерфейса на активную (последнюю) цепь стека на этом объекте ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="f9e7e-104">Gets an interface pointer to the active (most recent) stack chain on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9e7e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f9e7e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveChain (  
    [out] ICorDebugChain **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9e7e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f9e7e-106">Parameters</span></span>  

 `ppChain`  
 <span data-ttu-id="f9e7e-107">заполняет Указатель на адрес объекта ICorDebugChain, который представляет цепочку стека.</span><span class="sxs-lookup"><span data-stu-id="f9e7e-107">[out] A pointer to the address of an ICorDebugChain object that represents the stack chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9e7e-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="f9e7e-108">Remarks</span></span>  

 <span data-ttu-id="f9e7e-109">`ppChain`Параметр имеет значение null, если цепочка стека в данный момент не активна.</span><span class="sxs-lookup"><span data-stu-id="f9e7e-109">The `ppChain` parameter is null if no stack chain is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9e7e-110">Требования</span><span class="sxs-lookup"><span data-stu-id="f9e7e-110">Requirements</span></span>  

 <span data-ttu-id="f9e7e-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9e7e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9e7e-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f9e7e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9e7e-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9e7e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9e7e-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9e7e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
