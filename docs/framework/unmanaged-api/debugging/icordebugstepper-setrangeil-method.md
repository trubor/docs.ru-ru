---
description: 'Дополнительные сведения о методе ICorDebugStepper:: SetRangeIL'
title: Метод ICorDebugStepper::SetRangeIL
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetRangeIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetRangeIL
helpviewer_keywords:
- SetRangeIL method [.NET Framework debugging]
- ICorDebugStepper::SetRangeIL method [.NET Framework debugging]
ms.assetid: a20c95f0-6da7-4b41-b27f-584211cebb92
topic_type:
- apiref
ms.openlocfilehash: 8bccaf8ba8e52a7fe94555fa99b1c3cf92842efe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717720"
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="d2f2c-103">Метод ICorDebugStepper::SetRangeIL</span><span class="sxs-lookup"><span data-stu-id="d2f2c-103">ICorDebugStepper::SetRangeIL Method</span></span>

<span data-ttu-id="d2f2c-104">Задает значение, указывающее, будут ли вызовы метода [ICorDebugStepper:: степранже](icordebugstepper-steprange-method.md) передавать значения аргумента, которые относятся к машинному коду или по коду языка MSIL в методе, через который выполняется пошаговое выполнение.</span><span class="sxs-lookup"><span data-stu-id="d2f2c-104">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2f2c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d2f2c-105">Syntax</span></span>  
  
```cpp  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2f2c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d2f2c-106">Parameters</span></span>  

 `bIL`  
 <span data-ttu-id="d2f2c-107">окне Задайте значение, `true` чтобы указать, что диапазоны зависят от кода MSIL.</span><span class="sxs-lookup"><span data-stu-id="d2f2c-107">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="d2f2c-108">Задайте значение, `false` чтобы указать, что диапазоны зависят от машинного кода.</span><span class="sxs-lookup"><span data-stu-id="d2f2c-108">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="d2f2c-109">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="d2f2c-109">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2f2c-110">Требования</span><span class="sxs-lookup"><span data-stu-id="d2f2c-110">Requirements</span></span>  

 <span data-ttu-id="d2f2c-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2f2c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2f2c-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d2f2c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d2f2c-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2f2c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2f2c-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2f2c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
