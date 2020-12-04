---
title: События среды выполнения ThreadPool
description: См. раздел События пула потоков среды выполнения .NET, собирающий диагностические сведения о пуле потоков в .NET Core. События пула потоков — это события пула рабочих потоков или события пула потоков ввода-вывода.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- ThreadPool events (CoreCLR)
- ETW, thread pool events (CoreCLR)
ms.openlocfilehash: cdd6041c5842d4922c60e33daf6db366f7d35327
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96594122"
---
# <a name="net-runtime-thread-pool-events"></a><span data-ttu-id="00cab-104">События пула потоков среды выполнения .NET</span><span class="sxs-lookup"><span data-stu-id="00cab-104">.NET runtime thread pool events</span></span>

<span data-ttu-id="00cab-105">Эти события собираются сведения о рабочем процессе и потоках ввода-вывода в ThreadPool.</span><span class="sxs-lookup"><span data-stu-id="00cab-105">These events collect information about worker and I/O threads in the threadpool.</span></span> <span data-ttu-id="00cab-106">Дополнительные сведения об использовании этих событий в целях диагностики см. в разделе [ведение журнала и трассировка приложений .NET](../../core/diagnostics/logging-tracing.md) .</span><span class="sxs-lookup"><span data-stu-id="00cab-106">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="iothreadcreate_v1-event"></a><span data-ttu-id="00cab-107">IOThreadCreate_V1 событие</span><span class="sxs-lookup"><span data-stu-id="00cab-107">IOThreadCreate_V1 event</span></span>

 <span data-ttu-id="00cab-108">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="00cab-108">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="00cab-109">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="00cab-109">Keyword for raising the event</span></span>|<span data-ttu-id="00cab-110">Level</span><span class="sxs-lookup"><span data-stu-id="00cab-110">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="00cab-111">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="00cab-111">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="00cab-112">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="00cab-112">Informational (4)</span></span>|

 <span data-ttu-id="00cab-113">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="00cab-113">The following table shows the event information.</span></span>

|<span data-ttu-id="00cab-114">Событие</span><span class="sxs-lookup"><span data-stu-id="00cab-114">Event</span></span>|<span data-ttu-id="00cab-115">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="00cab-115">Event ID</span></span>|<span data-ttu-id="00cab-116">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="00cab-116">Raised when</span></span>|
|-----------------------------------|-----------|
|`IOThreadCreate_V1`|<span data-ttu-id="00cab-117">44</span><span class="sxs-lookup"><span data-stu-id="00cab-117">44</span></span>|<span data-ttu-id="00cab-118">Поток ввода-вывода создается в пуле потоков.</span><span class="sxs-lookup"><span data-stu-id="00cab-118">An I/O thread is created in the thread pool.</span></span>|

 <span data-ttu-id="00cab-119">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="00cab-119">The following table shows the event data.</span></span>

|<span data-ttu-id="00cab-120">Имя поля</span><span class="sxs-lookup"><span data-stu-id="00cab-120">Field name</span></span>|<span data-ttu-id="00cab-121">Тип данных</span><span class="sxs-lookup"><span data-stu-id="00cab-121">Data type</span></span>|<span data-ttu-id="00cab-122">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-122">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|<span data-ttu-id="00cab-123">Число потоков ввода-вывода, включая вновь созданный поток.</span><span class="sxs-lookup"><span data-stu-id="00cab-123">Number of I/O threads, including the newly created thread.</span></span>|
|`NumRetired`|`win:UInt64`|<span data-ttu-id="00cab-124">Число завершенных рабочих потоков.</span><span class="sxs-lookup"><span data-stu-id="00cab-124">Number of retired worker threads.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="00cab-125">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="00cab-125">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="iothreadterminate_v1-event"></a><span data-ttu-id="00cab-126">IOThreadTerminate_V1 событие</span><span class="sxs-lookup"><span data-stu-id="00cab-126">IOThreadTerminate_V1 event</span></span>

 <span data-ttu-id="00cab-127">В следующей таблице показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="00cab-127">The following table shows the keyword and level</span></span>

|<span data-ttu-id="00cab-128">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="00cab-128">Keyword for raising the event</span></span>|<span data-ttu-id="00cab-129">Level</span><span class="sxs-lookup"><span data-stu-id="00cab-129">Level</span></span>
|-----------------------------------|-----------
|<span data-ttu-id="00cab-130">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="00cab-130">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="00cab-131">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="00cab-131">Informational (4)</span></span>

 <span data-ttu-id="00cab-132">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="00cab-132">The following table shows the event information.</span></span>

|<span data-ttu-id="00cab-133">Событие</span><span class="sxs-lookup"><span data-stu-id="00cab-133">Event</span></span>|<span data-ttu-id="00cab-134">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="00cab-134">Event ID</span></span>|<span data-ttu-id="00cab-135">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="00cab-135">Raised when</span></span>|
|-----------|--------------|-----------------|
|`IOThreadTerminate`|<span data-ttu-id="00cab-136">45</span><span class="sxs-lookup"><span data-stu-id="00cab-136">45</span></span>|<span data-ttu-id="00cab-137">Поток ввода-вывода завершается в пуле потоков.</span><span class="sxs-lookup"><span data-stu-id="00cab-137">An I/O thread is terminated in the thread pool.</span></span>|

 <span data-ttu-id="00cab-138">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="00cab-138">The following table shows the event data.</span></span>

