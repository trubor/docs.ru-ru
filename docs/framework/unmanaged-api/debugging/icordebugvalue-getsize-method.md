---
description: 'Дополнительные сведения о методе ICorDebugValue:: resize'
title: Метод ICorDebugValue::GetSize
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugValue interface [.NET Framework debugging]
- ICorDebugValue::GetSize method [.NET Framework debugging]
ms.assetid: 445a9ee3-e050-4f3a-931a-96b0efb00110
topic_type:
- apiref
ms.openlocfilehash: 3fc2582990d58fa2e42f240dfd3e563eed34e372
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690344"
---
# <a name="icordebugvaluegetsize-method"></a><span data-ttu-id="b69aa-103">Метод ICorDebugValue::GetSize</span><span class="sxs-lookup"><span data-stu-id="b69aa-103">ICorDebugValue::GetSize Method</span></span>

<span data-ttu-id="b69aa-104">Возвращает размер этого объекта "ICorDebugValue" в байтах.</span><span class="sxs-lookup"><span data-stu-id="b69aa-104">Gets the size, in bytes, of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b69aa-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b69aa-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b69aa-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b69aa-106">Parameters</span></span>  

 `pSize`  
 <span data-ttu-id="b69aa-107">заполняет Размер данного объекта значения в байтах.</span><span class="sxs-lookup"><span data-stu-id="b69aa-107">[out] The size, in bytes, of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b69aa-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="b69aa-108">Remarks</span></span>  

 <span data-ttu-id="b69aa-109">Если типом значения является ссылочный тип, этот метод возвращает размер указателя, а не размер объекта.</span><span class="sxs-lookup"><span data-stu-id="b69aa-109">If the value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="b69aa-110">`ICorDebugValue::GetSize`Метод возвращает `COR_E_OVERFLOW` для объектов, размер которых ПРЕВЫШАЕТ 4 гб на 64-разрядных платформах.</span><span class="sxs-lookup"><span data-stu-id="b69aa-110">The `ICorDebugValue::GetSize` method returns `COR_E_OVERFLOW` for objects that are larger than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="b69aa-111">Используйте вместо него метод [ICorDebugValue3:: GetSize64](icordebugvalue3-getsize64-method.md) для объектов, размер которых ПРЕВЫШАЕТ 4 ГБ.</span><span class="sxs-lookup"><span data-stu-id="b69aa-111">Use the [ICorDebugValue3::GetSize64](icordebugvalue3-getsize64-method.md) method instead for objects that are larger than 4 GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b69aa-112">Требования</span><span class="sxs-lookup"><span data-stu-id="b69aa-112">Requirements</span></span>  

 <span data-ttu-id="b69aa-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b69aa-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b69aa-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b69aa-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b69aa-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b69aa-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b69aa-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b69aa-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b69aa-117">См. также</span><span class="sxs-lookup"><span data-stu-id="b69aa-117">See also</span></span>

- [<span data-ttu-id="b69aa-118">Метод GetSize64</span><span class="sxs-lookup"><span data-stu-id="b69aa-118">GetSize64 Method</span></span>](icordebugvalue3-getsize64-method.md)
