---
description: 'Дополнительные сведения о методе: ICorDebugILFrame:: CanSetIP'
title: Метод ICorDebugILFrame::CanSetIP
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::CanSetIP
helpviewer_keywords:
- CanSetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::CanSetIP method [.NET Framework debugging]
ms.assetid: 16caf02f-c71e-486c-90b0-f0e54357d8f0
topic_type:
- apiref
ms.openlocfilehash: d6ba0d073e8807ac6173f7f3e3982fe1d3eb4e01
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791443"
---
# <a name="icordebugilframecansetip-method"></a><span data-ttu-id="044a7-103">Метод ICorDebugILFrame::CanSetIP</span><span class="sxs-lookup"><span data-stu-id="044a7-103">ICorDebugILFrame::CanSetIP Method</span></span>

<span data-ttu-id="044a7-104">Возвращает значение HRESULT, указывающее, безопасно ли устанавливать указатель инструкции в указанном расположении смещения в коде на языке MSIL.</span><span class="sxs-lookup"><span data-stu-id="044a7-104">Gets an HRESULT that indicates whether it is safe to set the instruction pointer to the specified offset location in Microsoft Intermediate Language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="044a7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="044a7-105">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="044a7-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="044a7-106">Parameters</span></span>  

 `nOffset`  
 <span data-ttu-id="044a7-107">окне Требуемый параметр для указателя инструкции.</span><span class="sxs-lookup"><span data-stu-id="044a7-107">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="044a7-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="044a7-108">Remarks</span></span>  

 <span data-ttu-id="044a7-109">Используйте `CanSetIP` метод перед вызовом метода [ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md) .</span><span class="sxs-lookup"><span data-stu-id="044a7-109">Use the `CanSetIP` method before calling the [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) method.</span></span> <span data-ttu-id="044a7-110">Если `CanSetIP` возвращает любое значение HRESULT, отличное от S_OK, можно по-прежнему вызывать `ICorDebugILFrame::SetIP` , но не существует гарантии того, что отладчик продолжит безопасность и правильное выполнение отлаживаемого кода.</span><span class="sxs-lookup"><span data-stu-id="044a7-110">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugILFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="044a7-111">Требования</span><span class="sxs-lookup"><span data-stu-id="044a7-111">Requirements</span></span>  

 <span data-ttu-id="044a7-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="044a7-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="044a7-113">**Заголовок:** CorDebug. idl, CorDebug, h</span><span class="sxs-lookup"><span data-stu-id="044a7-113">**Header:** CorDebug.idl, CorDebug,h</span></span>  
  
 <span data-ttu-id="044a7-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="044a7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="044a7-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="044a7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
