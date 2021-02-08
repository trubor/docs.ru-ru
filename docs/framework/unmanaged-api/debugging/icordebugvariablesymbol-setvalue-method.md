---
description: 'Дополнительные сведения о методе: ICorDebugVariableSymbol:: SetValue'
title: Метод ICorDebugVariableSymbol::SetValue
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
ms.openlocfilehash: aa36712defcf44039f17fe846113c15814549e09
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800855"
---
# <a name="icordebugvariablesymbolsetvalue-method"></a><span data-ttu-id="7e887-103">Метод ICorDebugVariableSymbol::SetValue</span><span class="sxs-lookup"><span data-stu-id="7e887-103">ICorDebugVariableSymbol::SetValue Method</span></span>

<span data-ttu-id="7e887-104">Присваивает переменной значение массива байтов.</span><span class="sxs-lookup"><span data-stu-id="7e887-104">Assigns the value of a byte array to a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e887-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7e887-105">Syntax</span></span>  
  
```cpp  
HRESULT SetValue(  
   [in] ULONG32 offset,  
   [in] DWORD threadID,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [in, size_is(cbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e887-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7e887-106">Parameters</span></span>  

 `offset`  
 <span data-ttu-id="7e887-107">[in] Начальное смещение в переменной, с которого следует задавать значение.</span><span class="sxs-lookup"><span data-stu-id="7e887-107">[in] The starting offset in the variable at which to set the value.</span></span> <span data-ttu-id="7e887-108">Этот параметр используется при записи в поля членов в объекте.</span><span class="sxs-lookup"><span data-stu-id="7e887-108">This parameter is used when writing to member fields in an object.</span></span>  
  
 `threadID`  
 <span data-ttu-id="7e887-109">[in] Идентификатор потока, чей контекст должен быть обновлен в соответствии с новым значением.</span><span class="sxs-lookup"><span data-stu-id="7e887-109">[in] The thread identifier of the thread whose context must be updated to reflect the new value.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="7e887-110">[in] Размер контекста потока в байтах.</span><span class="sxs-lookup"><span data-stu-id="7e887-110">[in] The size in bytes of the thread context.</span></span>  
  
 `context`  
 <span data-ttu-id="7e887-111">[in] Контекст потока, используемый для записи значения.</span><span class="sxs-lookup"><span data-stu-id="7e887-111">[in] The thread context used to write the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="7e887-112">[in] Размер буфера `pValue` в байтах.</span><span class="sxs-lookup"><span data-stu-id="7e887-112">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="7e887-113">[in] Буфер, содержащий значение, которое требуется задать.</span><span class="sxs-lookup"><span data-stu-id="7e887-113">[in] The buffer that contains the value to set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e887-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="7e887-114">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7e887-115">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="7e887-115">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e887-116">Требования</span><span class="sxs-lookup"><span data-stu-id="7e887-116">Requirements</span></span>  

 <span data-ttu-id="7e887-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e887-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e887-118">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e887-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e887-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e887-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e887-120">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e887-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e887-121">См. также</span><span class="sxs-lookup"><span data-stu-id="7e887-121">See also</span></span>

- [<span data-ttu-id="7e887-122">Интерфейс ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="7e887-122">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="7e887-123">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="7e887-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
