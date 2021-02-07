---
description: 'Дополнительные сведения о методе ICorDebugFrame:: Function'
title: Метод ICorDebugFrame::GetFunction
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetFunction method [.NET Framework debugging]
ms.assetid: 879d2311-0ff1-4616-a8b3-959ea5868b2e
topic_type:
- apiref
ms.openlocfilehash: 0309a066f686e55d086de1cbb040eea58e031df3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692996"
---
# <a name="icordebugframegetfunction-method"></a><span data-ttu-id="cb24c-103">Метод ICorDebugFrame::GetFunction</span><span class="sxs-lookup"><span data-stu-id="cb24c-103">ICorDebugFrame::GetFunction Method</span></span>

<span data-ttu-id="cb24c-104">Возвращает функцию, содержащую код, связанный с данным кадром стека.</span><span class="sxs-lookup"><span data-stu-id="cb24c-104">Gets the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb24c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cb24c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb24c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="cb24c-106">Parameters</span></span>  

 `ppFunction`  
 <span data-ttu-id="cb24c-107">заполняет Указатель на адрес объекта ICorDebugFunction, представляющего функцию, содержащую код, связанный с данным кадром стека.</span><span class="sxs-lookup"><span data-stu-id="cb24c-107">[out] A pointer to the address of an ICorDebugFunction object that represents the function containing the code associated with this stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb24c-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="cb24c-108">Remarks</span></span>  

 <span data-ttu-id="cb24c-109">`GetFunction`Метод может завершиться ошибкой, если фрейм не связан с какой-либо определенной функцией.</span><span class="sxs-lookup"><span data-stu-id="cb24c-109">The `GetFunction` method may fail if the frame is not associated with any particular function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb24c-110">Требования</span><span class="sxs-lookup"><span data-stu-id="cb24c-110">Requirements</span></span>  

 <span data-ttu-id="cb24c-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb24c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb24c-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cb24c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb24c-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb24c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb24c-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb24c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
