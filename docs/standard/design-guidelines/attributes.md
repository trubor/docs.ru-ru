---
description: 'Узнайте подробнее о: Атрибуты'
title: Атрибуты
ms.date: 10/22/2008
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
ms.openlocfilehash: 1557ba0945da0c8498c67f70ba4a01dd0bbe432e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642426"
---
# <a name="attributes"></a><span data-ttu-id="d4107-103">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="d4107-103">Attributes</span></span>

<span data-ttu-id="d4107-104"><xref:System.Attribute?displayProperty=nameWithType> — это базовый класс, используемый для определения пользовательских атрибутов.</span><span class="sxs-lookup"><span data-stu-id="d4107-104"><xref:System.Attribute?displayProperty=nameWithType> is a base class used to define custom attributes.</span></span>

 <span data-ttu-id="d4107-105">Атрибуты — это заметки, которые можно добавить к элементам программирования, таким как сборки, типы, элементы и параметры.</span><span class="sxs-lookup"><span data-stu-id="d4107-105">Attributes are annotations that can be added to programming elements such as assemblies, types, members, and parameters.</span></span> <span data-ttu-id="d4107-106">Они хранятся в метаданных сборки, а доступ к ним можно получить в среде выполнения с помощью API-интерфейсов отражения.</span><span class="sxs-lookup"><span data-stu-id="d4107-106">They are stored in the metadata of the assembly and can be accessed at runtime using the reflection APIs.</span></span> <span data-ttu-id="d4107-107">Например, платформа определяет атрибут <xref:System.ObsoleteAttribute>, который можно применить к типу или элементу, чтобы указать, что он является устаревшим.</span><span class="sxs-lookup"><span data-stu-id="d4107-107">For example, the Framework defines the <xref:System.ObsoleteAttribute>, which can be applied to a type or a member to indicate that the type or member has been deprecated.</span></span>

 <span data-ttu-id="d4107-108">Атрибуты могут иметь одно или несколько свойств, которые содержат дополнительные данные, связанные с атрибутом.</span><span class="sxs-lookup"><span data-stu-id="d4107-108">Attributes can have one or more properties that carry additional data related to the attribute.</span></span> <span data-ttu-id="d4107-109">Например, атрибут `ObsoleteAttribute` может содержать дополнительные сведения о выпуске, в котором устарел тип или элемент, а также описание новых интерфейсов API, заменяющих устаревший API-интерфейс.</span><span class="sxs-lookup"><span data-stu-id="d4107-109">For example, `ObsoleteAttribute` could carry additional information about the release in which a type or a member got deprecated and the description of the new APIs replacing the obsolete API.</span></span>

 <span data-ttu-id="d4107-110">При применении атрибута необходимо указать некоторые его свойства.</span><span class="sxs-lookup"><span data-stu-id="d4107-110">Some properties of an attribute must be specified when the attribute is applied.</span></span> <span data-ttu-id="d4107-111">Они называются обязательными свойствами или аргументами, так как представлены как позиционные параметры конструктора.</span><span class="sxs-lookup"><span data-stu-id="d4107-111">These are referred to as the required properties or required arguments, because they are represented as positional constructor parameters.</span></span> <span data-ttu-id="d4107-112">Например, свойство <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> атрибута <xref:System.Diagnostics.ConditionalAttribute> является обязательным.</span><span class="sxs-lookup"><span data-stu-id="d4107-112">For example, the <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> property of the <xref:System.Diagnostics.ConditionalAttribute> is a required property.</span></span>

 <span data-ttu-id="d4107-113">Свойства, которые не нужно обязательно указывать при применении атрибута, называются необязательными свойствами (или необязательными аргументами).</span><span class="sxs-lookup"><span data-stu-id="d4107-113">Properties that do not necessarily have to be specified when the attribute is applied are called optional properties (or optional arguments).</span></span> <span data-ttu-id="d4107-114">Они представлены настраиваемыми свойствами.</span><span class="sxs-lookup"><span data-stu-id="d4107-114">They are represented by settable properties.</span></span> <span data-ttu-id="d4107-115">Компиляторы предоставляют специальный синтаксис для задания этих свойств при применении атрибута.</span><span class="sxs-lookup"><span data-stu-id="d4107-115">Compilers provide special syntax to set these properties when an attribute is applied.</span></span> <span data-ttu-id="d4107-116">Например, свойство <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> представляет необязательный аргумент.</span><span class="sxs-lookup"><span data-stu-id="d4107-116">For example, the <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property represents an optional argument.</span></span>

 <span data-ttu-id="d4107-117">✔️ ПРИСВАИВАЙТЕ классам настраиваемых атрибутов имена с суффиксом "Attribute".</span><span class="sxs-lookup"><span data-stu-id="d4107-117">✔️ DO name custom attribute classes with the suffix "Attribute."</span></span>

 <span data-ttu-id="d4107-118">✔️ ПРИМЕНЯЙТЕ атрибут <xref:System.AttributeUsageAttribute> к настраиваемым атрибутам.</span><span class="sxs-lookup"><span data-stu-id="d4107-118">✔️ DO apply the <xref:System.AttributeUsageAttribute> to custom attributes.</span></span>

 <span data-ttu-id="d4107-119">✔️ ПРЕДОСТАВЛЯЙТЕ настраиваемые свойства для необязательных аргументов.</span><span class="sxs-lookup"><span data-stu-id="d4107-119">✔️ DO provide settable properties for optional arguments.</span></span>

 <span data-ttu-id="d4107-120">✔ ПРЕДОСТАВЛЯЙТЕ свойства, отвечающие только за получение, для обязательных аргументов.</span><span class="sxs-lookup"><span data-stu-id="d4107-120">✔️ DO provide get-only properties for required arguments.</span></span>

 <span data-ttu-id="d4107-121">✔️ ПРЕДОСТАВЛЯЙТЕ параметры конструктора для инициализации свойств, соответствующих обязательным аргументам.</span><span class="sxs-lookup"><span data-stu-id="d4107-121">✔️ DO provide constructor parameters to initialize properties corresponding to required arguments.</span></span> <span data-ttu-id="d4107-122">Имя каждого параметра должно совпадать (но в другом регистре) с именем соответствующего свойства.</span><span class="sxs-lookup"><span data-stu-id="d4107-122">Each parameter should have the same name (although with different casing) as the corresponding property.</span></span>

 <span data-ttu-id="d4107-123">❌ ИЗБЕГАЙТЕ️ предоставления параметров конструктора для инициализации свойств, соответствующих обязательным аргументам.</span><span class="sxs-lookup"><span data-stu-id="d4107-123">❌ AVOID providing constructor parameters to initialize properties corresponding to the optional arguments.</span></span>

 <span data-ttu-id="d4107-124">Иными словами, не используйте свойства, которые можно задать с помощью конструктора и метода задания.</span><span class="sxs-lookup"><span data-stu-id="d4107-124">In other words, do not have properties that can be set with both a constructor and a setter.</span></span> <span data-ttu-id="d4107-125">В этой рекомендации явно указано, какие аргументы являются необязательными, а какие обязательными, и она не предусматривает выполнение одного и того же действия двумя способами.</span><span class="sxs-lookup"><span data-stu-id="d4107-125">This guideline makes very explicit which arguments are optional and which are required, and avoids having two ways of doing the same thing.</span></span>

 <span data-ttu-id="d4107-126">❌ ИЗБЕГАЙТЕ перегрузки конструкторов настраиваемых атрибутов.</span><span class="sxs-lookup"><span data-stu-id="d4107-126">❌ AVOID overloading custom attribute constructors.</span></span>

 <span data-ttu-id="d4107-127">При наличии только одного конструктора пользователь получает более четкие инструкции относительно того, какие аргументы являются обязательными, а какие — необязательными.</span><span class="sxs-lookup"><span data-stu-id="d4107-127">Having only one constructor clearly communicates to the user which arguments are required and which are optional.</span></span>

 <span data-ttu-id="d4107-128">✔️ ЗАПЕЧАТЫВАЙТЕ классы настраиваемых атрибутов, если это возможно.</span><span class="sxs-lookup"><span data-stu-id="d4107-128">✔️ DO seal custom attribute classes, if possible.</span></span> <span data-ttu-id="d4107-129">Это позволяет ускорить поиск атрибута.</span><span class="sxs-lookup"><span data-stu-id="d4107-129">This makes the look-up for the attribute faster.</span></span>

 <span data-ttu-id="d4107-130">*Фрагменты: &copy; Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="d4107-130">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="d4107-131">*Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="d4107-131">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="d4107-132">См. также</span><span class="sxs-lookup"><span data-stu-id="d4107-132">See also</span></span>

- [<span data-ttu-id="d4107-133">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="d4107-133">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="d4107-134">Правила использования</span><span class="sxs-lookup"><span data-stu-id="d4107-134">Usage Guidelines</span></span>](usage-guidelines.md)
