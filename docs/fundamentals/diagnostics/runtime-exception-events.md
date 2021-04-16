---
title: События исключения среды выполнения
description: Сведения о событиях среды выполнения .NET, собирающих диагностическую информацию, относящуюся к исключениям и обработке исключений.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- exception events (CoreCLR)
- exception handling events (CoreCLR)
- ETW, EventPipe, LTTng exception events (CoreCLR)
ms.openlocfilehash: f4f63c8469f9c734b872ddaec8d1d7f7f0427576
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "96594104"
---
# <a name="net-runtime-exception-events"></a><span data-ttu-id="74065-103">События исключения среды выполнения .NET</span><span class="sxs-lookup"><span data-stu-id="74065-103">.NET runtime exception events</span></span>

<span data-ttu-id="74065-104">Эти события среды выполнения собирают сведения о возникших исключениях.</span><span class="sxs-lookup"><span data-stu-id="74065-104">These runtime events capture information about exceptions that are thrown.</span></span> <span data-ttu-id="74065-105">Дополнительные сведения об использовании этих событий в целях диагностики см. в статье [Ведение журнала и трассировка в приложениях .NET](../../core/diagnostics/logging-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="74065-105">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="exceptionthrown_v1-event"></a><span data-ttu-id="74065-106">Событие ExceptionThrown_V1</span><span class="sxs-lookup"><span data-stu-id="74065-106">ExceptionThrown_V1 event</span></span>

|<span data-ttu-id="74065-107">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="74065-107">Keyword for raising the event</span></span>|<span data-ttu-id="74065-108">Level</span><span class="sxs-lookup"><span data-stu-id="74065-108">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="74065-109">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="74065-109">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="74065-110">Ошибка (1)</span><span class="sxs-lookup"><span data-stu-id="74065-110">Error (1)</span></span>|

 <span data-ttu-id="74065-111">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="74065-111">The following table shows event information.</span></span>

|<span data-ttu-id="74065-112">Событие</span><span class="sxs-lookup"><span data-stu-id="74065-112">Event</span></span>|<span data-ttu-id="74065-113">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="74065-113">Event ID</span></span>|<span data-ttu-id="74065-114">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="74065-114">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionThrown_V1`|<span data-ttu-id="74065-115">80</span><span class="sxs-lookup"><span data-stu-id="74065-115">80</span></span>|<span data-ttu-id="74065-116">Возникло управляемое исключение.</span><span class="sxs-lookup"><span data-stu-id="74065-116">A managed exception is thrown.</span></span>|

|<span data-ttu-id="74065-117">Имя поля</span><span class="sxs-lookup"><span data-stu-id="74065-117">Field name</span></span>|<span data-ttu-id="74065-118">Тип данных</span><span class="sxs-lookup"><span data-stu-id="74065-118">Data type</span></span>|<span data-ttu-id="74065-119">Описание</span><span class="sxs-lookup"><span data-stu-id="74065-119">Description</span></span>|
|----------------|---------------|-----------------|
|`ExceptionType`|`win:UnicodeString`|<span data-ttu-id="74065-120">Тип исключения, например `System.NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="74065-120">Type of the exception; for example, `System.NullReferenceException`.</span></span>|
|`ExceptionMessage`|`win:UnicodeString`|<span data-ttu-id="74065-121">Фактическое сообщение об исключении.</span><span class="sxs-lookup"><span data-stu-id="74065-121">Actual exception message.</span></span>|
|`EIPCodeThrow`|`win:Pointer`|<span data-ttu-id="74065-122">Указатель на инструкцию, в которой возникло исключение.</span><span class="sxs-lookup"><span data-stu-id="74065-122">Instruction pointer where exception occurred.</span></span>|
|`ExceptionHR`|`win:UInt32`|<span data-ttu-id="74065-123">Исключение [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span><span class="sxs-lookup"><span data-stu-id="74065-123">Exception [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span></span>|
|`ExceptionFlags`|`win:UInt16`|<span data-ttu-id="74065-124">`0x01`: HasInnerException.</span><span class="sxs-lookup"><span data-stu-id="74065-124">`0x01`: HasInnerException.</span></span><br /><br /> <span data-ttu-id="74065-125">`0x02`: IsNestedException.</span><span class="sxs-lookup"><span data-stu-id="74065-125">`0x02`: IsNestedException.</span></span><br /><br /> <span data-ttu-id="74065-126">`0x04`: IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="74065-126">`0x04`: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="74065-127">`0x08`: IsCorruptedStateException (указывает, что процесс находится в поврежденном состоянии, см. раздел [Обработка исключений поврежденного состояния](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span><span class="sxs-lookup"><span data-stu-id="74065-127">`0x08`: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span></span><br /><br /> <span data-ttu-id="74065-128">`0x10`: IsCLSCompliant (исключение, производное от <xref:System.Exception>, является CLS-совместимым; в противном случае такое исключение не является CLS-совместимым).</span><span class="sxs-lookup"><span data-stu-id="74065-128">`0x10`: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="74065-129">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="74065-129">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="exceptioncatchstart-event"></a><span data-ttu-id="74065-130">Событие ExceptionCatchStart</span><span class="sxs-lookup"><span data-stu-id="74065-130">ExceptionCatchStart event</span></span>

<span data-ttu-id="74065-131">Это событие возникает при запуске обработчика перехвата управляемых исключений.</span><span class="sxs-lookup"><span data-stu-id="74065-131">This event is emitted when a managed exception catch handler begins.</span></span>

|<span data-ttu-id="74065-132">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="74065-132">Keyword for raising the event</span></span>|<span data-ttu-id="74065-133">Level</span><span class="sxs-lookup"><span data-stu-id="74065-133">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="74065-134">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="74065-134">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="74065-135">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="74065-135">Informational (4)</span></span>|

 <span data-ttu-id="74065-136">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="74065-136">The following table shows event information.</span></span>

|<span data-ttu-id="74065-137">Событие</span><span class="sxs-lookup"><span data-stu-id="74065-137">Event</span></span>|<span data-ttu-id="74065-138">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="74065-138">Event ID</span></span>|<span data-ttu-id="74065-139">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="74065-139">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionCatchStart`|<span data-ttu-id="74065-140">250</span><span class="sxs-lookup"><span data-stu-id="74065-140">250</span></span>|<span data-ttu-id="74065-141">Управляемое исключение обрабатывается средой выполнения.</span><span class="sxs-lookup"><span data-stu-id="74065-141">A managed exception is handled by the runtime.</span></span>|

|<span data-ttu-id="74065-142">Имя поля</span><span class="sxs-lookup"><span data-stu-id="74065-142">Field name</span></span>|<span data-ttu-id="74065-143">Тип данных</span><span class="sxs-lookup"><span data-stu-id="74065-143">Data type</span></span>|<span data-ttu-id="74065-144">Описание</span><span class="sxs-lookup"><span data-stu-id="74065-144">Description</span></span>|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|<span data-ttu-id="74065-145">Указатель на инструкцию, в которой возникло исключение.</span><span class="sxs-lookup"><span data-stu-id="74065-145">Instruction pointer where exception occurred.</span></span>|
|`MethodID`|`win:Pointer`|<span data-ttu-id="74065-146">Указатель на дескриптор метода в методе, где возникло исключение.</span><span class="sxs-lookup"><span data-stu-id="74065-146">Pointer to the method descriptor on the method where exception occurred.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="74065-147">Имя метода, где возникло исключение.</span><span class="sxs-lookup"><span data-stu-id="74065-147">Name of the method where exception occurred.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="74065-148">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="74065-148">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="exceptioncatchstop-event"></a><span data-ttu-id="74065-149">Событие ExceptionCatchStop</span><span class="sxs-lookup"><span data-stu-id="74065-149">ExceptionCatchStop event</span></span>

<span data-ttu-id="74065-150">Это событие возникает при завершении работы обработчика перехвата управляемых исключений.</span><span class="sxs-lookup"><span data-stu-id="74065-150">This event is emitted when a managed exception catch handler ends.</span></span>

|<span data-ttu-id="74065-151">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="74065-151">Keyword for raising the event</span></span>|<span data-ttu-id="74065-152">Level</span><span class="sxs-lookup"><span data-stu-id="74065-152">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="74065-153">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="74065-153">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="74065-154">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="74065-154">Informational (4)</span></span>|

 <span data-ttu-id="74065-155">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="74065-155">The following table shows event information.</span></span>

|<span data-ttu-id="74065-156">Событие</span><span class="sxs-lookup"><span data-stu-id="74065-156">Event</span></span>|<span data-ttu-id="74065-157">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="74065-157">Event ID</span></span>|<span data-ttu-id="74065-158">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="74065-158">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionCatchStop`|<span data-ttu-id="74065-159">251</span><span class="sxs-lookup"><span data-stu-id="74065-159">251</span></span>|<span data-ttu-id="74065-160">Работа обработчика перехвата управляемых исключений завершена.</span><span class="sxs-lookup"><span data-stu-id="74065-160">A managed exception catch handler is done.</span></span>|

## <a name="exceptionfinallystart-event"></a><span data-ttu-id="74065-161">Событие ExceptionFinallyStart</span><span class="sxs-lookup"><span data-stu-id="74065-161">ExceptionFinallyStart event</span></span>

<span data-ttu-id="74065-162">Это событие возникает при окончательном запуске обработчика перехвата управляемых исключений.</span><span class="sxs-lookup"><span data-stu-id="74065-162">This event is emitted when a managed exception finally handler begins.</span></span>

|<span data-ttu-id="74065-163">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="74065-163">Keyword for raising the event</span></span>|<span data-ttu-id="74065-164">Level</span><span class="sxs-lookup"><span data-stu-id="74065-164">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="74065-165">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="74065-165">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="74065-166">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="74065-166">Informational (4)</span></span>|

 <span data-ttu-id="74065-167">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="74065-167">The following table shows event information.</span></span>

|<span data-ttu-id="74065-168">Событие</span><span class="sxs-lookup"><span data-stu-id="74065-168">Event</span></span>|<span data-ttu-id="74065-169">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="74065-169">Event ID</span></span>|<span data-ttu-id="74065-170">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="74065-170">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionFinallyStart`|<span data-ttu-id="74065-171">252</span><span class="sxs-lookup"><span data-stu-id="74065-171">252</span></span>|<span data-ttu-id="74065-172">Управляемое исключение обрабатывается средой выполнения.</span><span class="sxs-lookup"><span data-stu-id="74065-172">A managed exception is handled by the runtime.</span></span>|

|<span data-ttu-id="74065-173">Имя поля</span><span class="sxs-lookup"><span data-stu-id="74065-173">Field name</span></span>|<span data-ttu-id="74065-174">Тип данных</span><span class="sxs-lookup"><span data-stu-id="74065-174">Data type</span></span>|<span data-ttu-id="74065-175">Описание</span><span class="sxs-lookup"><span data-stu-id="74065-175">Description</span></span>|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|<span data-ttu-id="74065-176">Указатель на инструкцию, в которой возникло исключение.</span><span class="sxs-lookup"><span data-stu-id="74065-176">Instruction pointer where exception occurred.</span></span>|
|`MethodID`|`win:Pointer`|<span data-ttu-id="74065-177">Указатель на дескриптор метода в методе, где возникло исключение.</span><span class="sxs-lookup"><span data-stu-id="74065-177">Pointer to the method descriptor on the method where exception occurred.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="74065-178">Имя метода, где возникло исключение.</span><span class="sxs-lookup"><span data-stu-id="74065-178">Name of the method where exception occurred.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="74065-179">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="74065-179">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="exceptionfinallystop-event"></a><span data-ttu-id="74065-180">Событие ExceptionFinallyStop</span><span class="sxs-lookup"><span data-stu-id="74065-180">ExceptionFinallyStop event</span></span>

<span data-ttu-id="74065-181">Это событие возникает при завершении работы обработчика перехвата управляемых исключений.</span><span class="sxs-lookup"><span data-stu-id="74065-181">This event is emitted when a managed exception catch handler ends.</span></span>

|<span data-ttu-id="74065-182">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="74065-182">Keyword for raising the event</span></span>|<span data-ttu-id="74065-183">Level</span><span class="sxs-lookup"><span data-stu-id="74065-183">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="74065-184">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="74065-184">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="74065-185">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="74065-185">Informational (4)</span></span>|

 <span data-ttu-id="74065-186">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="74065-186">The following table shows event information.</span></span>

|<span data-ttu-id="74065-187">Событие</span><span class="sxs-lookup"><span data-stu-id="74065-187">Event</span></span>|<span data-ttu-id="74065-188">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="74065-188">Event ID</span></span>|<span data-ttu-id="74065-189">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="74065-189">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionFinallyStop`|<span data-ttu-id="74065-190">253</span><span class="sxs-lookup"><span data-stu-id="74065-190">253</span></span>|<span data-ttu-id="74065-191">Обработчик перехвата управляемых исключений окончательно остановлен.</span><span class="sxs-lookup"><span data-stu-id="74065-191">A managed exception finally handler is done.</span></span>|

## <a name="exceptionfilterstart-event"></a><span data-ttu-id="74065-192">Событие ExceptionFilterStart</span><span class="sxs-lookup"><span data-stu-id="74065-192">ExceptionFilterStart event</span></span>

<span data-ttu-id="74065-193">Это событие возникает при начале фильтрации управляемых исключений.</span><span class="sxs-lookup"><span data-stu-id="74065-193">This event is emitted when a managed exception filtering begins.</span></span>

|<span data-ttu-id="74065-194">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="74065-194">Keyword for raising the event</span></span>|<span data-ttu-id="74065-195">Level</span><span class="sxs-lookup"><span data-stu-id="74065-195">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="74065-196">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="74065-196">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="74065-197">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="74065-197">Informational (4)</span></span>|

 <span data-ttu-id="74065-198">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="74065-198">The following table shows event information.</span></span>

|<span data-ttu-id="74065-199">Событие</span><span class="sxs-lookup"><span data-stu-id="74065-199">Event</span></span>|<span data-ttu-id="74065-200">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="74065-200">Event ID</span></span>|<span data-ttu-id="74065-201">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="74065-201">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionFilterStart`|<span data-ttu-id="74065-202">254</span><span class="sxs-lookup"><span data-stu-id="74065-202">254</span></span>|<span data-ttu-id="74065-203">Начинается фильтрация управляемого исключения.</span><span class="sxs-lookup"><span data-stu-id="74065-203">A managed exception filtering begins.</span></span>|

|<span data-ttu-id="74065-204">Имя поля</span><span class="sxs-lookup"><span data-stu-id="74065-204">Field name</span></span>|<span data-ttu-id="74065-205">Тип данных</span><span class="sxs-lookup"><span data-stu-id="74065-205">Data type</span></span>|<span data-ttu-id="74065-206">Описание</span><span class="sxs-lookup"><span data-stu-id="74065-206">Description</span></span>|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|<span data-ttu-id="74065-207">Указатель на инструкцию, в которой возникло исключение.</span><span class="sxs-lookup"><span data-stu-id="74065-207">Instruction pointer where exception occurred.</span></span>|
|`MethodID`|`win:Pointer`|<span data-ttu-id="74065-208">Указатель на дескриптор метода в методе, где возникло исключение.</span><span class="sxs-lookup"><span data-stu-id="74065-208">Pointer to the method descriptor on the method where exception occurred.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="74065-209">Имя метода, где возникло исключение.</span><span class="sxs-lookup"><span data-stu-id="74065-209">Name of the method where exception occurred.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="74065-210">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="74065-210">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="exceptionfilterstop-event"></a><span data-ttu-id="74065-211">Событие ExceptionFilterStop</span><span class="sxs-lookup"><span data-stu-id="74065-211">ExceptionFilterStop event</span></span>

<span data-ttu-id="74065-212">Это событие возникает при окончании фильтрации управляемых исключений.</span><span class="sxs-lookup"><span data-stu-id="74065-212">This event is emitted when a managed exception filtering ends.</span></span>

|<span data-ttu-id="74065-213">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="74065-213">Keyword for raising the event</span></span>|<span data-ttu-id="74065-214">Level</span><span class="sxs-lookup"><span data-stu-id="74065-214">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="74065-215">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="74065-215">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="74065-216">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="74065-216">Informational (4)</span></span>|

 <span data-ttu-id="74065-217">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="74065-217">The following table shows event information.</span></span>

|<span data-ttu-id="74065-218">Событие</span><span class="sxs-lookup"><span data-stu-id="74065-218">Event</span></span>|<span data-ttu-id="74065-219">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="74065-219">Event ID</span></span>|<span data-ttu-id="74065-220">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="74065-220">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionFilteringStart`|<span data-ttu-id="74065-221">255</span><span class="sxs-lookup"><span data-stu-id="74065-221">255</span></span>|<span data-ttu-id="74065-222">Заканчивается фильтрация управляемого исключения.</span><span class="sxs-lookup"><span data-stu-id="74065-222">A managed exception filtering ends.</span></span>|

## <a name="exceptionthrownstop-event"></a><span data-ttu-id="74065-223">Событие ExceptionThrownStop</span><span class="sxs-lookup"><span data-stu-id="74065-223">ExceptionThrownStop event</span></span>

<span data-ttu-id="74065-224">Это событие вызывается, когда среда выполнения завершила обработку созданного управляемого исключение.</span><span class="sxs-lookup"><span data-stu-id="74065-224">This event is emitted when the runtime is done handling a managed exception that was thrown.</span></span>

|<span data-ttu-id="74065-225">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="74065-225">Keyword for raising the event</span></span>|<span data-ttu-id="74065-226">Level</span><span class="sxs-lookup"><span data-stu-id="74065-226">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="74065-227">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="74065-227">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="74065-228">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="74065-228">Informational (4)</span></span>|
  
 <span data-ttu-id="74065-229">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="74065-229">The following table shows event information.</span></span>

|<span data-ttu-id="74065-230">Событие</span><span class="sxs-lookup"><span data-stu-id="74065-230">Event</span></span>|<span data-ttu-id="74065-231">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="74065-231">Event ID</span></span>|<span data-ttu-id="74065-232">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="74065-232">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionThrownStop`|<span data-ttu-id="74065-233">256</span><span class="sxs-lookup"><span data-stu-id="74065-233">256</span></span>|<span data-ttu-id="74065-234">Заканчивается фильтрация управляемого исключения.</span><span class="sxs-lookup"><span data-stu-id="74065-234">A managed exception filtering ends.</span></span>|
