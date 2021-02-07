---
description: 'Дополнительные сведения о методе: ICorDebugAssembly2:: Исфуллитрустед'
title: Метод ICorDebugAssembly2::IsFullyTrusted
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly2.IsFullyTrusted
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly2::IsFullyTrusted
helpviewer_keywords:
- ICorDebugAssembly2::IsFullyTrusted method [.NET Framework debugging]
- IsFullyTrusted method [.NET Framework debugging]
ms.assetid: 26cbd27d-12bf-444a-8197-ccd14d37dda3
topic_type:
- apiref
ms.openlocfilehash: bc1c4d9a4fa84bac3469aafe8aaa061473e50413
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754112"
---
# <a name="icordebugassembly2isfullytrusted-method"></a><span data-ttu-id="2e96c-103">Метод ICorDebugAssembly2::IsFullyTrusted</span><span class="sxs-lookup"><span data-stu-id="2e96c-103">ICorDebugAssembly2::IsFullyTrusted Method</span></span>

<span data-ttu-id="2e96c-104">Возвращает значение, указывающее, предоставлено ли сборке полное доверие системой безопасности среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="2e96c-104">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e96c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2e96c-105">Syntax</span></span>  
  
```cpp  
HRESULT IsFullyTrusted(  
    [out] BOOL *pbFullyTrusted  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e96c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="2e96c-106">Parameters</span></span>  

 `pbFullyTrusted`  
 <span data-ttu-id="2e96c-107">[out] `true` значение, если сборке было предоставлено полное доверие системой безопасности среды выполнения; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="2e96c-107">[out] `true` if the assembly has been granted full trust by the runtime security system; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e96c-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="2e96c-108">Remarks</span></span>  

 <span data-ttu-id="2e96c-109">Этот метод возвращает значение HRESULT CORDBG_E_NOTREADY, если политика безопасности для сборки еще не разрешена, то есть если код в сборке еще не выполнялся.</span><span class="sxs-lookup"><span data-stu-id="2e96c-109">This method returns an HRESULT of CORDBG_E_NOTREADY if the security policy for the assembly has not yet been resolved, that is, if no code in the assembly has been run yet.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e96c-110">Требования</span><span class="sxs-lookup"><span data-stu-id="2e96c-110">Requirements</span></span>  

 <span data-ttu-id="2e96c-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e96c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e96c-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2e96c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e96c-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e96c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e96c-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e96c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
