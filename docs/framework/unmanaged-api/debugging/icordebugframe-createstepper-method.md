---
description: 'Дополнительные сведения: метод ICorDebugFrame:: Креатестеппер'
title: Метод ICorDebugFrame::CreateStepper
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::CreateStepper
helpviewer_keywords:
- ICorDebugFrame::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 689e7f28-20c1-4d5c-9baa-17441cd63a88
topic_type:
- apiref
ms.openlocfilehash: 394418b89fd7a1c780a5bc33b97b8ef40bab8df2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693100"
---
# <a name="icordebugframecreatestepper-method"></a><span data-ttu-id="dda54-103">Метод ICorDebugFrame::CreateStepper</span><span class="sxs-lookup"><span data-stu-id="dda54-103">ICorDebugFrame::CreateStepper Method</span></span>

<span data-ttu-id="dda54-104">Возвращает средство, позволяющее отладчику выполнять операции пошагового выполнения по отношению к этому ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="dda54-104">Gets a stepper that allows the debugger to perform stepping operations relative to this ICorDebugFrame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dda54-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dda54-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dda54-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="dda54-106">Parameters</span></span>  

 `ppStepper`  
 <span data-ttu-id="dda54-107">заполняет Указатель на адрес объекта ICorDebugStepper, который позволяет отладчику выполнять операции пошагового выполнения по отношению к текущему кадру.</span><span class="sxs-lookup"><span data-stu-id="dda54-107">[out] A pointer to the address of an ICorDebugStepper object that allows the debugger to perform stepping operations relative to the current frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dda54-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="dda54-108">Remarks</span></span>  

 <span data-ttu-id="dda54-109">Если кадр неактивен, объект средства Организации, как правило, должен вернуться к кадру до завершения этого шага.</span><span class="sxs-lookup"><span data-stu-id="dda54-109">If the frame is not active, the stepper object will typically have to return to the frame before the step is completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dda54-110">Требования</span><span class="sxs-lookup"><span data-stu-id="dda54-110">Requirements</span></span>  

 <span data-ttu-id="dda54-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dda54-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dda54-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dda54-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dda54-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dda54-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dda54-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dda54-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