|<span data-ttu-id="00cab-139">Имя поля</span><span class="sxs-lookup"><span data-stu-id="00cab-139">Field name</span></span>|<span data-ttu-id="00cab-140">Тип данных</span><span class="sxs-lookup"><span data-stu-id="00cab-140">Data type</span></span>|<span data-ttu-id="00cab-141">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-141">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|<span data-ttu-id="00cab-142">Число потоков ввода-вывода, остающихся в пуле потоков.</span><span class="sxs-lookup"><span data-stu-id="00cab-142">Number of I/O threads remaining in the thread pool.</span></span>|
|`NumRetired`|`win:UInt64`|<span data-ttu-id="00cab-143">Число завершенных потоков ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="00cab-143">Number of retired I/O threads.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="00cab-144">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="00cab-144">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="iothreadretire_v1-event"></a><span data-ttu-id="00cab-145">IOThreadRetire_V1 событие</span><span class="sxs-lookup"><span data-stu-id="00cab-145">IOThreadRetire_V1 event</span></span>

 <span data-ttu-id="00cab-146">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="00cab-146">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="00cab-147">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="00cab-147">Keyword for raising the event</span></span>|<span data-ttu-id="00cab-148">Level</span><span class="sxs-lookup"><span data-stu-id="00cab-148">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="00cab-149">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="00cab-149">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="00cab-150">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="00cab-150">Informational (4)</span></span>|

 <span data-ttu-id="00cab-151">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="00cab-151">The following table shows the event information.</span></span>

|<span data-ttu-id="00cab-152">Событие</span><span class="sxs-lookup"><span data-stu-id="00cab-152">Event</span></span>|<span data-ttu-id="00cab-153">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="00cab-153">Event ID</span></span>|<span data-ttu-id="00cab-154">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="00cab-154">Raised when</span></span>|
|-----------|--------------|-----------------|
|`IOThreadRetire_V1`|<span data-ttu-id="00cab-155">46</span><span class="sxs-lookup"><span data-stu-id="00cab-155">46</span></span>|<span data-ttu-id="00cab-156">Поток ввода-вывода становится кандидатом на завершение.</span><span class="sxs-lookup"><span data-stu-id="00cab-156">An I/O thread becomes a retirement candidate.</span></span>|

 <span data-ttu-id="00cab-157">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="00cab-157">The following table shows the event data.</span></span>

|<span data-ttu-id="00cab-158">Имя поля</span><span class="sxs-lookup"><span data-stu-id="00cab-158">Field name</span></span>|<span data-ttu-id="00cab-159">Тип данных</span><span class="sxs-lookup"><span data-stu-id="00cab-159">Data type</span></span>|<span data-ttu-id="00cab-160">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-160">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|<span data-ttu-id="00cab-161">Число потоков ввода-вывода, остающихся в пуле потоков.</span><span class="sxs-lookup"><span data-stu-id="00cab-161">Number of I/O threads remaining in the thread pool.</span></span>|
|`NumRetired`|`win:UInt64`|<span data-ttu-id="00cab-162">Число завершенных потоков ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="00cab-162">Number of retired I/O threads.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="00cab-163">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="00cab-163">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="iothreadunretire_v1-event"></a><span data-ttu-id="00cab-164">IOThreadUnretire_V1 событие</span><span class="sxs-lookup"><span data-stu-id="00cab-164">IOThreadUnretire_V1 event</span></span>

 <span data-ttu-id="00cab-165">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="00cab-165">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="00cab-166">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="00cab-166">Keyword for raising the event</span></span>|<span data-ttu-id="00cab-167">Level</span><span class="sxs-lookup"><span data-stu-id="00cab-167">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="00cab-168">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="00cab-168">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="00cab-169">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="00cab-169">Informational (4)</span></span>|

 <span data-ttu-id="00cab-170">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="00cab-170">The following table shows the event information.</span></span>

|<span data-ttu-id="00cab-171">Событие</span><span class="sxs-lookup"><span data-stu-id="00cab-171">Event</span></span>|<span data-ttu-id="00cab-172">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="00cab-172">Event ID</span></span>|<span data-ttu-id="00cab-173">Условие вызова</span><span class="sxs-lookup"><span data-stu-id="00cab-173">Raised when</span></span>|
|-----------|--------------|-----------------|
|`IOThreadUnretire_V1`|<span data-ttu-id="00cab-174">47</span><span class="sxs-lookup"><span data-stu-id="00cab-174">47</span></span>|<span data-ttu-id="00cab-175">Завершенный поток ввода-вывода повторно активируется из-за ввода-вывода, поступающего в течение периода ожидания после того, как поток стал кандидатом на завершение.</span><span class="sxs-lookup"><span data-stu-id="00cab-175">An I/O thread is unretired because of I/O that arrives within a waiting period after the thread becomes a retirement candidate.</span></span>|

 <span data-ttu-id="00cab-176">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="00cab-176">The following table shows the event data.</span></span>

|<span data-ttu-id="00cab-177">Имя поля</span><span class="sxs-lookup"><span data-stu-id="00cab-177">Field name</span></span>|<span data-ttu-id="00cab-178">Тип данных</span><span class="sxs-lookup"><span data-stu-id="00cab-178">Data type</span></span>|<span data-ttu-id="00cab-179">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-179">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|<span data-ttu-id="00cab-180">Число потоков ввода-вывода в пуле потоков, включая этот поток.</span><span class="sxs-lookup"><span data-stu-id="00cab-180">Number of I/O threads in the thread pool, including this one.</span></span>|
|`NumRetired`|`win:UInt64`|<span data-ttu-id="00cab-181">Число завершенных потоков ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="00cab-181">Number of retired I/O threads.</span></span>|
|`ClrInstanceID`|`Win:UInt16`|<span data-ttu-id="00cab-182">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="00cab-182">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadstart-event"></a><span data-ttu-id="00cab-183">Событие Среадпулворкерсреадстарт</span><span class="sxs-lookup"><span data-stu-id="00cab-183">ThreadPoolWorkerThreadStart event</span></span>

|<span data-ttu-id="00cab-184">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="00cab-184">Keyword for raising the event</span></span>|<span data-ttu-id="00cab-185">Level</span><span class="sxs-lookup"><span data-stu-id="00cab-185">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="00cab-186">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="00cab-186">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="00cab-187">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="00cab-187">Informational (4)</span></span>|

|<span data-ttu-id="00cab-188">Событие</span><span class="sxs-lookup"><span data-stu-id="00cab-188">Event</span></span>|<span data-ttu-id="00cab-189">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="00cab-189">Event ID</span></span>|<span data-ttu-id="00cab-190">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-190">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadStart`|<span data-ttu-id="00cab-191">50</span><span class="sxs-lookup"><span data-stu-id="00cab-191">50</span></span>|<span data-ttu-id="00cab-192">Создается рабочий поток.</span><span class="sxs-lookup"><span data-stu-id="00cab-192">A worker thread is created.</span></span>|

