---
description: 'Дополнительные сведения о методе: ICorDebugProcess6::D Екодивент'
title: Метод ICorDebugProcess6::DecodeEvent
ms.date: 03/30/2017
ms.assetid: 1453bc0c-6e0d-4d5a-b176-22607f8a3e6c
ms.openlocfilehash: 241b24335f96a250156effde34683c8f32a47e3f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746221"
---
# <a name="icordebugprocess6decodeevent-method"></a><span data-ttu-id="33580-103">Метод ICorDebugProcess6::DecodeEvent</span><span class="sxs-lookup"><span data-stu-id="33580-103">ICorDebugProcess6::DecodeEvent Method</span></span>

<span data-ttu-id="33580-104">Декодирует события управляемой отладки, которые были инкапсулированы в полезную нагрузку из событий отладки специально созданных собственных исключений.</span><span class="sxs-lookup"><span data-stu-id="33580-104">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33580-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="33580-105">Syntax</span></span>  
  
```cpp  
HRESULT DecodeEvent(  
        [in, length_is(countBytes), size_is(countBytes)]  const BYTE pRecord[],  
        [in] DWORD countBytes,  
        [in] CorDebugRecordFormat format,  
        [in] DWORD dwFlags,
        [in] DWORD dwThreadId,
        [out] ICorDebugDebugEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33580-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="33580-106">Parameters</span></span>  

 `pRecord`  
 <span data-ttu-id="33580-107">[входной] Указатель на массив байтов из события отладки собственного исключения, содержащий данные о событии управляемой отладки.</span><span class="sxs-lookup"><span data-stu-id="33580-107">[in] A pointer to a byte array from a native exception debug event that includes information about a managed debug event.</span></span>  
  
 `countBytes`  
 <span data-ttu-id="33580-108">[входной] Количество элементов в массиве байтов `pRecord`.</span><span class="sxs-lookup"><span data-stu-id="33580-108">[in] The number of elements in the `pRecord` byte array.</span></span>  
  
 `format`  
 <span data-ttu-id="33580-109">окне Элемент перечисления [кордебугрекордформат](cordebugrecordformat-enumeration.md) , указывающий формат неуправляемого события отладки.</span><span class="sxs-lookup"><span data-stu-id="33580-109">[in] A [CorDebugRecordFormat](cordebugrecordformat-enumeration.md) enumeration member that specifies the format of the unmanaged debug event.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="33580-110">[входной] Битовое поле, которое зависит от целевой архитектуры и содержит дополнительные сведения о событии отладки.</span><span class="sxs-lookup"><span data-stu-id="33580-110">[in] A bit field that depends on the target architecture and that specifies additional information about the debug event.</span></span> <span data-ttu-id="33580-111">Для систем Windows он может быть членом перечисления [кордебугдекодивентфлагсвиндовс](cordebugdecodeeventflagswindows-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="33580-111">For Windows systems, it can be a member of the [CorDebugDecodeEventFlagsWindows](cordebugdecodeeventflagswindows-enumeration.md) enumeration.</span></span>  
  
 `dwThreadId`  
 <span data-ttu-id="33580-112">[входной] Идентификатор операционной системы для потока, в котором возникло исключение.</span><span class="sxs-lookup"><span data-stu-id="33580-112">[in] The operating system identifier of the thread on which the exception was thrown.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="33580-113">заполняет Указатель на адрес объекта [ICorDebugDebugEvent](icordebugdebugevent-interface.md) , который представляет декодированное управляемое событие отладки.</span><span class="sxs-lookup"><span data-stu-id="33580-113">[out] A pointer to the address of an [ICorDebugDebugEvent](icordebugdebugevent-interface.md) object that represents a decoded managed debug event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33580-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="33580-114">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="33580-115">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="33580-115">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33580-116">Требования</span><span class="sxs-lookup"><span data-stu-id="33580-116">Requirements</span></span>  

 <span data-ttu-id="33580-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33580-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33580-118">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="33580-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33580-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33580-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33580-120">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33580-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33580-121">См. также</span><span class="sxs-lookup"><span data-stu-id="33580-121">See also</span></span>

- [<span data-ttu-id="33580-122">Интерфейс ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="33580-122">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="33580-123">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="33580-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
