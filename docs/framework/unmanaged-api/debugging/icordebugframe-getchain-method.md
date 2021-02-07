---
description: 'Дополнительные сведения о методе ICorDebugFrame:: "Chain"'
title: Метод ICorDebugFrame::GetChain
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetChain
helpviewer_keywords:
- ICorDebugFrame::GetChain method [.NET Framework debugging]
- GetChain method [.NET Framework debugging]
ms.assetid: e28e51d3-8f73-494f-bcd4-48bac239fbe1
topic_type:
- apiref
ms.openlocfilehash: d162d484a54f107fb5937e57f60e2b82cad90ca1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693061"
---
# <a name="icordebugframegetchain-method"></a><span data-ttu-id="bb0c8-103">Метод ICorDebugFrame::GetChain</span><span class="sxs-lookup"><span data-stu-id="bb0c8-103">ICorDebugFrame::GetChain Method</span></span>

<span data-ttu-id="bb0c8-104">Возвращает указатель на цепочку, частью которой является этот кадр.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-104">Gets a pointer to the chain this frame is a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb0c8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bb0c8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetChain (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb0c8-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="bb0c8-106">Parameters</span></span>  

 `ppChain`  
 <span data-ttu-id="bb0c8-107">заполняет Указатель на адрес объекта ICorDebugChain, который представляет цепочку, содержащую этот кадр.</span><span class="sxs-lookup"><span data-stu-id="bb0c8-107">[out] A pointer to the address of an ICorDebugChain object that represents the chain containing this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb0c8-108">Требования</span><span class="sxs-lookup"><span data-stu-id="bb0c8-108">Requirements</span></span>  

 <span data-ttu-id="bb0c8-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb0c8-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb0c8-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bb0c8-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb0c8-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb0c8-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb0c8-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb0c8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
