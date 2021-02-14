---
description: 'Узнайте подробнее о: Разработка интерфейса'
title: Разработка интерфейса
ms.date: 10/22/2008
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
ms.openlocfilehash: 387f921f8bdbe6c6d398aa31dcc8a22c7da455f7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641984"
---
# <a name="interface-design"></a><span data-ttu-id="c20e4-103">Разработка интерфейса</span><span class="sxs-lookup"><span data-stu-id="c20e4-103">Interface Design</span></span>

<span data-ttu-id="c20e4-104">Хотя большинство API-интерфейсов лучше всего моделировать с помощью классов и структур, бывают случаи, когда интерфейсы подходят больше или являются единственным вариантом.</span><span class="sxs-lookup"><span data-stu-id="c20e4-104">Although most APIs are best modeled using classes and structs, there are cases in which interfaces are more appropriate or are the only option.</span></span>

 <span data-ttu-id="c20e4-105">Среда CLR не поддерживает множественное наследование (т. е. классы CLR не могут наследовать от нескольких базовых классов), но позволяют типам реализовать один или несколько интерфейсов в дополнение к наследованию от базового класса.</span><span class="sxs-lookup"><span data-stu-id="c20e4-105">The CLR does not support multiple inheritance (i.e., CLR classes cannot inherit from more than one base class), but it does allow types to implement one or more interfaces in addition to inheriting from a base class.</span></span> <span data-ttu-id="c20e4-106">Поэтому интерфейсы часто используются для получения эффекта множественного наследования.</span><span class="sxs-lookup"><span data-stu-id="c20e4-106">Therefore, interfaces are often used to achieve the effect of multiple inheritance.</span></span> <span data-ttu-id="c20e4-107">Например, <xref:System.IDisposable> является интерфейсом, который позволяет типам поддерживать возможность удаления независимо от любых других иерархий наследования, в которых они хотят участвовать.</span><span class="sxs-lookup"><span data-stu-id="c20e4-107">For example, <xref:System.IDisposable> is an interface that allows types to support disposability independent of any other inheritance hierarchy in which they want to participate.</span></span>

 <span data-ttu-id="c20e4-108">Другая ситуация, при которой необходимо определить интерфейс, — это создание общего интерфейса, который может поддерживаться несколькими типами, включая некоторые типы значений.</span><span class="sxs-lookup"><span data-stu-id="c20e4-108">The other situation in which defining an interface is appropriate is in creating a common interface that can be supported by several types, including some value types.</span></span> <span data-ttu-id="c20e4-109">Типы значений не могут наследовать от типов, отличных от <xref:System.ValueType>, но они могут реализовывать интерфейсы, поэтому использование интерфейса — это единственный доступный вариант для предоставления общего базового типа.</span><span class="sxs-lookup"><span data-stu-id="c20e4-109">Value types cannot inherit from types other than <xref:System.ValueType>, but they can implement interfaces, so using an interface is the only option in order to provide a common base type.</span></span>

 <span data-ttu-id="c20e4-110">✔ ОПРЕДЕЛИТЕ интерфейс, если требуется, чтобы набор типов, включая типы значений, поддерживал некоторые общие API-интерфейсы.</span><span class="sxs-lookup"><span data-stu-id="c20e4-110">✔️ DO define an interface if you need some common API to be supported by a set of types that includes value types.</span></span>

 <span data-ttu-id="c20e4-111">✔️ Рассмотрите возможность определения интерфейса, если требуется поддержка его функциональных возможностей для типов, которые уже наследуются от другого типа.</span><span class="sxs-lookup"><span data-stu-id="c20e4-111">✔️ CONSIDER defining an interface if you need to support its functionality on types that already inherit from some other type.</span></span>

 <span data-ttu-id="c20e4-112">❌ Избегайте использования интерфейсов метки (интерфейсы без элементов).</span><span class="sxs-lookup"><span data-stu-id="c20e4-112">❌ AVOID using marker interfaces (interfaces with no members).</span></span>

 <span data-ttu-id="c20e4-113">Если необходимо пометить класс как имеющий определенную характеристику (метку), как правило, используйте настраиваемый атрибут, а не интерфейс.</span><span class="sxs-lookup"><span data-stu-id="c20e4-113">If you need to mark a class as having a specific characteristic (marker), in general, use a custom attribute rather than an interface.</span></span>

 <span data-ttu-id="c20e4-114">✔ ПРЕДОСТАВЬТЕ по крайней мере один тип, который является реализацией интерфейса.</span><span class="sxs-lookup"><span data-stu-id="c20e4-114">✔️ DO provide at least one type that is an implementation of an interface.</span></span>

 <span data-ttu-id="c20e4-115">Это помогает проверить структуру интерфейса.</span><span class="sxs-lookup"><span data-stu-id="c20e4-115">Doing this helps to validate the design of the interface.</span></span> <span data-ttu-id="c20e4-116">Например, <xref:System.Collections.Generic.List%601> — это реализация интерфейса <xref:System.Collections.Generic.IList%601>.</span><span class="sxs-lookup"><span data-stu-id="c20e4-116">For example, <xref:System.Collections.Generic.List%601> is an implementation of the <xref:System.Collections.Generic.IList%601> interface.</span></span>

 <span data-ttu-id="c20e4-117">✔️ ПРЕДОСТАВЬТЕ по крайней мере один API-интерфейс, который использует каждый определяемый интерфейс (метод, принимающий интерфейс в качестве параметра или свойства, типизированного как интерфейс).</span><span class="sxs-lookup"><span data-stu-id="c20e4-117">✔️ DO provide at least one API that consumes each interface you define (a method taking the interface as a parameter or a property typed as the interface).</span></span>

 <span data-ttu-id="c20e4-118">Это помогает проверить структуру интерфейса.</span><span class="sxs-lookup"><span data-stu-id="c20e4-118">Doing this helps to validate the interface design.</span></span> <span data-ttu-id="c20e4-119">Например, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> использует интерфейс <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c20e4-119">For example, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> consumes the <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> interface.</span></span>

 <span data-ttu-id="c20e4-120">❌ НЕ добавляйте элементы к интерфейсу, который уже отправлен.</span><span class="sxs-lookup"><span data-stu-id="c20e4-120">❌ DO NOT add members to an interface that has previously shipped.</span></span>

 <span data-ttu-id="c20e4-121">Это приведет к нарушению реализаций интерфейса.</span><span class="sxs-lookup"><span data-stu-id="c20e4-121">Doing so would break implementations of the interface.</span></span> <span data-ttu-id="c20e4-122">Чтобы избежать проблем с управлением версиями, необходимо создать новый интерфейс.</span><span class="sxs-lookup"><span data-stu-id="c20e4-122">You should create a new interface in order to avoid versioning problems.</span></span>

 <span data-ttu-id="c20e4-123">За исключением ситуаций, описанных в этих рекомендациях, в целом при проектировании многократно используемых библиотек с управляемым кодом следует выбирать классы, а не интерфейсы.</span><span class="sxs-lookup"><span data-stu-id="c20e4-123">Except for the situations described in these guidelines, you should, in general, choose classes rather than interfaces in designing managed code reusable libraries.</span></span>

 <span data-ttu-id="c20e4-124">*Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="c20e4-124">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="c20e4-125">*Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="c20e4-125">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="c20e4-126">См. также</span><span class="sxs-lookup"><span data-stu-id="c20e4-126">See also</span></span>

- [<span data-ttu-id="c20e4-127">Рекомендации по разработке типов</span><span class="sxs-lookup"><span data-stu-id="c20e4-127">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="c20e4-128">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="c20e4-128">Framework Design Guidelines</span></span>](index.md)
