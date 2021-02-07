---
description: 'Дополнительные сведения о методе: ICorDebugNativeFrame::/Register'
title: Метод ICorDebugNativeFrame::GetRegisterSet
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetRegisterSet
helpviewer_keywords:
- ICorDebugNativeFrame::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 6f309b5f-5556-4f1e-b1dd-4fe97fc81d01
topic_type:
- apiref
ms.openlocfilehash: 8878c438ad76b1a87429e09b8a4a8bbffb90d00d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722416"
---
# <a name="icordebugnativeframegetregisterset-method"></a><span data-ttu-id="b84a3-103">Метод ICorDebugNativeFrame::GetRegisterSet</span><span class="sxs-lookup"><span data-stu-id="b84a3-103">ICorDebugNativeFrame::GetRegisterSet Method</span></span>

<span data-ttu-id="b84a3-104">Возвращает набор регистров для этого кадра стека.</span><span class="sxs-lookup"><span data-stu-id="b84a3-104">Gets the register set for this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b84a3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b84a3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b84a3-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b84a3-106">Parameters</span></span>  

 `ppRegisters`  
 <span data-ttu-id="b84a3-107">заполняет Указатель на адрес объекта [ICorDebugRegisterSet](icordebugregisterset-interface.md) , который представляет набор регистров для данного кадра стека.</span><span class="sxs-lookup"><span data-stu-id="b84a3-107">[out] A pointer to the address of an [ICorDebugRegisterSet](icordebugregisterset-interface.md) object that represents the register set for this stack frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b84a3-108">Требования</span><span class="sxs-lookup"><span data-stu-id="b84a3-108">Requirements</span></span>  

 <span data-ttu-id="b84a3-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b84a3-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b84a3-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b84a3-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b84a3-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b84a3-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b84a3-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b84a3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b84a3-113">См. также</span><span class="sxs-lookup"><span data-stu-id="b84a3-113">See also</span></span>
