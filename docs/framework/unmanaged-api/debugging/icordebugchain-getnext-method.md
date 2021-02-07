---
description: 'Дополнительные сведения о методе: ICorDebugChain:: GetNext'
title: Метод ICorDebugChain::GetNext
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetNext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetNext
helpviewer_keywords:
- GetNext method [.NET Framework debugging]
- ICorDebugChain::GetNext method [.NET Framework debugging]
ms.assetid: 8d9744a5-e08b-4ab2-9855-5c22711cc1e6
topic_type:
- apiref
ms.openlocfilehash: ced7032feffa4c14c07341242b854c08b8c897a5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661328"
---
# <a name="icordebugchaingetnext-method"></a><span data-ttu-id="3003b-103">Метод ICorDebugChain::GetNext</span><span class="sxs-lookup"><span data-stu-id="3003b-103">ICorDebugChain::GetNext Method</span></span>

<span data-ttu-id="3003b-104">Возвращает следующую цепь кадров для потока.</span><span class="sxs-lookup"><span data-stu-id="3003b-104">Gets the next chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3003b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3003b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNext (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3003b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="3003b-106">Parameters</span></span>  

 `ppChain`  
 <span data-ttu-id="3003b-107">заполняет Указатель на адрес объекта ICorDebugChain, который представляет следующую цепь кадров для потока.</span><span class="sxs-lookup"><span data-stu-id="3003b-107">[out] A pointer to the address of an ICorDebugChain object that represents the next chain of frames for the thread.</span></span> <span data-ttu-id="3003b-108">Если цепочка является последней, `ppChain` значение равно null.</span><span class="sxs-lookup"><span data-stu-id="3003b-108">If this chain is the last chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3003b-109">Требования</span><span class="sxs-lookup"><span data-stu-id="3003b-109">Requirements</span></span>  

 <span data-ttu-id="3003b-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3003b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3003b-111">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3003b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3003b-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3003b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3003b-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3003b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
