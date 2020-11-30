---
title: Практическое руководство. Реализация наблюдателя
description: Реализация наблюдателя в .NET. Конструктивный шаблон наблюдателя подразумевает разделение ролей наблюдателя, который регистрируется для получения уведомлений, и поставщика.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- observers [.NET], observer design pattern
- observer design pattern [.NET], implementing observers
ms.assetid: 8ecfa9f5-b500-473d-bcf0-5652ffb1e53d
ms.openlocfilehash: 73f6d2c25c727717394c79268b71b44ea9ff7800
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697484"
---
# <a name="how-to-implement-an-observer"></a><span data-ttu-id="3fdd0-104">Практическое руководство. Реализация наблюдателя</span><span class="sxs-lookup"><span data-stu-id="3fdd0-104">How to: Implement an Observer</span></span>

<span data-ttu-id="3fdd0-105">Шаблон разработки наблюдателя подразумевает разделение ролей наблюдателя, который регистрируется для получения уведомлений, и поставщика, который отслеживает данные и отправляет уведомления одному или нескольким наблюдателям.</span><span class="sxs-lookup"><span data-stu-id="3fdd0-105">The observer design pattern requires a division between an observer, which registers for notifications, and a provider, which monitors data and sends notifications to one or more observers.</span></span> <span data-ttu-id="3fdd0-106">В этой статье объясняется, как создать наблюдатель.</span><span class="sxs-lookup"><span data-stu-id="3fdd0-106">This topic discusses how to create an observer.</span></span> <span data-ttu-id="3fdd0-107">Создание поставщика рассматривается в связанной статье [Практическое руководство. Реализация поставщика](how-to-implement-a-provider.md).</span><span class="sxs-lookup"><span data-stu-id="3fdd0-107">A related topic, [How to: Implement a Provider](how-to-implement-a-provider.md), discusses how to create an provider.</span></span>  
  
### <a name="to-create-an-observer"></a><span data-ttu-id="3fdd0-108">Создание наблюдателя</span><span class="sxs-lookup"><span data-stu-id="3fdd0-108">To create an observer</span></span>  
  