|<span data-ttu-id="00cab-193">Имя поля</span><span class="sxs-lookup"><span data-stu-id="00cab-193">Field name</span></span>|<span data-ttu-id="00cab-194">Тип данных</span><span class="sxs-lookup"><span data-stu-id="00cab-194">Data type</span></span>|<span data-ttu-id="00cab-195">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-195">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="00cab-196">Число рабочих потоков, доступных для выполнения процесса, включая уже работающие потоки.</span><span class="sxs-lookup"><span data-stu-id="00cab-196">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="00cab-197">Число рабочих потоков, которые недоступны для выполнения процесса, но находятся в резерве на случай, если позже понадобятся дополнительные потоки.</span><span class="sxs-lookup"><span data-stu-id="00cab-197">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="00cab-198">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="00cab-198">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadstop-event"></a><span data-ttu-id="00cab-199">Событие Среадпулворкерсреадстоп</span><span class="sxs-lookup"><span data-stu-id="00cab-199">ThreadPoolWorkerThreadStop event</span></span>

|<span data-ttu-id="00cab-200">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="00cab-200">Keyword for raising the event</span></span>|<span data-ttu-id="00cab-201">Level</span><span class="sxs-lookup"><span data-stu-id="00cab-201">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="00cab-202">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="00cab-202">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="00cab-203">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="00cab-203">Informational (4)</span></span>|

|<span data-ttu-id="00cab-204">Событие</span><span class="sxs-lookup"><span data-stu-id="00cab-204">Event</span></span>|<span data-ttu-id="00cab-205">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="00cab-205">Event ID</span></span>|<span data-ttu-id="00cab-206">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-206">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadStop`|<span data-ttu-id="00cab-207">51</span><span class="sxs-lookup"><span data-stu-id="00cab-207">51</span></span>|<span data-ttu-id="00cab-208">Рабочий поток останавливается.</span><span class="sxs-lookup"><span data-stu-id="00cab-208">A worker thread is stopped.</span></span>|

|<span data-ttu-id="00cab-209">Имя поля</span><span class="sxs-lookup"><span data-stu-id="00cab-209">Field name</span></span>|<span data-ttu-id="00cab-210">Тип данных</span><span class="sxs-lookup"><span data-stu-id="00cab-210">Data type</span></span>|<span data-ttu-id="00cab-211">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-211">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="00cab-212">Число рабочих потоков, доступных для выполнения процесса, включая уже работающие потоки.</span><span class="sxs-lookup"><span data-stu-id="00cab-212">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="00cab-213">Число рабочих потоков, которые недоступны для выполнения процесса, но находятся в резерве на случай, если позже понадобятся дополнительные потоки.</span><span class="sxs-lookup"><span data-stu-id="00cab-213">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="00cab-214">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="00cab-214">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadwait-event"></a><span data-ttu-id="00cab-215">Событие Среадпулворкерсреадваит</span><span class="sxs-lookup"><span data-stu-id="00cab-215">ThreadPoolWorkerThreadWait event</span></span>

|<span data-ttu-id="00cab-216">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="00cab-216">Keyword for raising the event</span></span>|<span data-ttu-id="00cab-217">Level</span><span class="sxs-lookup"><span data-stu-id="00cab-217">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="00cab-218">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="00cab-218">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="00cab-219">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="00cab-219">Informational (4)</span></span>|

|<span data-ttu-id="00cab-220">Событие</span><span class="sxs-lookup"><span data-stu-id="00cab-220">Event</span></span>|<span data-ttu-id="00cab-221">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="00cab-221">Event ID</span></span>|<span data-ttu-id="00cab-222">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-222">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadWait`|<span data-ttu-id="00cab-223">57</span><span class="sxs-lookup"><span data-stu-id="00cab-223">57</span></span>|<span data-ttu-id="00cab-224">Рабочий поток начинает ожидание работы.</span><span class="sxs-lookup"><span data-stu-id="00cab-224">A worker thread starts waiting for work.</span></span>|

|<span data-ttu-id="00cab-225">Имя поля</span><span class="sxs-lookup"><span data-stu-id="00cab-225">Field name</span></span>|<span data-ttu-id="00cab-226">Тип данных</span><span class="sxs-lookup"><span data-stu-id="00cab-226">Data type</span></span>|<span data-ttu-id="00cab-227">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-227">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="00cab-228">Число рабочих потоков, доступных для выполнения процесса, включая уже работающие потоки.</span><span class="sxs-lookup"><span data-stu-id="00cab-228">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="00cab-229">Число рабочих потоков, которые недоступны для выполнения процесса, но находятся в резерве на случай, если позже понадобятся дополнительные потоки.</span><span class="sxs-lookup"><span data-stu-id="00cab-229">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="00cab-230">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="00cab-230">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadretirementstart-event"></a><span data-ttu-id="00cab-231">Событие Среадпулворкерсреадретирементстарт</span><span class="sxs-lookup"><span data-stu-id="00cab-231">ThreadPoolWorkerThreadRetirementStart event</span></span>

|<span data-ttu-id="00cab-232">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="00cab-232">Keyword for raising the event</span></span>|<span data-ttu-id="00cab-233">Level</span><span class="sxs-lookup"><span data-stu-id="00cab-233">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="00cab-234">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="00cab-234">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="00cab-235">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="00cab-235">Informational (4)</span></span>|

|<span data-ttu-id="00cab-236">Событие</span><span class="sxs-lookup"><span data-stu-id="00cab-236">Event</span></span>|<span data-ttu-id="00cab-237">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="00cab-237">Event ID</span></span>|<span data-ttu-id="00cab-238">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-238">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadRetirementStart`|<span data-ttu-id="00cab-239">52</span><span class="sxs-lookup"><span data-stu-id="00cab-239">52</span></span>|<span data-ttu-id="00cab-240">Рабочий поток завершается.</span><span class="sxs-lookup"><span data-stu-id="00cab-240">A worker thread retires.</span></span>|

