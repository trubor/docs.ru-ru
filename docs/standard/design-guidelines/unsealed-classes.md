---
description: 'Узнайте подробнее о: Незапечатанные классы'
title: Незапечатанные классы
ms.date: 10/22/2008
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
ms.openlocfilehash: 6fe30c3a2ef8df6b983d857b9502805e90ab83dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641828"
---
# <a name="unsealed-classes"></a><span data-ttu-id="de484-103">Незапечатанные классы</span><span class="sxs-lookup"><span data-stu-id="de484-103">Unsealed Classes</span></span>

<span data-ttu-id="de484-104">Запечатанные классы не могут наследоваться. Они препятствуют расширяемости.</span><span class="sxs-lookup"><span data-stu-id="de484-104">Sealed classes cannot be inherited from, and they prevent extensibility.</span></span> <span data-ttu-id="de484-105">Классы, которые могут быть унаследованы, напротив, называются незапечатанными.</span><span class="sxs-lookup"><span data-stu-id="de484-105">In contrast, classes that can be inherited from are called unsealed classes.</span></span>

 <span data-ttu-id="de484-106">✔️ РАССМОТРИТЕ возможность использования незапечатанных классов без добавленных виртуальных или защищенных элементов. Это отличный способ предоставить недорогую, но довольно ценную возможность расширяемости для платформы.</span><span class="sxs-lookup"><span data-stu-id="de484-106">✔️ CONSIDER using unsealed classes with no added virtual or protected members as a great way to provide inexpensive yet much appreciated extensibility to a framework.</span></span>

 <span data-ttu-id="de484-107">Разработчикам часто требуется наследовать незапечатанные классы, чтобы добавить удобные элементы, такие как пользовательские конструкторы, новые методы или перегрузки методов.</span><span class="sxs-lookup"><span data-stu-id="de484-107">Developers often want to inherit from unsealed classes so as to add convenience members such as custom constructors, new methods, or method overloads.</span></span> <span data-ttu-id="de484-108">Например, `System.Messaging.MessageQueue` является незапечатанным классом. Таким образом, он позволяет пользователям создавать пользовательские очереди по умолчанию для конкретного пути очереди или добавлять пользовательские методы, упрощающие API для конкретных сценариев.</span><span class="sxs-lookup"><span data-stu-id="de484-108">For example,  `System.Messaging.MessageQueue` is unsealed and thus allows users to create custom queues that default to a particular queue path or to add custom methods that simplify the API for specific scenarios.</span></span>

 <span data-ttu-id="de484-109">В большинстве языков программирования классы не запечатаны по умолчанию. Это рекомендуемое значение по умолчанию для большинства классов в платформах.</span><span class="sxs-lookup"><span data-stu-id="de484-109">Classes are unsealed by default in most programming languages, and this is also the recommended default for most classes in frameworks.</span></span> <span data-ttu-id="de484-110">Расширяемость, обеспечиваемая незапечатанными типами, высоко ценится пользователями платформы. Она довольно недорогая из-за сравнительно низких затрат на тестирование, связанных с незапечатанными типами.</span><span class="sxs-lookup"><span data-stu-id="de484-110">The extensibility afforded by unsealed types is much appreciated by framework users and quite inexpensive to provide because of relatively low test costs associated with unsealed types.</span></span>

 <span data-ttu-id="de484-111">*Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="de484-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="de484-112">*Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="de484-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="de484-113">См. также</span><span class="sxs-lookup"><span data-stu-id="de484-113">See also</span></span>

- [<span data-ttu-id="de484-114">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="de484-114">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="de484-115">Разработка с обеспечением расширяемости</span><span class="sxs-lookup"><span data-stu-id="de484-115">Designing for Extensibility</span></span>](designing-for-extensibility.md)
- [<span data-ttu-id="de484-116">Запечатывание</span><span class="sxs-lookup"><span data-stu-id="de484-116">Sealing</span></span>](sealing.md)
