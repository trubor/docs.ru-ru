---
description: 'Дополнительные сведения о методе: ICorDebugNativeFrame:: GetIP'
title: Метод ICorDebugNativeFrame::GetIP
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
- ICorDebugNativeFrame::GetIP method [.NET Framework debugging]
ms.assetid: 99f693f3-d3b9-4fd8-9d09-b8efd03f7b67
topic_type:
- apiref
ms.openlocfilehash: f36a14c38aa6c3754cf78eca8c657adc76469067
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637843"
---
# <a name="icordebugnativeframegetip-method"></a><span data-ttu-id="73711-103">Метод ICorDebugNativeFrame::GetIP</span><span class="sxs-lookup"><span data-stu-id="73711-103">ICorDebugNativeFrame::GetIP Method</span></span>

<span data-ttu-id="73711-104">Возвращает расположение смещения машинного кода, в котором в данный момент установлен указатель инструкции.</span><span class="sxs-lookup"><span data-stu-id="73711-104">Gets the native code offset location to which the instruction pointer is currently set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73711-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="73711-105">Syntax</span></span>  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32           *pnOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73711-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="73711-106">Parameters</span></span>  

 `pnOffset`  
 <span data-ttu-id="73711-107">заполняет Указатель на положение смещения в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="73711-107">[out] A pointer to the offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73711-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="73711-108">Remarks</span></span>  

 <span data-ttu-id="73711-109">Если кадр стека, представленный этим «ICorDebugNativeFrame», активен, то смещение — это адрес следующей инструкции, которая будет выполнена.</span><span class="sxs-lookup"><span data-stu-id="73711-109">If the stack frame that is represented by this "ICorDebugNativeFrame" is active, the offset is the address of the next instruction to be executed.</span></span> <span data-ttu-id="73711-110">Если этот кадр стека неактивен, то смещение является адресом следующей инструкции, которая будет выполнена при повторной активации кадра стека.</span><span class="sxs-lookup"><span data-stu-id="73711-110">If this stack frame is not active, the offset is the address of the next instruction to be executed when the stack frame is reactivated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73711-111">Требования</span><span class="sxs-lookup"><span data-stu-id="73711-111">Requirements</span></span>  

 <span data-ttu-id="73711-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73711-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73711-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73711-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73711-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73711-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73711-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73711-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73711-116">См. также</span><span class="sxs-lookup"><span data-stu-id="73711-116">See also</span></span>