1. <span data-ttu-id="3fdd0-109">Определите наблюдатель в виде типа, реализующего интерфейс <xref:System.IObserver%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3fdd0-109">Define the observer, which is a type that implements the <xref:System.IObserver%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="3fdd0-110">Например, в следующем примере кода определяется тип с именем `TemperatureReporter`, представляющий собой реализацию <xref:System.IObserver%601?displayProperty=nameWithType> с аргументом универсального типа `Temperature`.</span><span class="sxs-lookup"><span data-stu-id="3fdd0-110">For example, the following code defines a type named `TemperatureReporter` that is a constructed <xref:System.IObserver%601?displayProperty=nameWithType> implementation with a generic type argument of `Temperature`.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2. <span data-ttu-id="3fdd0-111">Если наблюдатель может прекратить получение уведомлений до вызова поставщиком его реализации <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, определите частную переменную, которая будет содержать реализацию <xref:System.IDisposable>, полученную из метода <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> поставщика.</span><span class="sxs-lookup"><span data-stu-id="3fdd0-111">If the observer can stop receiving notifications before the provider calls its <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementation, define a private variable that will hold the <xref:System.IDisposable> implementation returned by the provider's <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3fdd0-112">Также следует определить метод подписки, который вызывает метод <xref:System.IObservable%601.Subscribe%2A> поставщика и сохраняет возвращенный объект <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="3fdd0-112">You should also define a subscription method that calls the provider's <xref:System.IObservable%601.Subscribe%2A> method and stores the returned <xref:System.IDisposable> object.</span></span> <span data-ttu-id="3fdd0-113">Например, следующий код определяет закрытую переменную с именем `unsubscriber` и определяет метод `Subscribe`, который вызывает метод <xref:System.IObservable%601.Subscribe%2A> поставщика и назначает возвращенный объект переменной `unsubscriber`.</span><span class="sxs-lookup"><span data-stu-id="3fdd0-113">For example, the following code defines a private variable named `unsubscriber` and defines a `Subscribe` method that calls the provider's <xref:System.IObservable%601.Subscribe%2A> method and assigns the returned object to the `unsubscriber` variable.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3. <span data-ttu-id="3fdd0-114">Определите метод, позволяющий наблюдателю прекратить получение уведомлений до вызова поставщиком его реализации <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, если вам нужна такая функциональность.</span><span class="sxs-lookup"><span data-stu-id="3fdd0-114">Define a method that enables the observer to stop receiving notifications before the provider calls its <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementation, if this feature is required.</span></span> <span data-ttu-id="3fdd0-115">В следующем примере определяется метод `Unsubscribe`.</span><span class="sxs-lookup"><span data-stu-id="3fdd0-115">The following example defines an `Unsubscribe` method.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4. <span data-ttu-id="3fdd0-116">Предоставьте реализацию трех методов, определяемых интерфейсом <xref:System.IObserver%601>: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType> и <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3fdd0-116">Provide implementations of the three methods defined by the <xref:System.IObserver%601> interface: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, and <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3fdd0-117">В зависимости от поставщика и задач приложения, для методов <xref:System.IObserver%601.OnError%2A> и <xref:System.IObserver%601.OnCompleted%2A> можно использовать заглушки.</span><span class="sxs-lookup"><span data-stu-id="3fdd0-117">Depending on the provider and the needs of the application, the <xref:System.IObserver%601.OnError%2A> and <xref:System.IObserver%601.OnCompleted%2A> methods can be stub implementations.</span></span> <span data-ttu-id="3fdd0-118">Обратите внимание, что метод <xref:System.IObserver%601.OnError%2A> не должен обрабатывать переданный объект <xref:System.Exception> как исключение, а метод <xref:System.IObserver%601.OnCompleted%2A> может вызывать реализацию <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> поставщика.</span><span class="sxs-lookup"><span data-stu-id="3fdd0-118">Note that the <xref:System.IObserver%601.OnError%2A> method should not handle the passed <xref:System.Exception> object as an exception, and the <xref:System.IObserver%601.OnCompleted%2A> method is free to call the provider's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="3fdd0-119">В приведенном ниже примере показана реализация <xref:System.IObserver%601> для класса `TemperatureReporter`.</span><span class="sxs-lookup"><span data-stu-id="3fdd0-119">The following example shows the <xref:System.IObserver%601> implementation of the `TemperatureReporter` class.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="3fdd0-120">Пример</span><span class="sxs-lookup"><span data-stu-id="3fdd0-120">Example</span></span>  

 <span data-ttu-id="3fdd0-121">Ниже представлен полный пример исходного кода для класса `TemperatureReporter`, который предоставляет реализацию <xref:System.IObserver%601> для приложения мониторинга температуры.</span><span class="sxs-lookup"><span data-stu-id="3fdd0-121">The following example contains the complete source code for the `TemperatureReporter` class, which provides the <xref:System.IObserver%601> implementation for a temperature monitoring application.</span></span>  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="3fdd0-122">См. также</span><span class="sxs-lookup"><span data-stu-id="3fdd0-122">See also</span></span>

- <xref:System.IObserver%601>
- [<span data-ttu-id="3fdd0-123">Шаблон разработки наблюдателя</span><span class="sxs-lookup"><span data-stu-id="3fdd0-123">Observer Design Pattern</span></span>](observer-design-pattern.md)
- [<span data-ttu-id="3fdd0-124">Практическое руководство. Реализация поставщика</span><span class="sxs-lookup"><span data-stu-id="3fdd0-124">How to: Implement a Provider</span></span>](how-to-implement-a-provider.md)
- [<span data-ttu-id="3fdd0-125">Рекомендации по шаблону разработки Observer</span><span class="sxs-lookup"><span data-stu-id="3fdd0-125">Observer Design Pattern Best Practices</span></span>](observer-design-pattern-best-practices.md)
