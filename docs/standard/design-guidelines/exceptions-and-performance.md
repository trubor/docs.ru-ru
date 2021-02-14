---
description: 'Узнайте подробнее о: Исключения и производительность'
title: Исключения и производительность
ms.date: 10/22/2008
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
ms.openlocfilehash: 72b35ccca5514e56dcc04fc0a07d1f9887c4a2f7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642127"
---
# <a name="exceptions-and-performance"></a><span data-ttu-id="dcd7c-103">Исключения и производительность</span><span class="sxs-lookup"><span data-stu-id="dcd7c-103">Exceptions and Performance</span></span>

<span data-ttu-id="dcd7c-104">Одной из распространенных проблем, связанных с исключениями, является то, что если исключения используются для кода, который регулярно завершается ошибкой, производительность реализации будет неприемлемой.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-104">One common concern related to exceptions is that if exceptions are used for code that routinely fails, the performance of the implementation will be unacceptable.</span></span> <span data-ttu-id="dcd7c-105">Это является действительной проблемой.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-105">This is a valid concern.</span></span> <span data-ttu-id="dcd7c-106">Когда элемент выдает исключение, его производительность может быть на порядок ниже.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-106">When a member throws an exception, its performance can be orders of magnitude slower.</span></span> <span data-ttu-id="dcd7c-107">Тем не менее можно достичь хорошей производительности, строго придерживаясь рекомендаций по исключениям, которые не допускают использование кодов ошибок.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-107">However, it is possible to achieve good performance while strictly adhering to the exception guidelines that disallow using error codes.</span></span> <span data-ttu-id="dcd7c-108">В двух шаблонах, описанных в этом разделе, предложены способы сделать это.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-108">Two patterns described in this section suggest ways to do this.</span></span>

 <span data-ttu-id="dcd7c-109">❌ НЕ используйте коды ошибок из-за опасений, что исключения могут негативно сказаться на производительности.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-109">❌ DO NOT use error codes because of concerns that exceptions might affect performance negatively.</span></span>

 <span data-ttu-id="dcd7c-110">Повысить производительность можно с помощью шаблона Tester-Doer или Try-Parse, описанных в следующих двух разделах.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-110">To improve performance, it is possible to use either the Tester-Doer Pattern or the Try-Parse Pattern, described in the next two sections.</span></span>

## <a name="tester-doer-pattern"></a><span data-ttu-id="dcd7c-111">Шаблон Tester-Doer</span><span class="sxs-lookup"><span data-stu-id="dcd7c-111">Tester-Doer Pattern</span></span>

 <span data-ttu-id="dcd7c-112">Иногда производительность элемента, вызывающего исключение, можно улучшить, разбив его на два элемента.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-112">Sometimes performance of an exception-throwing member can be improved by breaking the member into two.</span></span> <span data-ttu-id="dcd7c-113">Рассмотрим метод <xref:System.Collections.Generic.ICollection%601.Add%2A> интерфейса <xref:System.Collections.Generic.ICollection%601>.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-113">Let’s look at the <xref:System.Collections.Generic.ICollection%601.Add%2A> method of the <xref:System.Collections.Generic.ICollection%601> interface.</span></span>

```csharp
ICollection<int> numbers = ...
numbers.Add(1);
```

 <span data-ttu-id="dcd7c-114">Будет возвращен метод `Add`, если коллекция доступна только для чтения.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-114">The method `Add` throws if the collection is read-only.</span></span> <span data-ttu-id="dcd7c-115">В сценариях, когда ожидается, что вызов метода будет часто завершаться ошибкой, это может быть проблемой с производительностью.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-115">This can be a performance problem in scenarios where the method call is expected to fail often.</span></span> <span data-ttu-id="dcd7c-116">Один из способов устранения проблемы — проверить, является ли коллекция доступной для записи, прежде чем пытаться добавить значение.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-116">One of the ways to mitigate the problem is to test whether the collection is writable before trying to add a value.</span></span>

