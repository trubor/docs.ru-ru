---
description: 'Узнайте подробнее о: Разработка с обеспечением расширяемости'
title: Разработка с обеспечением расширяемости
ms.date: 10/22/2008
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
ms.openlocfilehash: 148ae25380698a5a1161fb9fbdd3cc60102e865d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642270"
---
# <a name="designing-for-extensibility"></a><span data-ttu-id="d391f-103">Разработка с обеспечением расширяемости</span><span class="sxs-lookup"><span data-stu-id="d391f-103">Designing for Extensibility</span></span>

<span data-ttu-id="d391f-104">Один важный аспект разработки платформы заключается в уделении пристального внимания расширяемости платформы.</span><span class="sxs-lookup"><span data-stu-id="d391f-104">One important aspect of designing a framework is making sure the extensibility of the framework has been carefully considered.</span></span> <span data-ttu-id="d391f-105">Для этого вы должны знать о затратах и преимуществах, которые связаны с разными механизмами расширяемости.</span><span class="sxs-lookup"><span data-stu-id="d391f-105">This requires that you understand the costs and benefits associated with various extensibility mechanisms.</span></span> <span data-ttu-id="d391f-106">Приведенные в этой главе сведения помогут вам подобрать оптимальный механизм расширяемости — создание подклассов, события, виртуальные члены, обратные вызовы и т. д. — для удовлетворения требований вашей платформы.</span><span class="sxs-lookup"><span data-stu-id="d391f-106">This chapter helps you decide which of the extensibility mechanisms—subclassing, events, virtual members, callbacks, and so on—can best meet the requirements of your framework.</span></span>  
  
 <span data-ttu-id="d391f-107">Существует множество способов реализовать расширяемость на платформах.</span><span class="sxs-lookup"><span data-stu-id="d391f-107">There are many ways to allow extensibility in frameworks.</span></span> <span data-ttu-id="d391f-108">Они могут быть как менее эффективными, но и более экономичными, так и очень эффективными и затратными.</span><span class="sxs-lookup"><span data-stu-id="d391f-108">They range from less powerful but less costly to very powerful but expensive.</span></span> <span data-ttu-id="d391f-109">Для удовлетворения требований к расширяемости при возможности выбирайте такой механизм, который связан с минимальными затратами.</span><span class="sxs-lookup"><span data-stu-id="d391f-109">For any given extensibility requirement, you should choose the least costly extensibility mechanism that meets the requirements.</span></span> <span data-ttu-id="d391f-110">Помните, что обычно вы можете без проблем повысить уровень расширяемости, но его понижение требует кардинальных изменений.</span><span class="sxs-lookup"><span data-stu-id="d391f-110">Keep in mind that it’s usually possible to add more extensibility later, but you can never take it away without introducing breaking changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d391f-111">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="d391f-111">In This Section</span></span>  

 [<span data-ttu-id="d391f-112">Незапечатанные классы</span><span class="sxs-lookup"><span data-stu-id="d391f-112">Unsealed Classes</span></span>](unsealed-classes.md)  
 [<span data-ttu-id="d391f-113">Защищенные члены</span><span class="sxs-lookup"><span data-stu-id="d391f-113">Protected Members</span></span>](protected-members.md)  
 [<span data-ttu-id="d391f-114">События и обратные вызовы</span><span class="sxs-lookup"><span data-stu-id="d391f-114">Events and Callbacks</span></span>](events-and-callbacks.md)  
 [<span data-ttu-id="d391f-115">Виртуальные члены</span><span class="sxs-lookup"><span data-stu-id="d391f-115">Virtual Members</span></span>](virtual-members.md)  
 [<span data-ttu-id="d391f-116">Абстракции (абстрактные типы и интерфейсы)</span><span class="sxs-lookup"><span data-stu-id="d391f-116">Abstractions (Abstract Types and Interfaces)</span></span>](abstractions-abstract-types-and-interfaces.md)  
 [<span data-ttu-id="d391f-117">Базовые классы для реализации абстракций</span><span class="sxs-lookup"><span data-stu-id="d391f-117">Base Classes for Implementing Abstractions</span></span>](base-classes-for-implementing-abstractions.md)  
 [<span data-ttu-id="d391f-118">Запечатывание</span><span class="sxs-lookup"><span data-stu-id="d391f-118">Sealing</span></span>](sealing.md)  
 <span data-ttu-id="d391f-119">*Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="d391f-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="d391f-120">*Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="d391f-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d391f-121">См. также</span><span class="sxs-lookup"><span data-stu-id="d391f-121">See also</span></span>

- [<span data-ttu-id="d391f-122">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="d391f-122">Framework Design Guidelines</span></span>](index.md)
