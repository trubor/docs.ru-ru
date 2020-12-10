---
title: Источник события BinaryFormatter
description: Узнайте, как использовать источник событий BinaryFormatter для записи событий сериализации или десериализации в журнал.
ms.date: 12/03/2020
ms.author: levib
author: GrabYourPitchforks
ms.openlocfilehash: 9ae2af77b6cfc270207fb0f2969ada8c2eca1153
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740394"
---
# <a name="binaryformatter-event-source"></a><span data-ttu-id="a012b-103">Источник события BinaryFormatter</span><span class="sxs-lookup"><span data-stu-id="a012b-103">BinaryFormatter event source</span></span>

<span data-ttu-id="a012b-104">Начиная с .NET 5.0, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> включает встроенный класс <xref:System.Diagnostics.Tracing.EventSource>, который позволяет реализовать визуализацию данных о сериализации или десериализации объекта.</span><span class="sxs-lookup"><span data-stu-id="a012b-104">Starting with .NET 5.0, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> includes a built-in <xref:System.Diagnostics.Tracing.EventSource> that gives you visibility into when an object serialization or deserialization is occurring.</span></span> <span data-ttu-id="a012b-105">Приложения могут использовать типы, производные от <xref:System.Diagnostics.Tracing.EventListener>, для прослушивания этих уведомлений и их записи в журнал.</span><span class="sxs-lookup"><span data-stu-id="a012b-105">Apps can use <xref:System.Diagnostics.Tracing.EventListener>-derived types to listen for these notifications and log them.</span></span>

<span data-ttu-id="a012b-106">Эта функция не заменяет <xref:System.Runtime.Serialization.SerializationBinder> или <xref:System.Runtime.Serialization.ISerializationSurrogate> и не может использоваться для изменения сериализуемых или десериализуемых данных.</span><span class="sxs-lookup"><span data-stu-id="a012b-106">This functionality is not a substitute for a <xref:System.Runtime.Serialization.SerializationBinder> or an <xref:System.Runtime.Serialization.ISerializationSurrogate> and can't be used to modify the data being serialized or deserialized.</span></span> <span data-ttu-id="a012b-107">Напротив, эта система событий предназначена для получения полезных сведений о сериализуемых или десериализуемых типах.</span><span class="sxs-lookup"><span data-stu-id="a012b-107">Rather, this eventing system is intended to provide insight into the types being serialized or deserialized.</span></span> <span data-ttu-id="a012b-108">Ее также можно использовать для обнаружения нежелательных вызовов к инфраструктуре `BinaryFormatter`, например из кода сторонней библиотеки.</span><span class="sxs-lookup"><span data-stu-id="a012b-108">It can also be used to detect unintended calls into the `BinaryFormatter` infrastructure, such as calls originating from third-party library code.</span></span>

## <a name="description-of-events"></a><span data-ttu-id="a012b-109">Описание событий</span><span class="sxs-lookup"><span data-stu-id="a012b-109">Description of events</span></span>

<span data-ttu-id="a012b-110">Источник событий `BinaryFormatter` имеет известное имя `System.Runtime.Serialization.Formatters.Binary.BinaryFormatterEventSource`.</span><span class="sxs-lookup"><span data-stu-id="a012b-110">The `BinaryFormatter` event source has the well-known name `System.Runtime.Serialization.Formatters.Binary.BinaryFormatterEventSource`.</span></span> <span data-ttu-id="a012b-111">Прослушиватели могут подписаться на 6 событий.</span><span class="sxs-lookup"><span data-stu-id="a012b-111">Listeners may subscribe to 6 events.</span></span>

### <a name="serializationstart-event-id--10"></a><span data-ttu-id="a012b-112">Событие SerializationStart с идентификатором `10`</span><span class="sxs-lookup"><span data-stu-id="a012b-112">SerializationStart event (id = `10`)</span></span>

<span data-ttu-id="a012b-113">Возникает при вызове метода <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>, который запускает процесс сериализации.</span><span class="sxs-lookup"><span data-stu-id="a012b-113">Raised when <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> has been called and has started the serialization process.</span></span> <span data-ttu-id="a012b-114">Это событие используется в паре с событием `SerializationEnd`.</span><span class="sxs-lookup"><span data-stu-id="a012b-114">This event is paired with the `SerializationEnd` event.</span></span> <span data-ttu-id="a012b-115">Событие `SerializationStart` может вызываться рекурсивно, если объект вызывает `BinaryFormatter.Serialize` в своей подпрограмме сериализации.</span><span class="sxs-lookup"><span data-stu-id="a012b-115">The `SerializationStart` event can be called recursively if an object calls `BinaryFormatter.Serialize` within its own serialization routine.</span></span>

