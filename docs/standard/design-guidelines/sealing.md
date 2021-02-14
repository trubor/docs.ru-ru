---
description: 'Узнайте подробнее о: Запечатывание'
title: Запечатывание
ms.date: 10/22/2008
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
ms.openlocfilehash: 94673f793aa7373e1076e13cbda900fba83786f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731725"
---
# <a name="sealing"></a><span data-ttu-id="09292-103">Запечатывание</span><span class="sxs-lookup"><span data-stu-id="09292-103">Sealing</span></span>

<span data-ttu-id="09292-104">Одна из возможностей объектно-ориентированных платформ состоит в том, что разработчики могут расширять и настраивать их способами, не предусмотренными конструкторами платформы.</span><span class="sxs-lookup"><span data-stu-id="09292-104">One of the features of object-oriented frameworks is that developers can extend and customize them in ways unanticipated by the framework designers.</span></span> <span data-ttu-id="09292-105">В этом заключается как мощь, так и опасность расширяемого проектирования.</span><span class="sxs-lookup"><span data-stu-id="09292-105">This is both the power and danger of extensible design.</span></span> <span data-ttu-id="09292-106">Поэтому при разработке платформы очень важно тщательно проектировать расширяемость, когда она необходима, и ограничивать ее, когда она может быть опасна.</span><span class="sxs-lookup"><span data-stu-id="09292-106">When you design your framework, it is, therefore, very important to carefully design for extensibility when it is desired, and to limit extensibility when it is dangerous.</span></span>

 <span data-ttu-id="09292-107">Эффективным механизмом, который предотвращает расширяемость, является запечатывание.</span><span class="sxs-lookup"><span data-stu-id="09292-107">A powerful mechanism that prevents extensibility is sealing.</span></span> <span data-ttu-id="09292-108">Вы можете запечатать класс или отдельные элементы.</span><span class="sxs-lookup"><span data-stu-id="09292-108">You can seal either the class or individual members.</span></span> <span data-ttu-id="09292-109">При запечатывании класса пользователи не смогут наследовать от него.</span><span class="sxs-lookup"><span data-stu-id="09292-109">Sealing a class prevents users from inheriting from the class.</span></span> <span data-ttu-id="09292-110">При запечатывании элемента пользователи не смогут переопределять конкретный элемент.</span><span class="sxs-lookup"><span data-stu-id="09292-110">Sealing a member prevents users from overriding a particular member.</span></span>

 <span data-ttu-id="09292-111">❌ Не запечатывайте классы без веской на то причины.</span><span class="sxs-lookup"><span data-stu-id="09292-111">❌ DO NOT seal classes without having a good reason to do so.</span></span>

 <span data-ttu-id="09292-112">Запечатывание класса из-за невозможности придумать сценарий расширяемости не является веской причиной.</span><span class="sxs-lookup"><span data-stu-id="09292-112">Sealing a class because you cannot think of an extensibility scenario is not a good reason.</span></span> <span data-ttu-id="09292-113">Пользователи платформы могут наследовать от классов по различным неочевидным причинам, например для добавления удобных элементов.</span><span class="sxs-lookup"><span data-stu-id="09292-113">Framework users like to inherit from classes for various nonobvious reasons, like adding convenience members.</span></span> <span data-ttu-id="09292-114">Примеры неочевидных причин, по которым пользователи могут наследовать от типа, см. в статье [Незапечатанные классы](unsealed-classes.md).</span><span class="sxs-lookup"><span data-stu-id="09292-114">See [Unsealed Classes](unsealed-classes.md) for examples of nonobvious reasons users want to inherit from a type.</span></span>

 <span data-ttu-id="09292-115">Ниже приведены веские причины для запечатывания класса.</span><span class="sxs-lookup"><span data-stu-id="09292-115">Good reasons for sealing a class include the following:</span></span>

- <span data-ttu-id="09292-116">Класс является статическим.</span><span class="sxs-lookup"><span data-stu-id="09292-116">The class is a static class.</span></span> <span data-ttu-id="09292-117">См. статью [Разработка статических классов](static-class.md).</span><span class="sxs-lookup"><span data-stu-id="09292-117">See [Static Class Design](static-class.md).</span></span>

