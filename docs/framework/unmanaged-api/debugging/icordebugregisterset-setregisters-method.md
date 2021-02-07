---
description: 'Дополнительные сведения о методе: ICorDebugRegisterSet:: SetRegisters'
title: Метод ICorDebugRegisterSet::SetRegisters
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.SetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::SetRegisters
helpviewer_keywords:
- SetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::SetRegisters method [.NET Framework debugging]
ms.assetid: ac6244b9-54ba-475f-b72a-abed6afc46ec
topic_type:
- apiref
ms.openlocfilehash: 7a83d9d01a392d7ed435292f45ee0c75765ced36
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690682"
---
# <a name="icordebugregistersetsetregisters-method"></a><span data-ttu-id="6cb89-103">Метод ICorDebugRegisterSet::SetRegisters</span><span class="sxs-lookup"><span data-stu-id="6cb89-103">ICorDebugRegisterSet::SetRegisters Method</span></span>

<span data-ttu-id="6cb89-104">`SetRegisters` не реализован в платформа .NET Framework версии 2,0.</span><span class="sxs-lookup"><span data-stu-id="6cb89-104">`SetRegisters` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="6cb89-105">Этот метод не следует вызывать.</span><span class="sxs-lookup"><span data-stu-id="6cb89-105">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6cb89-106">Используйте операции более высокого уровня, такие как [ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md) или [ICorDebugNativeFrame:: SetIP](icordebugnativeframe-setip-method.md).</span><span class="sxs-lookup"><span data-stu-id="6cb89-106">Use the higher-level operations such as [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) or [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cb89-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6cb89-107">Syntax</span></span>  
  
```cpp  
HRESULT SetRegisters (  
    [in] ULONG64   mask,  
    [in] ULONG32   regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="6cb89-108">Требования</span><span class="sxs-lookup"><span data-stu-id="6cb89-108">Requirements</span></span>  

 <span data-ttu-id="6cb89-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cb89-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cb89-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6cb89-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6cb89-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6cb89-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6cb89-112">**Платформа .NET Framework версии:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="6cb89-112">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cb89-113">См. также</span><span class="sxs-lookup"><span data-stu-id="6cb89-113">See also</span></span>

- [<span data-ttu-id="6cb89-114">Интерфейс ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="6cb89-114">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="6cb89-115">Интерфейс ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="6cb89-115">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