|<span data-ttu-id="00cab-241">Имя поля</span><span class="sxs-lookup"><span data-stu-id="00cab-241">Field name</span></span>|<span data-ttu-id="00cab-242">Тип данных</span><span class="sxs-lookup"><span data-stu-id="00cab-242">Data type</span></span>|<span data-ttu-id="00cab-243">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-243">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="00cab-244">Число рабочих потоков, доступных для выполнения процесса, включая уже работающие потоки.</span><span class="sxs-lookup"><span data-stu-id="00cab-244">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="00cab-245">Число рабочих потоков, которые недоступны для выполнения процесса, но находятся в резерве на случай, если позже понадобятся дополнительные потоки.</span><span class="sxs-lookup"><span data-stu-id="00cab-245">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="00cab-246">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="00cab-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadretirementstop-event"></a><span data-ttu-id="00cab-247">Событие Среадпулворкерсреадретирементстоп</span><span class="sxs-lookup"><span data-stu-id="00cab-247">ThreadPoolWorkerThreadRetirementStop event</span></span>

|<span data-ttu-id="00cab-248">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="00cab-248">Keyword for raising the event</span></span>|<span data-ttu-id="00cab-249">Level</span><span class="sxs-lookup"><span data-stu-id="00cab-249">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="00cab-250">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="00cab-250">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="00cab-251">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="00cab-251">Informational (4)</span></span>|

|<span data-ttu-id="00cab-252">Событие</span><span class="sxs-lookup"><span data-stu-id="00cab-252">Event</span></span>|<span data-ttu-id="00cab-253">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="00cab-253">Event ID</span></span>|<span data-ttu-id="00cab-254">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-254">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadRetirementStop`|<span data-ttu-id="00cab-255">53</span><span class="sxs-lookup"><span data-stu-id="00cab-255">53</span></span>|<span data-ttu-id="00cab-256">Завершенный рабочий поток снова становится активным.</span><span class="sxs-lookup"><span data-stu-id="00cab-256">A retired worker thread becomes active again.</span></span>|

|<span data-ttu-id="00cab-257">Имя поля</span><span class="sxs-lookup"><span data-stu-id="00cab-257">Field name</span></span>|<span data-ttu-id="00cab-258">Тип данных</span><span class="sxs-lookup"><span data-stu-id="00cab-258">Data type</span></span>|<span data-ttu-id="00cab-259">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-259">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="00cab-260">Число рабочих потоков, доступных для выполнения процесса, включая уже работающие потоки.</span><span class="sxs-lookup"><span data-stu-id="00cab-260">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="00cab-261">Число рабочих потоков, которые недоступны для выполнения процесса, но находятся в резерве на случай, если позже понадобятся дополнительные потоки.</span><span class="sxs-lookup"><span data-stu-id="00cab-261">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="00cab-262">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="00cab-262">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadadjustmentsample-event"></a><span data-ttu-id="00cab-263">Событие Среадпулворкерсреададжустментсампле</span><span class="sxs-lookup"><span data-stu-id="00cab-263">ThreadPoolWorkerThreadAdjustmentSample event</span></span>

 <span data-ttu-id="00cab-264">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="00cab-264">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="00cab-265">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="00cab-265">Keyword for raising the event</span></span>|<span data-ttu-id="00cab-266">Level</span><span class="sxs-lookup"><span data-stu-id="00cab-266">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="00cab-267">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="00cab-267">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="00cab-268">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="00cab-268">Informational (4)</span></span>|

 <span data-ttu-id="00cab-269">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="00cab-269">The following table shows the event information.</span></span>

|<span data-ttu-id="00cab-270">Событие</span><span class="sxs-lookup"><span data-stu-id="00cab-270">Event</span></span>|<span data-ttu-id="00cab-271">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="00cab-271">Event ID</span></span>|<span data-ttu-id="00cab-272">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-272">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentSample`|<span data-ttu-id="00cab-273">54</span><span class="sxs-lookup"><span data-stu-id="00cab-273">54</span></span>|<span data-ttu-id="00cab-274">Указывает на сбор сведений для одного образца, то есть измерение пропускной способности с определенным уровнем параллелизма в некоторый момент времени.</span><span class="sxs-lookup"><span data-stu-id="00cab-274">Refers to the collection of information for one sample; that is, a measurement of throughput with a certain concurrency level, in an instant of time.</span></span>|

 <span data-ttu-id="00cab-275">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="00cab-275">The following table shows the event data.</span></span>

|<span data-ttu-id="00cab-276">Имя поля</span><span class="sxs-lookup"><span data-stu-id="00cab-276">Field name</span></span>|<span data-ttu-id="00cab-277">Тип данных</span><span class="sxs-lookup"><span data-stu-id="00cab-277">Data type</span></span>|<span data-ttu-id="00cab-278">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-278">Description</span></span>|
|----------------|---------------|-----------------|
|`Throughput`|`win:Double`|<span data-ttu-id="00cab-279">Число завершений в единицу времени.</span><span class="sxs-lookup"><span data-stu-id="00cab-279">Number of completions per unit of time.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="00cab-280">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="00cab-280">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadadjustmentadjustment-event"></a><span data-ttu-id="00cab-281">Событие Среадпулворкерсреададжустментаджустмент</span><span class="sxs-lookup"><span data-stu-id="00cab-281">ThreadPoolWorkerThreadAdjustmentAdjustment event</span></span>

 <span data-ttu-id="00cab-282">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="00cab-282">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="00cab-283">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="00cab-283">Keyword for raising the event</span></span>|<span data-ttu-id="00cab-284">Level</span><span class="sxs-lookup"><span data-stu-id="00cab-284">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="00cab-285">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="00cab-285">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="00cab-286">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="00cab-286">Informational (4)</span></span>|

 <span data-ttu-id="00cab-287">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="00cab-287">The following table shows the event information.</span></span>

