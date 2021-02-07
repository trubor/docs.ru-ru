---
description: 'Дополнительные сведения: метод ICorDebugFunction:: CreateBreakpoint'
title: Метод ICorDebugFunction::CreateBreakpoint
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.CreateBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::CreateBreakpoint
helpviewer_keywords:
- ICorDebugFunction::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: ffd0f708-0d21-4fae-a395-63b6c45828fa
topic_type:
- apiref
ms.openlocfilehash: 4d55a818352ff98b67c95d5ef15417f2e9e64d40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692632"
---
# <a name="icordebugfunctioncreatebreakpoint-method"></a><span data-ttu-id="8d42a-103">Метод ICorDebugFunction::CreateBreakpoint</span><span class="sxs-lookup"><span data-stu-id="8d42a-103">ICorDebugFunction::CreateBreakpoint Method</span></span>

<span data-ttu-id="8d42a-104">Создает точку останова в начале этой функции.</span><span class="sxs-lookup"><span data-stu-id="8d42a-104">Creates a breakpoint at the beginning of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d42a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8d42a-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateBreakpoint (  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d42a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8d42a-106">Parameters</span></span>  

 `ppBreakpoint`  
 <span data-ttu-id="8d42a-107">заполняет Указатель на адрес объекта ICorDebugFunctionBreakpoint, который представляет новую точку останова для функции.</span><span class="sxs-lookup"><span data-stu-id="8d42a-107">[out] A pointer to the address of an ICorDebugFunctionBreakpoint object that represents the new breakpoint for the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d42a-108">Требования</span><span class="sxs-lookup"><span data-stu-id="8d42a-108">Requirements</span></span>  

 <span data-ttu-id="8d42a-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d42a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d42a-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8d42a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d42a-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d42a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d42a-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d42a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
