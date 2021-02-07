---
description: 'Дополнительные сведения о методе: ICorDebugChain:: Reason'
title: Метод ICorDebugChain::GetReason
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- GetReason
helpviewer_keywords:
- GetReason method [.NET Framework debugging]
- ICorDebugChain::GetReason method [.NET Framework debugging]
ms.assetid: 9f9f62b9-113a-4a98-8f9b-b593cef27b03
topic_type:
- apiref
ms.openlocfilehash: 0952d09db6d43f7970ba9e8c46c409fb2cd4b131
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694973"
---
# <a name="icordebugchaingetreason-method"></a><span data-ttu-id="bbf11-103">Метод ICorDebugChain::GetReason</span><span class="sxs-lookup"><span data-stu-id="bbf11-103">ICorDebugChain::GetReason Method</span></span>

<span data-ttu-id="bbf11-104">Возвращает причину женесис данной вызывающей цепочки.</span><span class="sxs-lookup"><span data-stu-id="bbf11-104">Gets the reason for the genesis of this calling chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbf11-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bbf11-105">Syntax</span></span>  
  
```cpp  
HRESULT GetReason (  
    [out] CorDebugChainReason *pReason  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bbf11-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="bbf11-106">Parameters</span></span>  

 `pReason`  
 <span data-ttu-id="bbf11-107">заполняет Указатель на значение (побитовое сочетание) перечисления Кордебугчаинреасон, которое указывает причину женесис данной вызывающей цепочки.</span><span class="sxs-lookup"><span data-stu-id="bbf11-107">[out] A pointer to a value (a bitwise combination) of the CorDebugChainReason enumeration that indicates the reason for the genesis of this calling chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbf11-108">Требования</span><span class="sxs-lookup"><span data-stu-id="bbf11-108">Requirements</span></span>  

 <span data-ttu-id="bbf11-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbf11-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbf11-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bbf11-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bbf11-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bbf11-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bbf11-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbf11-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
