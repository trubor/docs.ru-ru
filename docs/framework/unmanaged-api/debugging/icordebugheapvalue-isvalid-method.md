---
description: 'Дополнительные сведения о методе: ICorDebugHeapValue:: IsValid'
title: Метод ICorDebugHeapValue::IsValid
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue.IsValid
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue::IsValid
helpviewer_keywords:
- IsValid method [.NET Framework debugging]
- ICorDebugHeapValue::IsValid method [.NET Framework debugging]
ms.assetid: 68e20e62-203d-46d8-bb91-8d3c61cfacc3
topic_type:
- apiref
ms.openlocfilehash: 27eca844170b31934cd32dad5cf5fccc0b0e324e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660795"
---
# <a name="icordebugheapvalueisvalid-method"></a><span data-ttu-id="f87be-103">Метод ICorDebugHeapValue::IsValid</span><span class="sxs-lookup"><span data-stu-id="f87be-103">ICorDebugHeapValue::IsValid Method</span></span>

<span data-ttu-id="f87be-104">Возвращает значение, указывающее, является ли допустимым объект, представленный этим ICorDebugHeapValue.</span><span class="sxs-lookup"><span data-stu-id="f87be-104">Gets a value that indicates whether the object represented by this ICorDebugHeapValue is valid.</span></span>  
  
 <span data-ttu-id="f87be-105">Этот метод не рекомендуется к использованию в платформа .NET Framework версии 2,0.</span><span class="sxs-lookup"><span data-stu-id="f87be-105">This method has been deprecated in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f87be-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f87be-106">Syntax</span></span>  
  
```cpp  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f87be-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="f87be-107">Parameters</span></span>  

 `pbValid`  
 <span data-ttu-id="f87be-108">заполняет Указатель на логическое значение, указывающее, является ли значение в куче допустимым.</span><span class="sxs-lookup"><span data-stu-id="f87be-108">[out] A pointer to a Boolean value that indicates whether this value on the heap is valid.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f87be-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="f87be-109">Remarks</span></span>  

 <span data-ttu-id="f87be-110">Значение недопустимо, если оно было освобождено сборщиком мусора.</span><span class="sxs-lookup"><span data-stu-id="f87be-110">The value is invalid if it has been reclaimed by the garbage collector.</span></span>  
  
 <span data-ttu-id="f87be-111">Этот метод использовать не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="f87be-111">This method has been deprecated.</span></span> <span data-ttu-id="f87be-112">В платформа .NET Framework 2,0 все значения являются допустимыми до тех пор, пока не будет вызван метод [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) , после чего значения становятся недействительными.</span><span class="sxs-lookup"><span data-stu-id="f87be-112">In the .NET Framework 2.0, all values are valid until [ICorDebugController::Continue](icordebugcontroller-continue-method.md) is called, at which time the values are invalidated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f87be-113">Требования</span><span class="sxs-lookup"><span data-stu-id="f87be-113">Requirements</span></span>  

 <span data-ttu-id="f87be-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f87be-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f87be-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f87be-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f87be-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f87be-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f87be-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f87be-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
