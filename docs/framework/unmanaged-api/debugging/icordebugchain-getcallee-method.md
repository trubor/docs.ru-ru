---
description: 'Дополнительные сведения о методе: ICorDebugChain:: Зовите.'
title: Метод ICorDebugChain::GetCallee
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCallee method
helpviewer_keywords:
- ICorDebugChain::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 19560c79-abdc-4bdf-a5fe-eb362a59edc0
topic_type:
- apiref
ms.openlocfilehash: 4787893c86804c648dae14bf2e6f7425808104b7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661432"
---
# <a name="icordebugchaingetcallee-method"></a><span data-ttu-id="ed278-103">Метод ICorDebugChain::GetCallee</span><span class="sxs-lookup"><span data-stu-id="ed278-103">ICorDebugChain::GetCallee Method</span></span>

<span data-ttu-id="ed278-104">Возвращает цепочку, вызванную этой цепочкой.</span><span class="sxs-lookup"><span data-stu-id="ed278-104">Gets the chain that was called by this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed278-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ed278-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed278-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ed278-106">Parameters</span></span>  

 `ppChain`  
 <span data-ttu-id="ed278-107">заполняет Указатель на адрес объекта ICorDebugChain, который представляет вызываемую цепочку.</span><span class="sxs-lookup"><span data-stu-id="ed278-107">[out] A pointer to the address of an ICorDebugChain object that represents the called chain.</span></span> <span data-ttu-id="ed278-108">Если эта цепочка выполняется в данный момент (то есть если эта цепочка не ожидает возврата вызванной цепочки), `ppChain` будет иметь значение null.</span><span class="sxs-lookup"><span data-stu-id="ed278-108">If this chain is currently executing (that is, if this chain is not waiting for a called chain to return), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed278-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="ed278-109">Remarks</span></span>  

 <span data-ttu-id="ed278-110">Эта цепочка будет ожидать возврата вызванной цепочки перед возобновлением выполнения.</span><span class="sxs-lookup"><span data-stu-id="ed278-110">This chain will wait for the called chain to return before it resumes execution.</span></span> <span data-ttu-id="ed278-111">Вызываемая цепочка может находиться в другом потоке в случае маршалинга вызовов между потоками.</span><span class="sxs-lookup"><span data-stu-id="ed278-111">The called chain may be on another thread in the case of cross-thread marshaled calls.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed278-112">Требования</span><span class="sxs-lookup"><span data-stu-id="ed278-112">Requirements</span></span>  

 <span data-ttu-id="ed278-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed278-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed278-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ed278-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ed278-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ed278-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed278-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed278-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
