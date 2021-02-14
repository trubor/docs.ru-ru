---
description: 'Узнайте подробнее о: Разработка событий'
title: Разработка событий
ms.date: 10/22/2008
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
ms.openlocfilehash: d64bfb13792aa9d646560de844acddd9b7e188c0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642205"
---
# <a name="event-design"></a><span data-ttu-id="99174-103">Разработка событий</span><span class="sxs-lookup"><span data-stu-id="99174-103">Event Design</span></span>

<span data-ttu-id="99174-104">События — это наиболее часто используемая форма обратных вызовов (конструкции, позволяющие платформе вызывать пользовательский код).</span><span class="sxs-lookup"><span data-stu-id="99174-104">Events are the most commonly used form of callbacks (constructs that allow the framework to call into user code).</span></span> <span data-ttu-id="99174-105">Другие механизмы обратного вызова включают элементы, принимающие делегаты, виртуальные элементы и подключаемые модули на основе интерфейсов. Данные исследований на предмет удобства использования указывают на то, что для большинства разработчиков лучше использовать события, чем другие механизмы обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="99174-105">Other callback mechanisms include members taking delegates, virtual members, and interface-based plug-ins. Data from usability studies indicate that the majority of developers are more comfortable using events than they are using the other callback mechanisms.</span></span> <span data-ttu-id="99174-106">События хорошо интегрируются с Visual Studio и многими языками.</span><span class="sxs-lookup"><span data-stu-id="99174-106">Events are nicely integrated with Visual Studio and many languages.</span></span>

 <span data-ttu-id="99174-107">Важно отметить, что существует две группы событий: события, вызванные до изменений состояния системы (события до операции), и события, вызванные после изменений состояния (события после операции).</span><span class="sxs-lookup"><span data-stu-id="99174-107">It is important to note that there are two groups of events: events raised before a state of the system changes, called pre-events, and events raised after a state changes, called post-events.</span></span> <span data-ttu-id="99174-108">Примером события до операции может быть `Form.Closing`, которое вызывается перед закрытием формы.</span><span class="sxs-lookup"><span data-stu-id="99174-108">An example of a pre-event would be `Form.Closing`, which is raised before a form is closed.</span></span> <span data-ttu-id="99174-109">Примером события после операции может быть `Form.Closed`, которое вызывается после закрытия формы.</span><span class="sxs-lookup"><span data-stu-id="99174-109">An example of a post-event would be `Form.Closed`, which is raised after a form is closed.</span></span>

 <span data-ttu-id="99174-110">✔️ Для событий СЛЕДУЕТ использовать термин "вызывать", а не "инициировать" или "активировать".</span><span class="sxs-lookup"><span data-stu-id="99174-110">✔️ DO use the term "raise" for events rather than "fire" or "trigger."</span></span>

 <span data-ttu-id="99174-111">✔️ Чтобы вручную не создавать делегаты для использования в качестве обработчиков событий, СЛЕДУЕТ использовать <xref:System.EventHandler%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="99174-111">✔️ DO use <xref:System.EventHandler%601?displayProperty=nameWithType> instead of manually creating new delegates to be used as event handlers.</span></span>

 <span data-ttu-id="99174-112">✔️ Рассмотрите возможность использования подкласса <xref:System.EventArgs> в качестве аргумента события, если вы не уверены, что событию никогда не нужно будет передавать какие-либо данные в метод обработки событий. В этом случае можно использовать тип `EventArgs` напрямую.</span><span class="sxs-lookup"><span data-stu-id="99174-112">✔️ CONSIDER using a subclass of <xref:System.EventArgs> as the event argument, unless you are absolutely sure the event will never need to carry any data to the event handling method, in which case you can use the `EventArgs` type directly.</span></span>

 <span data-ttu-id="99174-113">Если вы подаете API с помощью `EventArgs` напрямую, вы никогда не сможете добавить данные, которые будут передаваться вместе с событием, не нарушая совместимости.</span><span class="sxs-lookup"><span data-stu-id="99174-113">If you ship an API using `EventArgs` directly, you will never be able to add any data to be carried with the event without breaking compatibility.</span></span> <span data-ttu-id="99174-114">Если используется подкласс, при необходимости вы сможете добавлять в него свойства (даже если изначально он полностью пустой).</span><span class="sxs-lookup"><span data-stu-id="99174-114">If you use a subclass, even if initially completely empty, you will be able to add properties to the subclass when needed.</span></span>

 <span data-ttu-id="99174-115">✔️ СЛЕДУЕТ использовать защищенный виртуальный метод для вызова каждого события.</span><span class="sxs-lookup"><span data-stu-id="99174-115">✔️ DO use a protected virtual method to raise each event.</span></span> <span data-ttu-id="99174-116">Это применимо только к нестатическим событиям для незапечатанных классов, а не к структурам, запечатанным классам или статическим событиям.</span><span class="sxs-lookup"><span data-stu-id="99174-116">This is only applicable to nonstatic events on unsealed classes, not to structs, sealed classes, or static events.</span></span>

 <span data-ttu-id="99174-117">Цель метода — предоставить для производного класса способ обработать событие с помощью переопределения.</span><span class="sxs-lookup"><span data-stu-id="99174-117">The purpose of the method is to provide a way for a derived class to handle the event using an override.</span></span> <span data-ttu-id="99174-118">Переопределение является более гибким, быстрым и естественным способом для обработки событий базового класса в производных классах.</span><span class="sxs-lookup"><span data-stu-id="99174-118">Overriding is a more flexible, faster, and more natural way to handle base class events in derived classes.</span></span> <span data-ttu-id="99174-119">По соглашению имя метода должно начинаться с префикса On, после него должно следовать имя события.</span><span class="sxs-lookup"><span data-stu-id="99174-119">By convention, the name of the method should start with "On" and be followed with the name of the event.</span></span>

 <span data-ttu-id="99174-120">Производный класс может не вызывать базовую реализацию метода в его переопределении.</span><span class="sxs-lookup"><span data-stu-id="99174-120">The derived class can choose not to call the base implementation of the method in its override.</span></span> <span data-ttu-id="99174-121">Будьте готовы к этому: не включайте какую-либо обработку в метод, который требуется для правильной работы базового класса.</span><span class="sxs-lookup"><span data-stu-id="99174-121">Be prepared for this by not including any processing in the method that is required for the base class to work correctly.</span></span>

 <span data-ttu-id="99174-122">✔️ СЛЕДУЕТ️ принять один параметр для защищенного метода, который порождает событие.</span><span class="sxs-lookup"><span data-stu-id="99174-122">✔️ DO take one parameter to the protected method that raises an event.</span></span>

 <span data-ttu-id="99174-123">Параметр должен называться `e` и быть типизированным как класс аргумента события.</span><span class="sxs-lookup"><span data-stu-id="99174-123">The parameter should be named `e` and should be typed as the event argument class.</span></span>

 <span data-ttu-id="99174-124">❌ НЕ передавайте значение NULL в качестве отправителя при вызове нестатического события.</span><span class="sxs-lookup"><span data-stu-id="99174-124">❌ DO NOT pass null as the sender when raising a nonstatic event.</span></span>

 <span data-ttu-id="99174-125">✔️ ПЕРЕДАВАЙТЕ значение NULL в качестве отправителя при вызове статического события.</span><span class="sxs-lookup"><span data-stu-id="99174-125">✔️ DO pass null as the sender when raising a static event.</span></span>

 <span data-ttu-id="99174-126">❌ НЕ передавайте значение NULL в качестве параметра данных события при вызове события.</span><span class="sxs-lookup"><span data-stu-id="99174-126">❌ DO NOT pass null as the event data parameter when raising an event.</span></span>

 <span data-ttu-id="99174-127">Следует передать `EventArgs.Empty`, если вы не хотите передавать какие-либо данные в метод обработки событий.</span><span class="sxs-lookup"><span data-stu-id="99174-127">You should pass `EventArgs.Empty` if you don’t want to pass any data to the event handling method.</span></span> <span data-ttu-id="99174-128">Разработчики предполагают, что этот параметр не должен иметь значение NULL.</span><span class="sxs-lookup"><span data-stu-id="99174-128">Developers expect this parameter not to be null.</span></span>

 <span data-ttu-id="99174-129">✔️ РАССМОТРИТЕ возможность вызова событий, которые может отменить пользователь.</span><span class="sxs-lookup"><span data-stu-id="99174-129">✔️ CONSIDER raising events that the end user can cancel.</span></span> <span data-ttu-id="99174-130">Это применяется только к событиям до операции.</span><span class="sxs-lookup"><span data-stu-id="99174-130">This only applies to pre-events.</span></span>

 <span data-ttu-id="99174-131">Чтобы разрешить пользователю отменять события, используйте в качестве аргумента события <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> или его подкласс.</span><span class="sxs-lookup"><span data-stu-id="99174-131">Use <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> or its subclass as the event argument to allow the end user to cancel events.</span></span>

