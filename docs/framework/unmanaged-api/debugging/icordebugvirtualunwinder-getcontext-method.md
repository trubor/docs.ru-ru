---
description: 'Дополнительные сведения о методе: ICorDebugVirtualUnwinder:: oncontext'
title: Метод ICorDebugVirtualUnwinder::GetContext
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
ms.openlocfilehash: 864f32ce82149658b2d4a617b08e8d7aa41fe642
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790533"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a><span data-ttu-id="5ee61-103">Метод ICorDebugVirtualUnwinder::GetContext</span><span class="sxs-lookup"><span data-stu-id="5ee61-103">ICorDebugVirtualUnwinder::GetContext Method</span></span>

<span data-ttu-id="5ee61-104">Получает текущий контекст этого средства очистки.</span><span class="sxs-lookup"><span data-stu-id="5ee61-104">Gets the current context of this unwinder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ee61-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5ee61-105">Syntax</span></span>  
  
```cpp  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ee61-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="5ee61-106">Parameters</span></span>  

 `contextFlags`  
 <span data-ttu-id="5ee61-107">[in] Флаги, указывающие, какие части контекста следует возвращать (определенные в заголовке WinNt.h).</span><span class="sxs-lookup"><span data-stu-id="5ee61-107">[in] Flags that specify which parts of the context to return (defined in WinNT.h).</span></span>  
  
 `cbContextBuf`  
 <span data-ttu-id="5ee61-108">[in] Количество байтов в `contextBuf`.</span><span class="sxs-lookup"><span data-stu-id="5ee61-108">[in] The number of bytes in `contextBuf`.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="5ee61-109">[out] Указатель на число байтов, фактически записанных в `contextBuf`.</span><span class="sxs-lookup"><span data-stu-id="5ee61-109">[out] A pointer to the number of bytes actually written to `contextBuf`.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="5ee61-110">[out] Байтовый массив, содержащий текущий контекст этого средства очистки.</span><span class="sxs-lookup"><span data-stu-id="5ee61-110">[out] A byte array that contains the current context of this unwinder.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5ee61-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="5ee61-111">Return Value</span></span>  

 <span data-ttu-id="5ee61-112">Любое ошибочное значение HRESULT , полученное процессом mscordbi, считается неустранимым и приводит к возврату интерфейсами API ICorDebug значения `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="5ee61-112">Any failing HRESULT value received by mscordbi is considered fatal and will cause ICorDebug APIs to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ee61-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="5ee61-113">Remarks</span></span>  

 <span data-ttu-id="5ee61-114">Начальное значение аргумента задается `contextBuf` в буфере контекста, возвращаемом путем вызова метода [икордебугстакквалк:: oncontext](icordebugstackwalk-getcontext-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5ee61-114">You set the initial value of the `contextBuf` argument to the context buffer returned by calling the [ICorDebugStackWalk::GetContext](icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5ee61-115">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="5ee61-115">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="5ee61-116">Поскольку очистка может восстановить только подмножество регистров, например только неизменяемые регистры, контекст может не соответствовать в точности состоянию регистра во время фактического вызова метода.</span><span class="sxs-lookup"><span data-stu-id="5ee61-116">Because unwinding may only restore a subset of the registers, such as the non-volatile registers only, the context may not exactly match the register state at the time of the actual method call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ee61-117">Требования</span><span class="sxs-lookup"><span data-stu-id="5ee61-117">Requirements</span></span>  

 <span data-ttu-id="5ee61-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ee61-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ee61-119">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5ee61-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5ee61-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ee61-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ee61-121">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ee61-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ee61-122">См. также</span><span class="sxs-lookup"><span data-stu-id="5ee61-122">See also</span></span>

- [<span data-ttu-id="5ee61-123">Интерфейс ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="5ee61-123">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="5ee61-124">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="5ee61-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
