---
description: 'Дополнительные сведения о методе: Икордебугблоккингобжектенум:: Next'
title: Метод ICorDebugBlockingObjectEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugBlockingObjectEnum.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBlockingObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
- ICorDebugBlockingObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 0121753f-ebea-48d0-aeb2-ed7fda76dc60
topic_type:
- apiref
ms.openlocfilehash: 66999ebf333c7115790b56afc1dc1d1ab7c47d69
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711821"
---
# <a name="icordebugblockingobjectenumnext-method"></a><span data-ttu-id="e04a1-103">Метод ICorDebugBlockingObjectEnum::Next</span><span class="sxs-lookup"><span data-stu-id="e04a1-103">ICorDebugBlockingObjectEnum::Next Method</span></span>

<span data-ttu-id="e04a1-104">Возвращает указанное число объектов [CorDebugBlockingObject](cordebugblockingobject-structure.md) из перечисления, начиная с текущей позиции.</span><span class="sxs-lookup"><span data-stu-id="e04a1-104">Gets the specified number of [CorDebugBlockingObject](cordebugblockingobject-structure.md) objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e04a1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e04a1-105">Syntax</span></span>  
  
```cpp  
HRESULT Next([in] ULONG  celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                           CorDebugBlockingObject values[],  
             [out] ULONG *pceltFetched;  
```  
  
## <a name="parameters"></a><span data-ttu-id="e04a1-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e04a1-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="e04a1-107">окне Число извлекаемых объектов.</span><span class="sxs-lookup"><span data-stu-id="e04a1-107">[in] The number of objects to retrieve.</span></span>  
  
 `values`  
 <span data-ttu-id="e04a1-108">заполняет Массив указателей на объекты [CorDebugBlockingObject](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="e04a1-108">[out] An array of pointers to [CorDebugBlockingObject](cordebugblockingobject-structure.md) objects.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="e04a1-109">заполняет Указатель на количество полученных объектов.</span><span class="sxs-lookup"><span data-stu-id="e04a1-109">[out] A pointer to the number of objects that were retrieved.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e04a1-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="e04a1-110">Return Value</span></span>  

 <span data-ttu-id="e04a1-111">Этот метод возвращает следующие специфичные результаты HRESULT.</span><span class="sxs-lookup"><span data-stu-id="e04a1-111">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="e04a1-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e04a1-112">HRESULT</span></span>|<span data-ttu-id="e04a1-113">Описание:</span><span class="sxs-lookup"><span data-stu-id="e04a1-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e04a1-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="e04a1-114">S_OK</span></span>|<span data-ttu-id="e04a1-115">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="e04a1-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="e04a1-116">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e04a1-116">S_FALSE</span></span>|<span data-ttu-id="e04a1-117">Значение параметра `pceltFetched` не равно `celt`.</span><span class="sxs-lookup"><span data-stu-id="e04a1-117">`pceltFetched` does not equal `celt`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e04a1-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="e04a1-118">Remarks</span></span>  

 <span data-ttu-id="e04a1-119">Этот метод работает, как типичный перечислитель COM.</span><span class="sxs-lookup"><span data-stu-id="e04a1-119">This method functions like a typical COM enumerator.</span></span>  
  
 <span data-ttu-id="e04a1-120">Значения входного массива должны иметь размер не ниже `celt` .</span><span class="sxs-lookup"><span data-stu-id="e04a1-120">The input array values must be at least of size `celt`.</span></span> <span data-ttu-id="e04a1-121">Массив будет заполнен либо следующими `celt` значениями в перечислении, либо со всеми оставшимися значениями, если они меньше `celt` , чем осталось.</span><span class="sxs-lookup"><span data-stu-id="e04a1-121">The array will be filled with either the next `celt` values in the enumeration or with all remaining values if fewer than `celt` remain.</span></span> <span data-ttu-id="e04a1-122">При возврате из этого метода `pceltFetched` будет заполнено количество полученных значений.</span><span class="sxs-lookup"><span data-stu-id="e04a1-122">When this method returns, `pceltFetched` will be filled with the number of values that were retrieved.</span></span> <span data-ttu-id="e04a1-123">Если `values` содержит недопустимые указатели или указывает на буфер, который меньше `celt` , или если `pceltFetched` является недопустимым указателем, результат не определен.</span><span class="sxs-lookup"><span data-stu-id="e04a1-123">If `values` contains invalid pointers or points to a buffer that is smaller than `celt`, or if `pceltFetched` is an invalid pointer, the result is undefined.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e04a1-124">Хотя структуру [CorDebugBlockingObject](cordebugblockingobject-structure.md) не нужно освобождать, интерфейс "ICorDebugValue" внутри него должен быть освобожден.</span><span class="sxs-lookup"><span data-stu-id="e04a1-124">Although the [CorDebugBlockingObject](cordebugblockingobject-structure.md) structure does not need to be released, the "ICorDebugValue" interface inside of it does need to be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e04a1-125">Требования</span><span class="sxs-lookup"><span data-stu-id="e04a1-125">Requirements</span></span>  

 <span data-ttu-id="e04a1-126">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e04a1-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e04a1-127">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e04a1-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e04a1-128">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e04a1-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e04a1-129">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e04a1-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e04a1-130">См. также</span><span class="sxs-lookup"><span data-stu-id="e04a1-130">See also</span></span>

- [<span data-ttu-id="e04a1-131">Интерфейс ICorDebugDataTarget</span><span class="sxs-lookup"><span data-stu-id="e04a1-131">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="e04a1-132">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="e04a1-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e04a1-133">Отладка</span><span class="sxs-lookup"><span data-stu-id="e04a1-133">Debugging</span></span>](index.md)
