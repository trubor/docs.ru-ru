---
title: Стандартные поставщики событий в .NET
description: Сведения о поставщиках и событиях, публикуемых в библиотеках и среде выполнения .NET.
ms.topic: reference
ms.date: 12/21/2020
ms.openlocfilehash: 37aa9551397bb3e3e8858a1289ddc3921327b722
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105171"
---
# <a name="well-known-event-providers-in-net"></a>Стандартные поставщики событий в .NET

Библиотеки и среда выполнения .NET записывают диагностические события с помощью ряда разных поставщиков событий. Вы можете включать нужные поставщики в зависимости от задач диагностики. В этой статье описываются некоторые популярные поставщики событий в библиотеках и среде выполнения .NET.

## <a name="coreclr"></a>CoreCLR

### <a name="microsoft-windows-dotnetruntime-provider"></a>Поставщик "Microsoft-Windows-DotNETRuntime"

Этот поставщик генерирует различные события из среды выполнения .NET, в том числе события сборки мусора, загрузчика, JIT, исключения и другие события. Дополнительные сведения обо всех событиях этого поставщика см. в [списке событий поставщика среды выполнения](../../fundamentals/diagnostics/runtime-events.md).

### <a name="microsoft-dotnetcore-sampleprofiler-provider"></a>Поставщик "Microsoft-DotNETCore-SampleProfiler"

Этот поставщик событий среды выполнения .NET используется для выборки циклов ЦП для управляемых стеков вызовов. Если он включен, каждые 10 миллисекунд создается моментальный снимок управляемого стека вызовов для каждого потока. Чтобы использовать эту возможность, необходимо настроить уровень <xref:System.Diagnostics.Tracing.EventLevel> не ниже `Informational`.

## <a name="framework-libraries"></a>Библиотеки платформы

### <a name="microsoft-extensions-dependencyinjection-provider"></a>Поставщик "Microsoft-Extensions-DependencyInjection"

Этот поставщик регистрирует сведения из DependencyInjection. События, регистрируемые поставщиком `Microsoft-Extensions-DependencyInjection`, представлены в следующей таблице:

|Имя события|Level|Описание|
|----------|-----|-----------|
|`CallSiteBuilt`|Подробный (5)|Создан сайт вызова.|
|`ServiceResolved`|Подробный (5)|Была разрешена служба.|
|`ExpressionTreeGenerated`|Подробный (5)|Создано дерево выражения.|
|`DynamicMethodBuilt`|Подробный (5)|Создан <xref:System.Reflection.Emit.DynamicMethod>.|

### <a name="systembuffersarraypooleventsource-provider"></a>Поставщик "System.Buffers.ArrayPoolEventSource"

Этот поставщик регистрирует сведения из ArrayPool. События, регистрируемые поставщиком `ArrayPoolEventSource`, представлены в следующей таблице:

|Имя события|Level|Описание|
|----------|-----|-----------|
|`BufferRented`|Подробный (5)|Буфер успешно арендован.|
|`BufferAllocated`|Информационный (4)|Буфер выделен из пула.|
|`BufferReturned`|Подробный (5)|Буфер возвращен в пул.|
|`BufferTrimmed`|Информационный (4)|Предпринята попытка освободить буфер из-за нехватки памяти или отсутствия активности.|
|`BufferTrimPoll`|Информационный (4)|Выполняется проверка для усечения буферов.|

### <a name="systemnethttp-provider"></a>Поставщик "System.Net.Http"

Этот поставщик регистрирует сведения из стека HTTP. События, регистрируемые поставщиком `System.Net.Http`, представлены в следующей таблице:

|Имя события|Level|Описание|
|----------|-----|-----------|
|RequestStart|Информационный (4)|Начало HTTP-запроса.|
|RequestStop|Информационный (4)|Конец HTTP-запроса.|
|RequestFailed|Ошибка (2)|Сбой HTTP-запроса.|
|ConnectionEstablished|Информационный (4)|Установлено HTTP-соединение.|
|ConnectionClosed|Информационный (4)|HTTP-соединение закрыто.|
|RequestLeftQueue|Информационный (4)|HTTP-запрос покинул очередь запросов.|
|RequestHeadersStart|Информационный (4)|Начало HTTP-запроса заголовка.|
|RequestHeaderStop|Информационный (4)|Конец HTTP-запроса заголовка.|
|RequestContentStart|Информационный (4)|Начало HTTP-запроса содержимого.|
|RequestContentStop|Информационный (4)|Конец HTTP-запроса содержимого.|
|ResponseHeadersStart|Информационный (4)|Начало HTTP-ответа для заголовка.|
|ResponseHeaderStop|Информационный (4)|Конец HTTP-ответа для заголовка.|
|ResponseContentStart|Информационный (4)|Начало HTTP-ответа для содержимого.|
|ResponseContentStop|Информационный (4)|Конец HTTP-ответа для содержимого.|

