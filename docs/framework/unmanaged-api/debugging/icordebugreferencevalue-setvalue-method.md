---
description: 'Дополнительные сведения о методе: ICorDebugReferenceValue:: SetValue'
title: Метод ICorDebugReferenceValue::SetValue
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.SetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::SetValue
helpviewer_keywords:
- SetValue method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::SetValue method [.NET Framework debugging]
ms.assetid: 3d3f6eec-d772-401f-a028-1a2ecdc31e95
topic_type:
- apiref
ms.openlocfilehash: 44909962d2716ddb606d98a2f6b3804247c581cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690916"
---
# <a name="icordebugreferencevaluesetvalue-method"></a><span data-ttu-id="4a1d4-103">Метод ICorDebugReferenceValue::SetValue</span><span class="sxs-lookup"><span data-stu-id="4a1d4-103">ICorDebugReferenceValue::SetValue Method</span></span>

<span data-ttu-id="4a1d4-104">Задает указанный адрес памяти.</span><span class="sxs-lookup"><span data-stu-id="4a1d4-104">Sets the specified memory address.</span></span> <span data-ttu-id="4a1d4-105">Это значит, что этот метод задает ICorDebugReferenceValue для указания объекта.</span><span class="sxs-lookup"><span data-stu-id="4a1d4-105">That is, this method sets this ICorDebugReferenceValue to point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a1d4-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4a1d4-106">Syntax</span></span>  
  
```cpp  
HRESULT SetValue (  
    [in] CORDB_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a1d4-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="4a1d4-107">Parameters</span></span>  

 `value`  
 <span data-ttu-id="4a1d4-108">окне `CORDB_ADDRESS` Значение типа, указывающее адрес объекта, на который `ICorDebugReferenceValue` указывает эта точка.</span><span class="sxs-lookup"><span data-stu-id="4a1d4-108">[in] A `CORDB_ADDRESS` value that specifies the address of the object to which this `ICorDebugReferenceValue` points.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a1d4-109">Требования</span><span class="sxs-lookup"><span data-stu-id="4a1d4-109">Requirements</span></span>  

 <span data-ttu-id="4a1d4-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a1d4-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a1d4-111">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a1d4-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a1d4-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a1d4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a1d4-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a1d4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
