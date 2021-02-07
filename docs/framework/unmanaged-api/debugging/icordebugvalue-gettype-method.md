---
description: 'Дополнительные сведения о методе ICorDebugValue:: GetType'
title: Метод ICorDebugValue::GetType
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetType
helpviewer_keywords:
- ICorDebugValue::GetType method [.NET Framework debugging]
- GetType method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: 41e2d503-e1f1-407b-abe0-6a29adb3e0d1
topic_type:
- apiref
ms.openlocfilehash: 750e73634683a03e811d2756cc62c16b6dcea3de
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690331"
---
# <a name="icordebugvaluegettype-method"></a><span data-ttu-id="f2d13-103">Метод ICorDebugValue::GetType</span><span class="sxs-lookup"><span data-stu-id="f2d13-103">ICorDebugValue::GetType Method</span></span>

<span data-ttu-id="f2d13-104">Возвращает тип примитива этого объекта "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="f2d13-104">Gets the primitive type of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2d13-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f2d13-105">Syntax</span></span>  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2d13-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f2d13-106">Parameters</span></span>  

 `pType`  
 <span data-ttu-id="f2d13-107">заполняет Указатель на значение перечисления "Корелементтипе", которое указывает тип значения.</span><span class="sxs-lookup"><span data-stu-id="f2d13-107">[out] A pointer to a value of the "CorElementType" enumeration that indicates the value's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2d13-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="f2d13-108">Remarks</span></span>  

 <span data-ttu-id="f2d13-109">Если объект является сложным типом времени выполнения, этот тип можно исследовать с помощью соответствующих подклассов `ICorDebugValue` интерфейса.</span><span class="sxs-lookup"><span data-stu-id="f2d13-109">If the object is a complex run-time type, that type may be examined through the appropriate subclasses of the `ICorDebugValue` interface.</span></span> <span data-ttu-id="f2d13-110">Например, "ICorDebugObjectValue", который наследует от `ICorDebugValue` , представляет сложный тип.</span><span class="sxs-lookup"><span data-stu-id="f2d13-110">For example, "ICorDebugObjectValue", which inherits from `ICorDebugValue`, represents a complex type.</span></span>  
  
 <span data-ttu-id="f2d13-111">`GetType`Методы и [ICorDebugObjectValue:: coclass](icordebugobjectvalue-getclass-method.md) возвращают сведения о типе значения.</span><span class="sxs-lookup"><span data-stu-id="f2d13-111">The `GetType` and [ICorDebugObjectValue::GetClass](icordebugobjectvalue-getclass-method.md) methods each return information about the type of a value.</span></span> <span data-ttu-id="f2d13-112">Они заменяются методом [ICorDebugValue2:: GetExactType](icordebugvalue2-getexacttype-method.md) , поддерживающим универсальные шаблоны.</span><span class="sxs-lookup"><span data-stu-id="f2d13-112">They are both superseded by the generics-aware [ICorDebugValue2::GetExactType](icordebugvalue2-getexacttype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2d13-113">Требования</span><span class="sxs-lookup"><span data-stu-id="f2d13-113">Requirements</span></span>  

 <span data-ttu-id="f2d13-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2d13-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2d13-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f2d13-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2d13-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2d13-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2d13-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2d13-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2d13-118">См. также</span><span class="sxs-lookup"><span data-stu-id="f2d13-118">See also</span></span>
