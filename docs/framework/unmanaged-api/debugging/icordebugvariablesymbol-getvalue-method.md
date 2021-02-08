---
description: 'Дополнительные сведения о методе: ICorDebugVariableSymbol:: GetValue'
title: Метод ICorDebugVariableSymbol::GetValue
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
ms.openlocfilehash: ccd7eae5cc4740e83d0210a903ba0e7778aa8896
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790572"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a><span data-ttu-id="c1843-103">Метод ICorDebugVariableSymbol::GetValue</span><span class="sxs-lookup"><span data-stu-id="c1843-103">ICorDebugVariableSymbol::GetValue Method</span></span>

<span data-ttu-id="c1843-104">Возвращает значение переменной в виде массива байтов.</span><span class="sxs-lookup"><span data-stu-id="c1843-104">Gets the value of a variable as a byte array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1843-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c1843-105">Syntax</span></span>  
  
```cpp  
HRESULT GetValue(  
   [in] ULONG32 offset,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [out] ULONG32 *pcbValue,  
   [out, size_is(cbValue), length_is(*pcbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1843-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c1843-106">Parameters</span></span>  

 `offset`  
 <span data-ttu-id="c1843-107">[in] Начальное смещение в переменной, с которого следует читать значение.</span><span class="sxs-lookup"><span data-stu-id="c1843-107">[in] The starting offset in the variable from which to read the value.</span></span> <span data-ttu-id="c1843-108">Этот параметр используется при чтении полей членов в объекте.</span><span class="sxs-lookup"><span data-stu-id="c1843-108">This parameter is used when reading member fields in an object.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="c1843-109">[in] Размер аргумента `context` в байтах.</span><span class="sxs-lookup"><span data-stu-id="c1843-109">[in] The size in bytes of the `context` argument.</span></span>  
  
 `context`  
 <span data-ttu-id="c1843-110">[in] Контекст потока, используемый для чтения значения.</span><span class="sxs-lookup"><span data-stu-id="c1843-110">[in] The thread context used to read the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="c1843-111">[in] Размер буфера `pValue` в байтах.</span><span class="sxs-lookup"><span data-stu-id="c1843-111">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pcbValue`  
 <span data-ttu-id="c1843-112">[out] Число байтов, фактически записанных в буфер `pValue`.</span><span class="sxs-lookup"><span data-stu-id="c1843-112">[out] The number of bytes actually written to the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="c1843-113">[out] Массив байтов, содержащий значение переменной.</span><span class="sxs-lookup"><span data-stu-id="c1843-113">[out] A byte array that contains the value of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1843-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="c1843-114">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c1843-115">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="c1843-115">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1843-116">Требования</span><span class="sxs-lookup"><span data-stu-id="c1843-116">Requirements</span></span>  

 <span data-ttu-id="c1843-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1843-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1843-118">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c1843-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c1843-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1843-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1843-120">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1843-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1843-121">См. также</span><span class="sxs-lookup"><span data-stu-id="c1843-121">See also</span></span>

- [<span data-ttu-id="c1843-122">Интерфейс ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="c1843-122">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="c1843-123">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="c1843-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
