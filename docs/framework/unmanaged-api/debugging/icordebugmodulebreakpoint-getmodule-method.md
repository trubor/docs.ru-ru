---
description: 'Дополнительные сведения о методе: Икордебугмодулебреакпоинт:: module'
title: Метод ICorDebugModuleBreakpoint::GetModule
ms.date: 03/30/2017
api_name:
- ICorDebugModuleBreakpoint.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleBreakpoint::GetModule
helpviewer_keywords:
- ICorDebugModuleBreakpoint::GetModule method [.NET Framework debugging]
- GetModule method, ICorDebugModuleBreakpoint interface [.NET Framework debugging]
ms.assetid: ffd5d9ec-4564-4200-b625-b306eec0ebd7
topic_type:
- apiref
ms.openlocfilehash: 3498f9d644d6195f2cd0f83d30417c447d200f3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790793"
---
# <a name="icordebugmodulebreakpointgetmodule-method"></a><span data-ttu-id="65664-103">Метод ICorDebugModuleBreakpoint::GetModule</span><span class="sxs-lookup"><span data-stu-id="65664-103">ICorDebugModuleBreakpoint::GetModule Method</span></span>

<span data-ttu-id="65664-104">Возвращает указатель интерфейса на "ICorDebugModule", ссылающийся на модуль, в котором задана эта точка останова.</span><span class="sxs-lookup"><span data-stu-id="65664-104">Gets an interface pointer to an "ICorDebugModule" that references the module in which this breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65664-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="65664-105">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule   **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65664-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="65664-106">Parameters</span></span>  

 `ppModule`  
 <span data-ttu-id="65664-107">заполняет Указатель на адрес `ICorDebugModule` интерфейса, который ссылается на модуль, в котором задана точка останова.</span><span class="sxs-lookup"><span data-stu-id="65664-107">[out] A pointer to the address of an `ICorDebugModule` interface that references the module in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65664-108">Требования</span><span class="sxs-lookup"><span data-stu-id="65664-108">Requirements</span></span>  

 <span data-ttu-id="65664-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65664-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65664-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="65664-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65664-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65664-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65664-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65664-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65664-113">См. также</span><span class="sxs-lookup"><span data-stu-id="65664-113">See also</span></span>
