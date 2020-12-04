---
title: События времени выполнения исключения
description: См. события среды выполнения .NET, собирающие диагностическую информацию, относящуюся к исключениям и обработке исключений.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- exception events (CoreCLR)
- exception handling events (CoreCLR)
- ETW, EventPipe, LTTng exception events (CoreCLR)
ms.openlocfilehash: f4f63c8469f9c734b872ddaec8d1d7f7f0427576
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96594104"
---
# <a name="net-runtime-exception-events"></a><span data-ttu-id="aaed6-103">События исключения среды выполнения .NET</span><span class="sxs-lookup"><span data-stu-id="aaed6-103">.NET runtime exception events</span></span>

<span data-ttu-id="aaed6-104">Эти события времени выполнения захватывают сведения о возникших исключениях.</span><span class="sxs-lookup"><span data-stu-id="aaed6-104">These runtime events capture information about exceptions that are thrown.</span></span> <span data-ttu-id="aaed6-105">Дополнительные сведения об использовании этих событий в целях диагностики см. в разделе [ведение журнала и трассировка приложений .NET](../../core/diagnostics/logging-tracing.md) .</span><span class="sxs-lookup"><span data-stu-id="aaed6-105">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="exceptionthrown_v1-event"></a><span data-ttu-id="aaed6-106">ExceptionThrown_V1 событие</span><span class="sxs-lookup"><span data-stu-id="aaed6-106">ExceptionThrown_V1 event</span></span>

|<span data-ttu-id="aaed6-107">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="aaed6-107">Keyword for raising the event</span></span>|<span data-ttu-id="aaed6-108">Level</span><span class="sxs-lookup"><span data-stu-id="aaed6-108">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="aaed6-109">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="aaed6-109">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="aaed6-110">Ошибка (1)</span><span class="sxs-lookup"><span data-stu-id="aaed6-110">Error (1)</span></span>|

 <span data-ttu-id="aaed6-111">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="aaed6-111">The following table shows event information.</span></span>