```csharp
ICollection<int> numbers = ...
...
if (!numbers.IsReadOnly)
{
    numbers.Add(1);
}
```

 <span data-ttu-id="dcd7c-117">Элемент, используемый для проверки условия, которое в нашем примере является свойством `IsReadOnly`, называется тестировщиком (tester).</span><span class="sxs-lookup"><span data-stu-id="dcd7c-117">The member used to test a condition, which in our example is the property `IsReadOnly`, is referred to as the tester.</span></span> <span data-ttu-id="dcd7c-118">Элемент, используемый для выполнения операции, которая может приводить к исключениям (метод `Add` в нашем примере), называется исполнителем (doer).</span><span class="sxs-lookup"><span data-stu-id="dcd7c-118">The member used to perform a potentially throwing operation, the `Add` method in our example, is referred to as the doer.</span></span>

 <span data-ttu-id="dcd7c-119">✔️ Рассмотрите возможность использования шаблона Test-Doer для элементов, которые могут выдавать исключения в распространенных сценариях, чтобы избежать проблем с производительностью, вызванных исключениями.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-119">✔️ CONSIDER the Tester-Doer Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>

## <a name="try-parse-pattern"></a><span data-ttu-id="dcd7c-120">Шаблон Try-Parse</span><span class="sxs-lookup"><span data-stu-id="dcd7c-120">Try-Parse Pattern</span></span>

 <span data-ttu-id="dcd7c-121">Для API-интерфейсов, в которых очень важна производительность, следует использовать более быстрый шаблон, чем шаблон Test-Doer, описанный в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-121">For extremely performance-sensitive APIs, an even faster pattern than the Tester-Doer Pattern described in the previous section should be used.</span></span> <span data-ttu-id="dcd7c-122">Шаблон вызывает метод для корректировки имени элемента, чтобы сделать строго определенный тестовый случай частью семантики элемента.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-122">The pattern calls for adjusting the member name to make a well-defined test case a part of the member semantics.</span></span> <span data-ttu-id="dcd7c-123">Например, <xref:System.DateTime> определяет метод <xref:System.DateTime.Parse%2A>, который выдает исключение, если синтаксический анализ строки завершается ошибкой.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-123">For example, <xref:System.DateTime> defines a <xref:System.DateTime.Parse%2A> method that throws an exception if parsing of a string fails.</span></span> <span data-ttu-id="dcd7c-124">Он также определяет соответствующий метод <xref:System.DateTime.TryParse%2A>, который пытается выполнить синтаксический анализ, но возвращает значение false, если синтаксический анализ завершается неудачно, и возвращает результат успешного синтаксического анализа с помощью параметра `out`.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-124">It also defines a corresponding <xref:System.DateTime.TryParse%2A> method that attempts to parse, but returns false if parsing is unsuccessful and returns the result of a successful parsing using an `out` parameter.</span></span>

```csharp
public struct DateTime
{
    public static DateTime Parse(string dateTime)
    {
        ...
    }
    public static bool TryParse(string dateTime, out DateTime result)
    {
        ...
    }
}
```

 <span data-ttu-id="dcd7c-125">При использовании этого шаблона важно определить функциональность Try в сжатые сроки.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-125">When using this pattern, it is important to define the try functionality in strict terms.</span></span> <span data-ttu-id="dcd7c-126">Если элемент завершается ошибкой по какой-либо причине, отличной от правильно определенного шаблона Try, элемент должен по-прежнему вызывать соответствующее исключение.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-126">If the member fails for any reason other than the well-defined try, the member must still throw a corresponding exception.</span></span>

 <span data-ttu-id="dcd7c-127">✔️ Рассмотрите возможность использования шаблона Try-Parse для элементов, которые могут выдавать исключения в распространенных сценариях, чтобы избежать проблем с производительностью, вызванных исключениями.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-127">✔️ CONSIDER the Try-Parse Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>

 <span data-ttu-id="dcd7c-128">✔️ ИСПОЛЬЗУЙТЕ префикс "Try" и логический тип возвращаемого значения для методов, реализующих этот шаблон.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-128">✔️ DO use the prefix "Try" and Boolean return type for methods implementing this pattern.</span></span>

 <span data-ttu-id="dcd7c-129">✔️ ПРЕДОСТАВЬТЕ элемент, выдающий исключения, для каждого элемента с помощью шаблона Try-Parse.</span><span class="sxs-lookup"><span data-stu-id="dcd7c-129">✔️ DO provide an exception-throwing member for each member using the Try-Parse Pattern.</span></span>

 <span data-ttu-id="dcd7c-130">*Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="dcd7c-130">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="dcd7c-131">*Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="dcd7c-131">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="dcd7c-132">См. также</span><span class="sxs-lookup"><span data-stu-id="dcd7c-132">See also</span></span>

- [<span data-ttu-id="dcd7c-133">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="dcd7c-133">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="dcd7c-134">Правила разработки исключений</span><span class="sxs-lookup"><span data-stu-id="dcd7c-134">Design Guidelines for Exceptions</span></span>](exceptions.md)