|<span data-ttu-id="00cab-288">Событие</span><span class="sxs-lookup"><span data-stu-id="00cab-288">Event</span></span>|<span data-ttu-id="00cab-289">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="00cab-289">Event ID</span></span>|<span data-ttu-id="00cab-290">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-290">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentAdjustment`|<span data-ttu-id="00cab-291">55</span><span class="sxs-lookup"><span data-stu-id="00cab-291">55</span></span>|<span data-ttu-id="00cab-292">Регистрирует изменение в управлении, когда алгоритм вставки потока (поиск экстремума) определяет, что произошло изменение уровня параллелизма.</span><span class="sxs-lookup"><span data-stu-id="00cab-292">Records a change in control, when the thread injection (hill-climbing) algorithm determines that a change in concurrency level is in place.</span></span>|

 <span data-ttu-id="00cab-293">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="00cab-293">The following table shows the event data.</span></span>

|<span data-ttu-id="00cab-294">Имя поля</span><span class="sxs-lookup"><span data-stu-id="00cab-294">Field name</span></span>|<span data-ttu-id="00cab-295">Тип данных</span><span class="sxs-lookup"><span data-stu-id="00cab-295">Data type</span></span>|<span data-ttu-id="00cab-296">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-296">Description</span></span>|
|----------------|---------------|-----------------|
|`AverageThroughput`|`win:Double`|<span data-ttu-id="00cab-297">Средняя пропускная способность образца измерений.</span><span class="sxs-lookup"><span data-stu-id="00cab-297">Average throughput of a sample of measurements.</span></span>|
|`NewWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="00cab-298">Новое число активных рабочих потоков.</span><span class="sxs-lookup"><span data-stu-id="00cab-298">New number of active worker threads.</span></span>|
|`Reason`|`win:UInt32`|<span data-ttu-id="00cab-299">Причина корректировки:</span><span class="sxs-lookup"><span data-stu-id="00cab-299">Reason for the adjustment.</span></span><br /><br /> <span data-ttu-id="00cab-300">`0x0` Прогрева.</span><span class="sxs-lookup"><span data-stu-id="00cab-300">`0x0` - Warmup.</span></span><br /><br /> <span data-ttu-id="00cab-301">`0x1` Инициализации.</span><span class="sxs-lookup"><span data-stu-id="00cab-301">`0x1` - Initializing.</span></span><br /><br /> <span data-ttu-id="00cab-302">`0x2` — Случайное перемещение.</span><span class="sxs-lookup"><span data-stu-id="00cab-302">`0x2` - Random move.</span></span><br /><br /> <span data-ttu-id="00cab-303">`0x3` -Увеличиваться перемещение.</span><span class="sxs-lookup"><span data-stu-id="00cab-303">`0x3` - Climbing move.</span></span><br /><br /> <span data-ttu-id="00cab-304">`0x4` — Точка изменения.</span><span class="sxs-lookup"><span data-stu-id="00cab-304">`0x4` - Change point.</span></span><br /><br /> <span data-ttu-id="00cab-305">`0x5` Стабилизация.</span><span class="sxs-lookup"><span data-stu-id="00cab-305">`0x5` - Stabilizing.</span></span><br /><br /> <span data-ttu-id="00cab-306">`0x6` Перегрузка.</span><span class="sxs-lookup"><span data-stu-id="00cab-306">`0x6` - Starvation.</span></span><br /><br /> <span data-ttu-id="00cab-307">`0x7` -Истекло время ожидания потока.</span><span class="sxs-lookup"><span data-stu-id="00cab-307">`0x7` - Thread timed out.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="00cab-308">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="00cab-308">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadadjustmentstats-event"></a><span data-ttu-id="00cab-309">Событие Среадпулворкерсреададжустментстатс</span><span class="sxs-lookup"><span data-stu-id="00cab-309">ThreadPoolWorkerThreadAdjustmentStats event</span></span>

 <span data-ttu-id="00cab-310">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="00cab-310">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="00cab-311">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="00cab-311">Keyword for raising the event</span></span>|<span data-ttu-id="00cab-312">Level</span><span class="sxs-lookup"><span data-stu-id="00cab-312">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="00cab-313">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="00cab-313">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="00cab-314">Подробный (5)</span><span class="sxs-lookup"><span data-stu-id="00cab-314">Verbose (5)</span></span>

 <span data-ttu-id="00cab-315">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="00cab-315">The following table shows the event information.</span></span>

|<span data-ttu-id="00cab-316">Событие</span><span class="sxs-lookup"><span data-stu-id="00cab-316">Event</span></span>|<span data-ttu-id="00cab-317">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="00cab-317">Event ID</span></span>|<span data-ttu-id="00cab-318">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-318">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentStats`|<span data-ttu-id="00cab-319">56</span><span class="sxs-lookup"><span data-stu-id="00cab-319">56</span></span>|<span data-ttu-id="00cab-320">Собирает данные по пулу потоков.</span><span class="sxs-lookup"><span data-stu-id="00cab-320">Gathers data on the thread pool.</span></span>|

 <span data-ttu-id="00cab-321">В следующей таблице показаны данные события.</span><span class="sxs-lookup"><span data-stu-id="00cab-321">The following table shows the event data</span></span>

