---
description: 'Дополнительные сведения о методе ICorDebugValue:: метода Address'
title: Метод ICorDebugValue::GetAddress
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetAddress
helpviewer_keywords:
- ICorDebugValue::GetAddress method [.NET Framework debugging]
- GetAddress method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: a247c792-45e1-4538-9e1f-b46acca4a463
topic_type:
- apiref
ms.openlocfilehash: c922388fbab820e50edffc140be94a2c0920099d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690435"
---
# <a name="icordebugvaluegetaddress-method"></a><span data-ttu-id="bec3f-103">Метод ICorDebugValue::GetAddress</span><span class="sxs-lookup"><span data-stu-id="bec3f-103">ICorDebugValue::GetAddress Method</span></span>

<span data-ttu-id="bec3f-104">Возвращает адрес этого объекта "ICorDebugValue", который находится в процессе отладки.</span><span class="sxs-lookup"><span data-stu-id="bec3f-104">Gets the address of this "ICorDebugValue" object, which is in the process of being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bec3f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bec3f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bec3f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="bec3f-106">Parameters</span></span>  

 `pAddress`  
 <span data-ttu-id="bec3f-107">заполняет Указатель на `CORDB_ADDRESS` объект, указывающий адрес этого объекта значения.</span><span class="sxs-lookup"><span data-stu-id="bec3f-107">[out] Pointer to a `CORDB_ADDRESS` object that specifies the address of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bec3f-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="bec3f-108">Remarks</span></span>  

 <span data-ttu-id="bec3f-109">Если значение недоступно, возвращается 0 (нуль).</span><span class="sxs-lookup"><span data-stu-id="bec3f-109">If the value is unavailable, 0 (zero) is returned.</span></span> <span data-ttu-id="bec3f-110">Это может произойти, если значение не меньше частично в регистрах или хранится в обработчике сборщика мусора ( `GCHandle` ).</span><span class="sxs-lookup"><span data-stu-id="bec3f-110">This could happen if the value is at least partly in registers or stored in a garbage collector handle (`GCHandle`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bec3f-111">Требования</span><span class="sxs-lookup"><span data-stu-id="bec3f-111">Requirements</span></span>  

 <span data-ttu-id="bec3f-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bec3f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bec3f-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bec3f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bec3f-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bec3f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bec3f-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bec3f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bec3f-116">См. также</span><span class="sxs-lookup"><span data-stu-id="bec3f-116">See also</span></span>
