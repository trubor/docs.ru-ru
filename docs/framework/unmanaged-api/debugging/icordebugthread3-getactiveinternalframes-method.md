---
description: 'Дополнительные сведения о методе: ICorDebugThread3:: Жетактивеинтерналфрамес'
title: Метод ICorDebugThread3::GetActiveInternalFrames
ms.date: 03/30/2017
api_name:
- ICorDebugThread3.GetActiveInternalFrames Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::GetActiveInternalFrames
helpviewer_keywords:
- ICorDebugThread3::GetActiveInternalFrames method [.NET Framework debugging]
- GetActiveInternalFrames method [.NET Framework debugging]
ms.assetid: d69796b4-5b6d-457c-85f6-2cf42e8a8773
topic_type:
- apiref
ms.openlocfilehash: f228dd84708478bb364ac09407a68df3e8d971b6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800985"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a><span data-ttu-id="7a72d-103">Метод ICorDebugThread3::GetActiveInternalFrames</span><span class="sxs-lookup"><span data-stu-id="7a72d-103">ICorDebugThread3::GetActiveInternalFrames Method</span></span>

<span data-ttu-id="7a72d-104">Возвращает массив внутренних кадров (объектов[ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) ) в стеке.</span><span class="sxs-lookup"><span data-stu-id="7a72d-104">Returns an array of internal frames ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objects) on the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a72d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7a72d-105">Syntax</span></span>  
  
```cpp
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a72d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7a72d-106">Parameters</span></span>  

 `cInternalFrames`  
 <span data-ttu-id="7a72d-107">окне Число внутренних кадров, ожидаемых в `ppInternalFrames` .</span><span class="sxs-lookup"><span data-stu-id="7a72d-107">[in] The number of internal frames expected in `ppInternalFrames`.</span></span>  
  
 `pcInternalFrames`  
 <span data-ttu-id="7a72d-108">заполняет Указатель на объект `ULONG32` , который содержит количество внутренних кадров в стеке.</span><span class="sxs-lookup"><span data-stu-id="7a72d-108">[out] A pointer to a `ULONG32` that contains the number of internal frames on the stack.</span></span>  
  
 `ppInternalFrames`  
 <span data-ttu-id="7a72d-109">[вход, выход] Указатель на адрес массива внутренних кадров в стеке.</span><span class="sxs-lookup"><span data-stu-id="7a72d-109">[in, out] A pointer to the address of an array of internal frames on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7a72d-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="7a72d-110">Return Value</span></span>  

 <span data-ttu-id="7a72d-111">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="7a72d-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7a72d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7a72d-112">HRESULT</span></span>|<span data-ttu-id="7a72d-113">Описание:</span><span class="sxs-lookup"><span data-stu-id="7a72d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7a72d-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="7a72d-114">S_OK</span></span>|<span data-ttu-id="7a72d-115">Объект [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) успешно создан.</span><span class="sxs-lookup"><span data-stu-id="7a72d-115">The [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) object was successfully created.</span></span>|  
|<span data-ttu-id="7a72d-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="7a72d-116">E_INVALIDARG</span></span>|<span data-ttu-id="7a72d-117">`cInternalFrames` не равен нулю `ppInternalFrames` , имеет значение `null` , или `pcInternalFrames` имеет значение `null` .</span><span class="sxs-lookup"><span data-stu-id="7a72d-117">`cInternalFrames` is not zero and `ppInternalFrames` is `null`, or `pcInternalFrames` is `null`.</span></span>|  
|<span data-ttu-id="7a72d-118">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="7a72d-118">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="7a72d-119">`ppInternalFrames` меньше, чем число внутренних кадров.</span><span class="sxs-lookup"><span data-stu-id="7a72d-119">`ppInternalFrames` is smaller than the count of internal frames.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="7a72d-120">Исключения</span><span class="sxs-lookup"><span data-stu-id="7a72d-120">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a72d-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="7a72d-121">Remarks</span></span>  

 <span data-ttu-id="7a72d-122">Внутренние кадры — это структуры данных, помещаемые в стек средой выполнения для хранения временных данных.</span><span class="sxs-lookup"><span data-stu-id="7a72d-122">Internal frames are data structures pushed onto the stack by the runtime to store temporary data.</span></span>  
  
 <span data-ttu-id="7a72d-123">При первом вызове `GetActiveInternalFrames` следует присвоить `cInternalFrames` параметру значение 0 (ноль), а `ppInternalFrames` параметр — значению NULL.</span><span class="sxs-lookup"><span data-stu-id="7a72d-123">When you first call `GetActiveInternalFrames`, you should set the `cInternalFrames` parameter to 0 (zero), and the `ppInternalFrames` parameter to null.</span></span> <span data-ttu-id="7a72d-124">При `GetActiveInternalFrames` первом возвращении `pcInternalFrames` содержит количество внутренних кадров в стеке.</span><span class="sxs-lookup"><span data-stu-id="7a72d-124">When `GetActiveInternalFrames` first returns, `pcInternalFrames` contains the count of the internal frames on the stack.</span></span>  
  
 <span data-ttu-id="7a72d-125">`GetActiveInternalFrames` Затем следует вызвать второй раз.</span><span class="sxs-lookup"><span data-stu-id="7a72d-125">`GetActiveInternalFrames` should then be called a second time.</span></span> <span data-ttu-id="7a72d-126">Необходимо передать соответствующее значение Count ( `pcInternalFrames` ) в `cInternalFrames` параметре и указать указатель на массив соответствующего размера в `ppInternalFrames` .</span><span class="sxs-lookup"><span data-stu-id="7a72d-126">You should pass the proper count (`pcInternalFrames`) in the `cInternalFrames` parameter, and specify a pointer to an appropriately sized array in `ppInternalFrames`.</span></span>  
  
 <span data-ttu-id="7a72d-127">Используйте метод [икордебугстакквалк:: noframes](icordebugthread3-getactiveinternalframes-method.md) для возврата фактических кадров стека.</span><span class="sxs-lookup"><span data-stu-id="7a72d-127">Use the [ICorDebugStackWalk::GetFrame](icordebugthread3-getactiveinternalframes-method.md) method to return actual stack frames.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a72d-128">Требования</span><span class="sxs-lookup"><span data-stu-id="7a72d-128">Requirements</span></span>  

 <span data-ttu-id="7a72d-129">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a72d-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a72d-130">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a72d-130">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a72d-131">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a72d-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a72d-132">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a72d-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a72d-133">См. также</span><span class="sxs-lookup"><span data-stu-id="7a72d-133">See also</span></span>

- [<span data-ttu-id="7a72d-134">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="7a72d-134">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="7a72d-135">Отладка</span><span class="sxs-lookup"><span data-stu-id="7a72d-135">Debugging</span></span>](index.md)
