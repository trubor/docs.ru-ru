---
description: 'Узнайте подробнее о: Разработка статичных классов'
title: Разработка статичных классов
ms.date: 10/22/2008
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
ms.openlocfilehash: 16db470ab0975a5545617c9c5471d6ac157e688b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782472"
---
# <a name="static-class-design"></a><span data-ttu-id="f5357-103">Разработка статичных классов</span><span class="sxs-lookup"><span data-stu-id="f5357-103">Static Class Design</span></span>

<span data-ttu-id="f5357-104">Статический класс определяется как класс, который содержит только статические элементы (разумеется, помимо элементов экземпляра, наследуемых от <xref:System.Object?displayProperty=nameWithType> и, возможно, закрытого конструктора).</span><span class="sxs-lookup"><span data-stu-id="f5357-104">A static class is defined as a class that contains only static members (of course besides the instance members inherited from <xref:System.Object?displayProperty=nameWithType> and possibly a private constructor).</span></span> <span data-ttu-id="f5357-105">Некоторые языки предоставляют встроенную поддержку для статических классов.</span><span class="sxs-lookup"><span data-stu-id="f5357-105">Some languages provide built-in support for static classes.</span></span> <span data-ttu-id="f5357-106">В C# 2.0 и более поздних версиях, когда класс объявлен как статический, он является запечатанным и абстрактным, а элементы экземпляра не могут быть переопределены или объявлены.</span><span class="sxs-lookup"><span data-stu-id="f5357-106">In C# 2.0 and later, when a class is declared to be static, it is sealed, abstract, and no instance members can be overridden or declared.</span></span>

 <span data-ttu-id="f5357-107">Статические классы представляют собой своего рода компромисс между чисто объектно-ориентированной разработкой и простотой.</span><span class="sxs-lookup"><span data-stu-id="f5357-107">Static classes are a compromise between pure object-oriented design and simplicity.</span></span> <span data-ttu-id="f5357-108">Они обычно используются, чтобы быстро перейти к другим операциям (например, <xref:System.IO.File?displayProperty=nameWithType>), держателям методов расширения или функциональным возможностям, для которых не гарантируется полная объектно-ориентированная оболочка (например, <xref:System.Environment?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="f5357-108">They are commonly used to provide shortcuts to other operations (such as <xref:System.IO.File?displayProperty=nameWithType>), holders of extension methods, or functionality for which a full object-oriented wrapper is unwarranted (such as <xref:System.Environment?displayProperty=nameWithType>).</span></span>

 <span data-ttu-id="f5357-109">✔️ ИСПОЛЬЗУЙТЕ статические классы c осторожностью.</span><span class="sxs-lookup"><span data-stu-id="f5357-109">✔️ DO use static classes sparingly.</span></span>

 <span data-ttu-id="f5357-110">Статические классы необходимо использовать только в качестве вспомогательных классов для объектно-ориентированного ядра платформы.</span><span class="sxs-lookup"><span data-stu-id="f5357-110">Static classes should be used only as supporting classes for the object-oriented core of the framework.</span></span>

 <span data-ttu-id="f5357-111">❌ Статические классы НЕ следует рассматривать как вспомогательные контейнеры.</span><span class="sxs-lookup"><span data-stu-id="f5357-111">❌ DO NOT treat static classes as a miscellaneous bucket.</span></span>

 <span data-ttu-id="f5357-112">❌ НЕ объявляйте и не переопределяйте элементы экземпляров в статических классах.</span><span class="sxs-lookup"><span data-stu-id="f5357-112">❌ DO NOT declare or override instance members in static classes.</span></span>

 <span data-ttu-id="f5357-113">✔ Если ваш язык программирования не имеет встроенной поддержки статических классов,️ объявите статические классы как запечатанные и абстрактные, а затем добавьте закрытый конструктор экземпляра.</span><span class="sxs-lookup"><span data-stu-id="f5357-113">✔️ DO declare static classes as sealed, abstract, and add a private instance constructor if your programming language does not have built-in support for static classes.</span></span>

 <span data-ttu-id="f5357-114">*Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="f5357-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="f5357-115">*Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="f5357-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="f5357-116">См. также</span><span class="sxs-lookup"><span data-stu-id="f5357-116">See also</span></span>

- [<span data-ttu-id="f5357-117">Рекомендации по разработке типов</span><span class="sxs-lookup"><span data-stu-id="f5357-117">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="f5357-118">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="f5357-118">Framework Design Guidelines</span></span>](index.md)
