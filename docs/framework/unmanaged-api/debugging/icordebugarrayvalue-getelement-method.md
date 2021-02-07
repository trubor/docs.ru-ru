---
description: 'Дополнительные сведения о методе: ICorDebugArrayValue:: WebMethod'
title: Метод ICorDebugArrayValue::GetElement
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElement
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElement
helpviewer_keywords:
- GetElement method [.NET Framework debugging]
- ICorDebugArrayValue::GetElement method [.NET Framework debugging]
ms.assetid: 7ac3cba5-c282-402e-b7ef-b46634f5176b
topic_type:
- apiref
ms.openlocfilehash: dfae074b78735934d1e71b13ce01c24741a5f2ed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723066"
---
# <a name="icordebugarrayvaluegetelement-method"></a><span data-ttu-id="bb54b-103">Метод ICorDebugArrayValue::GetElement</span><span class="sxs-lookup"><span data-stu-id="bb54b-103">ICorDebugArrayValue::GetElement Method</span></span>

<span data-ttu-id="bb54b-104">Возвращает значение заданного элемента массива.</span><span class="sxs-lookup"><span data-stu-id="bb54b-104">Gets the value of the given array element.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb54b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bb54b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb54b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="bb54b-106">Parameters</span></span>  

 `cdim`  
 <span data-ttu-id="bb54b-107">окне Число измерений данного `ICorDebugArrayValue` объекта.</span><span class="sxs-lookup"><span data-stu-id="bb54b-107">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="bb54b-108">Это значение также является размером `indices` массива, поскольку его размер равен числу измерений `ICorDebugArrayValue` объекта.</span><span class="sxs-lookup"><span data-stu-id="bb54b-108">This value is also the size of the `indices` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indices`  
 <span data-ttu-id="bb54b-109">окне Массив значений индекса, каждый из которых задает позиции в измерении `ICorDebugArrayValue` объекта.</span><span class="sxs-lookup"><span data-stu-id="bb54b-109">[in] An array of index values, each of which specifies a position within a dimension of the `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="bb54b-110">Это значение не должно быть равно NULL.</span><span class="sxs-lookup"><span data-stu-id="bb54b-110">This value must not be null.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="bb54b-111">заполняет Указатель на адрес объекта ICorDebugValue, представляющий значение указанного элемента.</span><span class="sxs-lookup"><span data-stu-id="bb54b-111">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified element.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb54b-112">Требования</span><span class="sxs-lookup"><span data-stu-id="bb54b-112">Requirements</span></span>  

 <span data-ttu-id="bb54b-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb54b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb54b-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bb54b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb54b-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb54b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb54b-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb54b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
