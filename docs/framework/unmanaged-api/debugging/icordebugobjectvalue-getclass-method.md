---
description: 'Дополнительные сведения о методе: ICorDebugObjectValue:: coclass'
title: Метод ICorDebugObjectValue::GetClass
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::GetClass
helpviewer_keywords:
- ICorDebugObjectValue::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 5be25292-8357-445f-a09b-f997c0de761c
topic_type:
- apiref
ms.openlocfilehash: 4ea6a47814777da934aa14bba947a047c075396c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722221"
---
# <a name="icordebugobjectvaluegetclass-method"></a><span data-ttu-id="b8e93-103">Метод ICorDebugObjectValue::GetClass</span><span class="sxs-lookup"><span data-stu-id="b8e93-103">ICorDebugObjectValue::GetClass Method</span></span>

<span data-ttu-id="b8e93-104">Возвращает класс этого значения объекта.</span><span class="sxs-lookup"><span data-stu-id="b8e93-104">Gets the class of this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8e93-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b8e93-105">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8e93-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b8e93-106">Parameters</span></span>  

 `ppClass`  
 <span data-ttu-id="b8e93-107">заполняет Указатель на адрес объекта "ICorDebugClass", который представляет класс значения объекта, представленного этим объектом "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="b8e93-107">[out] A pointer to the address of an "ICorDebugClass" object that represents the class of the object value represented by this "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8e93-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="b8e93-108">Remarks</span></span>  

 <span data-ttu-id="b8e93-109">`GetClass`Методы и [ICorDebugValue:: GetType](icordebugvalue-gettype-method.md) возвращают сведения о типе значения; они заменяются универсальными классами [ICorDebugValue2:: GetExactType](icordebugvalue2-getexacttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="b8e93-109">The `GetClass` and [ICorDebugValue::GetType](icordebugvalue-gettype-method.md) methods each return information about the type of a value; they are both superseded by the generics-aware [ICorDebugValue2::GetExactType](icordebugvalue2-getexacttype-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8e93-110">Требования</span><span class="sxs-lookup"><span data-stu-id="b8e93-110">Requirements</span></span>  

 <span data-ttu-id="b8e93-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8e93-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8e93-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8e93-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8e93-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8e93-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8e93-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8e93-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8e93-115">См. также</span><span class="sxs-lookup"><span data-stu-id="b8e93-115">See also</span></span>