|<span data-ttu-id="00cab-322">Имя поля</span><span class="sxs-lookup"><span data-stu-id="00cab-322">Field name</span></span>|<span data-ttu-id="00cab-323">Тип данных</span><span class="sxs-lookup"><span data-stu-id="00cab-323">Data type</span></span>|<span data-ttu-id="00cab-324">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-324">Description</span></span>|
|----------------|---------------|-----------------|
|`Duration`|`win:Double`|<span data-ttu-id="00cab-325">Время в секундах, в течение которого выполнялся сбор статистики.</span><span class="sxs-lookup"><span data-stu-id="00cab-325">Amount of time, in seconds, during which these statistics were collected.</span></span>|
|`Throughput`|`win:Double`|<span data-ttu-id="00cab-326">Среднее число завершений в секунду в течение данного интервала.</span><span class="sxs-lookup"><span data-stu-id="00cab-326">Average number of completions per second during this interval.</span></span>|
|`ThreadWave`|`win:Double`|<span data-ttu-id="00cab-327">Зарезервировано для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="00cab-327">Reserved for internal use.</span></span>|
|`ThroughputWave`|`win:Double`|<span data-ttu-id="00cab-328">Зарезервировано для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="00cab-328">Reserved for internal use.</span></span>|
|`ThroughputErrorEstimate`|`win:Double`|<span data-ttu-id="00cab-329">Зарезервировано для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="00cab-329">Reserved for internal use.</span></span>|
|`AverageThroughputErrorEstimate`|`win:Double`|<span data-ttu-id="00cab-330">Зарезервировано для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="00cab-330">Reserved for internal use.</span></span>|
|`ThroughputRatio`|`win:Double`|<span data-ttu-id="00cab-331">Относительное улучшение пропускной способности, вызванное изменениями числа активных рабочих потоков в течение этого интервала.</span><span class="sxs-lookup"><span data-stu-id="00cab-331">The relative improvement in throughput caused by variations in active worker thread count during this interval.</span></span>|
|`Confidence`|`win:Double`|<span data-ttu-id="00cab-332">Мера обоснованности поля ThroughputRatio.</span><span class="sxs-lookup"><span data-stu-id="00cab-332">A measure of the validity of the ThroughputRatio field.</span></span>|
|`NewcontrolSetting`|`win:Double`|<span data-ttu-id="00cab-333">Число активных рабочих потоков, которое будет служить основой для будущих изменений числа активных потоков.</span><span class="sxs-lookup"><span data-stu-id="00cab-333">The number of active worker threads that will serve as the baseline for future variations in active thread count.</span></span>|
|`NewThreadWaveMagnitude`|`win:UInt16`|<span data-ttu-id="00cab-334">Величина будущих изменений числа активных потоков.</span><span class="sxs-lookup"><span data-stu-id="00cab-334">The magnitude of future variations in active thread count.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="00cab-335">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="00cab-335">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolenqueue-event"></a><span data-ttu-id="00cab-336">Событие Среадпуленкуеуе</span><span class="sxs-lookup"><span data-stu-id="00cab-336">ThreadPoolEnqueue event</span></span>

 <span data-ttu-id="00cab-337">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="00cab-337">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="00cab-338">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="00cab-338">Keyword for raising the event</span></span>|<span data-ttu-id="00cab-339">Level</span><span class="sxs-lookup"><span data-stu-id="00cab-339">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="00cab-340">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="00cab-340">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="00cab-341">Подробный (5)</span><span class="sxs-lookup"><span data-stu-id="00cab-341">Verbose (5)</span></span>

 <span data-ttu-id="00cab-342">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="00cab-342">The following table shows the event information.</span></span>

|<span data-ttu-id="00cab-343">Событие</span><span class="sxs-lookup"><span data-stu-id="00cab-343">Event</span></span>|<span data-ttu-id="00cab-344">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="00cab-344">Event ID</span></span>|<span data-ttu-id="00cab-345">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-345">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolEnqueue`|<span data-ttu-id="00cab-346">61</span><span class="sxs-lookup"><span data-stu-id="00cab-346">61</span></span>|<span data-ttu-id="00cab-347">Рабочий элемент был поставлен в очередь пула потоков.</span><span class="sxs-lookup"><span data-stu-id="00cab-347">A work item was enqueued in the thread pool queue.</span></span>|

 <span data-ttu-id="00cab-348">В следующей таблице показаны данные события.</span><span class="sxs-lookup"><span data-stu-id="00cab-348">The following table shows the event data</span></span>

|<span data-ttu-id="00cab-349">Имя поля</span><span class="sxs-lookup"><span data-stu-id="00cab-349">Field name</span></span>|<span data-ttu-id="00cab-350">Тип данных</span><span class="sxs-lookup"><span data-stu-id="00cab-350">Data type</span></span>|<span data-ttu-id="00cab-351">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-351">Description</span></span>|
|----------------|---------------|-----------------|
|`WorkID`|`win:Pointer`|<span data-ttu-id="00cab-352">Указатель на рабочий запрос.</span><span class="sxs-lookup"><span data-stu-id="00cab-352">Pointer to the work request.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="00cab-353">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="00cab-353">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadpooldequeue-event"></a><span data-ttu-id="00cab-354">Событие Среадпулдекуеуе</span><span class="sxs-lookup"><span data-stu-id="00cab-354">ThreadPoolDequeue event</span></span>

 <span data-ttu-id="00cab-355">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="00cab-355">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="00cab-356">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="00cab-356">Keyword for raising the event</span></span>|<span data-ttu-id="00cab-357">Level</span><span class="sxs-lookup"><span data-stu-id="00cab-357">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="00cab-358">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="00cab-358">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="00cab-359">Подробный (5)</span><span class="sxs-lookup"><span data-stu-id="00cab-359">Verbose (5)</span></span>

 <span data-ttu-id="00cab-360">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="00cab-360">The following table shows the event information.</span></span>

|<span data-ttu-id="00cab-361">Событие</span><span class="sxs-lookup"><span data-stu-id="00cab-361">Event</span></span>|<span data-ttu-id="00cab-362">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="00cab-362">Event ID</span></span>|<span data-ttu-id="00cab-363">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-363">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolDequeue`|<span data-ttu-id="00cab-364">62</span><span class="sxs-lookup"><span data-stu-id="00cab-364">62</span></span>|<span data-ttu-id="00cab-365">Рабочий элемент был удален из очереди пула потоков.</span><span class="sxs-lookup"><span data-stu-id="00cab-365">A work item was dequeued from the thread pool queue.</span></span>|

 <span data-ttu-id="00cab-366">В следующей таблице показаны данные события.</span><span class="sxs-lookup"><span data-stu-id="00cab-366">The following table shows the event data</span></span>

