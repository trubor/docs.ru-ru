---
description: 'Дополнительные сведения о методе: ICorDebugChain:: Жетактивефраме'
title: Метод ICorDebugChain::GetActiveFrame
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetActiveFrame
helpviewer_keywords:
- ICorDebugChain::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 36887017-670b-4f21-b406-8fab956f84a3
topic_type:
- apiref
ms.openlocfilehash: d46906d9d6c671880d9446d889cdf9f83f3b4366
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661428"
---
# <a name="icordebugchaingetactiveframe-method"></a><span data-ttu-id="dd4fa-103">Метод ICorDebugChain::GetActiveFrame</span><span class="sxs-lookup"><span data-stu-id="dd4fa-103">ICorDebugChain::GetActiveFrame Method</span></span>

<span data-ttu-id="dd4fa-104">Возвращает активный (то есть самый последний) кадр в цепочке.</span><span class="sxs-lookup"><span data-stu-id="dd4fa-104">Gets the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd4fa-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dd4fa-105">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd4fa-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="dd4fa-106">Parameters</span></span>  

 `ppFrame`  
 <span data-ttu-id="dd4fa-107">заполняет Указатель на адрес объекта ICorDebugFrame, который представляет активный (то есть самый последний) кадр в цепочке.</span><span class="sxs-lookup"><span data-stu-id="dd4fa-107">[out] A pointer to the address of an ICorDebugFrame object that represents the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd4fa-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="dd4fa-108">Remarks</span></span>  

 <span data-ttu-id="dd4fa-109">Если управляемый фрейм стека недоступен, `ppFrame` устанавливается в значение null.</span><span class="sxs-lookup"><span data-stu-id="dd4fa-109">If no managed stack frame is available, `ppFrame` is set to null.</span></span>  
  
 <span data-ttu-id="dd4fa-110">Если активный кадр недоступен, вызов будет выполнен и `ppFrame` будет иметь значение null.</span><span class="sxs-lookup"><span data-stu-id="dd4fa-110">If the active frame is not available, the call will succeed and `ppFrame` will be null.</span></span> <span data-ttu-id="dd4fa-111">Активные фреймы не будут доступны для цепочек, инициированных из-за CHAIN_ENTER_UNMANAGED, и для некоторых цепочек, инициированных из-за CHAIN_CLASS_INIT.</span><span class="sxs-lookup"><span data-stu-id="dd4fa-111">Active frames will not be available for chains initiated due to CHAIN_ENTER_UNMANAGED, and for some chains initiated due to CHAIN_CLASS_INIT.</span></span> <span data-ttu-id="dd4fa-112">См. раздел перечисление Кордебугчаинреасон.</span><span class="sxs-lookup"><span data-stu-id="dd4fa-112">See the CorDebugChainReason enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd4fa-113">Требования</span><span class="sxs-lookup"><span data-stu-id="dd4fa-113">Requirements</span></span>  

 <span data-ttu-id="dd4fa-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd4fa-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd4fa-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dd4fa-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dd4fa-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd4fa-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd4fa-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd4fa-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
