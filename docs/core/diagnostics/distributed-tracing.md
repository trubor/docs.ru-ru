---
title: Распределенная трассировка — .NET
description: Общие сведения о распределенной трассировке .NET.
ms.date: 02/02/2021
ms.openlocfilehash: 44022232d4451f8d8a255a352206d7bdc9cb4e5c
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105575"
---
# <a name="net-distributed-tracing"></a><span data-ttu-id="9cff1-103">Распределенная трассировка .NET</span><span class="sxs-lookup"><span data-stu-id="9cff1-103">.NET Distributed Tracing</span></span>

<span data-ttu-id="9cff1-104">Распределенная трассировка — это способ публикации и наблюдения за данными трассировки в распределенной системе.</span><span class="sxs-lookup"><span data-stu-id="9cff1-104">Distributed tracing is the way to publish and observe tracing data in a distributed system.</span></span>
<span data-ttu-id="9cff1-105">.NET Framework и .NET Core поддерживают трассировку с использованием API <xref:System.Diagnostics>.</span><span class="sxs-lookup"><span data-stu-id="9cff1-105">.NET Framework and .NET Core has been supporting tracing through the <xref:System.Diagnostics> APIs.</span></span>

- <span data-ttu-id="9cff1-106">Класс <xref:System.Diagnostics.Activity?displayProperty=nameWithType> позволяет хранить и получать доступ к контексту диагностики и использовать его в системе ведения журналов.</span><span class="sxs-lookup"><span data-stu-id="9cff1-106"><xref:System.Diagnostics.Activity?displayProperty=nameWithType> class which allows storing and accessing diagnostics context and consuming it with logging system.</span></span>
- <span data-ttu-id="9cff1-107">Класс <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType> позволяет инструментировать код для ведения журнала расширенных полезных данных во время производства, которые будут использоваться в инструментированном процессе.</span><span class="sxs-lookup"><span data-stu-id="9cff1-107"><xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType> that allows code to be instrumented for production-time logging of rich data payloads for consumption within the process that was instrumented.</span></span>

<span data-ttu-id="9cff1-108">Ниже приведен пример публикации данных трассировки из входящих запросов HTTP:</span><span class="sxs-lookup"><span data-stu-id="9cff1-108">Here is an example that shows how to publish tracing data from the HTTP incoming requests:</span></span>

```csharp
   public void OnIncomingRequest(DiagnosticListener httpListener, HttpContext context)
   {
       if (httpListener.IsEnabled("Http_In"))
       {
           var activity = new Activity("Http_In");

           //add tags, baggage, etc.
           activity.SetParentId(context.Request.headers["Request-id"])
           foreach (var pair in context.Request.Headers["Correlation-Context"])
           {
               var baggageItem = NameValueHeaderValue.Parse(pair);
               activity.AddBaggage(baggageItem.Key, baggageItem.Value);
           }
           httpListener.StartActivity(activity, new { context });
           try
           {
               //process request ...
           }
           finally
           {
               //stop activity
               httpListener.StopActivity(activity, new {context} );
           }
       }
   }
```

<span data-ttu-id="9cff1-109">Ниже приведен пример прослушивания событий Activity:</span><span class="sxs-lookup"><span data-stu-id="9cff1-109">Here is example for how to listen to the Activity events:</span></span>

```csharp
    DiagnosticListener.AllListeners.Subscribe(delegate (DiagnosticListener listener)
    {
        if (listener.Name == "MyActivitySource")
        {
            listener.Subscribe(delegate (KeyValuePair<string, object> value)
            {
                if (value.Key.EndsWith("Start", StringComparison.Ordinal))
                    LogActivityStart();
                else if (value.Key.EndsWith("Stop", StringComparison.Ordinal))
                    LogActivityStop();
            });
        }
    }
```

