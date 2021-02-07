---
description: 'Дополнительные сведения о методе: ICorDebugArrayValue:: Жетелементтипе'
title: Метод ICorDebugArrayValue::GetElementType
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElementType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElementType
helpviewer_keywords:
- ICorDebugArrayValue::GetElementType method [.NET Framework debugging]
- GetElementType method [.NET Framework debugging]
ms.assetid: ed71961e-ae9b-4dfc-9554-06637696d697
topic_type:
- apiref
ms.openlocfilehash: 97c01a9c8ae7a1d73a1a15b97d3ce3e9aa079365
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723036"
---
# <a name="icordebugarrayvaluegetelementtype-method"></a><span data-ttu-id="bbeea-103">Метод ICorDebugArrayValue::GetElementType</span><span class="sxs-lookup"><span data-stu-id="bbeea-103">ICorDebugArrayValue::GetElementType Method</span></span>

<span data-ttu-id="bbeea-104">Возвращает значение, указывающее простой тип элементов в массиве.</span><span class="sxs-lookup"><span data-stu-id="bbeea-104">Gets a value that indicates the simple type of the elements in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbeea-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bbeea-105">Syntax</span></span>  
  
```cpp  
HRESULT GetElementType (  
    [out] CorElementType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bbeea-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="bbeea-106">Parameters</span></span>  

 `pType`  
 <span data-ttu-id="bbeea-107">заполняет Указатель на значение перечисления Корелементтипе, указывающее тип.</span><span class="sxs-lookup"><span data-stu-id="bbeea-107">[out] A pointer to a value of the CorElementType enumeration that indicates the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbeea-108">Требования</span><span class="sxs-lookup"><span data-stu-id="bbeea-108">Requirements</span></span>  

 <span data-ttu-id="bbeea-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbeea-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbeea-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bbeea-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bbeea-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bbeea-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bbeea-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbeea-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
