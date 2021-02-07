---
description: 'Дополнительные сведения о методе: ICorDebugChain:: Manage'
title: Метод ICorDebugChain::IsManaged
ms.date: 03/30/2017
api_name:
- ICorDebugChain.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::IsManaged
helpviewer_keywords:
- ICorDebugChain::IsManaged method [.NET Framework debugging]
- IsManaged method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 17b389a0-1a4d-4e8a-8613-9bc1769930f9
topic_type:
- apiref
ms.openlocfilehash: 200b76350d474645a40f8ee35859c2db5420ea0a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694856"
---
# <a name="icordebugchainismanaged-method"></a><span data-ttu-id="dec7a-103">Метод ICorDebugChain::IsManaged</span><span class="sxs-lookup"><span data-stu-id="dec7a-103">ICorDebugChain::IsManaged Method</span></span>

<span data-ttu-id="dec7a-104">Возвращает значение, указывающее, выполняется ли в этой цепочке управляемый код.</span><span class="sxs-lookup"><span data-stu-id="dec7a-104">Gets a value that indicates whether this chain is running managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dec7a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dec7a-105">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL               *pManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dec7a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="dec7a-106">Parameters</span></span>  

 `pManaged`  
 <span data-ttu-id="dec7a-107">[out] `true` значение, если в этой цепочке выполняется управляемый код; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="dec7a-107">[out] `true` if this chain is running managed code; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dec7a-108">Требования</span><span class="sxs-lookup"><span data-stu-id="dec7a-108">Requirements</span></span>  

 <span data-ttu-id="dec7a-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dec7a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dec7a-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dec7a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dec7a-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dec7a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dec7a-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dec7a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