<span data-ttu-id="9cff1-110">В .NET 5.0 расширены возможности распределенной трассировки, чтобы разрешить сценарии [OpenTelemetry](https://opentelemetry.io/), добавленные возможности выборки и упрощенный шаблон кода трассировки, а также упростить и сделать более удобным прослушивание событий Activity.</span><span class="sxs-lookup"><span data-stu-id="9cff1-110">.NET 5.0 has extended the capability of the distributed tracing to allow the [OpenTelemetry](https://opentelemetry.io/) tracing scenarios, added Sampling capabilities, simplified the tracing coding pattern, and made listening to the Activity events easier and flexible.</span></span>

> [!NOTE]
> <span data-ttu-id="9cff1-111">Для получения доступа ко всем добавленным возможностям .NET 5.0 убедитесь, что проект ссылается на класс [System.Diagnostics.DiagnosticSource](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) пакета NuGet версии 5.0 или более поздней.</span><span class="sxs-lookup"><span data-stu-id="9cff1-111">To access all added .NET 5.0 capabilities, ensure your project references the [System.Diagnostics.DiagnosticSource](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) NuGet package version 5.0 or later.</span></span> <span data-ttu-id="9cff1-112">Этот пакет можно использовать в библиотеках и приложениях, предназначенных для любой поддерживаемой версии .NET Framework, .NET Core и .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="9cff1-112">This package can be used in libraries and apps targeting any supported version of the .NET Framework, .NET Core, and .NET Standard.</span></span> <span data-ttu-id="9cff1-113">При использовании .NET версии 5.0 или более поздней нет необходимости создавать ссылку на пакет вручную, так как он включен в общую библиотеку, установленную вместе со средой выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="9cff1-113">If targeting .NET 5.0 or later, there is no need to manually reference the package as it is included in the shared library installed with the .NET Runtime.</span></span>

## <a name="getting-started-with-tracing"></a><span data-ttu-id="9cff1-114">Начало работы с трассировкой</span><span class="sxs-lookup"><span data-stu-id="9cff1-114">Getting Started With Tracing</span></span>

<span data-ttu-id="9cff1-115">Приложения и библиотеки могут легко публиковать данные трассировки, просто используя классы <xref:System.Diagnostics.ActivitySource?displayProperty=nameWithType> и <xref:System.Diagnostics.Activity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9cff1-115">Applications and libraries can easily publish tracing data by simply using the <xref:System.Diagnostics.ActivitySource?displayProperty=nameWithType> and the <xref:System.Diagnostics.Activity?displayProperty=nameWithType> classes.</span></span>

### <a name="activitysource"></a><span data-ttu-id="9cff1-116">ActivitySource</span><span class="sxs-lookup"><span data-stu-id="9cff1-116">ActivitySource</span></span>

<span data-ttu-id="9cff1-117">Первый шаг при публикации данных трассировки — создание экземпляра класса ActivitySource.</span><span class="sxs-lookup"><span data-stu-id="9cff1-117">The first step to publish tracing data is to create an instance of the ActivitySource class.</span></span> <span data-ttu-id="9cff1-118">ActivitySource — это класс, предоставляющий API для создания и запуска объектов Activity, а также для регистрации объектов ActivityListener для прослушивания событий Activity.</span><span class="sxs-lookup"><span data-stu-id="9cff1-118">The ActivitySource is the class that provides APIs to create and start Activity objects and to register ActivityListener objects to listen to the Activity events.</span></span>

```csharp
    private static ActivitySource source = new ActivitySource("MyCompany.MyComponent.SourceName", "v1");
```

#### <a name="best-practices"></a><span data-ttu-id="9cff1-119">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="9cff1-119">Best Practices</span></span>

- <span data-ttu-id="9cff1-120">Создайте класс ActivitySource и сохраните его в статической переменной, а затем используйте этот экземпляр при необходимости.</span><span class="sxs-lookup"><span data-stu-id="9cff1-120">Create the ActivitySource once and store it in a static variable and use that instance as long as needed.</span></span>

- <span data-ttu-id="9cff1-121">Имя источника, передаваемое конструктору, должно быть уникальным, чтобы избежать конфликтов с другими источниками.</span><span class="sxs-lookup"><span data-stu-id="9cff1-121">The source name passed to the constructor has to be unique to avoid the conflicts with any other sources.</span></span> <span data-ttu-id="9cff1-122">Рекомендуется использовать иерархическое имя, содержащее название компании, имя компонента и имя источника.</span><span class="sxs-lookup"><span data-stu-id="9cff1-122">It is recommended to use a hierarchical name contains the company name, the component name, and the source name.</span></span> <span data-ttu-id="9cff1-123">Например, `Microsoft.System.HttpClient.HttpInOutRequests`.</span><span class="sxs-lookup"><span data-stu-id="9cff1-123">For example, `Microsoft.System.HttpClient.HttpInOutRequests`.</span></span>

- <span data-ttu-id="9cff1-124">Параметр version является необязательным.</span><span class="sxs-lookup"><span data-stu-id="9cff1-124">The version parameter is optional.</span></span> <span data-ttu-id="9cff1-125">Рекомендуется указывать версию, если планируется выпуск нескольких версий библиотеки или приложения и вам нужно различать источники разных версий.</span><span class="sxs-lookup"><span data-stu-id="9cff1-125">It is recommended to provide the version in case you plan to release multiple versions of the library or the application and want to distinguish between the sources of different versions.</span></span>

### <a name="activity-creation"></a><span data-ttu-id="9cff1-126">Создание объектов Activity</span><span class="sxs-lookup"><span data-stu-id="9cff1-126">Activity Creation</span></span>

<span data-ttu-id="9cff1-127">Теперь созданный объект ActivitySource можно использовать для создания и запуска объектов Activity, которые используются для записи данных трассировки в нужных местах в коде.</span><span class="sxs-lookup"><span data-stu-id="9cff1-127">Now the created ActivitySource object can be used to create and start Activity objects which are used to log any tracing data in any desired places in the code.</span></span>

```csharp
        using (Activity activity = source.StartActivity("OperationName"))
        {
            // Do something

            activity?.AddTag("key", "value"); // log the tracing
        }
```

<span data-ttu-id="9cff1-128">В этом примере кода создается объект Activity, а затем записываются некоторые теги трассировки `key` и `value`.</span><span class="sxs-lookup"><span data-stu-id="9cff1-128">This sample code tries to create the Activity object and then logs some tracing tag `key` and `value`.</span></span>

#### <a name="notes"></a><span data-ttu-id="9cff1-129">Примечания</span><span class="sxs-lookup"><span data-stu-id="9cff1-129">Notes</span></span>

- <span data-ttu-id="9cff1-130">`ActivitySource.StartActivity` пытается создать и запустить действие в то же время.</span><span class="sxs-lookup"><span data-stu-id="9cff1-130">`ActivitySource.StartActivity` tries to create and start the activity at the same time.</span></span> <span data-ttu-id="9cff1-131">В приведенном шаблоне кода используется блок `using`, который автоматически удаляет созданный объект Activity после выполнения блока.</span><span class="sxs-lookup"><span data-stu-id="9cff1-131">The listed code pattern is using the `using` block which automatically disposes the created Activity object after executing the block.</span></span> <span data-ttu-id="9cff1-132">Удаление объекта Activity прервет это запущенное действие, и коду не нужно будет явно останавливать его.</span><span class="sxs-lookup"><span data-stu-id="9cff1-132">Disposing the Activity object will stop this started activity and the code doesn't have to explicitly stop the activity.</span></span> <span data-ttu-id="9cff1-133">Это упрощает шаблон кода.</span><span class="sxs-lookup"><span data-stu-id="9cff1-133">That simplifies the coding pattern.</span></span>

- <span data-ttu-id="9cff1-134">`ActivitySource.StartActivity` внутренним образом определяет наличие прослушивателей для таких событий.</span><span class="sxs-lookup"><span data-stu-id="9cff1-134">`ActivitySource.StartActivity` internally figures out if there are any listeners to such events.</span></span> <span data-ttu-id="9cff1-135">Если зарегистрированных прослушивателей нет или есть прослушиватели, которые не заинтересованы в таком событии, `ActivitySource.StartActivity` просто вернет `null`, не создавая объект Activity.</span><span class="sxs-lookup"><span data-stu-id="9cff1-135">If there are no registered listeners or there are listeners which are not interested in such an event, `ActivitySource.StartActivity` simply will return `null` and avoid creating the Activity object.</span></span> <span data-ttu-id="9cff1-136">Именно поэтому в коде использовался допускающий значение NULL оператор `?` в инструкции `activity?.AddTag`.</span><span class="sxs-lookup"><span data-stu-id="9cff1-136">That is why the code used the nullable operator `?`  in the statement `activity?.AddTag`.</span></span> <span data-ttu-id="9cff1-137">Как правило, внутри блока `using` всегда следует использовать допускающий значение NULL оператор `?` после имени объекта действия.</span><span class="sxs-lookup"><span data-stu-id="9cff1-137">In general, inside the `using` block, always use the nullable operator `?` after the activity object name.</span></span>

## <a name="listening-to-the-activity-events"></a><span data-ttu-id="9cff1-138">Прослушивание событий Activity</span><span class="sxs-lookup"><span data-stu-id="9cff1-138">Listening to the Activity Events</span></span>

<span data-ttu-id="9cff1-139">.NET предоставляет класс <xref:System.Diagnostics.ActivityListener?displayProperty=nameWithType>, который можно использовать для прослушивания событий Activity, активируемых из одного или нескольких экземпляров ActivitySource.</span><span class="sxs-lookup"><span data-stu-id="9cff1-139">.NET provides the class <xref:System.Diagnostics.ActivityListener?displayProperty=nameWithType> which can be used to listen to the Activity events triggered from one or more ActivitySources.</span></span>
<span data-ttu-id="9cff1-140">Прослушиватель можно использовать для получения данных трассировки, выборки или принудительного создания объекта Activity.</span><span class="sxs-lookup"><span data-stu-id="9cff1-140">The listener can be used to collect tracing data, sample, or force creating the Activity object.</span></span>

<span data-ttu-id="9cff1-141">Класс `ActivityListener` предоставляет разные обратные вызовы для управления разными событиями.</span><span class="sxs-lookup"><span data-stu-id="9cff1-141">The `ActivityListener` class provides a different callbacks to handle different events.</span></span>

```csharp
var listener = new ActivityListener
{
    ShouldListenTo = (activitySource) => object.ReferenceEquals(source, activitySource),
    ActivityStarted = activity => /* Handle the Activity start event here */ DoSomething(),
    ActivityStopped = activity => /* Handle the Activity stop event here */ DoSomething(),
    SampleUsingParentId = (ref ActivityCreationOptions<string> activityOptions) => ActivitySamplingResult.AllData,
    Sample = (ref ActivityCreationOptions<ActivityContext> activityOptions) => ActivitySamplingResult.AllData
};

// Enable the listener
ActivitySource.AddActivityListener(listener);
```

- <span data-ttu-id="9cff1-142">`ShouldListenTo` включает прослушивание определенных объектов `ActivitySource`.</span><span class="sxs-lookup"><span data-stu-id="9cff1-142">`ShouldListenTo` enables listening to specific `ActivitySource` objects.</span></span> <span data-ttu-id="9cff1-143">В этом примере разрешается прослушивание ранее созданного объекта `ActivitySource`.</span><span class="sxs-lookup"><span data-stu-id="9cff1-143">In the example, it enables listening to the `ActivitySource` object we have previously created.</span></span> <span data-ttu-id="9cff1-144">Для прослушивания любых других объектов `ActivitySource` можно обеспечить большую гибкость, проверив `Name` и `Version` входного экземпляра `ActivitySource`.</span><span class="sxs-lookup"><span data-stu-id="9cff1-144">There is more flexibility to listen to any other `ActivitySource` objects by checking the `Name` and `Version` of the input `ActivitySource`.</span></span>

- <span data-ttu-id="9cff1-145">`ActivityStarted` и `ActivityStopped` позволяют получать события Start и Stop `Activity` для всех объектов `Activity`, созданных объектами `ActivitySource`, которые были включены при обратном вызове `ShouldListenTo`.</span><span class="sxs-lookup"><span data-stu-id="9cff1-145">`ActivityStarted` and `ActivityStopped` enable getting the `Activity` Start and Stop events for all `Activity` objects created by the `ActivitySource` objects which were enabled by the `ShouldListenTo` callback.</span></span>

- <span data-ttu-id="9cff1-146">`Sample` и `SampleUsingParentId` являются основными методами обратного вызова, предназначенными для выборки.</span><span class="sxs-lookup"><span data-stu-id="9cff1-146">`Sample` and `SampleUsingParentId` are the main callbacks which intended for sampling.</span></span> <span data-ttu-id="9cff1-147">Эти два обратных вызова возвращают значение перечисления `ActivitySamplingResult`, которое может указывать на выборку из текущего запроса на создание `Activity`.</span><span class="sxs-lookup"><span data-stu-id="9cff1-147">These two callbacks return the `ActivitySamplingResult` enum value which can tell either to sample in or out the current `Activity` creation request.</span></span> <span data-ttu-id="9cff1-148">Если обратный вызов возвращает `ActivitySamplingResult.None` и другие включенные прослушиватели не возвращают другое значение, объект Activity не будет создан и `ActivitySource.StartActivity` вернет `null`.</span><span class="sxs-lookup"><span data-stu-id="9cff1-148">If the callback returns `ActivitySamplingResult.None` and no other enabled listeners return different value, then the Activity will not get created and `ActivitySource.StartActivity` will return `null`.</span></span> <span data-ttu-id="9cff1-149">В противном случае будет создан объект `Activity`.</span><span class="sxs-lookup"><span data-stu-id="9cff1-149">Otherwise, the `Activity` object will get created.</span></span>

## <a name="net-50-new-features"></a><span data-ttu-id="9cff1-150">Новые возможности .NET 5.0</span><span class="sxs-lookup"><span data-stu-id="9cff1-150">.NET 5.0 New Features</span></span>

<span data-ttu-id="9cff1-151">Некоторое время класс `Activity` поддерживал сценарии трассировки.</span><span class="sxs-lookup"><span data-stu-id="9cff1-151">For awhile the `Activity` class has been supporting tracing scenarios.</span></span> <span data-ttu-id="9cff1-152">Он позволял добавлять теги, которые представляют собой пары "ключ-значение" данных трассировки.</span><span class="sxs-lookup"><span data-stu-id="9cff1-152">It allowed adding tags which are key-value pairs of tracing data.</span></span> <span data-ttu-id="9cff1-153">Также класс поддерживал Baggage, то есть пары "ключ-значение", предназначенные для распространения по сети.</span><span class="sxs-lookup"><span data-stu-id="9cff1-153">It has been supporting Baggage which is are key-value pairs intended to be propagated across the wire.</span></span>

<span data-ttu-id="9cff1-154">.NET 5.0 поддерживает дополнительные функции, в основном для включения сценариев OpenTelemetry.</span><span class="sxs-lookup"><span data-stu-id="9cff1-154">.NET 5.0 supports more features mainly to enable OpenTelemetry scenarios.</span></span>

### <a name="activitycontext"></a><span data-ttu-id="9cff1-155">ActivityContext</span><span class="sxs-lookup"><span data-stu-id="9cff1-155">ActivityContext</span></span>

<span data-ttu-id="9cff1-156"><xref:System.Diagnostics.ActivityContext?displayProperty=nameWithType> — это структура, которая содержит контекст операций трассировки (включая идентификатор трассировки, идентификатор диапазона, флаги трассировки и состояние трассировки).</span><span class="sxs-lookup"><span data-stu-id="9cff1-156"><xref:System.Diagnostics.ActivityContext?displayProperty=nameWithType> is the struct carrying the context of the tracing operations (e.g. the trace Id, Span Id, trace flags, and trace state).</span></span> <span data-ttu-id="9cff1-157">Теперь можно создать новый объект `Activity`, предоставляющий родительский контекст трассировки.</span><span class="sxs-lookup"><span data-stu-id="9cff1-157">Now it is possible to create a new `Activity` providing the parent tracing context.</span></span> <span data-ttu-id="9cff1-158">Кроме того, можно легко извлечь контекст трассировки из любого объекта `Activity`, вызвав свойство `Activity.Context`.</span><span class="sxs-lookup"><span data-stu-id="9cff1-158">Also, it is easy to extract the tracing context from any `Activity` object by calling `Activity.Context` property.</span></span>

### <a name="activitylink"></a><span data-ttu-id="9cff1-159">ActivityLink</span><span class="sxs-lookup"><span data-stu-id="9cff1-159">ActivityLink</span></span>

<span data-ttu-id="9cff1-160"><xref:System.Diagnostics.ActivityLink?displayProperty=nameWithType> — это структура, содержащая экземпляр контекста трассировки, который может быть связан со случайным образом связанными объектами `Activity`.</span><span class="sxs-lookup"><span data-stu-id="9cff1-160"><xref:System.Diagnostics.ActivityLink?displayProperty=nameWithType> is the struct containing the tracing context instance which can be linked to casually related `Activity` objects.</span></span> <span data-ttu-id="9cff1-161">Ссылки можно добавить в объект `Activity`, передав список ссылок в метод `ActivitySource.StartActivity` при создании `Activity`.</span><span class="sxs-lookup"><span data-stu-id="9cff1-161">Links can be added to the `Activity` object by passing the links list to `ActivitySource.StartActivity` method when creating the `Activity`.</span></span> <span data-ttu-id="9cff1-162">Связанные с объектом `Activity` ссылки можно получить с помощью свойства `Activity.Links`.</span><span class="sxs-lookup"><span data-stu-id="9cff1-162">The `Activity` object attached links can be retrieved using the property `Activity.Links`.</span></span>

### <a name="activityevent"></a><span data-ttu-id="9cff1-163">ActivityEvent</span><span class="sxs-lookup"><span data-stu-id="9cff1-163">ActivityEvent</span></span>

<span data-ttu-id="9cff1-164"><xref:System.Diagnostics.ActivityEvent?displayProperty=nameWithType> представляет событие, которое содержит имя и метку времени, а также необязательный список тегов.</span><span class="sxs-lookup"><span data-stu-id="9cff1-164"><xref:System.Diagnostics.ActivityEvent?displayProperty=nameWithType> represents an event containing a name and a timestamp, as well as an optional list of tags.</span></span> <span data-ttu-id="9cff1-165">События можно добавить в объект `Activity`, вызвав метод `Activity.AddEvent`.</span><span class="sxs-lookup"><span data-stu-id="9cff1-165">Events can be added to the `Activity` object by calling `Activity.AddEvent` method.</span></span> <span data-ttu-id="9cff1-166">Весь список событий объекта `Activity` можно получить с помощью свойства `Activity.Events`.</span><span class="sxs-lookup"><span data-stu-id="9cff1-166">The whole list of the `Activity` object Events can be retrieved using the property `Activity.Events`.</span></span>

### <a name="activitykind"></a><span data-ttu-id="9cff1-167">ActivityKind</span><span class="sxs-lookup"><span data-stu-id="9cff1-167">ActivityKind</span></span>

<span data-ttu-id="9cff1-168"><xref:System.Diagnostics.ActivityKind?displayProperty=nameWithType> описывает связь между действием, а также его родительскими и дочерними элементами в трассировке.</span><span class="sxs-lookup"><span data-stu-id="9cff1-168"><xref:System.Diagnostics.ActivityKind?displayProperty=nameWithType> describes the relationship between the activity, its parents and its children in a trace.</span></span> <span data-ttu-id="9cff1-169">Для типа можно задать объект `Activity`, передав значение типа в метод `ActivitySource.StartActivity` при создании `Activity`.</span><span class="sxs-lookup"><span data-stu-id="9cff1-169">Kind can be set to the `Activity` object by passing the kind value to `ActivitySource.StartActivity` method when creating the `Activity`.</span></span> <span data-ttu-id="9cff1-170">Тип объекта `Activity` можно получить с помощью свойства `Activity.Kind`.</span><span class="sxs-lookup"><span data-stu-id="9cff1-170">The `Activity` object kind can be retrieved using the property `Activity.Kind`.</span></span>

### <a name="isalldatarequested"></a><span data-ttu-id="9cff1-171">IsAllDataRequested</span><span class="sxs-lookup"><span data-stu-id="9cff1-171">IsAllDataRequested</span></span>

<span data-ttu-id="9cff1-172"><xref:System.Diagnostics.Activity.IsAllDataRequested?displayProperty=nameWithType> указывает, должно ли это действие быть заполнено всеми сведениями о распространении, а также всеми другими свойствами, такими как ссылки, теги и события.</span><span class="sxs-lookup"><span data-stu-id="9cff1-172"><xref:System.Diagnostics.Activity.IsAllDataRequested?displayProperty=nameWithType> indicates whether this activity should be populated with all the propagation information, as well as all the other properties, such as links, tags, and events.</span></span> <span data-ttu-id="9cff1-173">Значение `IsAllDataRequested` определяется из результата, полученного из всех прослушивателей обратных вызовов `Sample` и `SampleUsingParentId`.</span><span class="sxs-lookup"><span data-stu-id="9cff1-173">The value of `IsAllDataRequested` is determined from the result returned from all listeners `Sample` and `SampleUsingParentId` callbacks.</span></span> <span data-ttu-id="9cff1-174">Значение можно получить с помощью свойства `Activity.IsAllDataRequested`.</span><span class="sxs-lookup"><span data-stu-id="9cff1-174">The value can be retrieved using `Activity.IsAllDataRequested` property.</span></span>

### <a name="activitysource"></a><span data-ttu-id="9cff1-175">Activity.Source</span><span class="sxs-lookup"><span data-stu-id="9cff1-175">Activity.Source</span></span>

<span data-ttu-id="9cff1-176"><xref:System.Diagnostics.Activity.Source?displayProperty=nameWithType> получает источник действия, связанный с этим действием.</span><span class="sxs-lookup"><span data-stu-id="9cff1-176"><xref:System.Diagnostics.Activity.Source?displayProperty=nameWithType> gets the activity source associated with this activity.</span></span>

### <a name="activitydisplayname"></a><span data-ttu-id="9cff1-177">Activity.DisplayName</span><span class="sxs-lookup"><span data-stu-id="9cff1-177">Activity.DisplayName</span></span>

<span data-ttu-id="9cff1-178"><xref:System.Diagnostics.Activity.DisplayName?displayProperty=nameWithType> позволяет получить или задать отображаемое имя для действия.</span><span class="sxs-lookup"><span data-stu-id="9cff1-178"><xref:System.Diagnostics.Activity.DisplayName?displayProperty=nameWithType> allows getting or setting a display name for the activity.</span></span>

### <a name="activitytagobjects"></a><span data-ttu-id="9cff1-179">Activity.TagObjects</span><span class="sxs-lookup"><span data-stu-id="9cff1-179">Activity.TagObjects</span></span>

<span data-ttu-id="9cff1-180">Класс `Activity` имеет свойство `Activity.Tags`, которое возвращает список пар "ключ-значение" для ключа и значения строкового типа.</span><span class="sxs-lookup"><span data-stu-id="9cff1-180">`Activity` class has the property `Activity.Tags` which return the a key-value pair list of the tags of type string for the key and value.</span></span> <span data-ttu-id="9cff1-181">Такие теги можно добавить в `Activity` с помощью метода `AddTag(string, string)`.</span><span class="sxs-lookup"><span data-stu-id="9cff1-181">Such Tags can be added to the `Activity` using the method `AddTag(string, string)`.</span></span> <span data-ttu-id="9cff1-182">`Activity` расширяет поддержку тегов, предоставляя перегруженный метод `AddTag(string, object)`, который допускает значения любого типа.</span><span class="sxs-lookup"><span data-stu-id="9cff1-182">`Activity` has extended the support of tags by providing the overloaded method `AddTag(string, object)` allowing values of any type.</span></span>  <span data-ttu-id="9cff1-183">Полный список таких тегов можно получить с помощью <xref:System.Diagnostics.Activity.TagObjects?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9cff1-183">The complete list of such tags can be retrieved using <xref:System.Diagnostics.Activity.TagObjects?displayProperty=nameWithType>.</span></span>

## <a name="sampling"></a><span data-ttu-id="9cff1-184">Выборка</span><span class="sxs-lookup"><span data-stu-id="9cff1-184">Sampling</span></span>

<span data-ttu-id="9cff1-185">Выборка — это механизм управления шумом и издержками путем снижения числа выборок трассировок, собираемых и отправляемых в серверную часть.</span><span class="sxs-lookup"><span data-stu-id="9cff1-185">Sampling is a mechanism to control the noise and overhead by reducing the number of samples of traces collected and sent to the backend.</span></span> <span data-ttu-id="9cff1-186">Выборка — это важный сценарий OpenTelemetry.</span><span class="sxs-lookup"><span data-stu-id="9cff1-186">Sampling is an important OpenTelemetry scenario.</span></span> <span data-ttu-id="9cff1-187">В .NET 5.0 можно легко разрешить выборку.</span><span class="sxs-lookup"><span data-stu-id="9cff1-187">In .NET 5.0 it is easy to allow sampling.</span></span> <span data-ttu-id="9cff1-188">Рекомендуется создать новые объекты `Activity` с помощью `ActivitySource.StartActivity` и попытаться предоставить все возможные доступные данные (включая теги, типы, ссылки и т. д.) при вызове этого метода.</span><span class="sxs-lookup"><span data-stu-id="9cff1-188">A good practice is to create the new `Activity` objects using `ActivitySource.StartActivity` and try to provide all possible available data (e.g. tags, kind, links, ...etc.) when calling this method.</span></span> <span data-ttu-id="9cff1-189">Предоставление данных позволит средствам выборки, реализованным с помощью `ActivityListener`, иметь правильное решение для выборки.</span><span class="sxs-lookup"><span data-stu-id="9cff1-189">Providing the data will allow the samplers implemented using the `ActivityListener` to have a proper sampling decision.</span></span> <span data-ttu-id="9cff1-190">Если важна производительность, чтобы избежать создания данных перед созданием объекта `Activity`, можно использовать свойство `ActivitySource.HasListeners` для определения того, есть ли прослушиватели.</span><span class="sxs-lookup"><span data-stu-id="9cff1-190">If the performance is critical to avoid creating the data before creating the `Activity` object, the property `ActivitySource.HasListeners` comes in handy to check if there are any listeners before creating the needed data.</span></span>

## <a name="opentelemetry"></a><span data-ttu-id="9cff1-191">OpenTelemetry</span><span class="sxs-lookup"><span data-stu-id="9cff1-191">OpenTelemetry</span></span>

<span data-ttu-id="9cff1-192">В состав пакета SDK OpenTelemetry входят многие функции с поддержкой комплексных сценариев распределенной трассировки.</span><span class="sxs-lookup"><span data-stu-id="9cff1-192">OpenTelemetry SDK comes with many features that support end-to-end distributed tracing scenarios.</span></span> <span data-ttu-id="9cff1-193">Он предоставляет несколько средств выборки и средств экспорта, которые можно выбрать.</span><span class="sxs-lookup"><span data-stu-id="9cff1-193">It provides multiple samplers and exporters which you can choose from.</span></span> <span data-ttu-id="9cff1-194">Он также позволяет создавать пользовательские средства выборки и средства экспорта.</span><span class="sxs-lookup"><span data-stu-id="9cff1-194">It allows creating a custom samplers and exporters too.</span></span>

<span data-ttu-id="9cff1-195">OpenTelemetry поддерживает экспорт собранных данных трассировки в разные серверные части (включая Jaeger, Zipkin, New Relic и т. д.).</span><span class="sxs-lookup"><span data-stu-id="9cff1-195">OpenTelemetry supports exporting the collected tracing data to different backends (e.g. Jaeger, Zipkin, New Relic,...etc.).</span></span> <span data-ttu-id="9cff1-196">Дополнительные сведения см. в описании [OpenTelemetry-dotnet](https://github.com/open-telemetry/opentelemetry-dotnet/). Также на сайте Nuget.org можно найти пакеты, начинающиеся с `OpenTelemetry.Exporter.`, чтобы получить список пакетов средств экспорта.</span><span class="sxs-lookup"><span data-stu-id="9cff1-196">Refer to [OpenTelemetry-dotnet](https://github.com/open-telemetry/opentelemetry-dotnet/) for more details and search Nuget.org for packages starting with `OpenTelemetry.Exporter.` to get the exporter packages list.</span></span>

<span data-ttu-id="9cff1-197">Ниже приведен пример кода, перенесенного из [руководства по началу работы с OpenTelemetry-dotnet](https://github.com/open-telemetry/opentelemetry-dotnet/tree/main/docs/trace/getting-started). Вы можете увидеть, насколько легко выполнить выборку и экспорт данных трассировки в консоль.</span><span class="sxs-lookup"><span data-stu-id="9cff1-197">Here is sample code ported from [OpenTelemetry-dotnet getting started](https://github.com/open-telemetry/opentelemetry-dotnet/tree/main/docs/trace/getting-started) showing how easy it is to sample and export tracing data to the console.</span></span>

```csharp
// <copyright file="Program.cs" company="OpenTelemetry Authors">
// Copyright The OpenTelemetry Authors
//
// Licensed under the Apache License, Version 2.0 (the "License");
// you may not use this file except in compliance with the License.
// You may obtain a copy of the License at
//
//     http://www.apache.org/licenses/LICENSE-2.0
//
// Unless required by applicable law or agreed to in writing, software
// distributed under the License is distributed on an "AS IS" BASIS,
// WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
// See the License for the specific language governing permissions and
// limitations under the License.
// </copyright>

using System.Diagnostics;
using OpenTelemetry;
using OpenTelemetry.Trace;

public class Program
{
    private static readonly ActivitySource MyActivitySource = new ActivitySource(
        "MyCompany.MyProduct.MyLibrary");

    public static void Main()
    {
        using var tracerProvider = Sdk.CreateTracerProviderBuilder()
            .SetSampler(new AlwaysOnSampler())
            .AddSource("MyCompany.MyProduct.MyLibrary")
            .AddConsoleExporter()
            .Build();

        using (var activity = MyActivitySource.StartActivity("SayHello"))
        {
            activity?.SetTag("foo", 1);
            activity?.SetTag("bar", "Hello, World!");
            activity?.SetTag("baz", new int[] { 1, 2, 3 });
        }
    }
}
```

<span data-ttu-id="9cff1-198">Выборка должна ссылаться на пакет [OpenTelemetry.Exporter.Console](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/1.0.0-rc2).</span><span class="sxs-lookup"><span data-stu-id="9cff1-198">The sample needs to reference the package [OpenTelemetry.Exporter.Console](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/1.0.0-rc2).</span></span>