|<span data-ttu-id="00cab-367">Имя поля</span><span class="sxs-lookup"><span data-stu-id="00cab-367">Field name</span></span>|<span data-ttu-id="00cab-368">Тип данных</span><span class="sxs-lookup"><span data-stu-id="00cab-368">Data type</span></span>|<span data-ttu-id="00cab-369">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-369">Description</span></span>|
|----------------|---------------|-----------------|
|`WorkID`|`win:Pointer`|<span data-ttu-id="00cab-370">Указатель на рабочий запрос.</span><span class="sxs-lookup"><span data-stu-id="00cab-370">Pointer to the work request.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="00cab-371">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="00cab-371">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadpoolioenqueue-event"></a><span data-ttu-id="00cab-372">Событие Среадпулиоенкуеуе</span><span class="sxs-lookup"><span data-stu-id="00cab-372">ThreadPoolIOEnqueue event</span></span>

 <span data-ttu-id="00cab-373">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="00cab-373">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="00cab-374">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="00cab-374">Keyword for raising the event</span></span>|<span data-ttu-id="00cab-375">Level</span><span class="sxs-lookup"><span data-stu-id="00cab-375">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="00cab-376">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="00cab-376">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="00cab-377">Подробный (5)</span><span class="sxs-lookup"><span data-stu-id="00cab-377">Verbose (5)</span></span>

 <span data-ttu-id="00cab-378">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="00cab-378">The following table shows the event information.</span></span>

|<span data-ttu-id="00cab-379">Событие</span><span class="sxs-lookup"><span data-stu-id="00cab-379">Event</span></span>|<span data-ttu-id="00cab-380">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="00cab-380">Event ID</span></span>|<span data-ttu-id="00cab-381">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-381">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolIOEnqueue`|<span data-ttu-id="00cab-382">63</span><span class="sxs-lookup"><span data-stu-id="00cab-382">63</span></span>|<span data-ttu-id="00cab-383">Поток помещает в очередь уведомление о завершении ввода-вывода после выполнения асинхронного ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="00cab-383">A thread enqueues an IO completion notification after an async IO completion occurs.</span></span>|

 <span data-ttu-id="00cab-384">В следующей таблице показаны данные события.</span><span class="sxs-lookup"><span data-stu-id="00cab-384">The following table shows the event data</span></span>

|<span data-ttu-id="00cab-385">Имя поля</span><span class="sxs-lookup"><span data-stu-id="00cab-385">Field name</span></span>|<span data-ttu-id="00cab-386">Тип данных</span><span class="sxs-lookup"><span data-stu-id="00cab-386">Data type</span></span>|<span data-ttu-id="00cab-387">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-387">Description</span></span>|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|<span data-ttu-id="00cab-388">Зарезервировано для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="00cab-388">Reserved for internal use.</span></span>|
|`Overlapped`|`win:Pointer`|<span data-ttu-id="00cab-389">Зарезервировано для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="00cab-389">Reserved for internal use.</span></span>|
|`MultiDequeues`|`win:Boolean`|<span data-ttu-id="00cab-390">Зарезервировано для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="00cab-390">Reserved for internal use.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="00cab-391">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="00cab-391">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadpooliodequeue-event"></a><span data-ttu-id="00cab-392">Событие Среадпулиодекуеуе</span><span class="sxs-lookup"><span data-stu-id="00cab-392">ThreadPoolIODequeue event</span></span>

 <span data-ttu-id="00cab-393">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="00cab-393">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="00cab-394">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="00cab-394">Keyword for raising the event</span></span>|<span data-ttu-id="00cab-395">Level</span><span class="sxs-lookup"><span data-stu-id="00cab-395">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="00cab-396">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="00cab-396">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="00cab-397">Подробный (5)</span><span class="sxs-lookup"><span data-stu-id="00cab-397">Verbose (5)</span></span>

 <span data-ttu-id="00cab-398">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="00cab-398">The following table shows the event information.</span></span>

|<span data-ttu-id="00cab-399">Событие</span><span class="sxs-lookup"><span data-stu-id="00cab-399">Event</span></span>|<span data-ttu-id="00cab-400">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="00cab-400">Event ID</span></span>|<span data-ttu-id="00cab-401">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-401">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolIODequeue`|<span data-ttu-id="00cab-402">64</span><span class="sxs-lookup"><span data-stu-id="00cab-402">64</span></span>|<span data-ttu-id="00cab-403">Поток выставит в очередь уведомление о завершении ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="00cab-403">A thread dequeues the IO completion notification.</span></span>|

 <span data-ttu-id="00cab-404">В следующей таблице показаны данные события.</span><span class="sxs-lookup"><span data-stu-id="00cab-404">The following table shows the event data</span></span>

|<span data-ttu-id="00cab-405">Имя поля</span><span class="sxs-lookup"><span data-stu-id="00cab-405">Field name</span></span>|<span data-ttu-id="00cab-406">Тип данных</span><span class="sxs-lookup"><span data-stu-id="00cab-406">Data type</span></span>|<span data-ttu-id="00cab-407">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-407">Description</span></span>|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|<span data-ttu-id="00cab-408">Зарезервировано для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="00cab-408">Reserved for internal use.</span></span>|
|`Overlapped`|`win:Pointer`|<span data-ttu-id="00cab-409">Зарезервировано для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="00cab-409">Reserved for internal use.</span></span>|
|`MultiDequeues`|`win:Boolean`|<span data-ttu-id="00cab-410">Зарезервировано для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="00cab-410">Reserved for internal use.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="00cab-411">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="00cab-411">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadpooliopack-event"></a><span data-ttu-id="00cab-412">Событие Среадпулиопакк</span><span class="sxs-lookup"><span data-stu-id="00cab-412">ThreadPoolIOPack event</span></span>

 <span data-ttu-id="00cab-413">В таблице ниже показаны ключевое слово и уровень.</span><span class="sxs-lookup"><span data-stu-id="00cab-413">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="00cab-414">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="00cab-414">Keyword for raising the event</span></span>|<span data-ttu-id="00cab-415">Level</span><span class="sxs-lookup"><span data-stu-id="00cab-415">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="00cab-416">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="00cab-416">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="00cab-417">Подробный (5)</span><span class="sxs-lookup"><span data-stu-id="00cab-417">Verbose (5)</span></span>|

 <span data-ttu-id="00cab-418">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="00cab-418">The following table shows the event information.</span></span>

