---
description: 'Дополнительные сведения о методе: ICorDebugChain::/Register'
title: Метод ICorDebugChain::GetRegisterSet
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetRegisterSet
helpviewer_keywords:
- ICorDebugChain::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: bc4288b6-3331-4ae3-990d-e1d6e62ecb67
topic_type:
- apiref
ms.openlocfilehash: 75c77838cb4ef49dd922a4e39b41e622693e928d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694960"
---
# <a name="icordebugchaingetregisterset-method"></a><span data-ttu-id="fe7b6-103">Метод ICorDebugChain::GetRegisterSet</span><span class="sxs-lookup"><span data-stu-id="fe7b6-103">ICorDebugChain::GetRegisterSet Method</span></span>

<span data-ttu-id="fe7b6-104">Возвращает набор регистров для активной части этой цепочки.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-104">Gets the register set for the active part of this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe7b6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fe7b6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe7b6-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="fe7b6-106">Parameters</span></span>  

 `ppRegisters`  
 <span data-ttu-id="fe7b6-107">заполняет Указатель на адрес объекта [ICorDebugRegisterSet](icordebugregisterset-interface.md) , который представляет набор регистров для активной части этой цепочки.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-107">[out] A pointer to the address of an [ICorDebugRegisterSet](icordebugregisterset-interface.md) object that represents the register set for the active part of this chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe7b6-108">Требования</span><span class="sxs-lookup"><span data-stu-id="fe7b6-108">Requirements</span></span>  

 <span data-ttu-id="fe7b6-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe7b6-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe7b6-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fe7b6-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fe7b6-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe7b6-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe7b6-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe7b6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
