---
title: События среды выполнения ThreadPool
description: См. события пула потоков среды выполнения .NET, которые собирают диагностические сведения о пуле потоков в .NET Core. События пула потоков — это события пула рабочих потоков или события пула потоков ввода-вывода.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- ThreadPool events (CoreCLR)
- ETW, thread pool events (CoreCLR)
ms.openlocfilehash: cdd6041c5842d4922c60e33daf6db366f7d35327
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "96594122"
---
# <a name="net-runtime-thread-pool-events"></a><span data-ttu-id="e74c7-104">События пула потоков среды выполнения .NET</span><span class="sxs-lookup"><span data-stu-id="e74c7-104">.NET runtime thread pool events</span></span>

<span data-ttu-id="e74c7-105">Эти события собирают сведения о рабочих потоках и потоках ввода-вывода в пуле потоков.</span><span class="sxs-lookup"><span data-stu-id="e74c7-105">These events collect information about worker and I/O threads in the threadpool.</span></span> <span data-ttu-id="e74c7-106">Дополнительные сведения об использовании этих событий в целях диагностики см. в статье [Ведение журнала и трассировка в приложениях .NET](../../core/diagnostics/logging-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="e74c7-106">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="iothreadcreate_v1-event"></a><span data-ttu-id="e74c7-107">Событие IOThreadCreate_V1</span><span class="sxs-lookup"><span data-stu-id="e74c7-107">IOThreadCreate_V1 event</span></span>

 <span data-ttu-id="e74c7-108">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="e74c7-108">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="e74c7-109">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="e74c7-109">Keyword for raising the event</span></span>|<span data-ttu-id="e74c7-110">Level</span><span class="sxs-lookup"><span data-stu-id="e74c7-110">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e74c7-111">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e74c7-111">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e74c7-112">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="e74c7-112">Informational (4)</span></span>|

 <span data-ttu-id="e74c7-113">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="e74c7-113">The following table shows the event information.</span></span>

|<span data-ttu-id="e74c7-114">Событие</span><span class="sxs-lookup"><span data-stu-id="e74c7-114">Event</span></span>|<span data-ttu-id="e74c7-115">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="e74c7-115">Event ID</span></span>|<span data-ttu-id="e74c7-116">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="e74c7-116">Raised when</span></span>|
|-----------------------------------|-----------|
|`IOThreadCreate_V1`|<span data-ttu-id="e74c7-117">44</span><span class="sxs-lookup"><span data-stu-id="e74c7-117">44</span></span>|<span data-ttu-id="e74c7-118">Поток ввода-вывода создается в пуле потоков.</span><span class="sxs-lookup"><span data-stu-id="e74c7-118">An I/O thread is created in the thread pool.</span></span>|

 <span data-ttu-id="e74c7-119">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="e74c7-119">The following table shows the event data.</span></span>

|<span data-ttu-id="e74c7-120">Имя поля</span><span class="sxs-lookup"><span data-stu-id="e74c7-120">Field name</span></span>|<span data-ttu-id="e74c7-121">Тип данных</span><span class="sxs-lookup"><span data-stu-id="e74c7-121">Data type</span></span>|<span data-ttu-id="e74c7-122">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-122">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|<span data-ttu-id="e74c7-123">Число потоков ввода-вывода, включая вновь созданный поток.</span><span class="sxs-lookup"><span data-stu-id="e74c7-123">Number of I/O threads, including the newly created thread.</span></span>|
|`NumRetired`|`win:UInt64`|<span data-ttu-id="e74c7-124">Число завершенных рабочих потоков.</span><span class="sxs-lookup"><span data-stu-id="e74c7-124">Number of retired worker threads.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="e74c7-125">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e74c7-125">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="iothreadterminate_v1-event"></a><span data-ttu-id="e74c7-126">Событие IOThreadTerminate_V1</span><span class="sxs-lookup"><span data-stu-id="e74c7-126">IOThreadTerminate_V1 event</span></span>

 <span data-ttu-id="e74c7-127">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="e74c7-127">The following table shows the keyword and level</span></span>

|<span data-ttu-id="e74c7-128">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="e74c7-128">Keyword for raising the event</span></span>|<span data-ttu-id="e74c7-129">Level</span><span class="sxs-lookup"><span data-stu-id="e74c7-129">Level</span></span>
|-----------------------------------|-----------
|<span data-ttu-id="e74c7-130">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e74c7-130">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e74c7-131">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="e74c7-131">Informational (4)</span></span>

 <span data-ttu-id="e74c7-132">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="e74c7-132">The following table shows the event information.</span></span>

|<span data-ttu-id="e74c7-133">Событие</span><span class="sxs-lookup"><span data-stu-id="e74c7-133">Event</span></span>|<span data-ttu-id="e74c7-134">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="e74c7-134">Event ID</span></span>|<span data-ttu-id="e74c7-135">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="e74c7-135">Raised when</span></span>|
|-----------|--------------|-----------------|
|`IOThreadTerminate`|<span data-ttu-id="e74c7-136">45</span><span class="sxs-lookup"><span data-stu-id="e74c7-136">45</span></span>|<span data-ttu-id="e74c7-137">Поток ввода-вывода прерывается в пуле потоков.</span><span class="sxs-lookup"><span data-stu-id="e74c7-137">An I/O thread is terminated in the thread pool.</span></span>|

 <span data-ttu-id="e74c7-138">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="e74c7-138">The following table shows the event data.</span></span>

|<span data-ttu-id="e74c7-139">Имя поля</span><span class="sxs-lookup"><span data-stu-id="e74c7-139">Field name</span></span>|<span data-ttu-id="e74c7-140">Тип данных</span><span class="sxs-lookup"><span data-stu-id="e74c7-140">Data type</span></span>|<span data-ttu-id="e74c7-141">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-141">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|<span data-ttu-id="e74c7-142">Число потоков ввода-вывода, остающихся в пуле потоков.</span><span class="sxs-lookup"><span data-stu-id="e74c7-142">Number of I/O threads remaining in the thread pool.</span></span>|
|`NumRetired`|`win:UInt64`|<span data-ttu-id="e74c7-143">Число завершенных потоков ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="e74c7-143">Number of retired I/O threads.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="e74c7-144">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e74c7-144">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="iothreadretire_v1-event"></a><span data-ttu-id="e74c7-145">Событие IOThreadRetire_V1</span><span class="sxs-lookup"><span data-stu-id="e74c7-145">IOThreadRetire_V1 event</span></span>

 <span data-ttu-id="e74c7-146">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="e74c7-146">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="e74c7-147">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="e74c7-147">Keyword for raising the event</span></span>|<span data-ttu-id="e74c7-148">Level</span><span class="sxs-lookup"><span data-stu-id="e74c7-148">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e74c7-149">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e74c7-149">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e74c7-150">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="e74c7-150">Informational (4)</span></span>|

 <span data-ttu-id="e74c7-151">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="e74c7-151">The following table shows the event information.</span></span>

|<span data-ttu-id="e74c7-152">Событие</span><span class="sxs-lookup"><span data-stu-id="e74c7-152">Event</span></span>|<span data-ttu-id="e74c7-153">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="e74c7-153">Event ID</span></span>|<span data-ttu-id="e74c7-154">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="e74c7-154">Raised when</span></span>|
|-----------|--------------|-----------------|
|`IOThreadRetire_V1`|<span data-ttu-id="e74c7-155">46</span><span class="sxs-lookup"><span data-stu-id="e74c7-155">46</span></span>|<span data-ttu-id="e74c7-156">Поток ввода-вывода становится кандидатом на завершение.</span><span class="sxs-lookup"><span data-stu-id="e74c7-156">An I/O thread becomes a retirement candidate.</span></span>|

 <span data-ttu-id="e74c7-157">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="e74c7-157">The following table shows the event data.</span></span>

|<span data-ttu-id="e74c7-158">Имя поля</span><span class="sxs-lookup"><span data-stu-id="e74c7-158">Field name</span></span>|<span data-ttu-id="e74c7-159">Тип данных</span><span class="sxs-lookup"><span data-stu-id="e74c7-159">Data type</span></span>|<span data-ttu-id="e74c7-160">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-160">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|<span data-ttu-id="e74c7-161">Число потоков ввода-вывода, остающихся в пуле потоков.</span><span class="sxs-lookup"><span data-stu-id="e74c7-161">Number of I/O threads remaining in the thread pool.</span></span>|
|`NumRetired`|`win:UInt64`|<span data-ttu-id="e74c7-162">Число завершенных потоков ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="e74c7-162">Number of retired I/O threads.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="e74c7-163">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e74c7-163">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="iothreadunretire_v1-event"></a><span data-ttu-id="e74c7-164">Событие IOThreadUnretire_V1</span><span class="sxs-lookup"><span data-stu-id="e74c7-164">IOThreadUnretire_V1 event</span></span>

 <span data-ttu-id="e74c7-165">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="e74c7-165">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="e74c7-166">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="e74c7-166">Keyword for raising the event</span></span>|<span data-ttu-id="e74c7-167">Level</span><span class="sxs-lookup"><span data-stu-id="e74c7-167">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e74c7-168">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e74c7-168">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e74c7-169">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="e74c7-169">Informational (4)</span></span>|

 <span data-ttu-id="e74c7-170">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="e74c7-170">The following table shows the event information.</span></span>

|<span data-ttu-id="e74c7-171">Событие</span><span class="sxs-lookup"><span data-stu-id="e74c7-171">Event</span></span>|<span data-ttu-id="e74c7-172">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="e74c7-172">Event ID</span></span>|<span data-ttu-id="e74c7-173">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="e74c7-173">Raised when</span></span>|
|-----------|--------------|-----------------|
|`IOThreadUnretire_V1`|<span data-ttu-id="e74c7-174">47</span><span class="sxs-lookup"><span data-stu-id="e74c7-174">47</span></span>|<span data-ttu-id="e74c7-175">Завершенный поток ввода-вывода повторно активируется из-за ввода-вывода, поступающего в течение периода ожидания после того, как поток стал кандидатом на завершение.</span><span class="sxs-lookup"><span data-stu-id="e74c7-175">An I/O thread is unretired because of I/O that arrives within a waiting period after the thread becomes a retirement candidate.</span></span>|

 <span data-ttu-id="e74c7-176">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="e74c7-176">The following table shows the event data.</span></span>

|<span data-ttu-id="e74c7-177">Имя поля</span><span class="sxs-lookup"><span data-stu-id="e74c7-177">Field name</span></span>|<span data-ttu-id="e74c7-178">Тип данных</span><span class="sxs-lookup"><span data-stu-id="e74c7-178">Data type</span></span>|<span data-ttu-id="e74c7-179">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-179">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|<span data-ttu-id="e74c7-180">Число потоков ввода-вывода в пуле потоков, включая этот поток.</span><span class="sxs-lookup"><span data-stu-id="e74c7-180">Number of I/O threads in the thread pool, including this one.</span></span>|
|`NumRetired`|`win:UInt64`|<span data-ttu-id="e74c7-181">Число завершенных потоков ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="e74c7-181">Number of retired I/O threads.</span></span>|
|`ClrInstanceID`|`Win:UInt16`|<span data-ttu-id="e74c7-182">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e74c7-182">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadstart-event"></a><span data-ttu-id="e74c7-183">Событие ThreadPoolWorkerThreadStart</span><span class="sxs-lookup"><span data-stu-id="e74c7-183">ThreadPoolWorkerThreadStart event</span></span>

|<span data-ttu-id="e74c7-184">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="e74c7-184">Keyword for raising the event</span></span>|<span data-ttu-id="e74c7-185">Level</span><span class="sxs-lookup"><span data-stu-id="e74c7-185">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="e74c7-186">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e74c7-186">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e74c7-187">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="e74c7-187">Informational (4)</span></span>|

|<span data-ttu-id="e74c7-188">Событие</span><span class="sxs-lookup"><span data-stu-id="e74c7-188">Event</span></span>|<span data-ttu-id="e74c7-189">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="e74c7-189">Event ID</span></span>|<span data-ttu-id="e74c7-190">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-190">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadStart`|<span data-ttu-id="e74c7-191">50</span><span class="sxs-lookup"><span data-stu-id="e74c7-191">50</span></span>|<span data-ttu-id="e74c7-192">Создается рабочий поток.</span><span class="sxs-lookup"><span data-stu-id="e74c7-192">A worker thread is created.</span></span>|

|<span data-ttu-id="e74c7-193">Имя поля</span><span class="sxs-lookup"><span data-stu-id="e74c7-193">Field name</span></span>|<span data-ttu-id="e74c7-194">Тип данных</span><span class="sxs-lookup"><span data-stu-id="e74c7-194">Data type</span></span>|<span data-ttu-id="e74c7-195">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-195">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="e74c7-196">Число рабочих потоков, доступных для выполнения процесса, включая уже работающие потоки.</span><span class="sxs-lookup"><span data-stu-id="e74c7-196">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="e74c7-197">Число рабочих потоков, которые недоступны для выполнения процесса, но находятся в резерве на случай, если позже понадобятся дополнительные потоки.</span><span class="sxs-lookup"><span data-stu-id="e74c7-197">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="e74c7-198">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e74c7-198">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadstop-event"></a><span data-ttu-id="e74c7-199">Событие ThreadPoolWorkerThreadStop</span><span class="sxs-lookup"><span data-stu-id="e74c7-199">ThreadPoolWorkerThreadStop event</span></span>

|<span data-ttu-id="e74c7-200">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="e74c7-200">Keyword for raising the event</span></span>|<span data-ttu-id="e74c7-201">Level</span><span class="sxs-lookup"><span data-stu-id="e74c7-201">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="e74c7-202">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e74c7-202">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e74c7-203">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="e74c7-203">Informational (4)</span></span>|

|<span data-ttu-id="e74c7-204">Событие</span><span class="sxs-lookup"><span data-stu-id="e74c7-204">Event</span></span>|<span data-ttu-id="e74c7-205">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="e74c7-205">Event ID</span></span>|<span data-ttu-id="e74c7-206">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-206">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadStop`|<span data-ttu-id="e74c7-207">51</span><span class="sxs-lookup"><span data-stu-id="e74c7-207">51</span></span>|<span data-ttu-id="e74c7-208">Рабочий поток останавливается.</span><span class="sxs-lookup"><span data-stu-id="e74c7-208">A worker thread is stopped.</span></span>|

|<span data-ttu-id="e74c7-209">Имя поля</span><span class="sxs-lookup"><span data-stu-id="e74c7-209">Field name</span></span>|<span data-ttu-id="e74c7-210">Тип данных</span><span class="sxs-lookup"><span data-stu-id="e74c7-210">Data type</span></span>|<span data-ttu-id="e74c7-211">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-211">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="e74c7-212">Число рабочих потоков, доступных для выполнения процесса, включая уже работающие потоки.</span><span class="sxs-lookup"><span data-stu-id="e74c7-212">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="e74c7-213">Число рабочих потоков, которые недоступны для выполнения процесса, но находятся в резерве на случай, если позже понадобятся дополнительные потоки.</span><span class="sxs-lookup"><span data-stu-id="e74c7-213">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="e74c7-214">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e74c7-214">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadwait-event"></a><span data-ttu-id="e74c7-215">Событие ThreadPoolWorkerThreadWait</span><span class="sxs-lookup"><span data-stu-id="e74c7-215">ThreadPoolWorkerThreadWait event</span></span>

|<span data-ttu-id="e74c7-216">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="e74c7-216">Keyword for raising the event</span></span>|<span data-ttu-id="e74c7-217">Level</span><span class="sxs-lookup"><span data-stu-id="e74c7-217">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="e74c7-218">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e74c7-218">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e74c7-219">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="e74c7-219">Informational (4)</span></span>|

|<span data-ttu-id="e74c7-220">Событие</span><span class="sxs-lookup"><span data-stu-id="e74c7-220">Event</span></span>|<span data-ttu-id="e74c7-221">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="e74c7-221">Event ID</span></span>|<span data-ttu-id="e74c7-222">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-222">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadWait`|<span data-ttu-id="e74c7-223">57</span><span class="sxs-lookup"><span data-stu-id="e74c7-223">57</span></span>|<span data-ttu-id="e74c7-224">Рабочий поток начинает ожидание работы.</span><span class="sxs-lookup"><span data-stu-id="e74c7-224">A worker thread starts waiting for work.</span></span>|

|<span data-ttu-id="e74c7-225">Имя поля</span><span class="sxs-lookup"><span data-stu-id="e74c7-225">Field name</span></span>|<span data-ttu-id="e74c7-226">Тип данных</span><span class="sxs-lookup"><span data-stu-id="e74c7-226">Data type</span></span>|<span data-ttu-id="e74c7-227">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-227">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="e74c7-228">Число рабочих потоков, доступных для выполнения процесса, включая уже работающие потоки.</span><span class="sxs-lookup"><span data-stu-id="e74c7-228">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="e74c7-229">Число рабочих потоков, которые недоступны для выполнения процесса, но находятся в резерве на случай, если позже понадобятся дополнительные потоки.</span><span class="sxs-lookup"><span data-stu-id="e74c7-229">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="e74c7-230">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e74c7-230">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadretirementstart-event"></a><span data-ttu-id="e74c7-231">Событие ThreadPoolWorkerThreadRetirementStart</span><span class="sxs-lookup"><span data-stu-id="e74c7-231">ThreadPoolWorkerThreadRetirementStart event</span></span>

|<span data-ttu-id="e74c7-232">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="e74c7-232">Keyword for raising the event</span></span>|<span data-ttu-id="e74c7-233">Level</span><span class="sxs-lookup"><span data-stu-id="e74c7-233">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="e74c7-234">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e74c7-234">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e74c7-235">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="e74c7-235">Informational (4)</span></span>|

|<span data-ttu-id="e74c7-236">Событие</span><span class="sxs-lookup"><span data-stu-id="e74c7-236">Event</span></span>|<span data-ttu-id="e74c7-237">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="e74c7-237">Event ID</span></span>|<span data-ttu-id="e74c7-238">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-238">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadRetirementStart`|<span data-ttu-id="e74c7-239">52</span><span class="sxs-lookup"><span data-stu-id="e74c7-239">52</span></span>|<span data-ttu-id="e74c7-240">Рабочий поток завершается.</span><span class="sxs-lookup"><span data-stu-id="e74c7-240">A worker thread retires.</span></span>|

|<span data-ttu-id="e74c7-241">Имя поля</span><span class="sxs-lookup"><span data-stu-id="e74c7-241">Field name</span></span>|<span data-ttu-id="e74c7-242">Тип данных</span><span class="sxs-lookup"><span data-stu-id="e74c7-242">Data type</span></span>|<span data-ttu-id="e74c7-243">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-243">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="e74c7-244">Число рабочих потоков, доступных для выполнения процесса, включая уже работающие потоки.</span><span class="sxs-lookup"><span data-stu-id="e74c7-244">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="e74c7-245">Число рабочих потоков, которые недоступны для выполнения процесса, но находятся в резерве на случай, если позже понадобятся дополнительные потоки.</span><span class="sxs-lookup"><span data-stu-id="e74c7-245">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="e74c7-246">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e74c7-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadretirementstop-event"></a><span data-ttu-id="e74c7-247">Событие ThreadPoolWorkerThreadRetirementStop</span><span class="sxs-lookup"><span data-stu-id="e74c7-247">ThreadPoolWorkerThreadRetirementStop event</span></span>

|<span data-ttu-id="e74c7-248">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="e74c7-248">Keyword for raising the event</span></span>|<span data-ttu-id="e74c7-249">Level</span><span class="sxs-lookup"><span data-stu-id="e74c7-249">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="e74c7-250">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e74c7-250">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e74c7-251">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="e74c7-251">Informational (4)</span></span>|

|<span data-ttu-id="e74c7-252">Событие</span><span class="sxs-lookup"><span data-stu-id="e74c7-252">Event</span></span>|<span data-ttu-id="e74c7-253">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="e74c7-253">Event ID</span></span>|<span data-ttu-id="e74c7-254">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-254">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadRetirementStop`|<span data-ttu-id="e74c7-255">53</span><span class="sxs-lookup"><span data-stu-id="e74c7-255">53</span></span>|<span data-ttu-id="e74c7-256">Завершенный рабочий поток снова становится активным.</span><span class="sxs-lookup"><span data-stu-id="e74c7-256">A retired worker thread becomes active again.</span></span>|

|<span data-ttu-id="e74c7-257">Имя поля</span><span class="sxs-lookup"><span data-stu-id="e74c7-257">Field name</span></span>|<span data-ttu-id="e74c7-258">Тип данных</span><span class="sxs-lookup"><span data-stu-id="e74c7-258">Data type</span></span>|<span data-ttu-id="e74c7-259">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-259">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="e74c7-260">Число рабочих потоков, доступных для выполнения процесса, включая уже работающие потоки.</span><span class="sxs-lookup"><span data-stu-id="e74c7-260">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="e74c7-261">Число рабочих потоков, которые недоступны для выполнения процесса, но находятся в резерве на случай, если позже понадобятся дополнительные потоки.</span><span class="sxs-lookup"><span data-stu-id="e74c7-261">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="e74c7-262">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e74c7-262">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadadjustmentsample-event"></a><span data-ttu-id="e74c7-263">Событие ThreadPoolWorkerThreadAdjustmentSample</span><span class="sxs-lookup"><span data-stu-id="e74c7-263">ThreadPoolWorkerThreadAdjustmentSample event</span></span>

 <span data-ttu-id="e74c7-264">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="e74c7-264">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="e74c7-265">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="e74c7-265">Keyword for raising the event</span></span>|<span data-ttu-id="e74c7-266">Level</span><span class="sxs-lookup"><span data-stu-id="e74c7-266">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e74c7-267">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e74c7-267">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e74c7-268">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="e74c7-268">Informational (4)</span></span>|

 <span data-ttu-id="e74c7-269">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="e74c7-269">The following table shows the event information.</span></span>

|<span data-ttu-id="e74c7-270">Событие</span><span class="sxs-lookup"><span data-stu-id="e74c7-270">Event</span></span>|<span data-ttu-id="e74c7-271">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="e74c7-271">Event ID</span></span>|<span data-ttu-id="e74c7-272">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-272">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentSample`|<span data-ttu-id="e74c7-273">54</span><span class="sxs-lookup"><span data-stu-id="e74c7-273">54</span></span>|<span data-ttu-id="e74c7-274">Указывает на сбор сведений для одного образца, то есть измерение пропускной способности с определенным уровнем параллелизма в некоторый момент времени.</span><span class="sxs-lookup"><span data-stu-id="e74c7-274">Refers to the collection of information for one sample; that is, a measurement of throughput with a certain concurrency level, in an instant of time.</span></span>|

 <span data-ttu-id="e74c7-275">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="e74c7-275">The following table shows the event data.</span></span>

|<span data-ttu-id="e74c7-276">Имя поля</span><span class="sxs-lookup"><span data-stu-id="e74c7-276">Field name</span></span>|<span data-ttu-id="e74c7-277">Тип данных</span><span class="sxs-lookup"><span data-stu-id="e74c7-277">Data type</span></span>|<span data-ttu-id="e74c7-278">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-278">Description</span></span>|
|----------------|---------------|-----------------|
|`Throughput`|`win:Double`|<span data-ttu-id="e74c7-279">Число завершений в единицу времени.</span><span class="sxs-lookup"><span data-stu-id="e74c7-279">Number of completions per unit of time.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="e74c7-280">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e74c7-280">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadadjustmentadjustment-event"></a><span data-ttu-id="e74c7-281">Событие ThreadPoolWorkerThreadAdjustmentAdjustment</span><span class="sxs-lookup"><span data-stu-id="e74c7-281">ThreadPoolWorkerThreadAdjustmentAdjustment event</span></span>

 <span data-ttu-id="e74c7-282">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="e74c7-282">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="e74c7-283">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="e74c7-283">Keyword for raising the event</span></span>|<span data-ttu-id="e74c7-284">Level</span><span class="sxs-lookup"><span data-stu-id="e74c7-284">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e74c7-285">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e74c7-285">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e74c7-286">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="e74c7-286">Informational (4)</span></span>|

 <span data-ttu-id="e74c7-287">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="e74c7-287">The following table shows the event information.</span></span>

|<span data-ttu-id="e74c7-288">Событие</span><span class="sxs-lookup"><span data-stu-id="e74c7-288">Event</span></span>|<span data-ttu-id="e74c7-289">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="e74c7-289">Event ID</span></span>|<span data-ttu-id="e74c7-290">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-290">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentAdjustment`|<span data-ttu-id="e74c7-291">55</span><span class="sxs-lookup"><span data-stu-id="e74c7-291">55</span></span>|<span data-ttu-id="e74c7-292">Регистрирует изменение в управлении, когда алгоритм вставки потока (поиск экстремума) определяет, что произошло изменение уровня параллелизма.</span><span class="sxs-lookup"><span data-stu-id="e74c7-292">Records a change in control, when the thread injection (hill-climbing) algorithm determines that a change in concurrency level is in place.</span></span>|

 <span data-ttu-id="e74c7-293">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="e74c7-293">The following table shows the event data.</span></span>

|<span data-ttu-id="e74c7-294">Имя поля</span><span class="sxs-lookup"><span data-stu-id="e74c7-294">Field name</span></span>|<span data-ttu-id="e74c7-295">Тип данных</span><span class="sxs-lookup"><span data-stu-id="e74c7-295">Data type</span></span>|<span data-ttu-id="e74c7-296">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-296">Description</span></span>|
|----------------|---------------|-----------------|
|`AverageThroughput`|`win:Double`|<span data-ttu-id="e74c7-297">Средняя пропускная способность образца измерений.</span><span class="sxs-lookup"><span data-stu-id="e74c7-297">Average throughput of a sample of measurements.</span></span>|
|`NewWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="e74c7-298">Новое число активных рабочих потоков.</span><span class="sxs-lookup"><span data-stu-id="e74c7-298">New number of active worker threads.</span></span>|
|`Reason`|`win:UInt32`|<span data-ttu-id="e74c7-299">Причина корректировки:</span><span class="sxs-lookup"><span data-stu-id="e74c7-299">Reason for the adjustment.</span></span><br /><br /> <span data-ttu-id="e74c7-300">`0x0` — прогрев.</span><span class="sxs-lookup"><span data-stu-id="e74c7-300">`0x0` - Warmup.</span></span><br /><br /> <span data-ttu-id="e74c7-301">`0x1` — инициализация.</span><span class="sxs-lookup"><span data-stu-id="e74c7-301">`0x1` - Initializing.</span></span><br /><br /> <span data-ttu-id="e74c7-302">`0x2` — случайное движение.</span><span class="sxs-lookup"><span data-stu-id="e74c7-302">`0x2` - Random move.</span></span><br /><br /> <span data-ttu-id="e74c7-303">`0x3` — движение вверх.</span><span class="sxs-lookup"><span data-stu-id="e74c7-303">`0x3` - Climbing move.</span></span><br /><br /> <span data-ttu-id="e74c7-304">`0x4` — точка изменения.</span><span class="sxs-lookup"><span data-stu-id="e74c7-304">`0x4` - Change point.</span></span><br /><br /> <span data-ttu-id="e74c7-305">`0x5` — стабилизация.</span><span class="sxs-lookup"><span data-stu-id="e74c7-305">`0x5` - Stabilizing.</span></span><br /><br /> <span data-ttu-id="e74c7-306">`0x6` — перегрузка.</span><span class="sxs-lookup"><span data-stu-id="e74c7-306">`0x6` - Starvation.</span></span><br /><br /> <span data-ttu-id="e74c7-307">`0x7` — истекло время ожидания потока.</span><span class="sxs-lookup"><span data-stu-id="e74c7-307">`0x7` - Thread timed out.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="e74c7-308">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e74c7-308">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadadjustmentstats-event"></a><span data-ttu-id="e74c7-309">Событие ThreadPoolWorkerThreadAdjustmentStats</span><span class="sxs-lookup"><span data-stu-id="e74c7-309">ThreadPoolWorkerThreadAdjustmentStats event</span></span>

 <span data-ttu-id="e74c7-310">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="e74c7-310">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="e74c7-311">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="e74c7-311">Keyword for raising the event</span></span>|<span data-ttu-id="e74c7-312">Level</span><span class="sxs-lookup"><span data-stu-id="e74c7-312">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e74c7-313">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e74c7-313">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e74c7-314">Подробный (5)</span><span class="sxs-lookup"><span data-stu-id="e74c7-314">Verbose (5)</span></span>

 <span data-ttu-id="e74c7-315">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="e74c7-315">The following table shows the event information.</span></span>

|<span data-ttu-id="e74c7-316">Событие</span><span class="sxs-lookup"><span data-stu-id="e74c7-316">Event</span></span>|<span data-ttu-id="e74c7-317">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="e74c7-317">Event ID</span></span>|<span data-ttu-id="e74c7-318">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-318">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentStats`|<span data-ttu-id="e74c7-319">56</span><span class="sxs-lookup"><span data-stu-id="e74c7-319">56</span></span>|<span data-ttu-id="e74c7-320">Собирает данные по пулу потоков.</span><span class="sxs-lookup"><span data-stu-id="e74c7-320">Gathers data on the thread pool.</span></span>|

 <span data-ttu-id="e74c7-321">В таблице ниже представлены данные события</span><span class="sxs-lookup"><span data-stu-id="e74c7-321">The following table shows the event data</span></span>

|<span data-ttu-id="e74c7-322">Имя поля</span><span class="sxs-lookup"><span data-stu-id="e74c7-322">Field name</span></span>|<span data-ttu-id="e74c7-323">Тип данных</span><span class="sxs-lookup"><span data-stu-id="e74c7-323">Data type</span></span>|<span data-ttu-id="e74c7-324">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-324">Description</span></span>|
|----------------|---------------|-----------------|
|`Duration`|`win:Double`|<span data-ttu-id="e74c7-325">Время в секундах, в течение которого выполнялся сбор статистики.</span><span class="sxs-lookup"><span data-stu-id="e74c7-325">Amount of time, in seconds, during which these statistics were collected.</span></span>|
|`Throughput`|`win:Double`|<span data-ttu-id="e74c7-326">Среднее число завершений в секунду в течение данного интервала.</span><span class="sxs-lookup"><span data-stu-id="e74c7-326">Average number of completions per second during this interval.</span></span>|
|`ThreadWave`|`win:Double`|<span data-ttu-id="e74c7-327">Зарезервировано для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="e74c7-327">Reserved for internal use.</span></span>|
|`ThroughputWave`|`win:Double`|<span data-ttu-id="e74c7-328">Зарезервировано для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="e74c7-328">Reserved for internal use.</span></span>|
|`ThroughputErrorEstimate`|`win:Double`|<span data-ttu-id="e74c7-329">Зарезервировано для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="e74c7-329">Reserved for internal use.</span></span>|
|`AverageThroughputErrorEstimate`|`win:Double`|<span data-ttu-id="e74c7-330">Зарезервировано для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="e74c7-330">Reserved for internal use.</span></span>|
|`ThroughputRatio`|`win:Double`|<span data-ttu-id="e74c7-331">Относительное улучшение пропускной способности, вызванное изменениями числа активных рабочих потоков в течение этого интервала.</span><span class="sxs-lookup"><span data-stu-id="e74c7-331">The relative improvement in throughput caused by variations in active worker thread count during this interval.</span></span>|
|`Confidence`|`win:Double`|<span data-ttu-id="e74c7-332">Мера обоснованности поля ThroughputRatio.</span><span class="sxs-lookup"><span data-stu-id="e74c7-332">A measure of the validity of the ThroughputRatio field.</span></span>|
|`NewcontrolSetting`|`win:Double`|<span data-ttu-id="e74c7-333">Число активных рабочих потоков, которое будет служить основой для будущих изменений числа активных потоков.</span><span class="sxs-lookup"><span data-stu-id="e74c7-333">The number of active worker threads that will serve as the baseline for future variations in active thread count.</span></span>|
|`NewThreadWaveMagnitude`|`win:UInt16`|<span data-ttu-id="e74c7-334">Величина будущих изменений числа активных потоков.</span><span class="sxs-lookup"><span data-stu-id="e74c7-334">The magnitude of future variations in active thread count.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="e74c7-335">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e74c7-335">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolenqueue-event"></a><span data-ttu-id="e74c7-336">Событие ThreadPoolEnqueue</span><span class="sxs-lookup"><span data-stu-id="e74c7-336">ThreadPoolEnqueue event</span></span>

 <span data-ttu-id="e74c7-337">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="e74c7-337">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="e74c7-338">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="e74c7-338">Keyword for raising the event</span></span>|<span data-ttu-id="e74c7-339">Level</span><span class="sxs-lookup"><span data-stu-id="e74c7-339">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e74c7-340">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e74c7-340">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e74c7-341">Подробный (5)</span><span class="sxs-lookup"><span data-stu-id="e74c7-341">Verbose (5)</span></span>

 <span data-ttu-id="e74c7-342">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="e74c7-342">The following table shows the event information.</span></span>

|<span data-ttu-id="e74c7-343">Событие</span><span class="sxs-lookup"><span data-stu-id="e74c7-343">Event</span></span>|<span data-ttu-id="e74c7-344">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="e74c7-344">Event ID</span></span>|<span data-ttu-id="e74c7-345">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-345">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolEnqueue`|<span data-ttu-id="e74c7-346">61</span><span class="sxs-lookup"><span data-stu-id="e74c7-346">61</span></span>|<span data-ttu-id="e74c7-347">Рабочий элемент был поставлен в очередь пула потоков.</span><span class="sxs-lookup"><span data-stu-id="e74c7-347">A work item was enqueued in the thread pool queue.</span></span>|

 <span data-ttu-id="e74c7-348">В таблице ниже представлены данные события</span><span class="sxs-lookup"><span data-stu-id="e74c7-348">The following table shows the event data</span></span>

|<span data-ttu-id="e74c7-349">Имя поля</span><span class="sxs-lookup"><span data-stu-id="e74c7-349">Field name</span></span>|<span data-ttu-id="e74c7-350">Тип данных</span><span class="sxs-lookup"><span data-stu-id="e74c7-350">Data type</span></span>|<span data-ttu-id="e74c7-351">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-351">Description</span></span>|
|----------------|---------------|-----------------|
|`WorkID`|`win:Pointer`|<span data-ttu-id="e74c7-352">Указатель на рабочий запрос.</span><span class="sxs-lookup"><span data-stu-id="e74c7-352">Pointer to the work request.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="e74c7-353">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e74c7-353">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadpooldequeue-event"></a><span data-ttu-id="e74c7-354">Событие ThreadPoolDequeue</span><span class="sxs-lookup"><span data-stu-id="e74c7-354">ThreadPoolDequeue event</span></span>

 <span data-ttu-id="e74c7-355">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="e74c7-355">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="e74c7-356">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="e74c7-356">Keyword for raising the event</span></span>|<span data-ttu-id="e74c7-357">Level</span><span class="sxs-lookup"><span data-stu-id="e74c7-357">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e74c7-358">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e74c7-358">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e74c7-359">Подробный (5)</span><span class="sxs-lookup"><span data-stu-id="e74c7-359">Verbose (5)</span></span>

 <span data-ttu-id="e74c7-360">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="e74c7-360">The following table shows the event information.</span></span>

|<span data-ttu-id="e74c7-361">Событие</span><span class="sxs-lookup"><span data-stu-id="e74c7-361">Event</span></span>|<span data-ttu-id="e74c7-362">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="e74c7-362">Event ID</span></span>|<span data-ttu-id="e74c7-363">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-363">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolDequeue`|<span data-ttu-id="e74c7-364">62</span><span class="sxs-lookup"><span data-stu-id="e74c7-364">62</span></span>|<span data-ttu-id="e74c7-365">Рабочий элемент был удален из очереди пула потоков.</span><span class="sxs-lookup"><span data-stu-id="e74c7-365">A work item was dequeued from the thread pool queue.</span></span>|

 <span data-ttu-id="e74c7-366">В таблице ниже представлены данные события</span><span class="sxs-lookup"><span data-stu-id="e74c7-366">The following table shows the event data</span></span>

|<span data-ttu-id="e74c7-367">Имя поля</span><span class="sxs-lookup"><span data-stu-id="e74c7-367">Field name</span></span>|<span data-ttu-id="e74c7-368">Тип данных</span><span class="sxs-lookup"><span data-stu-id="e74c7-368">Data type</span></span>|<span data-ttu-id="e74c7-369">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-369">Description</span></span>|
|----------------|---------------|-----------------|
|`WorkID`|`win:Pointer`|<span data-ttu-id="e74c7-370">Указатель на рабочий запрос.</span><span class="sxs-lookup"><span data-stu-id="e74c7-370">Pointer to the work request.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="e74c7-371">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e74c7-371">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadpoolioenqueue-event"></a><span data-ttu-id="e74c7-372">Событие ThreadPoolIOEnqueue</span><span class="sxs-lookup"><span data-stu-id="e74c7-372">ThreadPoolIOEnqueue event</span></span>

 <span data-ttu-id="e74c7-373">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="e74c7-373">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="e74c7-374">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="e74c7-374">Keyword for raising the event</span></span>|<span data-ttu-id="e74c7-375">Level</span><span class="sxs-lookup"><span data-stu-id="e74c7-375">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e74c7-376">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e74c7-376">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e74c7-377">Подробный (5)</span><span class="sxs-lookup"><span data-stu-id="e74c7-377">Verbose (5)</span></span>

 <span data-ttu-id="e74c7-378">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="e74c7-378">The following table shows the event information.</span></span>

|<span data-ttu-id="e74c7-379">Событие</span><span class="sxs-lookup"><span data-stu-id="e74c7-379">Event</span></span>|<span data-ttu-id="e74c7-380">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="e74c7-380">Event ID</span></span>|<span data-ttu-id="e74c7-381">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-381">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolIOEnqueue`|<span data-ttu-id="e74c7-382">63</span><span class="sxs-lookup"><span data-stu-id="e74c7-382">63</span></span>|<span data-ttu-id="e74c7-383">Поток помещает в очередь уведомление о завершении ввода-вывода после выполнения асинхронного ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="e74c7-383">A thread enqueues an IO completion notification after an async IO completion occurs.</span></span>|

 <span data-ttu-id="e74c7-384">В таблице ниже представлены данные события</span><span class="sxs-lookup"><span data-stu-id="e74c7-384">The following table shows the event data</span></span>

|<span data-ttu-id="e74c7-385">Имя поля</span><span class="sxs-lookup"><span data-stu-id="e74c7-385">Field name</span></span>|<span data-ttu-id="e74c7-386">Тип данных</span><span class="sxs-lookup"><span data-stu-id="e74c7-386">Data type</span></span>|<span data-ttu-id="e74c7-387">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-387">Description</span></span>|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|<span data-ttu-id="e74c7-388">Зарезервировано для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="e74c7-388">Reserved for internal use.</span></span>|
|`Overlapped`|`win:Pointer`|<span data-ttu-id="e74c7-389">Зарезервировано для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="e74c7-389">Reserved for internal use.</span></span>|
|`MultiDequeues`|`win:Boolean`|<span data-ttu-id="e74c7-390">Зарезервировано для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="e74c7-390">Reserved for internal use.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="e74c7-391">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e74c7-391">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadpooliodequeue-event"></a><span data-ttu-id="e74c7-392">Событие ThreadPoolIODequeue</span><span class="sxs-lookup"><span data-stu-id="e74c7-392">ThreadPoolIODequeue event</span></span>

 <span data-ttu-id="e74c7-393">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="e74c7-393">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="e74c7-394">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="e74c7-394">Keyword for raising the event</span></span>|<span data-ttu-id="e74c7-395">Level</span><span class="sxs-lookup"><span data-stu-id="e74c7-395">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e74c7-396">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e74c7-396">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e74c7-397">Подробный (5)</span><span class="sxs-lookup"><span data-stu-id="e74c7-397">Verbose (5)</span></span>

 <span data-ttu-id="e74c7-398">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="e74c7-398">The following table shows the event information.</span></span>

|<span data-ttu-id="e74c7-399">Событие</span><span class="sxs-lookup"><span data-stu-id="e74c7-399">Event</span></span>|<span data-ttu-id="e74c7-400">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="e74c7-400">Event ID</span></span>|<span data-ttu-id="e74c7-401">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-401">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolIODequeue`|<span data-ttu-id="e74c7-402">64</span><span class="sxs-lookup"><span data-stu-id="e74c7-402">64</span></span>|<span data-ttu-id="e74c7-403">Поток удаляет из очереди уведомление о завершении ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="e74c7-403">A thread dequeues the IO completion notification.</span></span>|

 <span data-ttu-id="e74c7-404">В таблице ниже представлены данные события</span><span class="sxs-lookup"><span data-stu-id="e74c7-404">The following table shows the event data</span></span>

|<span data-ttu-id="e74c7-405">Имя поля</span><span class="sxs-lookup"><span data-stu-id="e74c7-405">Field name</span></span>|<span data-ttu-id="e74c7-406">Тип данных</span><span class="sxs-lookup"><span data-stu-id="e74c7-406">Data type</span></span>|<span data-ttu-id="e74c7-407">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-407">Description</span></span>|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|<span data-ttu-id="e74c7-408">Зарезервировано для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="e74c7-408">Reserved for internal use.</span></span>|
|`Overlapped`|`win:Pointer`|<span data-ttu-id="e74c7-409">Зарезервировано для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="e74c7-409">Reserved for internal use.</span></span>|
|`MultiDequeues`|`win:Boolean`|<span data-ttu-id="e74c7-410">Зарезервировано для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="e74c7-410">Reserved for internal use.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="e74c7-411">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e74c7-411">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadpooliopack-event"></a><span data-ttu-id="e74c7-412">Событие ThreadPoolIOPack</span><span class="sxs-lookup"><span data-stu-id="e74c7-412">ThreadPoolIOPack event</span></span>

 <span data-ttu-id="e74c7-413">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="e74c7-413">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="e74c7-414">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="e74c7-414">Keyword for raising the event</span></span>|<span data-ttu-id="e74c7-415">Level</span><span class="sxs-lookup"><span data-stu-id="e74c7-415">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e74c7-416">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e74c7-416">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e74c7-417">Подробный (5)</span><span class="sxs-lookup"><span data-stu-id="e74c7-417">Verbose (5)</span></span>|

 <span data-ttu-id="e74c7-418">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="e74c7-418">The following table shows the event information.</span></span>

|<span data-ttu-id="e74c7-419">Событие</span><span class="sxs-lookup"><span data-stu-id="e74c7-419">Event</span></span>|<span data-ttu-id="e74c7-420">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="e74c7-420">Event ID</span></span>|<span data-ttu-id="e74c7-421">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-421">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolIOPack`|<span data-ttu-id="e74c7-422">65</span><span class="sxs-lookup"><span data-stu-id="e74c7-422">65</span></span>|<span data-ttu-id="e74c7-423">Вызывается перекрывающийся пакет операций ввода-вывода ThreadPool.</span><span class="sxs-lookup"><span data-stu-id="e74c7-423">ThreadPool overlapped IO pack is called.</span></span>|

 <span data-ttu-id="e74c7-424">В таблице ниже представлены данные события</span><span class="sxs-lookup"><span data-stu-id="e74c7-424">The following table shows the event data</span></span>

|<span data-ttu-id="e74c7-425">Имя поля</span><span class="sxs-lookup"><span data-stu-id="e74c7-425">Field name</span></span>|<span data-ttu-id="e74c7-426">Тип данных</span><span class="sxs-lookup"><span data-stu-id="e74c7-426">Data type</span></span>|<span data-ttu-id="e74c7-427">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-427">Description</span></span>|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|<span data-ttu-id="e74c7-428">Зарезервировано для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="e74c7-428">Reserved for internal use.</span></span>|
|`Overlapped`|`win:Pointer`|<span data-ttu-id="e74c7-429">Зарезервировано для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="e74c7-429">Reserved for internal use.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="e74c7-430">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e74c7-430">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadcreating-event"></a><span data-ttu-id="e74c7-431">Событие ThreadCreating</span><span class="sxs-lookup"><span data-stu-id="e74c7-431">ThreadCreating event</span></span>

 <span data-ttu-id="e74c7-432">В таблице ниже показаны ключевые слова и уровень.</span><span class="sxs-lookup"><span data-stu-id="e74c7-432">The following table shows the keywords and level.</span></span>

|<span data-ttu-id="e74c7-433">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="e74c7-433">Keyword for raising the event</span></span>|<span data-ttu-id="e74c7-434">Level</span><span class="sxs-lookup"><span data-stu-id="e74c7-434">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e74c7-435">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e74c7-435">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e74c7-436">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="e74c7-436">Informational (4)</span></span>|

 <span data-ttu-id="e74c7-437">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="e74c7-437">The following table shows the event information.</span></span>

|<span data-ttu-id="e74c7-438">Событие</span><span class="sxs-lookup"><span data-stu-id="e74c7-438">Event</span></span>|<span data-ttu-id="e74c7-439">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="e74c7-439">Event ID</span></span>|<span data-ttu-id="e74c7-440">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-440">Description</span></span>|
|----------------|---------------|-----------------|
|`ThreadCreating`|<span data-ttu-id="e74c7-441">70</span><span class="sxs-lookup"><span data-stu-id="e74c7-441">70</span></span>|<span data-ttu-id="e74c7-442">Поток создан.</span><span class="sxs-lookup"><span data-stu-id="e74c7-442">Thread has been created.</span></span>|

 <span data-ttu-id="e74c7-443">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="e74c7-443">The following table shows the event data.</span></span>

|<span data-ttu-id="e74c7-444">Имя поля</span><span class="sxs-lookup"><span data-stu-id="e74c7-444">Field name</span></span>|<span data-ttu-id="e74c7-445">Тип данных</span><span class="sxs-lookup"><span data-stu-id="e74c7-445">Data type</span></span>|<span data-ttu-id="e74c7-446">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-446">Description</span></span>|
|----------------|---------------|-----------------|
|`ID`|`win:Pointer`|<span data-ttu-id="e74c7-447">Идентификатор потока</span><span class="sxs-lookup"><span data-stu-id="e74c7-447">Thread ID</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="e74c7-448">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e74c7-448">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadrunning-event"></a><span data-ttu-id="e74c7-449">Событие ThreadRunning</span><span class="sxs-lookup"><span data-stu-id="e74c7-449">ThreadRunning event</span></span>

 <span data-ttu-id="e74c7-450">В таблице ниже показаны ключевые слова и уровень.</span><span class="sxs-lookup"><span data-stu-id="e74c7-450">The following table shows the keywords and level.</span></span>

|<span data-ttu-id="e74c7-451">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="e74c7-451">Keyword for raising the event</span></span>|<span data-ttu-id="e74c7-452">Level</span><span class="sxs-lookup"><span data-stu-id="e74c7-452">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="e74c7-453">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e74c7-453">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e74c7-454">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="e74c7-454">Informational (4)</span></span>|

 <span data-ttu-id="e74c7-455">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="e74c7-455">The following table shows the event information.</span></span>

|<span data-ttu-id="e74c7-456">Событие</span><span class="sxs-lookup"><span data-stu-id="e74c7-456">Event</span></span>|<span data-ttu-id="e74c7-457">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="e74c7-457">Event ID</span></span>|<span data-ttu-id="e74c7-458">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-458">Description</span></span>|
|----------------|---------------|-----------------|
|`ThreadRunning`|<span data-ttu-id="e74c7-459">71</span><span class="sxs-lookup"><span data-stu-id="e74c7-459">71</span></span>|<span data-ttu-id="e74c7-460">Поток начал выполнение.</span><span class="sxs-lookup"><span data-stu-id="e74c7-460">Thread has started running.</span></span>|

 <span data-ttu-id="e74c7-461">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="e74c7-461">The following table shows the event data.</span></span>

|<span data-ttu-id="e74c7-462">Имя поля</span><span class="sxs-lookup"><span data-stu-id="e74c7-462">Field name</span></span>|<span data-ttu-id="e74c7-463">Тип данных</span><span class="sxs-lookup"><span data-stu-id="e74c7-463">Data type</span></span>|<span data-ttu-id="e74c7-464">Описание</span><span class="sxs-lookup"><span data-stu-id="e74c7-464">Description</span></span>|
|----------------|---------------|-----------------|
|`ID`|`win:Pointer`|<span data-ttu-id="e74c7-465">Идентификатор потока</span><span class="sxs-lookup"><span data-stu-id="e74c7-465">Thread ID</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="e74c7-466">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="e74c7-466">Unique ID for the instance of CoreCLR.</span></span>|
