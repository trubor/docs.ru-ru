---
description: 'Дополнительные сведения о методе: ICorDebugExceptionObjectValue:: EnumerateExceptionCallStack'
title: Метод ICorDebugExceptionObjectValue::EnumerateExceptionCallStack
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectValue.EnumerateExceptionCallStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack
helpviewer_keywords:
- EnumerateExceptionCallStack method, ICorDebugExceptionObjectValue interface [.NET Framework debugging]
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack method [.NET Framework debugging]
ms.assetid: 00c64533-15dd-47f4-bb97-fe80a1ebadef
topic_type:
- apiref
ms.openlocfilehash: 97918d280299fae16eb55185baee19c27d99005b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693282"
---
# <a name="icordebugexceptionobjectvalueenumerateexceptioncallstack-method"></a><span data-ttu-id="c04be-103">Метод ICorDebugExceptionObjectValue::EnumerateExceptionCallStack</span><span class="sxs-lookup"><span data-stu-id="c04be-103">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Method</span></span>

<span data-ttu-id="c04be-104">Возвращает перечислитель для стека вызовов, внедренного в объект исключения.</span><span class="sxs-lookup"><span data-stu-id="c04be-104">Gets an enumerator to the call stack embedded in an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c04be-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c04be-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateExceptionCallStack(  
    [out] ICorDebugExceptionObjectCallStackEnum **ppCallStackEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c04be-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c04be-106">Parameters</span></span>  

 <span data-ttu-id="c04be-107">ппкаллстаккенум</span><span class="sxs-lookup"><span data-stu-id="c04be-107">ppCallStackEnum</span></span>  
 <span data-ttu-id="c04be-108">заполняет Указатель на адрес объекта интерфейса [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) , который является перечислителем трассировки стека для управляемого объекта исключения.</span><span class="sxs-lookup"><span data-stu-id="c04be-108">[out] A pointer to the address of an [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) interface object that is a stack trace enumerator for a managed exception object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c04be-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="c04be-109">Remarks</span></span>  

 <span data-ttu-id="c04be-110">Если сведения о стеке вызовов недоступны, метод возвращает значение `S_OK` , а [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) — допустимый перечислитель с длиной 0.</span><span class="sxs-lookup"><span data-stu-id="c04be-110">If no call stack information is available, the method returns `S_OK`, and [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) is a valid enumerator with a length of 0.</span></span> <span data-ttu-id="c04be-111">Если методу не удается получить сведения о трассировке стека, возвращается значение, `E_FAIL` а перечислитель не возвращается.</span><span class="sxs-lookup"><span data-stu-id="c04be-111">If the method is unable to retrieve stack trace information, the return value is `E_FAIL` and no enumerator is returned.</span></span>  
  
 <span data-ttu-id="c04be-112">Объект [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) отвечает за декодирование данных трассировки стека из `_stackTrace` поля объекта исключения.</span><span class="sxs-lookup"><span data-stu-id="c04be-112">The [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) object is responsible for decoding the stack trace data from the `_stackTrace` field of the exception object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c04be-113">Требования</span><span class="sxs-lookup"><span data-stu-id="c04be-113">Requirements</span></span>  

 <span data-ttu-id="c04be-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c04be-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c04be-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c04be-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c04be-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c04be-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c04be-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c04be-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c04be-118">См. также</span><span class="sxs-lookup"><span data-stu-id="c04be-118">See also</span></span>

- [<span data-ttu-id="c04be-119">Интерфейс ICorDebugExceptionObjectValue</span><span class="sxs-lookup"><span data-stu-id="c04be-119">ICorDebugExceptionObjectValue Interface</span></span>](icordebugexceptionobjectvalue-interface.md)
- [<span data-ttu-id="c04be-120">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="c04be-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
