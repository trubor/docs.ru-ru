---
description: 'Дополнительные сведения о методе: ICorDebugNativeFrame:: CanSetIP'
title: Метод ICorDebugNativeFrame::CanSetIP
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::CanSetIP
helpviewer_keywords:
- ICorDebugNativeFrame::CanSetIP method [.NET Framework debugging]
- CanSetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 13258ac6-f4e4-4f66-8fc3-f1244417a3c3
topic_type:
- apiref
ms.openlocfilehash: ec8f257b44143332063d7579b62dcc2afe0fccdd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637863"
---
# <a name="icordebugnativeframecansetip-method"></a><span data-ttu-id="ee977-103">Метод ICorDebugNativeFrame::CanSetIP</span><span class="sxs-lookup"><span data-stu-id="ee977-103">ICorDebugNativeFrame::CanSetIP Method</span></span>

<span data-ttu-id="ee977-104">Возвращает значение HRESULT, указывающее, можно ли задать для указателя инструкций (IP) заданное положение смещения в машинном коде.</span><span class="sxs-lookup"><span data-stu-id="ee977-104">Gets an HRESULT that indicates whether it is safe to set the instruction pointer (IP) to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee977-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ee977-105">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee977-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ee977-106">Parameters</span></span>  

 `nOffset`  
 <span data-ttu-id="ee977-107">окне Требуемый параметр для указателя инструкции.</span><span class="sxs-lookup"><span data-stu-id="ee977-107">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee977-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="ee977-108">Remarks</span></span>  

 <span data-ttu-id="ee977-109">Используйте `CanSetIP` метод перед вызовом метода [ICorDebugNativeFrame:: SetIP](icordebugnativeframe-setip-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ee977-109">Use the `CanSetIP` method prior to calling the [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md) method.</span></span> <span data-ttu-id="ee977-110">Если `CanSetIP` возвращает любое значение HRESULT, отличное от S_OK, можно по-прежнему вызывать `ICorDebugNativeFrame::SetIP` , но не существует гарантии того, что отладчик продолжит безопасность и правильное выполнение отлаживаемого кода.</span><span class="sxs-lookup"><span data-stu-id="ee977-110">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugNativeFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee977-111">Требования</span><span class="sxs-lookup"><span data-stu-id="ee977-111">Requirements</span></span>  

 <span data-ttu-id="ee977-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee977-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee977-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ee977-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee977-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee977-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee977-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee977-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee977-116">См. также</span><span class="sxs-lookup"><span data-stu-id="ee977-116">See also</span></span>
