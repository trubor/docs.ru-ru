---
description: 'Дополнительные сведения: метод ICorDebugFrame:: GetFunctionToken'
title: Метод ICorDebugFrame::GetFunctionToken
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetFunctionToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetFunctionToken
helpviewer_keywords:
- ICorDebugFrame::GetFunctionToken method [.NET Framework debugging]
- GetFunctionToken method [.NET Framework debugging]
ms.assetid: a46925b3-3bf8-404f-9f30-a86ae41032c1
topic_type:
- apiref
ms.openlocfilehash: c64bb8d59c8de03c3d8c667384ffe4118c996d8e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692944"
---
# <a name="icordebugframegetfunctiontoken-method"></a><span data-ttu-id="0f642-103">Метод ICorDebugFrame::GetFunctionToken</span><span class="sxs-lookup"><span data-stu-id="0f642-103">ICorDebugFrame::GetFunctionToken Method</span></span>

<span data-ttu-id="0f642-104">Возвращает маркер метаданных для функции, которая содержит код, связанный с этим кадром стека.</span><span class="sxs-lookup"><span data-stu-id="0f642-104">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f642-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0f642-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionToken (  
    [out] mdMethodDef        *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f642-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0f642-106">Parameters</span></span>  

 `pToken`  
 <span data-ttu-id="0f642-107">заполняет Указатель на `mdMethodDef` маркер, который ссылается на метаданные функции.</span><span class="sxs-lookup"><span data-stu-id="0f642-107">[out] A pointer to an `mdMethodDef` token that references the metadata for the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f642-108">Требования</span><span class="sxs-lookup"><span data-stu-id="0f642-108">Requirements</span></span>  

 <span data-ttu-id="0f642-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f642-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f642-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0f642-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0f642-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f642-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f642-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f642-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
