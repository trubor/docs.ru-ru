---
description: 'Дополнительные сведения о методе: ICorDebugValue2:: GetExactType'
title: Метод ICorDebugValue2::GetExactType
ms.date: 03/30/2017
api_name:
- ICorDebugValue2.GetExactType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue2::GetExactType
helpviewer_keywords:
- ICorDebugValue2::GetExactType method [.NET Framework debugging]
- GetExactType method [.NET Framework debugging]
ms.assetid: 8e9aae1b-d1b7-4b6e-b577-6faf36dcec85
topic_type:
- apiref
ms.openlocfilehash: d0ef08b119106ced89ec2094b5bf67d0c874b6bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690313"
---
# <a name="icordebugvalue2getexacttype-method"></a><span data-ttu-id="85c4f-103">Метод ICorDebugValue2::GetExactType</span><span class="sxs-lookup"><span data-stu-id="85c4f-103">ICorDebugValue2::GetExactType Method</span></span>

<span data-ttu-id="85c4f-104">Возвращает указатель интерфейса на объект "ICorDebugType", представляющий <xref:System.Type> это значение.</span><span class="sxs-lookup"><span data-stu-id="85c4f-104">Gets an interface pointer to an "ICorDebugType" object that represents the <xref:System.Type> of this value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85c4f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="85c4f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85c4f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="85c4f-106">Parameters</span></span>  

 `ppType`  
 <span data-ttu-id="85c4f-107">заполняет Указатель на адрес `ICorDebugType` объекта, представляющий <xref:System.Type> значение, представленное этим объектом "ICorDebugValue2".</span><span class="sxs-lookup"><span data-stu-id="85c4f-107">[out] A pointer to the address of an `ICorDebugType` object that represents the <xref:System.Type> of the value represented by this "ICorDebugValue2" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85c4f-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="85c4f-108">Remarks</span></span>  

 <span data-ttu-id="85c4f-109">Метод с учетом универсальных шаблонов `GetExactType` заменяет методы [ICorDebugObjectValue::](icordebugobjectvalue-getclass-method.md) noreturn и [ICorDebugValue:: GetType](icordebugvalue-gettype-method.md) , каждый из которых возвращает сведения о типе значения.</span><span class="sxs-lookup"><span data-stu-id="85c4f-109">The generics-aware `GetExactType` method supersedes both the [ICorDebugObjectValue::GetClass](icordebugobjectvalue-getclass-method.md) and the [ICorDebugValue::GetType](icordebugvalue-gettype-method.md) methods, each of which return information about the type of a value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85c4f-110">Требования</span><span class="sxs-lookup"><span data-stu-id="85c4f-110">Requirements</span></span>  

 <span data-ttu-id="85c4f-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85c4f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85c4f-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="85c4f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85c4f-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85c4f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85c4f-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85c4f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85c4f-115">См. также</span><span class="sxs-lookup"><span data-stu-id="85c4f-115">See also</span></span>
