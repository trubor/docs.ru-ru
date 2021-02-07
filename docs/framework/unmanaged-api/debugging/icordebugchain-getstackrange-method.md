---
description: 'Дополнительные сведения о методе: ICorDebugChain:: GetStackRange'
title: Метод ICorDebugChain::GetStackRange
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetStackRange
helpviewer_keywords:
- ICorDebugChain::GetStackRange method [.NET Framework debugging]
- GetStackRange method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 554284e7-3f6c-4d40-8da5-1c9317fbd484
topic_type:
- apiref
ms.openlocfilehash: 066dda06564655350d799dabb54acd622b828172
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694934"
---
# <a name="icordebugchaingetstackrange-method"></a><span data-ttu-id="d4de7-103">Метод ICorDebugChain::GetStackRange</span><span class="sxs-lookup"><span data-stu-id="d4de7-103">ICorDebugChain::GetStackRange Method</span></span>

<span data-ttu-id="d4de7-104">Возвращает диапазон адресов сегмента стека для этой цепочки.</span><span class="sxs-lookup"><span data-stu-id="d4de7-104">Gets the address range of the stack segment for this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4de7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d4de7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4de7-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d4de7-106">Parameters</span></span>  

 `pStart`  
 <span data-ttu-id="d4de7-107">заполняет Указатель на `CORDB_ADDRESS` значение, которое является начальным адресом сегмента стека.</span><span class="sxs-lookup"><span data-stu-id="d4de7-107">[out] A pointer to a `CORDB_ADDRESS` value that is the starting address of the stack segment.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="d4de7-108">заполняет Указатель на `CORDB_ADDRESS` значение, которое является конечным адресом сегмента стека.</span><span class="sxs-lookup"><span data-stu-id="d4de7-108">[out] A pointer to a `CORDB_ADDRESS` value that is the ending address of the stack segment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4de7-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="d4de7-109">Remarks</span></span>  

 <span data-ttu-id="d4de7-110">Числовой диапазон имеет смысл только для сравнения расположений в кадрах стека.</span><span class="sxs-lookup"><span data-stu-id="d4de7-110">The numeric range is meaningful only for comparison of stack frame locations.</span></span> <span data-ttu-id="d4de7-111">Вы не можете делать предположения о том, что фактически хранится в стеке.</span><span class="sxs-lookup"><span data-stu-id="d4de7-111">You cannot make any assumptions about what is actually stored on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4de7-112">Требования</span><span class="sxs-lookup"><span data-stu-id="d4de7-112">Requirements</span></span>  

 <span data-ttu-id="d4de7-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4de7-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4de7-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d4de7-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4de7-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4de7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4de7-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4de7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
