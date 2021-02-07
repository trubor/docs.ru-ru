---
description: 'Дополнительные сведения о методе: ICorDebugChain:: Call'
title: Метод ICorDebugChain::GetCaller
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCaller
helpviewer_keywords:
- ICorDebugChain::GetCaller method [.NET Framework debugging]
- GetCaller method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: d0b8ab4b-d7d2-4fa0-945f-3d2b87e7e991
topic_type:
- apiref
ms.openlocfilehash: 5af2132b7fec9e70704db980b95221db6eb273f8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695025"
---
# <a name="icordebugchaingetcaller-method"></a><span data-ttu-id="6a785-103">Метод ICorDebugChain::GetCaller</span><span class="sxs-lookup"><span data-stu-id="6a785-103">ICorDebugChain::GetCaller Method</span></span>

<span data-ttu-id="6a785-104">Возвращает цепочку, вызвавшую эту цепь.</span><span class="sxs-lookup"><span data-stu-id="6a785-104">Gets the chain that called this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a785-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6a785-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a785-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a785-106">Parameters</span></span>  

 `ppChain`  
 <span data-ttu-id="6a785-107">заполняет Указатель на адрес объекта ICorDebugChain, который представляет вызывающую цепочку.</span><span class="sxs-lookup"><span data-stu-id="6a785-107">[out] A pointer to the address of an ICorDebugChain object that represents the calling chain.</span></span>  
  
 <span data-ttu-id="6a785-108">Если эта цепочка была вызвана недостаточной (как в случае, если эта цепочка или отладчик инициализируют стек вызовов), `ppChain` будет иметь значение null.</span><span class="sxs-lookup"><span data-stu-id="6a785-108">If this chain was spontaneously called (as would be the case if this chain or the debugger initialized the call stack), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a785-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="6a785-109">Remarks</span></span>  

 <span data-ttu-id="6a785-110">Вызывающая цепочка может находиться в другом потоке, если вызов был маршалирован в потоках.</span><span class="sxs-lookup"><span data-stu-id="6a785-110">The calling chain may be on a different thread, if the call was marshaled across threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a785-111">Требования</span><span class="sxs-lookup"><span data-stu-id="6a785-111">Requirements</span></span>  

 <span data-ttu-id="6a785-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a785-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a785-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6a785-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a785-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a785-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a785-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a785-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
