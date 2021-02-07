---
description: 'Дополнительные сведения о методе: ICorDebugILFrame:: GetIP'
title: Метод ICorDebugILFrame::GetIP
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::GetIP method [.NET Framework debugging]
ms.assetid: 18217ba1-1776-4297-a3b9-f77e64b0fead
topic_type:
- apiref
ms.openlocfilehash: f3977d4fbe57b24e7b98b7a597b0db7ad171eb1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691878"
---
# <a name="icordebugilframegetip-method"></a><span data-ttu-id="3dddd-103">Метод ICorDebugILFrame::GetIP</span><span class="sxs-lookup"><span data-stu-id="3dddd-103">ICorDebugILFrame::GetIP Method</span></span>

<span data-ttu-id="3dddd-104">Возвращает значение указателя инструкции и битовое значение сочетания, которое описывает, как было получено значение указателя инструкции.</span><span class="sxs-lookup"><span data-stu-id="3dddd-104">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dddd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3dddd-105">Syntax</span></span>  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3dddd-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="3dddd-106">Parameters</span></span>  

 `pnOffset`  
 <span data-ttu-id="3dddd-107">заполняет Значение указателя инструкции.</span><span class="sxs-lookup"><span data-stu-id="3dddd-107">[out] The value of the instruction pointer.</span></span>  
  
 `pMappingResult`  
 <span data-ttu-id="3dddd-108">заполняет Указатель на побитовую комбинацию значений перечисления Кордебугмаппингресулт, описывающих, как было получено значение указателя инструкции.</span><span class="sxs-lookup"><span data-stu-id="3dddd-108">[out] A pointer to a bitwise combination of the CorDebugMappingResult enumeration values that describe how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3dddd-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="3dddd-109">Remarks</span></span>  

 <span data-ttu-id="3dddd-110">Значение указателя инструкции является смещением кадра стека в коде MSIL для функции.</span><span class="sxs-lookup"><span data-stu-id="3dddd-110">The value of the instruction pointer is the stack frame's offset into the function's Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="3dddd-111">Если кадр стека активен, то этот адрес является следующей инструкцией для выполнения.</span><span class="sxs-lookup"><span data-stu-id="3dddd-111">If the stack frame is active, this address is the next instruction to execute.</span></span> <span data-ttu-id="3dddd-112">Если кадр стека неактивен, этот адрес является следующей инструкцией для выполнения при повторной активации кадра стека.</span><span class="sxs-lookup"><span data-stu-id="3dddd-112">If the stack frame is not active, this address is the next instruction to execute when the stack frame is reactivated.</span></span>  
  
 <span data-ttu-id="3dddd-113">Если этот кадр является JIT-скомпилированным кадром, то значение указателя инструкции будет определяться в обратном направлении от фактического указателя инструкций в машинном виде, поэтому значение может быть только приблизительным.</span><span class="sxs-lookup"><span data-stu-id="3dddd-113">If this frame is a just-in-time (JIT) compiled frame, the value of the instruction pointer will be determined by mapping backwards from the actual native instruction pointer, so the value may be only approximate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dddd-114">Требования</span><span class="sxs-lookup"><span data-stu-id="3dddd-114">Requirements</span></span>  

 <span data-ttu-id="3dddd-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3dddd-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dddd-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3dddd-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3dddd-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3dddd-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3dddd-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3dddd-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
