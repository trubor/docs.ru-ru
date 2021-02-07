---
description: 'Дополнительные сведения о методе ICorDebugCode:: Function'
title: Метод ICorDebugCode::GetFunction
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetFunction method [.NET Framework debugging]
ms.assetid: c568b737-fdb2-4816-accd-051f5ab760f1
topic_type:
- apiref
ms.openlocfilehash: c90635bf1821d70d6d056d5cbd495ddfa2d2a2ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711210"
---
# <a name="icordebugcodegetfunction-method"></a><span data-ttu-id="e3949-103">Метод ICorDebugCode::GetFunction</span><span class="sxs-lookup"><span data-stu-id="e3949-103">ICorDebugCode::GetFunction Method</span></span>

<span data-ttu-id="e3949-104">Возвращает "ICorDebugFunction", связанный с этим "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="e3949-104">Gets the "ICorDebugFunction" associated with this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3949-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e3949-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3949-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e3949-106">Parameters</span></span>  

 `ppFunction`  
 <span data-ttu-id="e3949-107">заполняет Указатель на адрес функции.</span><span class="sxs-lookup"><span data-stu-id="e3949-107">[out] A pointer to the address of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3949-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="e3949-108">Remarks</span></span>  

 <span data-ttu-id="e3949-109">`ICorDebugCode` и `ICorDebugFunction` поддерживают связь «один к одному».</span><span class="sxs-lookup"><span data-stu-id="e3949-109">`ICorDebugCode` and `ICorDebugFunction` maintain a one-to-one relationship.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3949-110">Требования</span><span class="sxs-lookup"><span data-stu-id="e3949-110">Requirements</span></span>  

 <span data-ttu-id="e3949-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3949-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3949-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3949-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3949-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3949-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3949-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3949-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