|<span data-ttu-id="00cab-419">Событие</span><span class="sxs-lookup"><span data-stu-id="00cab-419">Event</span></span>|<span data-ttu-id="00cab-420">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="00cab-420">Event ID</span></span>|<span data-ttu-id="00cab-421">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-421">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolIOPack`|<span data-ttu-id="00cab-422">65</span><span class="sxs-lookup"><span data-stu-id="00cab-422">65</span></span>|<span data-ttu-id="00cab-423">Вызывается перекрытый пакет операций ввода-вывода с перекрытием ThreadPool.</span><span class="sxs-lookup"><span data-stu-id="00cab-423">ThreadPool overlapped IO pack is called.</span></span>|

 <span data-ttu-id="00cab-424">В следующей таблице показаны данные события.</span><span class="sxs-lookup"><span data-stu-id="00cab-424">The following table shows the event data</span></span>

|<span data-ttu-id="00cab-425">Имя поля</span><span class="sxs-lookup"><span data-stu-id="00cab-425">Field name</span></span>|<span data-ttu-id="00cab-426">Тип данных</span><span class="sxs-lookup"><span data-stu-id="00cab-426">Data type</span></span>|<span data-ttu-id="00cab-427">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-427">Description</span></span>|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|<span data-ttu-id="00cab-428">Зарезервировано для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="00cab-428">Reserved for internal use.</span></span>|
|`Overlapped`|`win:Pointer`|<span data-ttu-id="00cab-429">Зарезервировано для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="00cab-429">Reserved for internal use.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="00cab-430">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="00cab-430">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadcreating-event"></a><span data-ttu-id="00cab-431">Событие Среадкреатинг</span><span class="sxs-lookup"><span data-stu-id="00cab-431">ThreadCreating event</span></span>

 <span data-ttu-id="00cab-432">В следующей таблице показаны ключевые слова и уровень.</span><span class="sxs-lookup"><span data-stu-id="00cab-432">The following table shows the keywords and level.</span></span>

|<span data-ttu-id="00cab-433">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="00cab-433">Keyword for raising the event</span></span>|<span data-ttu-id="00cab-434">Level</span><span class="sxs-lookup"><span data-stu-id="00cab-434">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="00cab-435">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="00cab-435">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="00cab-436">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="00cab-436">Informational (4)</span></span>|

 <span data-ttu-id="00cab-437">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="00cab-437">The following table shows the event information.</span></span>

|<span data-ttu-id="00cab-438">Событие</span><span class="sxs-lookup"><span data-stu-id="00cab-438">Event</span></span>|<span data-ttu-id="00cab-439">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="00cab-439">Event ID</span></span>|<span data-ttu-id="00cab-440">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-440">Description</span></span>|
|----------------|---------------|-----------------|
|`ThreadCreating`|<span data-ttu-id="00cab-441">70</span><span class="sxs-lookup"><span data-stu-id="00cab-441">70</span></span>|<span data-ttu-id="00cab-442">Поток создан.</span><span class="sxs-lookup"><span data-stu-id="00cab-442">Thread has been created.</span></span>|

 <span data-ttu-id="00cab-443">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="00cab-443">The following table shows the event data.</span></span>

|<span data-ttu-id="00cab-444">Имя поля</span><span class="sxs-lookup"><span data-stu-id="00cab-444">Field name</span></span>|<span data-ttu-id="00cab-445">Тип данных</span><span class="sxs-lookup"><span data-stu-id="00cab-445">Data type</span></span>|<span data-ttu-id="00cab-446">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-446">Description</span></span>|
|----------------|---------------|-----------------|
|`ID`|`win:Pointer`|<span data-ttu-id="00cab-447">Идентификатор потока</span><span class="sxs-lookup"><span data-stu-id="00cab-447">Thread ID</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="00cab-448">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="00cab-448">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadrunning-event"></a><span data-ttu-id="00cab-449">Событие Среадруннинг</span><span class="sxs-lookup"><span data-stu-id="00cab-449">ThreadRunning event</span></span>

 <span data-ttu-id="00cab-450">В следующей таблице показаны ключевые слова и уровень.</span><span class="sxs-lookup"><span data-stu-id="00cab-450">The following table shows the keywords and level.</span></span>

|<span data-ttu-id="00cab-451">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="00cab-451">Keyword for raising the event</span></span>|<span data-ttu-id="00cab-452">Level</span><span class="sxs-lookup"><span data-stu-id="00cab-452">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="00cab-453">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="00cab-453">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="00cab-454">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="00cab-454">Informational (4)</span></span>|

 <span data-ttu-id="00cab-455">В таблице ниже представлены сведения о событии.</span><span class="sxs-lookup"><span data-stu-id="00cab-455">The following table shows the event information.</span></span>

|<span data-ttu-id="00cab-456">Событие</span><span class="sxs-lookup"><span data-stu-id="00cab-456">Event</span></span>|<span data-ttu-id="00cab-457">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="00cab-457">Event ID</span></span>|<span data-ttu-id="00cab-458">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-458">Description</span></span>|
|----------------|---------------|-----------------|
|`ThreadRunning`|<span data-ttu-id="00cab-459">71</span><span class="sxs-lookup"><span data-stu-id="00cab-459">71</span></span>|<span data-ttu-id="00cab-460">Поток начал выполнение.</span><span class="sxs-lookup"><span data-stu-id="00cab-460">Thread has started running.</span></span>|

 <span data-ttu-id="00cab-461">В таблице ниже представлены данные события.</span><span class="sxs-lookup"><span data-stu-id="00cab-461">The following table shows the event data.</span></span>

|<span data-ttu-id="00cab-462">Имя поля</span><span class="sxs-lookup"><span data-stu-id="00cab-462">Field name</span></span>|<span data-ttu-id="00cab-463">Тип данных</span><span class="sxs-lookup"><span data-stu-id="00cab-463">Data type</span></span>|<span data-ttu-id="00cab-464">Описание</span><span class="sxs-lookup"><span data-stu-id="00cab-464">Description</span></span>|
|----------------|---------------|-----------------|
|`ID`|`win:Pointer`|<span data-ttu-id="00cab-465">Идентификатор потока</span><span class="sxs-lookup"><span data-stu-id="00cab-465">Thread ID</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="00cab-466">Уникальный идентификатор для экземпляра CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="00cab-466">Unique ID for the instance of CoreCLR.</span></span>|