|<span data-ttu-id="aaed6-112">Событие</span><span class="sxs-lookup"><span data-stu-id="aaed6-112">Event</span></span>|<span data-ttu-id="aaed6-113">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="aaed6-113">Event ID</span></span>|<span data-ttu-id="aaed6-114">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="aaed6-114">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionThrown_V1`|<span data-ttu-id="aaed6-115">80</span><span class="sxs-lookup"><span data-stu-id="aaed6-115">80</span></span>|<span data-ttu-id="aaed6-116">Возникло управляемое исключение.</span><span class="sxs-lookup"><span data-stu-id="aaed6-116">A managed exception is thrown.</span></span>|

|<span data-ttu-id="aaed6-117">Имя поля</span><span class="sxs-lookup"><span data-stu-id="aaed6-117">Field name</span></span>|<span data-ttu-id="aaed6-118">Тип данных</span><span class="sxs-lookup"><span data-stu-id="aaed6-118">Data type</span></span>|<span data-ttu-id="aaed6-119">Описание</span><span class="sxs-lookup"><span data-stu-id="aaed6-119">Description</span></span>|
|----------------|---------------|-----------------|
|`ExceptionType`|`win:UnicodeString`|<span data-ttu-id="aaed6-120">Тип исключения, например `System.NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="aaed6-120">Type of the exception; for example, `System.NullReferenceException`.</span></span>|
|`ExceptionMessage`|`win:UnicodeString`|<span data-ttu-id="aaed6-121">Фактическое сообщение об исключении.</span><span class="sxs-lookup"><span data-stu-id="aaed6-121">Actual exception message.</span></span>|
|`EIPCodeThrow`|`win:Pointer`|<span data-ttu-id="aaed6-122">Указатель на инструкцию, в которой возникло исключение.</span><span class="sxs-lookup"><span data-stu-id="aaed6-122">Instruction pointer where exception occurred.</span></span>|
|`ExceptionHR`|`win:UInt32`|<span data-ttu-id="aaed6-123">Исключение [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span><span class="sxs-lookup"><span data-stu-id="aaed6-123">Exception [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span></span>|
|`ExceptionFlags`|`win:UInt16`|<span data-ttu-id="aaed6-124">`0x01`: Хасиннерексцептион.</span><span class="sxs-lookup"><span data-stu-id="aaed6-124">`0x01`: HasInnerException.</span></span><br /><br /> <span data-ttu-id="aaed6-125">`0x02`: Иснестедексцептион.</span><span class="sxs-lookup"><span data-stu-id="aaed6-125">`0x02`: IsNestedException.</span></span><br /><br /> <span data-ttu-id="aaed6-126">`0x04`: Исресровнексцептион.</span><span class="sxs-lookup"><span data-stu-id="aaed6-126">`0x04`: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="aaed6-127">`0x08`: Искорруптедстатиксцептион (указывает, что состояние процесса повреждено; см. раздел [обработка исключений поврежденного состояния](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span><span class="sxs-lookup"><span data-stu-id="aaed6-127">`0x08`: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span></span><br /><br /> <span data-ttu-id="aaed6-128">`0x10`: Исклскомплиант (исключение, производное от <xref:System.Exception> , является CLS-совместимым; в противном случае оно не совместимо с CLS).</span><span class="sxs-lookup"><span data-stu-id="aaed6-128">`0x10`: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="aaed6-129">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="aaed6-129">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="exceptioncatchstart-event"></a><span data-ttu-id="aaed6-130">Событие Ексцептионкатчстарт</span><span class="sxs-lookup"><span data-stu-id="aaed6-130">ExceptionCatchStart event</span></span>

<span data-ttu-id="aaed6-131">Это событие создается при начале управляемого обработчика перехвата исключений.</span><span class="sxs-lookup"><span data-stu-id="aaed6-131">This event is emitted when a managed exception catch handler begins.</span></span>

|<span data-ttu-id="aaed6-132">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="aaed6-132">Keyword for raising the event</span></span>|<span data-ttu-id="aaed6-133">Level</span><span class="sxs-lookup"><span data-stu-id="aaed6-133">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="aaed6-134">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="aaed6-134">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="aaed6-135">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="aaed6-135">Informational (4)</span></span>|

 <span data-ttu-id="aaed6-136">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="aaed6-136">The following table shows event information.</span></span>

|<span data-ttu-id="aaed6-137">Событие</span><span class="sxs-lookup"><span data-stu-id="aaed6-137">Event</span></span>|<span data-ttu-id="aaed6-138">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="aaed6-138">Event ID</span></span>|<span data-ttu-id="aaed6-139">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="aaed6-139">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionCatchStart`|<span data-ttu-id="aaed6-140">250</span><span class="sxs-lookup"><span data-stu-id="aaed6-140">250</span></span>|<span data-ttu-id="aaed6-141">Управляемое исключение обрабатывается средой выполнения.</span><span class="sxs-lookup"><span data-stu-id="aaed6-141">A managed exception is handled by the runtime.</span></span>|

|<span data-ttu-id="aaed6-142">Имя поля</span><span class="sxs-lookup"><span data-stu-id="aaed6-142">Field name</span></span>|<span data-ttu-id="aaed6-143">Тип данных</span><span class="sxs-lookup"><span data-stu-id="aaed6-143">Data type</span></span>|<span data-ttu-id="aaed6-144">Описание</span><span class="sxs-lookup"><span data-stu-id="aaed6-144">Description</span></span>|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|<span data-ttu-id="aaed6-145">Указатель на инструкцию, в которой возникло исключение.</span><span class="sxs-lookup"><span data-stu-id="aaed6-145">Instruction pointer where exception occurred.</span></span>|
|`MethodID`|`win:Pointer`|<span data-ttu-id="aaed6-146">Указатель на дескриптор метода в методе, где возникло исключение.</span><span class="sxs-lookup"><span data-stu-id="aaed6-146">Pointer to the method descriptor on the method where exception occurred.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="aaed6-147">Имя метода, где возникло исключение.</span><span class="sxs-lookup"><span data-stu-id="aaed6-147">Name of the method where exception occurred.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="aaed6-148">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="aaed6-148">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="exceptioncatchstop-event"></a><span data-ttu-id="aaed6-149">Событие Ексцептионкатчстоп</span><span class="sxs-lookup"><span data-stu-id="aaed6-149">ExceptionCatchStop event</span></span>

<span data-ttu-id="aaed6-150">Это событие создается при завершении управляемого обработчика перехвата исключений.</span><span class="sxs-lookup"><span data-stu-id="aaed6-150">This event is emitted when a managed exception catch handler ends.</span></span>

|<span data-ttu-id="aaed6-151">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="aaed6-151">Keyword for raising the event</span></span>|<span data-ttu-id="aaed6-152">Level</span><span class="sxs-lookup"><span data-stu-id="aaed6-152">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="aaed6-153">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="aaed6-153">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="aaed6-154">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="aaed6-154">Informational (4)</span></span>|

 <span data-ttu-id="aaed6-155">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="aaed6-155">The following table shows event information.</span></span>

|<span data-ttu-id="aaed6-156">Событие</span><span class="sxs-lookup"><span data-stu-id="aaed6-156">Event</span></span>|<span data-ttu-id="aaed6-157">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="aaed6-157">Event ID</span></span>|<span data-ttu-id="aaed6-158">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="aaed6-158">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionCatchStop`|<span data-ttu-id="aaed6-159">251</span><span class="sxs-lookup"><span data-stu-id="aaed6-159">251</span></span>|<span data-ttu-id="aaed6-160">Управляемый обработчик перехвата исключений выполнен.</span><span class="sxs-lookup"><span data-stu-id="aaed6-160">A managed exception catch handler is done.</span></span>|

## <a name="exceptionfinallystart-event"></a><span data-ttu-id="aaed6-161">Событие Ексцептионфиналлистарт</span><span class="sxs-lookup"><span data-stu-id="aaed6-161">ExceptionFinallyStart event</span></span>

<span data-ttu-id="aaed6-162">Это событие создается при запуске обработчика finally управляемого исключения.</span><span class="sxs-lookup"><span data-stu-id="aaed6-162">This event is emitted when a managed exception finally handler begins.</span></span>

|<span data-ttu-id="aaed6-163">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="aaed6-163">Keyword for raising the event</span></span>|<span data-ttu-id="aaed6-164">Level</span><span class="sxs-lookup"><span data-stu-id="aaed6-164">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="aaed6-165">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="aaed6-165">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="aaed6-166">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="aaed6-166">Informational (4)</span></span>|

 <span data-ttu-id="aaed6-167">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="aaed6-167">The following table shows event information.</span></span>

|<span data-ttu-id="aaed6-168">Событие</span><span class="sxs-lookup"><span data-stu-id="aaed6-168">Event</span></span>|<span data-ttu-id="aaed6-169">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="aaed6-169">Event ID</span></span>|<span data-ttu-id="aaed6-170">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="aaed6-170">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionFinallyStart`|<span data-ttu-id="aaed6-171">252</span><span class="sxs-lookup"><span data-stu-id="aaed6-171">252</span></span>|<span data-ttu-id="aaed6-172">Управляемое исключение обрабатывается средой выполнения.</span><span class="sxs-lookup"><span data-stu-id="aaed6-172">A managed exception is handled by the runtime.</span></span>|

|<span data-ttu-id="aaed6-173">Имя поля</span><span class="sxs-lookup"><span data-stu-id="aaed6-173">Field name</span></span>|<span data-ttu-id="aaed6-174">Тип данных</span><span class="sxs-lookup"><span data-stu-id="aaed6-174">Data type</span></span>|<span data-ttu-id="aaed6-175">Описание</span><span class="sxs-lookup"><span data-stu-id="aaed6-175">Description</span></span>|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|<span data-ttu-id="aaed6-176">Указатель на инструкцию, в которой возникло исключение.</span><span class="sxs-lookup"><span data-stu-id="aaed6-176">Instruction pointer where exception occurred.</span></span>|
|`MethodID`|`win:Pointer`|<span data-ttu-id="aaed6-177">Указатель на дескриптор метода в методе, где возникло исключение.</span><span class="sxs-lookup"><span data-stu-id="aaed6-177">Pointer to the method descriptor on the method where exception occurred.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="aaed6-178">Имя метода, где возникло исключение.</span><span class="sxs-lookup"><span data-stu-id="aaed6-178">Name of the method where exception occurred.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="aaed6-179">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="aaed6-179">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="exceptionfinallystop-event"></a><span data-ttu-id="aaed6-180">Событие Ексцептионфиналлистоп</span><span class="sxs-lookup"><span data-stu-id="aaed6-180">ExceptionFinallyStop event</span></span>

<span data-ttu-id="aaed6-181">Это событие создается при завершении управляемого обработчика перехвата исключений.</span><span class="sxs-lookup"><span data-stu-id="aaed6-181">This event is emitted when a managed exception catch handler ends.</span></span>

|<span data-ttu-id="aaed6-182">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="aaed6-182">Keyword for raising the event</span></span>|<span data-ttu-id="aaed6-183">Level</span><span class="sxs-lookup"><span data-stu-id="aaed6-183">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="aaed6-184">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="aaed6-184">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="aaed6-185">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="aaed6-185">Informational (4)</span></span>|

 <span data-ttu-id="aaed6-186">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="aaed6-186">The following table shows event information.</span></span>

|<span data-ttu-id="aaed6-187">Событие</span><span class="sxs-lookup"><span data-stu-id="aaed6-187">Event</span></span>|<span data-ttu-id="aaed6-188">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="aaed6-188">Event ID</span></span>|<span data-ttu-id="aaed6-189">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="aaed6-189">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionFinallyStop`|<span data-ttu-id="aaed6-190">253</span><span class="sxs-lookup"><span data-stu-id="aaed6-190">253</span></span>|<span data-ttu-id="aaed6-191">Обработчик finally управляемого исключения завершен.</span><span class="sxs-lookup"><span data-stu-id="aaed6-191">A managed exception finally handler is done.</span></span>|

## <a name="exceptionfilterstart-event"></a><span data-ttu-id="aaed6-192">Событие Ексцептионфилтерстарт</span><span class="sxs-lookup"><span data-stu-id="aaed6-192">ExceptionFilterStart event</span></span>

<span data-ttu-id="aaed6-193">Это событие создается, когда начинается фильтрация управляемого исключения.</span><span class="sxs-lookup"><span data-stu-id="aaed6-193">This event is emitted when a managed exception filtering begins.</span></span>

|<span data-ttu-id="aaed6-194">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="aaed6-194">Keyword for raising the event</span></span>|<span data-ttu-id="aaed6-195">Level</span><span class="sxs-lookup"><span data-stu-id="aaed6-195">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="aaed6-196">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="aaed6-196">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="aaed6-197">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="aaed6-197">Informational (4)</span></span>|

 <span data-ttu-id="aaed6-198">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="aaed6-198">The following table shows event information.</span></span>

|<span data-ttu-id="aaed6-199">Событие</span><span class="sxs-lookup"><span data-stu-id="aaed6-199">Event</span></span>|<span data-ttu-id="aaed6-200">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="aaed6-200">Event ID</span></span>|<span data-ttu-id="aaed6-201">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="aaed6-201">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionFilterStart`|<span data-ttu-id="aaed6-202">254</span><span class="sxs-lookup"><span data-stu-id="aaed6-202">254</span></span>|<span data-ttu-id="aaed6-203">Начинается фильтрация управляемого исключения.</span><span class="sxs-lookup"><span data-stu-id="aaed6-203">A managed exception filtering begins.</span></span>|

|<span data-ttu-id="aaed6-204">Имя поля</span><span class="sxs-lookup"><span data-stu-id="aaed6-204">Field name</span></span>|<span data-ttu-id="aaed6-205">Тип данных</span><span class="sxs-lookup"><span data-stu-id="aaed6-205">Data type</span></span>|<span data-ttu-id="aaed6-206">Описание</span><span class="sxs-lookup"><span data-stu-id="aaed6-206">Description</span></span>|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|<span data-ttu-id="aaed6-207">Указатель на инструкцию, в которой возникло исключение.</span><span class="sxs-lookup"><span data-stu-id="aaed6-207">Instruction pointer where exception occurred.</span></span>|
|`MethodID`|`win:Pointer`|<span data-ttu-id="aaed6-208">Указатель на дескриптор метода в методе, где возникло исключение.</span><span class="sxs-lookup"><span data-stu-id="aaed6-208">Pointer to the method descriptor on the method where exception occurred.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="aaed6-209">Имя метода, где возникло исключение.</span><span class="sxs-lookup"><span data-stu-id="aaed6-209">Name of the method where exception occurred.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="aaed6-210">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="aaed6-210">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="exceptionfilterstop-event"></a><span data-ttu-id="aaed6-211">Событие Ексцептионфилтерстоп</span><span class="sxs-lookup"><span data-stu-id="aaed6-211">ExceptionFilterStop event</span></span>

<span data-ttu-id="aaed6-212">Это событие создается при завершении фильтрации управляемого исключения.</span><span class="sxs-lookup"><span data-stu-id="aaed6-212">This event is emitted when a managed exception filtering ends.</span></span>

|<span data-ttu-id="aaed6-213">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="aaed6-213">Keyword for raising the event</span></span>|<span data-ttu-id="aaed6-214">Level</span><span class="sxs-lookup"><span data-stu-id="aaed6-214">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="aaed6-215">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="aaed6-215">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="aaed6-216">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="aaed6-216">Informational (4)</span></span>|

 <span data-ttu-id="aaed6-217">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="aaed6-217">The following table shows event information.</span></span>

|<span data-ttu-id="aaed6-218">Событие</span><span class="sxs-lookup"><span data-stu-id="aaed6-218">Event</span></span>|<span data-ttu-id="aaed6-219">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="aaed6-219">Event ID</span></span>|<span data-ttu-id="aaed6-220">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="aaed6-220">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionFilteringStart`|<span data-ttu-id="aaed6-221">255</span><span class="sxs-lookup"><span data-stu-id="aaed6-221">255</span></span>|<span data-ttu-id="aaed6-222">Завершение фильтрации управляемого исключения.</span><span class="sxs-lookup"><span data-stu-id="aaed6-222">A managed exception filtering ends.</span></span>|

## <a name="exceptionthrownstop-event"></a><span data-ttu-id="aaed6-223">Событие Ексцептионсровнстоп</span><span class="sxs-lookup"><span data-stu-id="aaed6-223">ExceptionThrownStop event</span></span>

<span data-ttu-id="aaed6-224">Это событие создается, когда среда выполнения обрабатывает созданное управляемое исключение.</span><span class="sxs-lookup"><span data-stu-id="aaed6-224">This event is emitted when the runtime is done handling a managed exception that was thrown.</span></span>

|<span data-ttu-id="aaed6-225">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="aaed6-225">Keyword for raising the event</span></span>|<span data-ttu-id="aaed6-226">Level</span><span class="sxs-lookup"><span data-stu-id="aaed6-226">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="aaed6-227">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="aaed6-227">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="aaed6-228">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="aaed6-228">Informational (4)</span></span>|
  
 <span data-ttu-id="aaed6-229">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="aaed6-229">The following table shows event information.</span></span>

|<span data-ttu-id="aaed6-230">Событие</span><span class="sxs-lookup"><span data-stu-id="aaed6-230">Event</span></span>|<span data-ttu-id="aaed6-231">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="aaed6-231">Event ID</span></span>|<span data-ttu-id="aaed6-232">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="aaed6-232">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionThrownStop`|<span data-ttu-id="aaed6-233">256</span><span class="sxs-lookup"><span data-stu-id="aaed6-233">256</span></span>|<span data-ttu-id="aaed6-234">Завершение фильтрации управляемого исключения.</span><span class="sxs-lookup"><span data-stu-id="aaed6-234">A managed exception filtering ends.</span></span>|
