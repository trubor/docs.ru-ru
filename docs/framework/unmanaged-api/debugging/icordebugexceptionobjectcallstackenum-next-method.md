---
description: 'Дополнительные сведения о методе: ICorDebugExceptionObjectCallStackEnum:: Next'
title: Метод ICorDebugExceptionObjectCallStackEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum::Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum::Next
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 3328a2c0-1e48-4a54-802a-9b474cf82c21
topic_type:
- apiref
ms.openlocfilehash: df68eb6e4794d294fc39dd943065582dc52a58a1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693321"
---
# <a name="icordebugexceptionobjectcallstackenumnext-method"></a><span data-ttu-id="0c270-103">Метод ICorDebugExceptionObjectCallStackEnum::Next</span><span class="sxs-lookup"><span data-stu-id="0c270-103">ICorDebugExceptionObjectCallStackEnum::Next Method</span></span>

<span data-ttu-id="0c270-104">Возвращает указанное число экземпляров [кордебужексцептионобжектстаккфраме](cordebugexceptionobjectstackframe-structure.md) , содержащих сведения из стека вызовов объекта исключения.</span><span class="sxs-lookup"><span data-stu-id="0c270-104">Gets the specified number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) instances that contain information from an exception object's call stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c270-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0c270-105">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] CorDebugExceptionObjectStackFrame values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c270-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0c270-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="0c270-107">окне Число извлекаемых экземпляров [кордебужексцептионобжектстаккфраме](cordebugexceptionobjectstackframe-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="0c270-107">[in] The number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="0c270-108">заполняет Массив указателей, каждый из которых указывает на объект [кордебужексцептионобжектстаккфраме](cordebugexceptionobjectstackframe-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="0c270-108">[out] An array of pointers, each of which points to a [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="0c270-109">заполняет Указатель на число фактически возвращенных экземпляров [кордебужексцептионобжектстаккфраме](cordebugexceptionobjectstackframe-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="0c270-109">[out] A pointer to the number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) instances actually returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c270-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="0c270-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c270-111">Требования</span><span class="sxs-lookup"><span data-stu-id="0c270-111">Requirements</span></span>  

 <span data-ttu-id="0c270-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c270-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c270-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0c270-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c270-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c270-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c270-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c270-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c270-116">См. также</span><span class="sxs-lookup"><span data-stu-id="0c270-116">See also</span></span>

- [<span data-ttu-id="0c270-117">Интерфейс ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="0c270-117">ICorDebugExceptionObjectCallStackEnum Interface</span></span>](icordebugexceptionobjectcallstackenum-interface.md)
- [<span data-ttu-id="0c270-118">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="0c270-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