- <span data-ttu-id="09292-118">В наследуемых защищенных элементах класса хранятся важные для обеспечения безопасности секреты.</span><span class="sxs-lookup"><span data-stu-id="09292-118">The class stores security-sensitive secrets in inherited protected members.</span></span>

- <span data-ttu-id="09292-119">Класс наследует множество виртуальных элементов, и запечатать их по отдельности может быть выгоднее, чем оставить класс незапечатанным.</span><span class="sxs-lookup"><span data-stu-id="09292-119">The class inherits many virtual members and the cost of sealing them individually would outweigh the benefits of leaving the class unsealed.</span></span>

- <span data-ttu-id="09292-120">Класс является атрибутом, для которого требуется очень быстро выполнять поиск в среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="09292-120">The class is an attribute that requires very fast runtime look-up.</span></span> <span data-ttu-id="09292-121">Уровни производительности у запечатанных атрибутов чуть выше, чем у незапечатанных.</span><span class="sxs-lookup"><span data-stu-id="09292-121">Sealed attributes have slightly higher performance levels than unsealed ones.</span></span> <span data-ttu-id="09292-122">См. статью [Атрибуты](attributes.md).</span><span class="sxs-lookup"><span data-stu-id="09292-122">See [Attributes](attributes.md).</span></span>

 <span data-ttu-id="09292-123">❌ НЕ объявляйте защищенные или виртуальные элементы в запечатанных типах.</span><span class="sxs-lookup"><span data-stu-id="09292-123">❌ DO NOT declare protected or virtual members on sealed types.</span></span>

 <span data-ttu-id="09292-124">По определению наследовать запечатанные типы невозможно.</span><span class="sxs-lookup"><span data-stu-id="09292-124">By definition, sealed types cannot be inherited from.</span></span> <span data-ttu-id="09292-125">Это означает, что защищенные элементы для запечатанных типов невозможно вызвать, а виртуальные методы для запечатанных типов невозможно перезаписать.</span><span class="sxs-lookup"><span data-stu-id="09292-125">This means that protected members on sealed types cannot be called, and virtual methods on sealed types cannot be overridden.</span></span>

 <span data-ttu-id="09292-126">✔️ РАССМОТРИТЕ возможность запечатывания элементов, которые планируете переопределить.</span><span class="sxs-lookup"><span data-stu-id="09292-126">✔️ CONSIDER sealing members that you override.</span></span>

 <span data-ttu-id="09292-127">Проблемы, которые могут возникнуть в результате введения виртуальных элементов (рассматриваются в статье [Виртуальные элементы](virtual-members.md)), касаются и переопределений, хоть и в немного меньшей степени.</span><span class="sxs-lookup"><span data-stu-id="09292-127">Problems that can result from introducing virtual members (discussed in [Virtual Members](virtual-members.md)) apply to overrides as well, although to a slightly lesser degree.</span></span> <span data-ttu-id="09292-128">Запечатывание переопределения обеспечивает защиту от этих проблем, начиная с этой точки в иерархии наследования.</span><span class="sxs-lookup"><span data-stu-id="09292-128">Sealing an override shields you from these problems starting from that point in the inheritance hierarchy.</span></span>

 <span data-ttu-id="09292-129">*Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="09292-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="09292-130">*Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="09292-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="09292-131">См. также</span><span class="sxs-lookup"><span data-stu-id="09292-131">See also</span></span>

- [<span data-ttu-id="09292-132">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="09292-132">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="09292-133">Разработка с обеспечением расширяемости</span><span class="sxs-lookup"><span data-stu-id="09292-133">Designing for Extensibility</span></span>](designing-for-extensibility.md)
- [<span data-ttu-id="09292-134">Незапечатанные классы</span><span class="sxs-lookup"><span data-stu-id="09292-134">Unsealed Classes</span></span>](unsealed-classes.md)
