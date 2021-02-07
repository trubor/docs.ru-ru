---
description: 'Дополнительные сведения: метод ICorDebugFunction:: module'
title: Метод ICorDebugFunction::GetModule
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetModule
helpviewer_keywords:
- ICorDebugFunction::GetModule method [.NET Framework debugging]
- GetModule method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 5031a5d3-2564-412a-9007-e36d4631308a
topic_type:
- apiref
ms.openlocfilehash: 62087cdf0443b2ef495461aab74cfa047b95efca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692476"
---
# <a name="icordebugfunctiongetmodule-method"></a><span data-ttu-id="412e8-103">Метод ICorDebugFunction::GetModule</span><span class="sxs-lookup"><span data-stu-id="412e8-103">ICorDebugFunction::GetModule Method</span></span>

<span data-ttu-id="412e8-104">Возвращает модуль, в котором определена эта функция.</span><span class="sxs-lookup"><span data-stu-id="412e8-104">Gets the module in which this function is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="412e8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="412e8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="412e8-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="412e8-106">Parameters</span></span>  

 `ppModule`  
 <span data-ttu-id="412e8-107">заполняет Указатель на адрес объекта ICorDebugModule, который представляет модуль, в котором определена эта функция.</span><span class="sxs-lookup"><span data-stu-id="412e8-107">[out] A pointer to the address of an ICorDebugModule object that represents the module in which this function is defined.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="412e8-108">Требования</span><span class="sxs-lookup"><span data-stu-id="412e8-108">Requirements</span></span>  

 <span data-ttu-id="412e8-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="412e8-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="412e8-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="412e8-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="412e8-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="412e8-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="412e8-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="412e8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
