---
description: 'Дополнительные сведения о методе: ICorDebugGenericValue:: SetValue'
title: Метод ICorDebugGenericValue::SetValue
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue.SetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue::SetValue
helpviewer_keywords:
- ICorDebugGenericValue::SetValue method [.NET Framework debugging]
- SetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: ed4c6458-0435-44fc-8e78-8ba00be362f2
topic_type:
- apiref
ms.openlocfilehash: e284d9987c8428fadedde0024fd3c65a0d8fe7a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791482"
---
# <a name="icordebuggenericvaluesetvalue-method"></a><span data-ttu-id="cbd26-103">Метод ICorDebugGenericValue::SetValue</span><span class="sxs-lookup"><span data-stu-id="cbd26-103">ICorDebugGenericValue::SetValue Method</span></span>

<span data-ttu-id="cbd26-104">Копирует новое значение из указанного буфера.</span><span class="sxs-lookup"><span data-stu-id="cbd26-104">Copies a new value from the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbd26-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cbd26-105">Syntax</span></span>  
  
```cpp  
HRESULT SetValue (  
    [in] void      *pFrom  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cbd26-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="cbd26-106">Parameters</span></span>  

 `pFrom`  
 <span data-ttu-id="cbd26-107">окне Указатель на буфер, из которого копируется значение.</span><span class="sxs-lookup"><span data-stu-id="cbd26-107">[in] A pointer to the buffer from which to copy the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cbd26-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="cbd26-108">Remarks</span></span>  

 <span data-ttu-id="cbd26-109">Для ссылочных типов значением является ссылка, а не содержимое.</span><span class="sxs-lookup"><span data-stu-id="cbd26-109">For reference types, the value is the reference, not the content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbd26-110">Требования</span><span class="sxs-lookup"><span data-stu-id="cbd26-110">Requirements</span></span>  

 <span data-ttu-id="cbd26-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbd26-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbd26-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cbd26-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cbd26-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cbd26-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cbd26-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbd26-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
