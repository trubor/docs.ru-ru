---
description: 'Дополнительные сведения о методе: ICorDebugRegisterSet2:: SetRegisters'
title: Метод ICorDebugRegisterSet2::SetRegisters
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.SetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::SetRegisters
helpviewer_keywords:
- ICorDebugRegisterSet2::SetRegisters method [.NET Framework debugging]
- SetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: fe0ac7e7-c9e1-4ec1-9f4e-1c56d63d73ac
topic_type:
- apiref
ms.openlocfilehash: d58717be34e146def2a54bb49d6cd58dde7564c8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794758"
---
# <a name="icordebugregisterset2setregisters-method"></a><span data-ttu-id="14363-103">Метод ICorDebugRegisterSet2::SetRegisters</span><span class="sxs-lookup"><span data-stu-id="14363-103">ICorDebugRegisterSet2::SetRegisters Method</span></span>

<span data-ttu-id="14363-104">`SetRegisters` не реализован в платформа .NET Framework версии 2,0.</span><span class="sxs-lookup"><span data-stu-id="14363-104">`SetRegisters` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="14363-105">Этот метод не следует вызывать.</span><span class="sxs-lookup"><span data-stu-id="14363-105">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="14363-106">Используйте операции более высокого уровня, такие как [ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md) или [ICorDebugNativeFrame:: SetIP](icordebugnativeframe-setip-method.md).</span><span class="sxs-lookup"><span data-stu-id="14363-106">Use the higher-level operations such as [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) or [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14363-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="14363-107">Syntax</span></span>  
  
```cpp  
HRESULT SetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="14363-108">Требования</span><span class="sxs-lookup"><span data-stu-id="14363-108">Requirements</span></span>  

 <span data-ttu-id="14363-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14363-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14363-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="14363-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14363-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14363-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14363-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14363-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14363-113">См. также</span><span class="sxs-lookup"><span data-stu-id="14363-113">See also</span></span>

- [<span data-ttu-id="14363-114">Интерфейс ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="14363-114">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
- [<span data-ttu-id="14363-115">Интерфейс ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="14363-115">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
