---
description: 'Дополнительные сведения о методе: ICorDebugManagedCallback2:: Exception'
title: Метод ICorDebugManagedCallback2::Exception
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::Exception
helpviewer_keywords:
- ICorDebugManagedCallback2::Exception method [.NET Framework debugging]
- Exception method, ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: 78b0f14f-2fae-4e63-8412-4df119ee8468
topic_type:
- apiref
ms.openlocfilehash: 18fd4efcfbd1f13ce527b212d7450ba0d7651a3c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790887"
---
# <a name="icordebugmanagedcallback2exception-method"></a><span data-ttu-id="4c2ab-103">Метод ICorDebugManagedCallback2::Exception</span><span class="sxs-lookup"><span data-stu-id="4c2ab-103">ICorDebugManagedCallback2::Exception Method</span></span>

<span data-ttu-id="4c2ab-104">Уведомляет отладчик о запуске поиска обработчика исключений.</span><span class="sxs-lookup"><span data-stu-id="4c2ab-104">Notifies the debugger that a search for an exception handler has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c2ab-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4c2ab-105">Syntax</span></span>  
  
```cpp  
HRESULT Exception (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFrame       *pFrame,  
    [in] ULONG32              nOffset,  
    [in] CorDebugExceptionCallbackType dwEventType,  
    [in] DWORD                dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c2ab-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="4c2ab-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="4c2ab-107">окне Указатель на объект ICorDebugAppDomain, представляющий домен приложения, содержащий поток, в котором было создано исключение.</span><span class="sxs-lookup"><span data-stu-id="4c2ab-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="4c2ab-108">окне Указатель на объект ICorDebugThread, представляющий поток, в котором было создано исключение.</span><span class="sxs-lookup"><span data-stu-id="4c2ab-108">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="4c2ab-109">окне Указатель на объект ICorDebugFrame, представляющий кадр, как определено `dwEventType` параметром.</span><span class="sxs-lookup"><span data-stu-id="4c2ab-109">[in] A pointer to an ICorDebugFrame object that represents a frame, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="4c2ab-110">Дополнительные сведения см. в таблице в разделе "Примечания".</span><span class="sxs-lookup"><span data-stu-id="4c2ab-110">For more information, see the table in the Remarks section.</span></span>  
  
 `nOffset`  
 <span data-ttu-id="4c2ab-111">окне Целое число, задающее смещение, определяемое `dwEventType` параметром.</span><span class="sxs-lookup"><span data-stu-id="4c2ab-111">[in] An integer that specifies an offset, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="4c2ab-112">Дополнительные сведения см. в таблице в разделе "Примечания".</span><span class="sxs-lookup"><span data-stu-id="4c2ab-112">For more information, see the table in the Remarks section.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="4c2ab-113">окне Значение перечисления CorDebugExceptionCallbackType, указывающее тип этого обратного вызова исключения.</span><span class="sxs-lookup"><span data-stu-id="4c2ab-113">[in] A value of the CorDebugExceptionCallbackType enumeration that specifies the type of this exception callback.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="4c2ab-114">окне Значение перечисления [кордебужексцептионфлагс](cordebugexceptionflags-enumeration.md) , которое указывает дополнительные сведения об исключении</span><span class="sxs-lookup"><span data-stu-id="4c2ab-114">[in] A value of the [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c2ab-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="4c2ab-115">Remarks</span></span>  

 <span data-ttu-id="4c2ab-116">`Exception`Обратный вызов вызывается в различных точках на этапе поиска процесса обработки исключений.</span><span class="sxs-lookup"><span data-stu-id="4c2ab-116">The `Exception` callback is called at various points during the search phase of the exception-handling process.</span></span> <span data-ttu-id="4c2ab-117">То есть он может быть вызван более одного раза при очистке исключения.</span><span class="sxs-lookup"><span data-stu-id="4c2ab-117">That is, it can be called more than once while unwinding an exception.</span></span>  
  
 <span data-ttu-id="4c2ab-118">Обрабатываемое исключение может быть получено из объекта ICorDebugThread, на который ссылается `pThread` параметр.</span><span class="sxs-lookup"><span data-stu-id="4c2ab-118">The exception being processed can be retrieved from the ICorDebugThread object referenced by the `pThread` parameter.</span></span>  
  
 <span data-ttu-id="4c2ab-119">Конкретный кадр и смещение определяются `dwEventType` параметром следующим образом:</span><span class="sxs-lookup"><span data-stu-id="4c2ab-119">The particular frame and offset are determined by the `dwEventType` parameter as follows:</span></span>  
  
|<span data-ttu-id="4c2ab-120">Значение параметра `dwEventType`</span><span class="sxs-lookup"><span data-stu-id="4c2ab-120">Value of `dwEventType`</span></span>|<span data-ttu-id="4c2ab-121">Значение параметра `pFrame`</span><span class="sxs-lookup"><span data-stu-id="4c2ab-121">Value of `pFrame`</span></span>|<span data-ttu-id="4c2ab-122">Значение параметра `nOffset`</span><span class="sxs-lookup"><span data-stu-id="4c2ab-122">Value of `nOffset`</span></span>|  
|----------------------------|-----------------------|------------------------|  
|<span data-ttu-id="4c2ab-123">DEBUG_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="4c2ab-123">DEBUG_EXCEPTION_FIRST_CHANCE</span></span>|<span data-ttu-id="4c2ab-124">Кадр, вызвавший исключение.</span><span class="sxs-lookup"><span data-stu-id="4c2ab-124">The frame that threw the exception.</span></span>|<span data-ttu-id="4c2ab-125">Указатель инструкции в кадре.</span><span class="sxs-lookup"><span data-stu-id="4c2ab-125">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="4c2ab-126">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="4c2ab-126">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span></span>|<span data-ttu-id="4c2ab-127">Кадр пользовательского кода, ближайший к точке вызванного исключения.</span><span class="sxs-lookup"><span data-stu-id="4c2ab-127">The user-code frame closest to the point of the thrown exception.</span></span>|<span data-ttu-id="4c2ab-128">Указатель инструкции в кадре.</span><span class="sxs-lookup"><span data-stu-id="4c2ab-128">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="4c2ab-129">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="4c2ab-129">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span></span>|<span data-ttu-id="4c2ab-130">Кадр, содержащий обработчик catch.</span><span class="sxs-lookup"><span data-stu-id="4c2ab-130">The frame that contains the catch handler.</span></span>|<span data-ttu-id="4c2ab-131">Смещение на языке MSIL, начинающееся с начала обработчика catch.</span><span class="sxs-lookup"><span data-stu-id="4c2ab-131">The Microsoft intermediate language (MSIL) offset of the beginning of the catch handler.</span></span>|  
|<span data-ttu-id="4c2ab-132">DEBUG_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="4c2ab-132">DEBUG_EXCEPTION_UNHANDLED</span></span>|<span data-ttu-id="4c2ab-133">NULL</span><span class="sxs-lookup"><span data-stu-id="4c2ab-133">NULL</span></span>|<span data-ttu-id="4c2ab-134">Не определено.</span><span class="sxs-lookup"><span data-stu-id="4c2ab-134">Undefined.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4c2ab-135">Требования</span><span class="sxs-lookup"><span data-stu-id="4c2ab-135">Requirements</span></span>  

 <span data-ttu-id="4c2ab-136">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c2ab-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c2ab-137">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4c2ab-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4c2ab-138">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c2ab-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c2ab-139">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c2ab-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c2ab-140">См. также</span><span class="sxs-lookup"><span data-stu-id="4c2ab-140">See also</span></span>

- [<span data-ttu-id="4c2ab-141">Интерфейс ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="4c2ab-141">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="4c2ab-142">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="4c2ab-142">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
