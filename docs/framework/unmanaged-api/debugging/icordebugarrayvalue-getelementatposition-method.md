---
description: 'Дополнительные сведения о методе: ICorDebugArrayValue:: GetElementAtPosition'
title: Метод ICorDebugArrayValue::GetElementAtPosition
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElementAtPosition
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElementAtPosition
helpviewer_keywords:
- GetElementAtPosition method [.NET Framework debugging]
- ICorDebugArrayValue::GetElementAtPosition method [.NET Framework debugging]
ms.assetid: 6fd5eaa4-1997-4910-82f5-3887480db764
topic_type:
- apiref
ms.openlocfilehash: ef8e4a39f5fe4088b1883803aee037c51f410241
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723040"
---
# <a name="icordebugarrayvaluegetelementatposition-method"></a><span data-ttu-id="21845-103">Метод ICorDebugArrayValue::GetElementAtPosition</span><span class="sxs-lookup"><span data-stu-id="21845-103">ICorDebugArrayValue::GetElementAtPosition Method</span></span>

<span data-ttu-id="21845-104">Возвращает элемент в заданной позиции, рассматривая массив как одномерный массив с отсчетом от нуля.</span><span class="sxs-lookup"><span data-stu-id="21845-104">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21845-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="21845-105">Syntax</span></span>  
  
```cpp  
HRESULT GetElementAtPosition (  
    [in]  ULONG32          nPosition,  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21845-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="21845-106">Parameters</span></span>  

 `nPosition`  
 <span data-ttu-id="21845-107">окне Расположение извлекаемого элемента.</span><span class="sxs-lookup"><span data-stu-id="21845-107">[in] The position of the element to be retrieved.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="21845-108">заполняет Указатель на адрес объекта ICorDebugValue, который представляет значение элемента.</span><span class="sxs-lookup"><span data-stu-id="21845-108">[out] A pointer to the address of an ICorDebugValue object that represents the value of the element.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21845-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="21845-109">Remarks</span></span>  

 <span data-ttu-id="21845-110">Компоновка многомерного массива соответствует стилю в C++ для макета массива.</span><span class="sxs-lookup"><span data-stu-id="21845-110">The layout of a multi-dimension array follows the C++ style of array layout.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21845-111">Требования</span><span class="sxs-lookup"><span data-stu-id="21845-111">Requirements</span></span>  

 <span data-ttu-id="21845-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21845-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21845-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="21845-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21845-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21845-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21845-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21845-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
