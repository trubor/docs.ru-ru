---
description: 'Дополнительные сведения: метод ICorDebugFunction:: GetLocalVarSigToken'
title: Метод ICorDebugFunction::GetLocalVarSigToken
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetLocalVarSigToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetLocalVarSigToken
helpviewer_keywords:
- ICorDebugFunction::GetLocalVarSigToken method [.NET Framework debugging]
- GetLocalVarSigToken method [.NET Framework debugging]
ms.assetid: 31e53494-bcc9-4981-91a4-f7e0f02cad48
topic_type:
- apiref
ms.openlocfilehash: cd7fb03829285ddcb1da2f1a93985fa1f98d3d39
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692502"
---
# <a name="icordebugfunctiongetlocalvarsigtoken-method"></a><span data-ttu-id="e44b7-103">Метод ICorDebugFunction::GetLocalVarSigToken</span><span class="sxs-lookup"><span data-stu-id="e44b7-103">ICorDebugFunction::GetLocalVarSigToken Method</span></span>

<span data-ttu-id="e44b7-104">Возвращает маркер метаданных для сигнатуры локальной переменной функции, представленной этим экземпляром ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="e44b7-104">Gets the metadata token for the local variable signature of the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e44b7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e44b7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVarSigToken (  
    [out] mdSignature *pmdSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e44b7-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e44b7-106">Parameters</span></span>  

 `pmdSig`  
 <span data-ttu-id="e44b7-107">заполняет Указатель на `mdSignature` маркер для сигнатуры локальной переменной этой функции или `mdSignatureNil` , если эта функция не имеет локальных переменных.</span><span class="sxs-lookup"><span data-stu-id="e44b7-107">[out] A pointer to the `mdSignature` token for the local variable signature of this function, or `mdSignatureNil`, if this function has no local variables.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e44b7-108">Требования</span><span class="sxs-lookup"><span data-stu-id="e44b7-108">Requirements</span></span>  

 <span data-ttu-id="e44b7-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e44b7-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e44b7-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e44b7-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e44b7-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e44b7-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e44b7-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e44b7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
