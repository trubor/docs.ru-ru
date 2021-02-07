---
description: 'Дополнительные сведения о методе: ICorDebugFunction2:: Жетжмкстатус'
title: Метод ICorDebugFunction2::GetJMCStatus
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::GetJMCStatus method [.NET Framework debugging]
- GetJMCStatus method [.NET Framework debugging]
ms.assetid: 840a71ed-bf5a-4f5e-8ed6-762222b34493
topic_type:
- apiref
ms.openlocfilehash: 42c72256df57b96a52737f4a0e5e90d6ba5d4e0c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692294"
---
# <a name="icordebugfunction2getjmcstatus-method"></a><span data-ttu-id="96883-103">Метод ICorDebugFunction2::GetJMCStatus</span><span class="sxs-lookup"><span data-stu-id="96883-103">ICorDebugFunction2::GetJMCStatus Method</span></span>

<span data-ttu-id="96883-104">Возвращает значение, указывающее, помечается ли функция, представленная этим объектом ICorDebugFunction2, как пользовательский код.</span><span class="sxs-lookup"><span data-stu-id="96883-104">Gets a value that indicates whether the function that is represented by this ICorDebugFunction2 object is marked as user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96883-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="96883-105">Syntax</span></span>  
  
```cpp  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96883-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="96883-106">Parameters</span></span>  

 `pbIsJustMyCode`  
 <span data-ttu-id="96883-107">заполняет Указатель на логическое значение, равное `true` , если эта функция помечена как пользовательский код; в противном случае — значение `false` .</span><span class="sxs-lookup"><span data-stu-id="96883-107">[out] A pointer to a Boolean value that is `true`, if this function is marked as user code; otherwise, the value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96883-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="96883-108">Remarks</span></span>  

 <span data-ttu-id="96883-109">Если функция, представленная этим объектом `ICorDebugFunction2` , не может быть отлажена, `pbIsJustMyCode` всегда будет иметь значение `false` .</span><span class="sxs-lookup"><span data-stu-id="96883-109">If the function represented by this `ICorDebugFunction2` cannot be debugged, `pbIsJustMyCode` will always be `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96883-110">Требования</span><span class="sxs-lookup"><span data-stu-id="96883-110">Requirements</span></span>  

 <span data-ttu-id="96883-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96883-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96883-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="96883-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96883-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96883-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96883-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96883-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
