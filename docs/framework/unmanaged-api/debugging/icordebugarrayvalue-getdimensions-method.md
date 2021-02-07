---
description: 'Дополнительные сведения о методе: ICorDebugArrayValue:: Dimension'
title: Метод ICorDebugArrayValue::GetDimensions
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetDimensions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetDimensions
helpviewer_keywords:
- ICorDebugArrayValue::GetDimensions method [.NET Framework debugging]
- GetDimensions method [.NET Framework debugging]
ms.assetid: 6c116592-134b-4ef2-a319-680e92d013aa
topic_type:
- apiref
ms.openlocfilehash: 007a48891a01e5779e3f9ef10cec720d6647c8f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723105"
---
# <a name="icordebugarrayvaluegetdimensions-method"></a><span data-ttu-id="3a422-103">Метод ICorDebugArrayValue::GetDimensions</span><span class="sxs-lookup"><span data-stu-id="3a422-103">ICorDebugArrayValue::GetDimensions Method</span></span>

<span data-ttu-id="3a422-104">Возвращает количество элементов в каждом измерении этого массива.</span><span class="sxs-lookup"><span data-stu-id="3a422-104">Gets the number of elements in each dimension of this array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a422-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3a422-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDimensions (  
    [in] ULONG32         cdim,  
    [out, size_is(cdim), length_is(cdim)]
        ULONG32          dims[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a422-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="3a422-106">Parameters</span></span>  

 `cdim`  
 <span data-ttu-id="3a422-107">окне Число измерений данного объекта ICorDebugArrayValue.</span><span class="sxs-lookup"><span data-stu-id="3a422-107">[in] The number of dimensions of this ICorDebugArrayValue object.</span></span>  
  
 <span data-ttu-id="3a422-108">Это значение также является размером `dims` массива, поскольку его размер равен числу измерений `ICorDebugArrayValue` объекта.</span><span class="sxs-lookup"><span data-stu-id="3a422-108">This value is also the size of the `dims` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `dims`  
 <span data-ttu-id="3a422-109">заполняет Массив целых чисел, каждый из которых указывает количество элементов в измерении в этом `ICorDebugArrayValue` объекте.</span><span class="sxs-lookup"><span data-stu-id="3a422-109">[out] An array of integers, each of which specifies the number of elements in a dimension in this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a422-110">Требования</span><span class="sxs-lookup"><span data-stu-id="3a422-110">Requirements</span></span>  

 <span data-ttu-id="3a422-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a422-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a422-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3a422-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a422-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a422-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a422-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a422-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
