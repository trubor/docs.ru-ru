---
description: 'Дополнительные сведения о методе: ICorDebugCode3:: Жетретурнвалуеливеоффсет'
title: Метод ICorDebugCode3::GetReturnValueLiveOffset
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugCode3.GetReturnValueLiveOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset
helpviewer_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset method [.NET Framework debugging]
- GetReturnValueLiveOffset method [.NET Framework debugging]
ms.assetid: 8c2ff5d8-8c04-4423-b1e1-e1c8764b36d3
topic_type:
- apiref
ms.openlocfilehash: 6ec9a342805c047d7331c3ce2af2a4ffba596a26
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711015"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a><span data-ttu-id="cc9bd-103">Метод ICorDebugCode3::GetReturnValueLiveOffset</span><span class="sxs-lookup"><span data-stu-id="cc9bd-103">ICorDebugCode3::GetReturnValueLiveOffset Method</span></span>

<span data-ttu-id="cc9bd-104">Для указанного смещения IL получает машинные смещения, в которых должна быть помещена точка останова, чтобы отладчик мог получить возвращаемое значение из функции.</span><span class="sxs-lookup"><span data-stu-id="cc9bd-104">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc9bd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cc9bd-105">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,
    [out] ULONG32 *pFetched,
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc9bd-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="cc9bd-106">Parameters</span></span>  

 `ILoffset`  
 <span data-ttu-id="cc9bd-107">Смещение IL.</span><span class="sxs-lookup"><span data-stu-id="cc9bd-107">The IL offset.</span></span> <span data-ttu-id="cc9bd-108">Это должен быть сайт вызова функции, иначе вызов функции завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="cc9bd-108">It must be a function call site or the function call will fail.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="cc9bd-109">Число байтов, доступных для хранения `pOffsets` .</span><span class="sxs-lookup"><span data-stu-id="cc9bd-109">The number of bytes available to store `pOffsets`.</span></span>  
  
 `pFetched`  
 <span data-ttu-id="cc9bd-110">Указатель на число фактически возвращенных смещений.</span><span class="sxs-lookup"><span data-stu-id="cc9bd-110">A pointer to the number of offsets actually returned.</span></span> <span data-ttu-id="cc9bd-111">Обычно его значение равно 1, но одна инструкция IL может сопоставляться с несколькими `CALL` инструкциями сборки.</span><span class="sxs-lookup"><span data-stu-id="cc9bd-111">Usually, its value is 1, but a single IL instruction can map to multiple `CALL` assembly instructions.</span></span>  
  
 `pOffsets`  
 <span data-ttu-id="cc9bd-112">Массив смещений машинного кода.</span><span class="sxs-lookup"><span data-stu-id="cc9bd-112">An array of native offsets.</span></span> <span data-ttu-id="cc9bd-113">Как правило, `pOffsets` содержит одно смещение, хотя одна инструкция il может сопоставляться с несколькими инструкциями сборки по нескольким схемам `CALL` .</span><span class="sxs-lookup"><span data-stu-id="cc9bd-113">Typically, `pOffsets` contains a single offset, although a single IL instruction can map to multiple map to multiple `CALL` assembly instructions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc9bd-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="cc9bd-114">Remarks</span></span>  

 <span data-ttu-id="cc9bd-115">Этот метод используется вместе с методом [ICorDebugILFrame3:: жетретурнвалуефорилоффсет](icordebugilframe3-getreturnvalueforiloffset-method.md) для получения возвращаемого значения метода, возвращающего ссылочный тип.</span><span class="sxs-lookup"><span data-stu-id="cc9bd-115">This method is used along with the [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value of a method that returns a reference type.</span></span> <span data-ttu-id="cc9bd-116">Передача смещения IL на сайт вызова функции в этот метод возвращает одно или несколько исходных смещений.</span><span class="sxs-lookup"><span data-stu-id="cc9bd-116">Passing an IL offset to a function call site to this method returns one or more native offsets.</span></span> <span data-ttu-id="cc9bd-117">Затем отладчик может установить точки останова для этих собственных смещений в функции.</span><span class="sxs-lookup"><span data-stu-id="cc9bd-117">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="cc9bd-118">Когда отладчик обращается к одной из точек останова, можно передать то же смещение IL, которое вы передали этому методу методу [ICorDebugILFrame3:: жетретурнвалуефорилоффсет](icordebugilframe3-getreturnvalueforiloffset-method.md) , чтобы получить возвращаемое значение.</span><span class="sxs-lookup"><span data-stu-id="cc9bd-118">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to the [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value.</span></span> <span data-ttu-id="cc9bd-119">Затем отладчик должен очистить все заданные точки останова.</span><span class="sxs-lookup"><span data-stu-id="cc9bd-119">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="cc9bd-120">`ICorDebugCode3::GetReturnValueLiveOffset`Методы и [ICorDebugILFrame3:: жетретурнвалуефорилоффсет](icordebugilframe3-getreturnvalueforiloffset-method.md) позволяют получать сведения о возвращаемых значениях только для ссылочных типов.</span><span class="sxs-lookup"><span data-stu-id="cc9bd-120">The `ICorDebugCode3::GetReturnValueLiveOffset` and [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="cc9bd-121">Получение сведений о возвращаемых значениях из типов значений (то есть все типы, производные от <xref:System.ValueType> ) не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="cc9bd-121">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="cc9bd-122">Функция возвращает значения, `HRESULT` показанные в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="cc9bd-122">The function returns the `HRESULT` values shown in the following table.</span></span>  
  
|<span data-ttu-id="cc9bd-123">Значение `HRESULT`</span><span class="sxs-lookup"><span data-stu-id="cc9bd-123">`HRESULT` value</span></span>|<span data-ttu-id="cc9bd-124">Описание</span><span class="sxs-lookup"><span data-stu-id="cc9bd-124">Description</span></span>|  
|---------------------|-----------------|  
|`S_OK`|<span data-ttu-id="cc9bd-125">Успешно.</span><span class="sxs-lookup"><span data-stu-id="cc9bd-125">Success.</span></span>|  
|`CORDBG_E_INVALID_OPCODE`|<span data-ttu-id="cc9bd-126">Указанный сайт смещения IL не является инструкцией вызова, или функция возвращает `void` .</span><span class="sxs-lookup"><span data-stu-id="cc9bd-126">The given IL offset site is not a call instruction, or the function returns `void`.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="cc9bd-127">Данное смещение IL является правильным вызовом, но возвращаемый тип не поддерживается для получения возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="cc9bd-127">The given IL offset is a proper call, but the return type is unsupported for getting a return value.</span></span>|  
  
 <span data-ttu-id="cc9bd-128">`ICorDebugCode3::GetReturnValueLiveOffset`Метод доступен только в системах на базе x86 и AMD64.</span><span class="sxs-lookup"><span data-stu-id="cc9bd-128">The `ICorDebugCode3::GetReturnValueLiveOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc9bd-129">Требования</span><span class="sxs-lookup"><span data-stu-id="cc9bd-129">Requirements</span></span>  

 <span data-ttu-id="cc9bd-130">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc9bd-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc9bd-131">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc9bd-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc9bd-132">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc9bd-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc9bd-133">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc9bd-133">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc9bd-134">См. также</span><span class="sxs-lookup"><span data-stu-id="cc9bd-134">See also</span></span>

- [<span data-ttu-id="cc9bd-135">Метод GetReturnValueForILOffset</span><span class="sxs-lookup"><span data-stu-id="cc9bd-135">GetReturnValueForILOffset Method</span></span>](icordebugilframe3-getreturnvalueforiloffset-method.md)
- [<span data-ttu-id="cc9bd-136">Интерфейс ICorDebugCode3</span><span class="sxs-lookup"><span data-stu-id="cc9bd-136">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
