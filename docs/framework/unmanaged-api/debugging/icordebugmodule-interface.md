---
description: 'Дополнительные сведения о: интерфейс ICorDebugModule'
title: Интерфейс ICorDebugModule
ms.date: 03/30/2017
api_name:
- ICorDebugModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule
helpviewer_keywords:
- ICorDebugModule interface [.NET Framework debugging]
ms.assetid: 32e4d6fa-e5a3-413e-9166-d5e2871d3114
topic_type:
- apiref
ms.openlocfilehash: f78023fe9975b609309c1c511380a3a394426283
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660119"
---
# <a name="icordebugmodule-interface"></a><span data-ttu-id="72dec-103">Интерфейс ICorDebugModule</span><span class="sxs-lookup"><span data-stu-id="72dec-103">ICorDebugModule Interface</span></span>

<span data-ttu-id="72dec-104">Представляет модуль среды CLR, который является либо исполняемым файлом, либо библиотекой динамической компоновки (DLL).</span><span class="sxs-lookup"><span data-stu-id="72dec-104">Represents a common language runtime (CLR) module, which is either an executable file or a dynamic-link library (DLL).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="72dec-105">Методы</span><span class="sxs-lookup"><span data-stu-id="72dec-105">Methods</span></span>  
  
|<span data-ttu-id="72dec-106">Метод</span><span class="sxs-lookup"><span data-stu-id="72dec-106">Method</span></span>|<span data-ttu-id="72dec-107">Описание</span><span class="sxs-lookup"><span data-stu-id="72dec-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="72dec-108">Метод CreateBreakpoint</span><span class="sxs-lookup"><span data-stu-id="72dec-108">CreateBreakpoint Method</span></span>](icordebugmodule-createbreakpoint-method.md)|<span data-ttu-id="72dec-109">Не реализован.</span><span class="sxs-lookup"><span data-stu-id="72dec-109">Not implemented.</span></span>|  
|[<span data-ttu-id="72dec-110">Метод EnableClassLoadCallbacks</span><span class="sxs-lookup"><span data-stu-id="72dec-110">EnableClassLoadCallbacks Method</span></span>](icordebugmodule-enableclassloadcallbacks-method.md)|<span data-ttu-id="72dec-111">Определяет, вызываются ли для этого модуля обратные вызовы [ICorDebugManagedCallback:: loadClass](icordebugmanagedcallback-loadclass-method.md) и [ICorDebugManagedCallback:: унлоадкласс](icordebugmanagedcallback-unloadclass-method.md) .</span><span class="sxs-lookup"><span data-stu-id="72dec-111">Determines whether the [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>|  
|[<span data-ttu-id="72dec-112">Метод EnableJITDebugging</span><span class="sxs-lookup"><span data-stu-id="72dec-112">EnableJITDebugging Method</span></span>](icordebugmodule-enablejitdebugging-method.md)|<span data-ttu-id="72dec-113">Определяет, будет ли JIT-компилятор сохранить отладочную информацию для методов в этом модуле.</span><span class="sxs-lookup"><span data-stu-id="72dec-113">Determines whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>|  
|[<span data-ttu-id="72dec-114">Метод GetAssembly</span><span class="sxs-lookup"><span data-stu-id="72dec-114">GetAssembly Method</span></span>](icordebugmodule-getassembly-method.md)|<span data-ttu-id="72dec-115">Возвращает содержащуюся сборку для этого модуля.</span><span class="sxs-lookup"><span data-stu-id="72dec-115">Gets the containing assembly for this module.</span></span>|  
|[<span data-ttu-id="72dec-116">Метод GetBaseAddress</span><span class="sxs-lookup"><span data-stu-id="72dec-116">GetBaseAddress Method</span></span>](icordebugmodule-getbaseaddress-method.md)|<span data-ttu-id="72dec-117">Возвращает базовый адрес модуля.</span><span class="sxs-lookup"><span data-stu-id="72dec-117">Gets the base address of the module.</span></span>|  
|[<span data-ttu-id="72dec-118">Метод GetClassFromToken</span><span class="sxs-lookup"><span data-stu-id="72dec-118">GetClassFromToken Method</span></span>](icordebugmodule-getclassfromtoken-method.md)|<span data-ttu-id="72dec-119">Возвращает ICorDebugClass из метаданных.</span><span class="sxs-lookup"><span data-stu-id="72dec-119">Gets the ICorDebugClass from the metadata.</span></span>|  
|[<span data-ttu-id="72dec-120">Метод GetEditAndContinueSnapshot</span><span class="sxs-lookup"><span data-stu-id="72dec-120">GetEditAndContinueSnapshot Method</span></span>](icordebugmodule-geteditandcontinuesnapshot-method.md)|<span data-ttu-id="72dec-121">Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="72dec-121">Deprecated.</span></span>|  
|[<span data-ttu-id="72dec-122">Метод GetFunctionFromRVA</span><span class="sxs-lookup"><span data-stu-id="72dec-122">GetFunctionFromRVA Method</span></span>](icordebugmodule-getfunctionfromrva-method.md)|<span data-ttu-id="72dec-123">Не реализован.</span><span class="sxs-lookup"><span data-stu-id="72dec-123">Not implemented.</span></span>|  
|[<span data-ttu-id="72dec-124">Метод GetFunctionFromToken</span><span class="sxs-lookup"><span data-stu-id="72dec-124">GetFunctionFromToken Method</span></span>](icordebugmodule-getfunctionfromtoken-method.md)|<span data-ttu-id="72dec-125">Возвращает функцию, заданную маркером метаданных.</span><span class="sxs-lookup"><span data-stu-id="72dec-125">Gets the function that is specified by the metadata token.</span></span>|  
|[<span data-ttu-id="72dec-126">Метод GetGlobalVariableValue</span><span class="sxs-lookup"><span data-stu-id="72dec-126">GetGlobalVariableValue Method</span></span>](icordebugmodule-getglobalvariablevalue-method.md)|<span data-ttu-id="72dec-127">Возвращает объект значения для указанной глобальной переменной.</span><span class="sxs-lookup"><span data-stu-id="72dec-127">Gets a value object for the specified global variable.</span></span>|  
|[<span data-ttu-id="72dec-128">Метод GetMetaDataInterface</span><span class="sxs-lookup"><span data-stu-id="72dec-128">GetMetaDataInterface Method</span></span>](icordebugmodule-getmetadatainterface-method.md)|<span data-ttu-id="72dec-129">Возвращает указатель интерфейса метаданных, который может использоваться для проверки метаданных модуля.</span><span class="sxs-lookup"><span data-stu-id="72dec-129">Gets a metadata interface pointer that can be used to examine the metadata for the module.</span></span>|  
|[<span data-ttu-id="72dec-130">Метод GetName</span><span class="sxs-lookup"><span data-stu-id="72dec-130">GetName Method</span></span>](icordebugmodule-getname-method.md)|<span data-ttu-id="72dec-131">Возвращает имя файла модуля.</span><span class="sxs-lookup"><span data-stu-id="72dec-131">Gets the file name of the module.</span></span>|  
|[<span data-ttu-id="72dec-132">Метод GetProcess</span><span class="sxs-lookup"><span data-stu-id="72dec-132">GetProcess Method</span></span>](icordebugmodule-getprocess-method.md)|<span data-ttu-id="72dec-133">Возвращает содержащий процесс для этого модуля.</span><span class="sxs-lookup"><span data-stu-id="72dec-133">Gets the containing process for this module.</span></span>|  
|[<span data-ttu-id="72dec-134">Метод GetSize</span><span class="sxs-lookup"><span data-stu-id="72dec-134">GetSize Method</span></span>](icordebugmodule-getsize-method.md)|<span data-ttu-id="72dec-135">Возвращает размер модуля в байтах.</span><span class="sxs-lookup"><span data-stu-id="72dec-135">Gets the size of the module in bytes.</span></span>|  
|[<span data-ttu-id="72dec-136">Метод GetToken</span><span class="sxs-lookup"><span data-stu-id="72dec-136">GetToken Method</span></span>](icordebugmodule-gettoken-method.md)|<span data-ttu-id="72dec-137">Возвращает маркер для записи таблицы для этого модуля.</span><span class="sxs-lookup"><span data-stu-id="72dec-137">Gets the token for the table entry for this module.</span></span>|  
|[<span data-ttu-id="72dec-138">Метод IsDynamic</span><span class="sxs-lookup"><span data-stu-id="72dec-138">IsDynamic Method</span></span>](icordebugmodule-isdynamic-method.md)|<span data-ttu-id="72dec-139">Указывает, является ли модуль динамическим.</span><span class="sxs-lookup"><span data-stu-id="72dec-139">Indicates whether the module is dynamic.</span></span>|  
|[<span data-ttu-id="72dec-140">Метод IsInMemory</span><span class="sxs-lookup"><span data-stu-id="72dec-140">IsInMemory Method</span></span>](icordebugmodule-isinmemory-method.md)|<span data-ttu-id="72dec-141">Указывает, существует ли этот модуль только в памяти.</span><span class="sxs-lookup"><span data-stu-id="72dec-141">Indicates whether this module exists only in memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72dec-142">Remarks</span><span class="sxs-lookup"><span data-stu-id="72dec-142">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="72dec-143">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="72dec-143">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72dec-144">Требования</span><span class="sxs-lookup"><span data-stu-id="72dec-144">Requirements</span></span>  

 <span data-ttu-id="72dec-145">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72dec-145">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72dec-146">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="72dec-146">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72dec-147">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72dec-147">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72dec-148">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72dec-148">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72dec-149">См. также</span><span class="sxs-lookup"><span data-stu-id="72dec-149">See also</span></span>

- [<span data-ttu-id="72dec-150">Интерфейс ICorDebug</span><span class="sxs-lookup"><span data-stu-id="72dec-150">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="72dec-151">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="72dec-151">Debugging Interfaces</span></span>](debugging-interfaces.md)
