---
description: 'Дополнительные сведения о методе: ICorDebugChain:: Thread'
title: Метод ICorDebugChain::GetThread
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetThread
helpviewer_keywords:
- GetThread method, ICorDebugChain interface [.NET Framework debugging]
- ICorDebugChain::GetThread method [.NET Framework debugging]
ms.assetid: b3390319-6366-418c-ba80-b552ac4dfc1e
topic_type:
- apiref
ms.openlocfilehash: 090cb40c3681792ce4a30cd342e65dc02ac3f381
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694927"
---
# <a name="icordebugchaingetthread-method"></a><span data-ttu-id="9062a-103">Метод ICorDebugChain::GetThread</span><span class="sxs-lookup"><span data-stu-id="9062a-103">ICorDebugChain::GetThread Method</span></span>

<span data-ttu-id="9062a-104">Возвращает физический поток, частью которого является эта цепочка вызовов.</span><span class="sxs-lookup"><span data-stu-id="9062a-104">Gets the physical thread this call chain is part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9062a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9062a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThread (  
    [out] ICorDebugThread    **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9062a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="9062a-106">Parameters</span></span>  

 `ppThread`  
 <span data-ttu-id="9062a-107">заполняет Указатель на объект ICorDebugThread, представляющий физический поток, частью которого является эта цепочка вызовов.</span><span class="sxs-lookup"><span data-stu-id="9062a-107">[out] A pointer to an ICorDebugThread object that represents the physical thread this call chain is part of.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9062a-108">Требования</span><span class="sxs-lookup"><span data-stu-id="9062a-108">Requirements</span></span>  

 <span data-ttu-id="9062a-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9062a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9062a-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9062a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9062a-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9062a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9062a-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9062a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
