---
description: 'Дополнительные сведения о: ICorDebugStepper::D еактивате Method'
title: Метод ICorDebugStepper::Deactivate
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.Deactivate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Deactivate
helpviewer_keywords:
- Deactivate method [.NET Framework debugging]
- ICorDebugStepper::Deactivate method [.NET Framework debugging]
ms.assetid: 855f4199-b62d-40ce-998e-1eb4a1772142
topic_type:
- apiref
ms.openlocfilehash: 039c52f5bc237506dcc648ace70789c8eb7ef8c9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794667"
---
# <a name="icordebugstepperdeactivate-method"></a><span data-ttu-id="7b5ef-103">Метод ICorDebugStepper::Deactivate</span><span class="sxs-lookup"><span data-stu-id="7b5ef-103">ICorDebugStepper::Deactivate Method</span></span>

<span data-ttu-id="7b5ef-104">Заставляет этот объект ICorDebugStepper отменить последнюю полученную команду шага.</span><span class="sxs-lookup"><span data-stu-id="7b5ef-104">Causes this ICorDebugStepper to cancel the last step command that it received.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b5ef-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7b5ef-105">Syntax</span></span>  
  
```cpp  
HRESULT Deactivate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="7b5ef-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="7b5ef-106">Remarks</span></span>  

 <span data-ttu-id="7b5ef-107">Новая команда пошагового выполнения может быть выдана после отмены последней полученной команды Step.</span><span class="sxs-lookup"><span data-stu-id="7b5ef-107">A new stepping command may be issued after the most recently received step command has been canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b5ef-108">Требования</span><span class="sxs-lookup"><span data-stu-id="7b5ef-108">Requirements</span></span>  

 <span data-ttu-id="7b5ef-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b5ef-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b5ef-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b5ef-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b5ef-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b5ef-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b5ef-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b5ef-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