### <a name="systemnetnameresolution-provider"></a>Поставщик "System.Net.NameResolution"

Этот поставщик регистрирует сведения, связанные с разрешением доменных имен. События, регистрируемые поставщиком `System.Net.NameResolution`, представлены в следующей таблице:

|Имя события|Level|Описание|
|----------|-----|-----------|
|`ResolutionStart`|Информационный (4)|Разрешение доменных имен начато.|
|`ResolutionStop`|Информационный (4)|Разрешение доменных имен завершено.|
|`ResolutionFailed`|Информационный (4)|Разрешение доменных имен завершилось сбоем.|

### <a name="systemnetsockets-provider"></a>Поставщик "System.Net.Sockets"

Этот поставщик регистрирует сведения из <xref:System.Net.Sockets.Socket>. События, регистрируемые поставщиком `System.Net.Sockets`, представлены в следующей таблице:

|Имя события|Level|Описание|
|----------|-----|-----------|
|`ConnectStart`|Информационный (4)|Предпринята попытка запустить подключение к сокету.|
|`ConnectStop`|Информационный (4)|Попытка запустить подключение к сокету завершена.|
|`ConnectFailed`|Информационный (4)|Попытка запустить подключение к сокету завершилась сбоем.|
|`AcceptStart`|Информационный (4)|Предпринята попытка принять подключение к сокету.|
|`AcceptStop`|Информационный (4)|Попытка принять подключение к сокету завершена.|
|`AcceptFailed`|Информационный (4)|Попытка принять подключение к сокету завершилась сбоем.|

### <a name="systemthreadingtaskstpleventsource-provider"></a>Поставщик "System.Threading.Tasks.TplEventSource"

Этот поставщик регистрирует сведения, относящиеся к [библиотеке параллельных задач](../../standard/parallel-programming/task-parallel-library-tpl.md), например события планировщика задач. События, регистрируемые поставщиком `TplEventSource`, представлены в следующей таблице:

|Имя события|Ключевое слово|Level|Описание|
|----------|-------|-----|-----------|
|`TaskScheduled`|`TaskTransfer`(`0x1`)<br /><br />`Tasks`(`0x2`)|Информационный (4)|Объект <xref:System.Threading.Tasks.Task> помещен в очередь планировщика задач.|
|`TaskStarted`|`Tasks`(`0x2`)|Информационный (4)|Начато выполнение объекта <xref:System.Threading.Tasks.Task>.|
|`TaskCompleted`|`TaskStops`(`0x40`)|Информационный (4)|Выполнение объекта <xref:System.Threading.Tasks.Task> завершено.|
|`TaskWaitBegin`|`TaskTransfer`(`0x1`)<br /><br />`TaskWait`(`0x2`)|Информационный (4)|Возникает при начале неявного или явного ожидания завершения объекта <xref:System.Threading.Tasks.Task>.|
|`TaskWaitEnd`|`Tasks`(`0x2`)|Подробный (5)|Возникает при возврате ожидания завершения объекта <xref:System.Threading.Tasks.Task>.|
|`TaskWaitContinuationStarted`|`Tasks`(`0x2`)|Подробный (5)|Возникает при запуске рабочего элемента (метода), связанного с `TaskWaitEnd`.|
|`TaskWaitContinuationCompleted`|`TaskStops`(`0x40`)|Подробный (5)|Возникает при завершении рабочего элемента (метода), связанного с `TaskWaitEnd`.|
|`AwaitTaskContinuationScheduled`|`TaskTransfer`(`0x1`)<br /><br />`Tasks`(`0x2`)|Информационный (4)|Возникает при планировании асинхронного продолжения для объекта <xref:System.Threading.Tasks.Task>.|

## <a name="aspnet-core"></a>ASP.NET Core

В ASP.NET Core также предусмотрен ряд событий, помогающих диагностировать проблемы в стеке ASP.NET Core.

Дополнительные сведения о событиях в ASP.NET Core и их использовании см. в разделе [Ведение журнала в .NET Core и ASP.NET Core](/aspnet/core/fundamentals/logging/).

## <a name="entity-framework-core"></a>Entity Framework Core

EF Core также предоставляет события, которые помогают диагностировать проблемы в EF Core.

Дополнительные сведения о событиях в EF Core и их использовании см. в разделе [События .NET в EF Core ](/ef/core/logging-events-diagnostics/events).
