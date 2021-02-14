---
description: 'Узнайте подробнее о: Виртуальные члены'
title: Виртуальные члены
ms.date: 10/22/2008
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
ms.openlocfilehash: 7618686764fb3a24ef53e5168b871366b7ffb5bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641789"
---
# <a name="virtual-members"></a><span data-ttu-id="21a45-103">Виртуальные члены</span><span class="sxs-lookup"><span data-stu-id="21a45-103">Virtual Members</span></span>

<span data-ttu-id="21a45-104">Виртуальные элементы можно переопределить, тем самым изменив поведение подкласса.</span><span class="sxs-lookup"><span data-stu-id="21a45-104">Virtual members can be overridden, thus changing the behavior of the subclass.</span></span> <span data-ttu-id="21a45-105">Они очень похожи на обратные вызовы с точки зрения расширяемости, которую они обеспечивают, но они лучше в плане производительности выполнения и потребления памяти.</span><span class="sxs-lookup"><span data-stu-id="21a45-105">They are quite similar to callbacks in terms of the extensibility they provide, but they are better in terms of execution performance and memory consumption.</span></span> <span data-ttu-id="21a45-106">Кроме того, виртуальные элементы являются более естественным вариантом в сценариях, требующих создания специального вида имеющегося типа (специализации).</span><span class="sxs-lookup"><span data-stu-id="21a45-106">Also, virtual members feel more natural in scenarios that require creating a special kind of an existing type (specialization).</span></span>

 <span data-ttu-id="21a45-107">Виртуальные элементы работают лучше, чем обратные вызовы и события, но хуже, чем невиртуальные методы.</span><span class="sxs-lookup"><span data-stu-id="21a45-107">Virtual members perform better than callbacks and events, but do not perform better than non-virtual methods.</span></span>

 <span data-ttu-id="21a45-108">Основным недостатком виртуальных элементов является то, что их поведение можно изменить только во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="21a45-108">The main disadvantage of virtual members is that the behavior of a virtual member can only be modified at the time of compilation.</span></span> <span data-ttu-id="21a45-109">Поведение обратного вызова можно изменить в среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="21a45-109">The behavior of a callback can be modified at runtime.</span></span>

 <span data-ttu-id="21a45-110">Виртуальные элементы, такие как обратные вызовы (и, возможно, не только обратные вызовы), являются дорогостоящими в плане проектирования, тестирования и обслуживания, так как любой вызов виртуального элемента может быть переопределен непредсказуемым образом и может выполнять произвольный код.</span><span class="sxs-lookup"><span data-stu-id="21a45-110">Virtual members, like callbacks (and maybe more than callbacks), are costly to design, test, and maintain because any call to a virtual member can be overridden in unpredictable ways and can execute arbitrary code.</span></span> <span data-ttu-id="21a45-111">Кроме того, чтобы четко определить контракт виртуальных элементов, обычно требуется приложить гораздо больше усилий, поэтому затраты на их проектирование и документирование более высокие.</span><span class="sxs-lookup"><span data-stu-id="21a45-111">Also, much more effort is usually required to clearly define the contract of virtual members, so the cost of designing and documenting them is higher.</span></span>

 <span data-ttu-id="21a45-112">❌ НЕ следует делать элементы виртуальными без веских на то причин, и вы должны быть осведомлены о затратах, связанных с проектированием, тестированием и обслуживанием виртуальных элементов.</span><span class="sxs-lookup"><span data-stu-id="21a45-112">❌ DO NOT make members virtual unless you have a good reason to do so and you are aware of all the costs related to designing, testing, and maintaining virtual members.</span></span>

 <span data-ttu-id="21a45-113">Виртуальные элементы менее устойчивы с точки зрения изменений, которые можно внести в них, не нарушив совместимость.</span><span class="sxs-lookup"><span data-stu-id="21a45-113">Virtual members are less forgiving in terms of changes that can be made to them without breaking compatibility.</span></span> <span data-ttu-id="21a45-114">Кроме того, они выполняются медленнее, чем невиртуальные элементы, в основном из-за того, что вызовы к виртуальным элементам не встроены.</span><span class="sxs-lookup"><span data-stu-id="21a45-114">Also, they are slower than non-virtual members, mostly because calls to virtual members are not inlined.</span></span>

 <span data-ttu-id="21a45-115">✔️ Рассмотрите возможность ограничения расширяемости только тем, что является абсолютно необходимым.</span><span class="sxs-lookup"><span data-stu-id="21a45-115">✔️ CONSIDER limiting extensibility to only what is absolutely necessary.</span></span>

 <span data-ttu-id="21a45-116">✔️ ОТДАВАЙТЕ предпочтение защищенному доступу к виртуальным элементам.</span><span class="sxs-lookup"><span data-stu-id="21a45-116">✔️ DO prefer protected accessibility over public accessibility for virtual members.</span></span> <span data-ttu-id="21a45-117">Открытые элементы должны обеспечивать расширяемость (при необходимости) путем вызова в защищенный виртуальный элемент.</span><span class="sxs-lookup"><span data-stu-id="21a45-117">Public members should provide extensibility (if required) by calling into a protected virtual member.</span></span>

 <span data-ttu-id="21a45-118">Открытые элементы класса должны предоставлять правильный набор функций для непосредственных потребителей этого класса.</span><span class="sxs-lookup"><span data-stu-id="21a45-118">The public members of a class should provide the right set of functionality for direct consumers of that class.</span></span> <span data-ttu-id="21a45-119">Виртуальные элементы предназначены для переопределения в подклассах, а защищенный доступ — это отличный способ определить область, в которой можно использовать все виртуальные точки расширяемости.</span><span class="sxs-lookup"><span data-stu-id="21a45-119">Virtual members are designed to be overridden in subclasses, and protected accessibility is a great way to scope all virtual extensibility points to where they can be used.</span></span>

 <span data-ttu-id="21a45-120">*Фрагменты: &copy; Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="21a45-120">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="21a45-121">*Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="21a45-121">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="21a45-122">См. также</span><span class="sxs-lookup"><span data-stu-id="21a45-122">See also</span></span>

- [<span data-ttu-id="21a45-123">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="21a45-123">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="21a45-124">Разработка с обеспечением расширяемости</span><span class="sxs-lookup"><span data-stu-id="21a45-124">Designing for Extensibility</span></span>](designing-for-extensibility.md)
