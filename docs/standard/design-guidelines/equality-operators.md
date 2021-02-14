---
description: 'Узнайте подробнее о: Операторы равенства'
title: Операторы равенства
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
ms.openlocfilehash: 8678ed1b4bc320f685cf7ae172f064b3dededd04
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642244"
---
# <a name="equality-operators"></a><span data-ttu-id="14989-103">Операторы равенства</span><span class="sxs-lookup"><span data-stu-id="14989-103">Equality Operators</span></span>

<span data-ttu-id="14989-104">В этом разделе рассматривается перегрузка операторов равенства. `operator==` и `operator!=` в этом разделе относятся к операторам равенства.</span><span class="sxs-lookup"><span data-stu-id="14989-104">This section discusses overloading equality operators and refers to `operator==` and `operator!=` as equality operators.</span></span>

 <span data-ttu-id="14989-105">❌ НЕ перегружайте только один оператор равенства.</span><span class="sxs-lookup"><span data-stu-id="14989-105">❌ DO NOT overload one of the equality operators and not the other.</span></span>

 <span data-ttu-id="14989-106">✔️ УБЕДИТЕСЬ, что <xref:System.Object.Equals%2A?displayProperty=nameWithType> и операторы равенства имеют одинаковую семантику и аналогичные характеристики производительности.</span><span class="sxs-lookup"><span data-stu-id="14989-106">✔️ DO ensure that <xref:System.Object.Equals%2A?displayProperty=nameWithType> and the equality operators have exactly the same semantics and similar performance characteristics.</span></span>

 <span data-ttu-id="14989-107">Часто это означает, что при перегрузке операторов равенства необходимо переопределить `Object.Equals`.</span><span class="sxs-lookup"><span data-stu-id="14989-107">This often means that `Object.Equals` needs to be overridden when the equality operators are overloaded.</span></span>

 <span data-ttu-id="14989-108">❌ НЕ создавайте исключения из операторов равенства.</span><span class="sxs-lookup"><span data-stu-id="14989-108">❌ AVOID throwing exceptions from equality operators.</span></span>

 <span data-ttu-id="14989-109">Например, чтобы не создавать исключение `NullReferenceException`, верните значение false, если один из аргументов имеет значение NULL.</span><span class="sxs-lookup"><span data-stu-id="14989-109">For example, return false if one of the arguments is null instead of throwing `NullReferenceException`.</span></span>

## <a name="equality-operators-on-value-types"></a><span data-ttu-id="14989-110">Операторы равенства для типов значений</span><span class="sxs-lookup"><span data-stu-id="14989-110">Equality Operators on Value Types</span></span>

 <span data-ttu-id="14989-111">✔️ ПЕРЕГРУЗИТЕ операторы равенства для типов значений, если равенство имеет смысл.</span><span class="sxs-lookup"><span data-stu-id="14989-111">✔️ DO overload the equality operators on value types, if equality is meaningful.</span></span>

 <span data-ttu-id="14989-112">В большинстве языков программирования стандартная реализация `operator==` для типов значений отсутствует.</span><span class="sxs-lookup"><span data-stu-id="14989-112">In most programming languages, there is no default implementation of `operator==` for value types.</span></span>

## <a name="equality-operators-on-reference-types"></a><span data-ttu-id="14989-113">Операторы равенства для ссылочных типов</span><span class="sxs-lookup"><span data-stu-id="14989-113">Equality Operators on Reference Types</span></span>

 <span data-ttu-id="14989-114">❌ ИЗБЕГАЙТЕ перегрузки операторов равенства для изменяемых ссылочных типов.</span><span class="sxs-lookup"><span data-stu-id="14989-114">❌ AVOID overloading equality operators on mutable reference types.</span></span>

 <span data-ttu-id="14989-115">У многих языков есть встроенные операторы для ссылочных типов.</span><span class="sxs-lookup"><span data-stu-id="14989-115">Many languages have built-in equality operators for reference types.</span></span> <span data-ttu-id="14989-116">Встроенные операторы обычно реализуют равенство ссылок. Многие разработчики удивляются, если поведение по умолчанию изменяется и применяются равные значения.</span><span class="sxs-lookup"><span data-stu-id="14989-116">The built-in operators usually implement the reference equality, and many developers are surprised when the default behavior is changed to the value equality.</span></span>

 <span data-ttu-id="14989-117">Эта проблема устранена для неизменяемых ссылочных типов, так как из-за неизменности значительно труднее обнаружить различия между равенством ссылок и равенством значений.</span><span class="sxs-lookup"><span data-stu-id="14989-117">This problem is mitigated for immutable reference types because immutability makes it much harder to notice the difference between reference equality and value equality.</span></span>

 <span data-ttu-id="14989-118">❌ ИЗБЕГАЙТЕ перегрузки операторов равенства для ссылочных типов, если реализация будет значительно медленнее, чем при равенстве ссылок.</span><span class="sxs-lookup"><span data-stu-id="14989-118">❌ AVOID overloading equality operators on reference types if the implementation would be significantly slower than that of reference equality.</span></span>

 <span data-ttu-id="14989-119">*Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="14989-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="14989-120">*Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="14989-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="14989-121">См. также</span><span class="sxs-lookup"><span data-stu-id="14989-121">See also</span></span>

- [<span data-ttu-id="14989-122">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="14989-122">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="14989-123">Правила использования</span><span class="sxs-lookup"><span data-stu-id="14989-123">Usage Guidelines</span></span>](usage-guidelines.md)
