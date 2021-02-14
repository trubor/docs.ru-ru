---
description: 'Узнайте подробнее о: Разработка абстрактных классов'
title: Разработка абстрактных классов
ms.date: 10/22/2008
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
ms.openlocfilehash: 5b1cd833bf43e5bf5731176243809393187e84d4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642465"
---
# <a name="abstract-class-design"></a><span data-ttu-id="c5768-103">Разработка абстрактных классов</span><span class="sxs-lookup"><span data-stu-id="c5768-103">Abstract Class Design</span></span>

<span data-ttu-id="c5768-104">❌ НЕ СЛЕДУЕТ определять открытые или защищенные внутренние конструкторы в абстрактных типах.</span><span class="sxs-lookup"><span data-stu-id="c5768-104">❌ DO NOT define public or protected internal constructors in abstract types.</span></span>

 <span data-ttu-id="c5768-105">Конструкторы должны быть открытыми только в том случае, если пользователям необходимо создавать экземпляры заданного типа.</span><span class="sxs-lookup"><span data-stu-id="c5768-105">Constructors should be public only if users will need to create instances of the type.</span></span> <span data-ttu-id="c5768-106">Так как невозможно создавать экземпляры абстрактного типа, абстрактный тип с открытым конструктором является недопустимым и вводит пользователей в заблуждение.</span><span class="sxs-lookup"><span data-stu-id="c5768-106">Because you cannot create instances of an abstract type, an abstract type with a public constructor is incorrectly designed and misleading to the users.</span></span>

 <span data-ttu-id="c5768-107">✔️ СЛЕДУЕТ определять защищенный или внутренний конструктор в абстрактных классах.</span><span class="sxs-lookup"><span data-stu-id="c5768-107">✔️ DO define a protected or an internal constructor in abstract classes.</span></span>

 <span data-ttu-id="c5768-108">Защищенные конструкторы более популярны и просто разрешают базовому классу выполнять собственную инициализацию при создании подтипов.</span><span class="sxs-lookup"><span data-stu-id="c5768-108">A protected constructor is more common and simply allows the base class to do its own initialization when subtypes are created.</span></span>

 <span data-ttu-id="c5768-109">Внутренний конструктор можно использовать для ограничения конкретных реализаций абстрактного класса сборкой, определяющей класс.</span><span class="sxs-lookup"><span data-stu-id="c5768-109">An internal constructor can be used to limit concrete implementations of the abstract class to the assembly defining the class.</span></span>

 <span data-ttu-id="c5768-110">✔️ СЛЕДУЕТ предоставить по крайней мере один конкретный тип, наследующий от каждого передаваемого абстрактного класса.</span><span class="sxs-lookup"><span data-stu-id="c5768-110">✔️ DO provide at least one concrete type that inherits from each abstract class that you ship.</span></span>

 <span data-ttu-id="c5768-111">Это помогает проверить структуру абстрактного класса.</span><span class="sxs-lookup"><span data-stu-id="c5768-111">Doing this helps to validate the design of the abstract class.</span></span> <span data-ttu-id="c5768-112">Например, <xref:System.IO.FileStream?displayProperty=nameWithType> является реализацией абстрактного класса <xref:System.IO.Stream?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c5768-112">For example,  <xref:System.IO.FileStream?displayProperty=nameWithType> is an implementation of the <xref:System.IO.Stream?displayProperty=nameWithType> abstract class.</span></span>

 <span data-ttu-id="c5768-113">*Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="c5768-113">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="c5768-114">*Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="c5768-114">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="c5768-115">См. также</span><span class="sxs-lookup"><span data-stu-id="c5768-115">See also</span></span>

- [<span data-ttu-id="c5768-116">Рекомендации по разработке типов</span><span class="sxs-lookup"><span data-stu-id="c5768-116">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="c5768-117">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="c5768-117">Framework Design Guidelines</span></span>](index.md)