<span data-ttu-id="a012b-116">Это событие не содержит полезных данных.</span><span class="sxs-lookup"><span data-stu-id="a012b-116">This event doesn't contain a payload.</span></span>

### <a name="serializationend-event-id--11"></a><span data-ttu-id="a012b-117">Событие SerializationEnd с идентификатором `11`</span><span class="sxs-lookup"><span data-stu-id="a012b-117">SerializationEnd event (id = `11`)</span></span>

<span data-ttu-id="a012b-118">Возникает, если метод `BinaryFormatter.Serialize` завершил свою работу.</span><span class="sxs-lookup"><span data-stu-id="a012b-118">Raised when `BinaryFormatter.Serialize` has completed its work.</span></span> <span data-ttu-id="a012b-119">Каждое событие `SerializationEnd` указывает на завершение последнего непарного события `SerializationStart`.</span><span class="sxs-lookup"><span data-stu-id="a012b-119">Each occurrence of `SerializationEnd` denotes the completion of the last unpaired `SerializationStart` event.</span></span>

<span data-ttu-id="a012b-120">Это событие не содержит полезных данных.</span><span class="sxs-lookup"><span data-stu-id="a012b-120">This event doesn't contain a payload.</span></span>

### <a name="serializingobject-event-id--12"></a><span data-ttu-id="a012b-121">Событие SerializingObject с идентификатором `12`</span><span class="sxs-lookup"><span data-stu-id="a012b-121">SerializingObject event (id = `12`)</span></span>

<span data-ttu-id="a012b-122">Возникает, когда `BinaryFormatter.Serialize` выполняет сериализацию непримитивного типа.</span><span class="sxs-lookup"><span data-stu-id="a012b-122">Raised when `BinaryFormatter.Serialize` is in the process of serializing a non-primitive type.</span></span> <span data-ttu-id="a012b-123">Инфраструктура `BinaryFormatter` исключает определенные типы (например, `string` и `int`) и не вызывает это событие при их появлении.</span><span class="sxs-lookup"><span data-stu-id="a012b-123">The `BinaryFormatter` infrastructure special-cases certain types (such as `string` and `int`) and doesn't raise this event when these types are encountered.</span></span> <span data-ttu-id="a012b-124">Это событие возникает для пользовательских типов и других типов, которые для `BinaryFormatter` не являются собственными.</span><span class="sxs-lookup"><span data-stu-id="a012b-124">This event is raised for user-defined types and other types that `BinaryFormatter` doesn't natively understand.</span></span>

<span data-ttu-id="a012b-125">Такое событие может возникать между событиями `SerializationStart` и `SerializationEnd` или не возникать вовсе.</span><span class="sxs-lookup"><span data-stu-id="a012b-125">This event may be raised zero or more times between `SerializationStart` and `SerializationEnd` events.</span></span>

<span data-ttu-id="a012b-126">Это событие содержит полезные данные с одним аргументом:</span><span class="sxs-lookup"><span data-stu-id="a012b-126">This event contains a payload with one argument:</span></span>

