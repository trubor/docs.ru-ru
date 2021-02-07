---
description: 'Дополнительные сведения о методе: ICorDebugClass2:: Сетжмкстатус'
title: Метод ICorDebugClass2::SetJMCStatus
ms.date: 03/30/2017
api_name:
- ICorDebugClass2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::SetJMCStatus
helpviewer_keywords:
- ICorDebugClass2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 077e6c7f-f857-480c-bebb-76ee1de4e8fc
topic_type:
- apiref
ms.openlocfilehash: 28859522052fd9587dc3890eb4137929dbdc6763
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711483"
---
# <a name="icordebugclass2setjmcstatus-method"></a><span data-ttu-id="3da4d-103">Метод ICorDebugClass2::SetJMCStatus</span><span class="sxs-lookup"><span data-stu-id="3da4d-103">ICorDebugClass2::SetJMCStatus Method</span></span>

<span data-ttu-id="3da4d-104">Для каждого метода класса задает значение, указывающее, является ли метод определяемым пользователем кодом.</span><span class="sxs-lookup"><span data-stu-id="3da4d-104">For each method of the class, sets a value that indicates whether the method is user-defined code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3da4d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3da4d-105">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3da4d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="3da4d-106">Parameters</span></span>  

 `bIsJustMyCode`  
 <span data-ttu-id="3da4d-107">окне Задайте значение, чтобы `true` указать, что метод является определяемым пользователем кодом; в противном случае задайте для значение `false` .</span><span class="sxs-lookup"><span data-stu-id="3da4d-107">[in] Set to `true` to indicate that the method is user-defined code; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3da4d-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="3da4d-108">Remarks</span></span>  

 <span data-ttu-id="3da4d-109">Средство "только мой код" (JMC) пропускает код, не определенный пользователем.</span><span class="sxs-lookup"><span data-stu-id="3da4d-109">A just-my-code (JMC) stepper will skip non-user-defined code.</span></span> <span data-ttu-id="3da4d-110">Определяемый пользователем код должен быть подмножеством отлаживаемого кода.</span><span class="sxs-lookup"><span data-stu-id="3da4d-110">User-defined code must be a subset of debuggable code.</span></span>  
  
 <span data-ttu-id="3da4d-111">`SetJMCStatus` Возвращает значение HRESULT, равное S_FALSE, если не удается задать значение для какого бы то ни было метода, даже если оно успешно задает значение для всех остальных методов.</span><span class="sxs-lookup"><span data-stu-id="3da4d-111">`SetJMCStatus` returns an HRESULT value of S_FALSE if it fails to set the value for any method, even if it successfully sets the value for all other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3da4d-112">Требования</span><span class="sxs-lookup"><span data-stu-id="3da4d-112">Requirements</span></span>  

 <span data-ttu-id="3da4d-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3da4d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3da4d-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3da4d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3da4d-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3da4d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3da4d-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3da4d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
