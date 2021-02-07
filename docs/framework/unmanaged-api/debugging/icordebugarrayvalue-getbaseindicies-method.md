---
description: 'Дополнительные сведения о методе: ICorDebugArrayValue:: ЖетбасеиндиЦиес'
title: Метод ICorDebugArrayValue::GetBaseIndicies
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetBaseIndicies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetBaseIndicies
helpviewer_keywords:
- ICorDebugArrayValue::GetBaseIndicies method [.NET Framework debugging]
- GetBaseIndicies method [.NET Framework debugging]
ms.assetid: 868b339b-acdb-4fe0-91c7-b85f4fba99eb
topic_type:
- apiref
ms.openlocfilehash: ac38123860cc3187b7dc2398b32244387d19c5ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723126"
---
# <a name="icordebugarrayvaluegetbaseindicies-method"></a><span data-ttu-id="d4630-103">Метод ICorDebugArrayValue::GetBaseIndicies</span><span class="sxs-lookup"><span data-stu-id="d4630-103">ICorDebugArrayValue::GetBaseIndicies Method</span></span>

<span data-ttu-id="d4630-104">Возвращает базовый индекс каждого измерения в массиве.</span><span class="sxs-lookup"><span data-stu-id="d4630-104">Gets the base index of each dimension in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4630-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d4630-105">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseIndicies (  
    [in] ULONG32          cdim,  
    [out, size_is(cdim), length_is(cdim)]
        ULONG32           indicies[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4630-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d4630-106">Parameters</span></span>  

 `cdim`  
 <span data-ttu-id="d4630-107">окне Число измерений данного `ICorDebugArrayValue` объекта.</span><span class="sxs-lookup"><span data-stu-id="d4630-107">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span> <span data-ttu-id="d4630-108">Это значение также является размером `indicies` массива, поскольку его размер равен числу измерений `ICorDebugArrayValue` объекта.</span><span class="sxs-lookup"><span data-stu-id="d4630-108">This value is also the size of the `indicies` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indicies`  
 <span data-ttu-id="d4630-109">заполняет Массив целых чисел, каждый из которых является базовым индексом (т. е. начальным индексом) измерения этого `ICorDebugArrayValue` объекта.</span><span class="sxs-lookup"><span data-stu-id="d4630-109">[out] An array of integers, each of which is the base index (that is, the starting index) of a dimension of this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4630-110">Требования</span><span class="sxs-lookup"><span data-stu-id="d4630-110">Requirements</span></span>  

 <span data-ttu-id="d4630-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4630-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4630-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d4630-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4630-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4630-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4630-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4630-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
