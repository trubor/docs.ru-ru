---
description: 'Дополнительные сведения о методе: ICorDebugChain:: Previous'
title: Метод ICorDebugChain::GetPrevious
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetPrevious
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetPrevious
helpviewer_keywords:
- ICorDebugChain::GetPrevious method [.NET Framework debugging]
- GetPrevious method [.NET Framework debugging]
ms.assetid: 58eed4c8-d80c-4c6a-a875-967a90dd926c
topic_type:
- apiref
ms.openlocfilehash: 169c46afd545835e6da87686a8e74ecd12173904
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661289"
---
# <a name="icordebugchaingetprevious-method"></a><span data-ttu-id="e26b2-103">Метод ICorDebugChain::GetPrevious</span><span class="sxs-lookup"><span data-stu-id="e26b2-103">ICorDebugChain::GetPrevious Method</span></span>

<span data-ttu-id="e26b2-104">Возвращает предыдущую цепочку кадров для потока.</span><span class="sxs-lookup"><span data-stu-id="e26b2-104">Gets the previous chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e26b2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e26b2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetPrevious (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e26b2-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e26b2-106">Parameters</span></span>  

 `ppChain`  
 <span data-ttu-id="e26b2-107">заполняет Указатель на адрес объекта ICorDebugChain, представляющий предыдущую цепочку кадров для данного потока.</span><span class="sxs-lookup"><span data-stu-id="e26b2-107">[out] A pointer to the address of an ICorDebugChain object that represents the previous chain of frames for this thread.</span></span> <span data-ttu-id="e26b2-108">Если эта цепочка является первой, `ppChain` то параметр имеет значение null.</span><span class="sxs-lookup"><span data-stu-id="e26b2-108">If this chain is the first chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e26b2-109">Требования</span><span class="sxs-lookup"><span data-stu-id="e26b2-109">Requirements</span></span>  

 <span data-ttu-id="e26b2-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e26b2-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e26b2-111">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e26b2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e26b2-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e26b2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e26b2-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e26b2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