### <a name="custom-event-handler-design"></a><span data-ttu-id="99174-132">Разработка пользовательского обработчика событий</span><span class="sxs-lookup"><span data-stu-id="99174-132">Custom Event Handler Design</span></span>

 <span data-ttu-id="99174-133">В некоторых случая нельзя использовать `EventHandler<T>`, например, если платформа должна работать с более ранними версиями среды CLR, которые не поддерживали универсальные шаблоны.</span><span class="sxs-lookup"><span data-stu-id="99174-133">There are cases in which `EventHandler<T>` cannot be used, such as when the framework needs to work with earlier versions of the CLR, which did not support Generics.</span></span> <span data-ttu-id="99174-134">В таких случаях может потребоваться спроектировать и разработать пользовательский делегат обработчика событий.</span><span class="sxs-lookup"><span data-stu-id="99174-134">In such cases, you might need to design and develop a custom event handler delegate.</span></span>

 <span data-ttu-id="99174-135">✔️ СЛЕДУЕТ️ использовать тип возвращаемого значения void для обработчиков событий.</span><span class="sxs-lookup"><span data-stu-id="99174-135">✔️ DO use a return type of void for event handlers.</span></span>

 <span data-ttu-id="99174-136">Обработчик событий может вызывать несколько методов обработки событий, возможно, для нескольких объектов.</span><span class="sxs-lookup"><span data-stu-id="99174-136">An event handler can invoke multiple event handling methods, possibly on multiple objects.</span></span> <span data-ttu-id="99174-137">Если бы методам обработки событий можно было возвращать значение, то для каждого вызова события было бы несколько возвращаемых значений.</span><span class="sxs-lookup"><span data-stu-id="99174-137">If event handling methods were allowed to return a value, there would be multiple return values for each event invocation.</span></span>

 <span data-ttu-id="99174-138">✔ В качества типа первого параметра обработчика событий СЛЕДУЕТ️ использовать `object`. Присвойте ему имя `sender`.</span><span class="sxs-lookup"><span data-stu-id="99174-138">✔️ DO use `object` as the type of the first parameter of the event handler, and call it `sender`.</span></span>

 <span data-ttu-id="99174-139">✔ В качества типа второго параметра обработчика событий СЛЕДУЕТ️ использовать <xref:System.EventArgs?displayProperty=nameWithType>. Присвойте ему имя `e`.</span><span class="sxs-lookup"><span data-stu-id="99174-139">✔️ DO use <xref:System.EventArgs?displayProperty=nameWithType> or its subclass as the type of the second parameter of the event handler, and call it `e`.</span></span>

 <span data-ttu-id="99174-140">❌ В обработчиках событий НЕ должно быть больше двух параметров.</span><span class="sxs-lookup"><span data-stu-id="99174-140">❌ DO NOT have more than two parameters on event handlers.</span></span>

 <span data-ttu-id="99174-141">*Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="99174-141">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="99174-142">*Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="99174-142">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="99174-143">См. также</span><span class="sxs-lookup"><span data-stu-id="99174-143">See also</span></span>

- [<span data-ttu-id="99174-144">Правила разработки членов</span><span class="sxs-lookup"><span data-stu-id="99174-144">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="99174-145">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="99174-145">Framework Design Guidelines</span></span>](index.md)
