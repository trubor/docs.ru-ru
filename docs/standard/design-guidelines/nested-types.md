---
description: 'Узнайте подробнее о: Вложенные типы'
title: Вложенные типы
ms.date: 10/22/2008
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
ms.openlocfilehash: 07d81827d67e50351f442ec15ca6cb18a63160fe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713381"
---
# <a name="nested-types"></a><span data-ttu-id="e7c31-103">Вложенные типы</span><span class="sxs-lookup"><span data-stu-id="e7c31-103">Nested Types</span></span>

<span data-ttu-id="e7c31-104">Вложенный тип — это тип, определенный в области другого типа, который называется включающим типом.</span><span class="sxs-lookup"><span data-stu-id="e7c31-104">A nested type is a type defined within the scope of another type, which is called the enclosing type.</span></span> <span data-ttu-id="e7c31-105">Вложенный тип имеет доступ ко всем элементам своего включающего типа.</span><span class="sxs-lookup"><span data-stu-id="e7c31-105">A nested type has access to all members of its enclosing type.</span></span> <span data-ttu-id="e7c31-106">Например, у него есть доступ к закрытым полям, определенным во включающем типе, и к защищенным полям, определенным во всех предках включающего типа.</span><span class="sxs-lookup"><span data-stu-id="e7c31-106">For example, it has access to private fields defined in the enclosing type and to protected fields defined in all ascendants of the enclosing type.</span></span>

 <span data-ttu-id="e7c31-107">Как правило, вложенные типы следует использовать экономно.</span><span class="sxs-lookup"><span data-stu-id="e7c31-107">In general, nested types should be used sparingly.</span></span> <span data-ttu-id="e7c31-108">Для этого есть несколько причин.</span><span class="sxs-lookup"><span data-stu-id="e7c31-108">There are several reasons for this.</span></span> <span data-ttu-id="e7c31-109">Некоторые разработчики не в полной мере знакомы с концепцией.</span><span class="sxs-lookup"><span data-stu-id="e7c31-109">Some developers are not fully familiar with the concept.</span></span> <span data-ttu-id="e7c31-110">У этих разработчиков могут, к примеру, возникнуть проблемы с синтаксисом объявления переменных вложенных типов.</span><span class="sxs-lookup"><span data-stu-id="e7c31-110">These developers might, for example, have problems with the syntax of declaring variables of nested types.</span></span> <span data-ttu-id="e7c31-111">Вложенные типы также тесно связаны со своими включающими типами, поэтому они не подходят для универсальных типов.</span><span class="sxs-lookup"><span data-stu-id="e7c31-111">Nested types are also very tightly coupled with their enclosing types, and as such are not suited to be general-purpose types.</span></span>

 <span data-ttu-id="e7c31-112">Вложенные типы лучше всего подходят для моделирования сведений о реализации своих включающих типов.</span><span class="sxs-lookup"><span data-stu-id="e7c31-112">Nested types are best suited for modeling implementation details of their enclosing types.</span></span> <span data-ttu-id="e7c31-113">Пользователю следует объявлять переменные вложенного типа лишь в редких случаях и почти никогда не прибегать к явному созданию экземпляров вложенных типов.</span><span class="sxs-lookup"><span data-stu-id="e7c31-113">The end user should rarely have to declare variables of a nested type and almost never should have to explicitly instantiate nested types.</span></span> <span data-ttu-id="e7c31-114">Например, перечислитель коллекции может быть вложенным типом этой коллекции.</span><span class="sxs-lookup"><span data-stu-id="e7c31-114">For example, the enumerator of a collection can be a nested type of that collection.</span></span> <span data-ttu-id="e7c31-115">Экземпляры перечислителей, как правило, создаются с помощью включающего типа, а так как многие языки поддерживают оператор foreach, пользователю следует лишь изредка прибегать к объявлению переменных перечислителя.</span><span class="sxs-lookup"><span data-stu-id="e7c31-115">Enumerators are usually instantiated by their enclosing type, and because many languages support the foreach statement, enumerator variables rarely have to be declared by the end user.</span></span>

 <span data-ttu-id="e7c31-116">✔ ИСПОЛЬЗУЙТЕ вложенные типы, если связь между вложенным типом и его внешним типом является предпочтительной для семантики доступности элементов.</span><span class="sxs-lookup"><span data-stu-id="e7c31-116">✔️ DO use nested types when the relationship between the nested type and its outer type is such that member-accessibility semantics are desirable.</span></span>

 <span data-ttu-id="e7c31-117">❌ НЕ используйте открытые вложенные типы в качестве логической конструкции группирования. Вместо этого используйте пространства имен.</span><span class="sxs-lookup"><span data-stu-id="e7c31-117">❌ DO NOT use public nested types as a logical grouping construct; use namespaces for this.</span></span>

 <span data-ttu-id="e7c31-118">❌ ИЗБЕГАЙТЕ общедоступных вложенных типов.</span><span class="sxs-lookup"><span data-stu-id="e7c31-118">❌ AVOID publicly exposed nested types.</span></span> <span data-ttu-id="e7c31-119">Единственным исключением является ситуация, когда необходимо объявить переменные вложенного типа, что случается очень редко, например при создании подклассов или в других расширенных сценариях настройки.</span><span class="sxs-lookup"><span data-stu-id="e7c31-119">The only exception to this is if variables of the nested type need to be declared only in rare scenarios such as subclassing or other advanced customization scenarios.</span></span>

 <span data-ttu-id="e7c31-120">❌ НЕ используйте вложенные типы, если на тип, вероятно, будет создана ссылка за пределами содержащего его типа.</span><span class="sxs-lookup"><span data-stu-id="e7c31-120">❌ DO NOT use nested types if the type is likely to be referenced outside of the containing type.</span></span>

 <span data-ttu-id="e7c31-121">Например, перечисление, переданное методу, определенному в классе, не должно быть определено как вложенный тип в классе.</span><span class="sxs-lookup"><span data-stu-id="e7c31-121">For example, an enum passed to a method defined on a class should not be defined as a nested type in the class.</span></span>

 <span data-ttu-id="e7c31-122">❌ НЕ используйте вложенные типы, если необходимо создать их экземпляр с помощью клиентского кода.</span><span class="sxs-lookup"><span data-stu-id="e7c31-122">❌ DO NOT use nested types if they need to be instantiated by client code.</span></span>  <span data-ttu-id="e7c31-123">Если для типа есть открытый конструктор, вероятно, он не должен быть вложенным.</span><span class="sxs-lookup"><span data-stu-id="e7c31-123">If a type has a public constructor, it should probably not be nested.</span></span>

 <span data-ttu-id="e7c31-124">Если можно создать экземпляр типа, скорее всего, это означает, что у типа есть свое место на платформе (его можно создать, работать с ним и уничтожить его без использования внешнего типа), следовательно, он не должен быть вложенным.</span><span class="sxs-lookup"><span data-stu-id="e7c31-124">If a type can be instantiated, that seems to indicate the type has a place in the framework on its own (you can create it, work with it, and destroy it without ever using the outer type), and thus should not be nested.</span></span> <span data-ttu-id="e7c31-125">Внутренние типы не должны широко использоваться повторно за пределами внешнего типа без какой-либо связи с внешним типом.</span><span class="sxs-lookup"><span data-stu-id="e7c31-125">Inner types should not be widely reused outside of the outer type without any relationship whatsoever to the outer type.</span></span>

 <span data-ttu-id="e7c31-126">❌ НЕ определяйте вложенный тип как элемент интерфейса.</span><span class="sxs-lookup"><span data-stu-id="e7c31-126">❌ DO NOT define a nested type as a member of an interface.</span></span> <span data-ttu-id="e7c31-127">Множество языков не поддерживают такую конструкцию.</span><span class="sxs-lookup"><span data-stu-id="e7c31-127">Many languages do not support such a construct.</span></span>

 <span data-ttu-id="e7c31-128">*Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="e7c31-128">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="e7c31-129">*Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="e7c31-129">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="e7c31-130">См. также</span><span class="sxs-lookup"><span data-stu-id="e7c31-130">See also</span></span>

- [<span data-ttu-id="e7c31-131">Рекомендации по разработке типов</span><span class="sxs-lookup"><span data-stu-id="e7c31-131">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="e7c31-132">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="e7c31-132">Framework Design Guidelines</span></span>](index.md)
