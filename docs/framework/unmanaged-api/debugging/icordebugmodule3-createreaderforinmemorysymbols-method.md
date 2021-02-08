---
description: 'Дополнительные сведения о методе: метод icordebugmodule3:: CreateReaderForInMemorySymbols'
title: Метод ICorDebugModule3::CreateReaderForInMemorySymbols
ms.date: 03/30/2017
api_name:
- ICorDebugModule3.CreateReaderForInMemorySymbols
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule3::CreateReaderForInMemorySymbols
helpviewer_keywords:
- CreateReaderForInMemorySymbols method, ICorDebugModule3 interface [.NET Framework debugging]
- ICorDebugModule3::CreateReaderForInMemorySymbols method [.NET Framework debugging]
ms.assetid: af317171-d66d-4114-89eb-063554c74940
topic_type:
- apiref
ms.openlocfilehash: af037cc891e83f53fd94bad290f40286ed665e6f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790780"
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a><span data-ttu-id="b7c1c-103">Метод ICorDebugModule3::CreateReaderForInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="b7c1c-103">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>

<span data-ttu-id="b7c1c-104">Создает средство чтения символов отладки для динамического модуля.</span><span class="sxs-lookup"><span data-stu-id="b7c1c-104">Creates a debug symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7c1c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b7c1c-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7c1c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b7c1c-106">Parameters</span></span>  

 <span data-ttu-id="b7c1c-107">riid</span><span class="sxs-lookup"><span data-stu-id="b7c1c-107">riid</span></span>  
 <span data-ttu-id="b7c1c-108">окне Идентификатор IID возвращаемого COM-интерфейса.</span><span class="sxs-lookup"><span data-stu-id="b7c1c-108">[in] The IID of the COM interface to return.</span></span> <span data-ttu-id="b7c1c-109">Как правило, это [Интерфейс ISymUnmanagedReader](../diagnostics/isymunmanagedreader-interface.md).</span><span class="sxs-lookup"><span data-stu-id="b7c1c-109">Typically, this is an [ISymUnmanagedReader Interface](../diagnostics/isymunmanagedreader-interface.md).</span></span>  
  
 <span data-ttu-id="b7c1c-110">ппобж</span><span class="sxs-lookup"><span data-stu-id="b7c1c-110">ppObj</span></span>  
 <span data-ttu-id="b7c1c-111">заполняет Указатель на указатель на возвращенный интерфейс.</span><span class="sxs-lookup"><span data-stu-id="b7c1c-111">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b7c1c-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="b7c1c-112">Return Value</span></span>  

 <span data-ttu-id="b7c1c-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="b7c1c-113">S_OK</span></span>  
 <span data-ttu-id="b7c1c-114">Модуль чтения успешно создан.</span><span class="sxs-lookup"><span data-stu-id="b7c1c-114">Successfully created the reader.</span></span>  
  
 <span data-ttu-id="b7c1c-115">CORDBG_E_MODULE_LOADED_FROM_DISK</span><span class="sxs-lookup"><span data-stu-id="b7c1c-115">CORDBG_E_MODULE_LOADED_FROM_DISK</span></span>  
 <span data-ttu-id="b7c1c-116">Модуль не является ни в памяти, ни динамическим модулем.</span><span class="sxs-lookup"><span data-stu-id="b7c1c-116">The module is not an in-memory or dynamic module.</span></span>  
  
 <span data-ttu-id="b7c1c-117">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b7c1c-117">CORDBG_E_SYMBOLS_NOT_AVAILABLE</span></span>  
 <span data-ttu-id="b7c1c-118">Символы не были предоставлены приложением или пока недоступны.</span><span class="sxs-lookup"><span data-stu-id="b7c1c-118">Symbols have not been supplied by the application or are not yet available.</span></span>  
  
 <span data-ttu-id="b7c1c-119">E_FAIL (или другие коды возврата E_)</span><span class="sxs-lookup"><span data-stu-id="b7c1c-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="b7c1c-120">Не удалось создать модуль чтения.</span><span class="sxs-lookup"><span data-stu-id="b7c1c-120">Unable to create the reader.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7c1c-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="b7c1c-121">Remarks</span></span>  

 <span data-ttu-id="b7c1c-122">Этот метод можно также использовать для создания объекта средства чтения символов для модулей, не являющихся динамическими, но только после того, как символы будут первыми доступны (обозначены обратным вызовом [метода UpdateModuleSymbols](icordebugmanagedcallback-updatemodulesymbols-method.md) ).</span><span class="sxs-lookup"><span data-stu-id="b7c1c-122">This method can also be used to create a symbol reader object for in-memory (non-dynamic) modules, but only after the symbols are first available (indicated by the [UpdateModuleSymbols Method](icordebugmanagedcallback-updatemodulesymbols-method.md) callback).</span></span>  
  
 <span data-ttu-id="b7c1c-123">Этот метод возвращает новый экземпляр модуля чтения при каждом вызове (например, [ккомптрбасе:: CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)).</span><span class="sxs-lookup"><span data-stu-id="b7c1c-123">This method returns a new reader instance every time it is called (like [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)).</span></span> <span data-ttu-id="b7c1c-124">Поэтому отладчик должен кэшировать результат и запросить новый экземпляр только в том случае, если базовые данные могли измениться (то есть при получении обратного вызова [метода loadClass](icordebugmanagedcallback-loadclass-method.md) ).</span><span class="sxs-lookup"><span data-stu-id="b7c1c-124">Therefore, the debugger should cache the result and request a new instance only when the underlying data may have changed (that is, when a [LoadClass Method](icordebugmanagedcallback-loadclass-method.md) callback is received).</span></span>  
  
 <span data-ttu-id="b7c1c-125">Динамические модули не имеют доступных символов, пока не будет загружен первый тип (как указано в обратном вызове [метода loadClass](icordebugmanagedcallback-loadclass-method.md) ).</span><span class="sxs-lookup"><span data-stu-id="b7c1c-125">Dynamic modules do not have any symbols available until the first type has been loaded (as indicated by the [LoadClass Method](icordebugmanagedcallback-loadclass-method.md) callback).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7c1c-126">Требования</span><span class="sxs-lookup"><span data-stu-id="b7c1c-126">Requirements</span></span>  

 <span data-ttu-id="b7c1c-127">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7c1c-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7c1c-128">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7c1c-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7c1c-129">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7c1c-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7c1c-130">**Платформа .NET Framework версии:** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="b7c1c-130">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7c1c-131">См. также</span><span class="sxs-lookup"><span data-stu-id="b7c1c-131">See also</span></span>

- [<span data-ttu-id="b7c1c-132">Интерфейс ICorDebugRemoteTarget</span><span class="sxs-lookup"><span data-stu-id="b7c1c-132">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="b7c1c-133">Интерфейс ICorDebug</span><span class="sxs-lookup"><span data-stu-id="b7c1c-133">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="b7c1c-134">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="b7c1c-134">Debugging Interfaces</span></span>](debugging-interfaces.md)
