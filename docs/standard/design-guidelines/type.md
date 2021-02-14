---
description: 'Узнайте подробнее о: Правила разработки типов'
title: Правила разработки типов
ms.date: 10/22/2008
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
ms.openlocfilehash: d2c193d41dda118558cc5e7541f7e2dfbaf1a369
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641841"
---
# <a name="type-design-guidelines"></a><span data-ttu-id="d3bd2-103">Правила разработки типов</span><span class="sxs-lookup"><span data-stu-id="d3bd2-103">Type Design Guidelines</span></span>

<span data-ttu-id="d3bd2-104">С точки зрения среды CLR существует только две категории типов — ссылочные типы и типы значений, — но в рамках обсуждения структуры платформы мы разделяем типы на несколько логических групп, каждая из которых имеет собственные определенные правила проектирования.</span><span class="sxs-lookup"><span data-stu-id="d3bd2-104">From the CLR perspective, there are only two categories of types—reference types and value types—but for the purpose of a discussion about framework design, we divide types into more logical groups, each with its own specific design rules.</span></span>

 <span data-ttu-id="d3bd2-105">Классы представляют собой общий случай ссылочных типов.</span><span class="sxs-lookup"><span data-stu-id="d3bd2-105">Classes are the general case of reference types.</span></span> <span data-ttu-id="d3bd2-106">Они составляют большую часть типов в большинстве платформ.</span><span class="sxs-lookup"><span data-stu-id="d3bd2-106">They make up the bulk of types in the majority of frameworks.</span></span> <span data-ttu-id="d3bd2-107">Своей популярностью классы обязаны обширному набору объектно-ориентированных функций, которые они поддерживают, и их общей применимости.</span><span class="sxs-lookup"><span data-stu-id="d3bd2-107">Classes owe their popularity to the rich set of object-oriented features they support and to their general applicability.</span></span> <span data-ttu-id="d3bd2-108">Базовые классы и абстрактные классы — это специальные логические группы, связанные с расширяемостью.</span><span class="sxs-lookup"><span data-stu-id="d3bd2-108">Base classes and abstract classes are special logical groups related to extensibility.</span></span>

 <span data-ttu-id="d3bd2-109">Интерфейсы — это типы, которые можно реализовать как ссылочные типы, так и типы значений.</span><span class="sxs-lookup"><span data-stu-id="d3bd2-109">Interfaces are types that can be implemented by both reference types and value types.</span></span> <span data-ttu-id="d3bd2-110">Таким образом, они выполняют функцию корней для полиморфных иерархий ссылочных типов и типов значений.</span><span class="sxs-lookup"><span data-stu-id="d3bd2-110">They can thus serve as roots of polymorphic hierarchies of reference types and value types.</span></span> <span data-ttu-id="d3bd2-111">Кроме того, интерфейсы можно использовать для моделирования множественного наследования, которое не имеет собственной поддержки в среде CLR.</span><span class="sxs-lookup"><span data-stu-id="d3bd2-111">In addition, interfaces can be used to simulate multiple inheritance, which is not natively supported by the CLR.</span></span>

 <span data-ttu-id="d3bd2-112">Структуры представляют собой общий случай типов значений и должны быть зарезервированы для небольших простых типов, аналогичных примитивам языка.</span><span class="sxs-lookup"><span data-stu-id="d3bd2-112">Structs are the general case of value types and should be reserved for small, simple types, similar to language primitives.</span></span>

 <span data-ttu-id="d3bd2-113">Перечисления — это особый случай типов значений, используемых для определения коротких наборов значений, таких как дни недели, цвета консоли и т. д.</span><span class="sxs-lookup"><span data-stu-id="d3bd2-113">Enums are a special case of value types used to define short sets of values, such as days of the week, console colors, and so on.</span></span>

 <span data-ttu-id="d3bd2-114">Статические классы — это типы, предназначенные выполнять роль контейнеров для статических элементов.</span><span class="sxs-lookup"><span data-stu-id="d3bd2-114">Static classes are types intended to be containers for static members.</span></span> <span data-ttu-id="d3bd2-115">Как правило, они используются для предоставления сочетаний клавиш для других операций.</span><span class="sxs-lookup"><span data-stu-id="d3bd2-115">They are commonly used to provide shortcuts to other operations.</span></span>

 <span data-ttu-id="d3bd2-116">Делегаты, исключения, атрибуты, массивы и коллекции являются особыми случаями ссылочных типов, предназначенными для определенных целей, а рекомендации по их проектированию и использованию обсуждаются в других разделах этой книги.</span><span class="sxs-lookup"><span data-stu-id="d3bd2-116">Delegates, exceptions, attributes, arrays, and collections are all special cases of reference types intended for specific uses, and guidelines for their design and usage are discussed elsewhere in this book.</span></span>

 <span data-ttu-id="d3bd2-117">✔️ УБЕДИТЕСЬ, что каждый тип является четко определенным набором связанных элементов, а не просто случайным набором несвязанных функций.</span><span class="sxs-lookup"><span data-stu-id="d3bd2-117">✔️ DO ensure that each type is a well-defined set of related members, not just a random collection of unrelated functionality.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d3bd2-118">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="d3bd2-118">In This Section</span></span>

 <span data-ttu-id="d3bd2-119">[Выбор между классом и структурой](choosing-between-class-and-struct.md) [Разработка абстрактных классов](abstract-class.md) [Разработка статических классов](static-class.md) [Разработка интерфейса](interface.md) [Разработка структур](struct.md) [Разработка перечислений](enum.md) [Вложенные типы](nested-types.md) *Фрагменты © Корпорация Майкрософт (Microsoft Corporation) 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="d3bd2-119">[Choosing Between Class and Struct](choosing-between-class-and-struct.md) [Abstract Class Design](abstract-class.md) [Static Class Design](static-class.md) [Interface Design](interface.md) [Struct Design](struct.md) [Enum Design](enum.md) [Nested Types](nested-types.md) *Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="d3bd2-120">*Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="d3bd2-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="d3bd2-121">См. также</span><span class="sxs-lookup"><span data-stu-id="d3bd2-121">See also</span></span>

- [<span data-ttu-id="d3bd2-122">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="d3bd2-122">Framework Design Guidelines</span></span>](index.md)