* <span data-ttu-id="a012b-127">`typeName` (`string`): имя сериализуемого типа с указанием сборки (см. статью о <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="a012b-127">`typeName` (`string`): The assembly-qualified name (see <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType>) of the type being serialized.</span></span>

### <a name="deserializationstart-event-id--20"></a><span data-ttu-id="a012b-128">Событие DeserializationStart с идентификатором `20`</span><span class="sxs-lookup"><span data-stu-id="a012b-128">DeserializationStart event (id = `20`)</span></span>

<span data-ttu-id="a012b-129">Возникает при вызове метода <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>, который запускает процесс десериализации.</span><span class="sxs-lookup"><span data-stu-id="a012b-129">Raised when <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> has been called and has started the deserialization process.</span></span> <span data-ttu-id="a012b-130">Это событие используется в паре с событием `DeserializationEnd`.</span><span class="sxs-lookup"><span data-stu-id="a012b-130">This event is paired with the `DeserializationEnd` event.</span></span> <span data-ttu-id="a012b-131">Событие `DeserializationStart` может вызываться рекурсивно, если объект вызывает `BinaryFormatter.Deserialize` в своей подпрограмме десериализации.</span><span class="sxs-lookup"><span data-stu-id="a012b-131">The `DeserializationStart` event can be called recursively if an object calls `BinaryFormatter.Deserialize` within its own deserialization routine.</span></span>

<span data-ttu-id="a012b-132">Это событие не содержит полезных данных.</span><span class="sxs-lookup"><span data-stu-id="a012b-132">This event doesn't contain a payload.</span></span>

### <a name="deserializationend-event-id--21"></a><span data-ttu-id="a012b-133">Событие DeserializationEnd с идентификатором `21`</span><span class="sxs-lookup"><span data-stu-id="a012b-133">DeserializationEnd event (id = `21`)</span></span>

<span data-ttu-id="a012b-134">Возникает, если метод `BinaryFormatter.Deserialize` завершил свою работу.</span><span class="sxs-lookup"><span data-stu-id="a012b-134">Raised when `BinaryFormatter.Deserialize` has completed its work.</span></span> <span data-ttu-id="a012b-135">Каждое событие `DeserializationEnd` указывает на завершение последнего непарного события `DeserializationStart`.</span><span class="sxs-lookup"><span data-stu-id="a012b-135">Each occurrence of `DeserializationEnd` denotes the completion of the last unpaired `DeserializationStart` event.</span></span>

<span data-ttu-id="a012b-136">Это событие не содержит полезных данных.</span><span class="sxs-lookup"><span data-stu-id="a012b-136">This event doesn't contain a payload.</span></span>

### <a name="deserializingobject-event-id--22"></a><span data-ttu-id="a012b-137">Событие DeserializingObject с идентификатором `22`</span><span class="sxs-lookup"><span data-stu-id="a012b-137">DeserializingObject event (id = `22`)</span></span>

<span data-ttu-id="a012b-138">Возникает, когда `BinaryFormatter.Deserialize` выполняет десериализацию непримитивного типа.</span><span class="sxs-lookup"><span data-stu-id="a012b-138">Raised when `BinaryFormatter.Deserialize` is in the process of deserializing a non-primitive type.</span></span> <span data-ttu-id="a012b-139">Инфраструктура `BinaryFormatter` исключает определенные типы (например, `string` и `int`) и не вызывает это событие при их появлении.</span><span class="sxs-lookup"><span data-stu-id="a012b-139">The `BinaryFormatter` infrastructure special-cases certain types (such as `string` and `int`) and doesn't raise this event when these types are encountered.</span></span> <span data-ttu-id="a012b-140">Это событие возникает для пользовательских типов и других типов, которые для `BinaryFormatter` не являются собственными.</span><span class="sxs-lookup"><span data-stu-id="a012b-140">This event is raised for user-defined types and other types that `BinaryFormatter` doesn't natively understand.</span></span>

<span data-ttu-id="a012b-141">Такое событие может возникать между событиями `DeserializationStart` и `DeserializationEnd` или не возникать вовсе.</span><span class="sxs-lookup"><span data-stu-id="a012b-141">This event may be raised zero or more times between `DeserializationStart` and `DeserializationEnd` events.</span></span>

<span data-ttu-id="a012b-142">Это событие содержит полезные данные с одним аргументом.</span><span class="sxs-lookup"><span data-stu-id="a012b-142">This event contains a payload with one argument.</span></span>

* <span data-ttu-id="a012b-143">`typeName` (`string`): имя десериализуемого типа с указанием сборки (см. статью о <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="a012b-143">`typeName` (`string`): The assembly-qualified name (see <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType>) of the type being deserialized.</span></span>

### <a name="advanced-subscribing-to-a-subset-of-notifications"></a><span data-ttu-id="a012b-144">\[Дополнительно\] Подписка на подмножество уведомлений</span><span class="sxs-lookup"><span data-stu-id="a012b-144">\[Advanced\] Subscribing to a subset of notifications</span></span>

<span data-ttu-id="a012b-145">Прослушиватели, которым нужно подписаться только на подмножество уведомлений, могут выбрать ключевые слова для добавления.</span><span class="sxs-lookup"><span data-stu-id="a012b-145">Listeners who wish to subscribe to only a subset of notifications can choose which keywords to enable.</span></span>

* <span data-ttu-id="a012b-146">`Serialization` = `(EventKeywords)1`: создает события `SerializationStart`, `SerializationEnd` и `SerializingObject`.</span><span class="sxs-lookup"><span data-stu-id="a012b-146">`Serialization` = `(EventKeywords)1`: Raises the `SerializationStart`, `SerializationEnd`, and `SerializingObject` events.</span></span>
* <span data-ttu-id="a012b-147">`Deserialization` = `(EventKeywords)2`: создает события `DeserializationStart`, `DeserializationEnd` и `DeserializingObject`.</span><span class="sxs-lookup"><span data-stu-id="a012b-147">`Deserialization` = `(EventKeywords)2`: Raises the `DeserializationStart`, `DeserializationEnd`, and `DeserializingObject` events.</span></span>

<span data-ttu-id="a012b-148">Если во время регистрации `EventListener` не указать фильтры ключевых слов, будут создаваться все события.</span><span class="sxs-lookup"><span data-stu-id="a012b-148">If no keyword filters are provided during `EventListener` registration, all events are raised.</span></span>

<span data-ttu-id="a012b-149">Для получения дополнительной информации см. <xref:System.Diagnostics.Tracing.EventKeywords?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a012b-149">For more information, see <xref:System.Diagnostics.Tracing.EventKeywords?displayProperty=nameWithType>.</span></span>

## <a name="sample-code"></a><span data-ttu-id="a012b-150">Образец кода</span><span class="sxs-lookup"><span data-stu-id="a012b-150">Sample code</span></span>

<span data-ttu-id="a012b-151">В приведенном ниже коде</span><span class="sxs-lookup"><span data-stu-id="a012b-151">The following code:</span></span>

- <span data-ttu-id="a012b-152">создается производный от `EventListener` тип, который выполняет запись в `System.Console`;</span><span class="sxs-lookup"><span data-stu-id="a012b-152">creates an `EventListener`-derived type that writes to `System.Console`,</span></span>
- <span data-ttu-id="a012b-153">для этого прослушивателя создается подписка на уведомления, создаваемые `BinaryFormatter`;</span><span class="sxs-lookup"><span data-stu-id="a012b-153">subscribes that listener to `BinaryFormatter`-produced notifications,</span></span>
- <span data-ttu-id="a012b-154">выполняется сериализация и десериализация графа простых объектов с помощью `BinaryFormatter`;</span><span class="sxs-lookup"><span data-stu-id="a012b-154">serializes and deserializes a simple object graph using `BinaryFormatter`, and</span></span>
- <span data-ttu-id="a012b-155">происходит анализ созданных событий.</span><span class="sxs-lookup"><span data-stu-id="a012b-155">analyzes the events that have been raised.</span></span>

:::code language="csharp" source="snippets/binaryformatter-event-source/csharp/Program.cs":::

<span data-ttu-id="a012b-156">Выходные данные приведенного выше кода будут примерно следующими:</span><span class="sxs-lookup"><span data-stu-id="a012b-156">The preceding code produces output similar to the following example:</span></span>

```output
Event SerializationStart (id=10) received.
Event SerializingObject (id=12) received.
typeName = BinaryFormatterEventSample.Person, BinaryFormatterEventSample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null
Event SerializingObject (id=12) received.
typeName = BinaryFormatterEventSample.Book, BinaryFormatterEventSample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null
Event SerializationStop (id=11) received.
Event DeserializationStart (id=20) received.
Event DeserializingObject (id=22) received.
typeName = BinaryFormatterEventSample.Person, BinaryFormatterEventSample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null
Event DeserializingObject (id=22) received.
typeName = BinaryFormatterEventSample.Book, BinaryFormatterEventSample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null
Event DeserializationStop (id=21) received.
Rehydrated person Logan Edwards
Favorite book: A Tale of Two Cities by Charles Dickens, list price 10.25
```

<span data-ttu-id="a012b-157">В этом примере `EventListener` определенной консоли регистрирует, что сначала запускается сериализация, сериализуются экземпляры `Person` и `Book`, а затем сериализация завершается.</span><span class="sxs-lookup"><span data-stu-id="a012b-157">In this sample, the console-based `EventListener` logs that serialization starts, instances of `Person` and `Book` are serialized, and then serialization completes.</span></span> <span data-ttu-id="a012b-158">Аналогичным образом происходит запуск десериализации, десериализуются экземпляры `Person` и `Book`, а затем десериализаця завершается.</span><span class="sxs-lookup"><span data-stu-id="a012b-158">Similarly, once deserialization has started, instances of `Person` and `Book` are deserialized, and then deserialization completes.</span></span>

<span data-ttu-id="a012b-159">Затем приложение выводит значения, содержащиеся в десериализованном экземпляре `Person`, чтобы продемонстрировать, что объект сериализован и десериализован правильно.</span><span class="sxs-lookup"><span data-stu-id="a012b-159">The app then prints the values contained in the deserialized `Person` to demonstrate that the object did in fact serialize and deserialize properly.</span></span>

## <a name="see-also"></a><span data-ttu-id="a012b-160">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a012b-160">See also</span></span>

<span data-ttu-id="a012b-161">Дополнительные сведения об использовании `EventListener` для получения уведомлений на основе `EventSource` см. в статье о [классе `EventListener`](xref:System.Diagnostics.Tracing.EventListener).</span><span class="sxs-lookup"><span data-stu-id="a012b-161">For more information on using `EventListener` to receive `EventSource`-based notifications, see [the `EventListener` class](xref:System.Diagnostics.Tracing.EventListener).</span></span>
