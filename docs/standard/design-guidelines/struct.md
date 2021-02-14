---
description: 'Узнайте подробнее о: Разработка структур'
title: Разработка структур
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
ms.openlocfilehash: a28dd3e452d22e61d95ec521fdbde6539e38ed78
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641906"
---
# <a name="struct-design"></a><span data-ttu-id="7ac24-103">Разработка структур</span><span class="sxs-lookup"><span data-stu-id="7ac24-103">Struct Design</span></span>

<span data-ttu-id="7ac24-104">Тип значения общего назначения чаще всего называется структурой. Он является ключевым словом C#.</span><span class="sxs-lookup"><span data-stu-id="7ac24-104">The general-purpose value type is most often referred to as a struct, its C# keyword.</span></span> <span data-ttu-id="7ac24-105">В этом разделе приводятся рекомендации по разработке общих структур.</span><span class="sxs-lookup"><span data-stu-id="7ac24-105">This section provides guidelines for general struct design.</span></span>

 <span data-ttu-id="7ac24-106">❌НЕ предоставляйте для структуры конструктор без параметров.</span><span class="sxs-lookup"><span data-stu-id="7ac24-106">❌ DO NOT provide a parameterless constructor for a struct.</span></span>

 <span data-ttu-id="7ac24-107">Следуя этой рекомендации, можно создавать массивы структур, не запуская конструктор для каждого элемента массива.</span><span class="sxs-lookup"><span data-stu-id="7ac24-107">Following this guideline allows arrays of structs to be created without having to run the constructor on each item of the array.</span></span> <span data-ttu-id="7ac24-108">Обратите внимание, что C# не разрешает структурам использовать конструкторы без параметров.</span><span class="sxs-lookup"><span data-stu-id="7ac24-108">Notice that C# does not allow structs to have parameterless constructors.</span></span>

 <span data-ttu-id="7ac24-109">❌ НЕ ОПРЕДЕЛЯЙТЕ изменяемые типы значений.</span><span class="sxs-lookup"><span data-stu-id="7ac24-109">❌ DO NOT define mutable value types.</span></span>

 <span data-ttu-id="7ac24-110">Изменяемые типы значений имеют несколько проблем.</span><span class="sxs-lookup"><span data-stu-id="7ac24-110">Mutable value types have several problems.</span></span> <span data-ttu-id="7ac24-111">Например, когда метод получения свойства возвращает тип значения, вызывающий объект получает копию.</span><span class="sxs-lookup"><span data-stu-id="7ac24-111">For example, when a property getter returns a value type, the caller receives a copy.</span></span> <span data-ttu-id="7ac24-112">Так как копия создается неявным образом, разработчики могут не знать, что они изменяют копию, а не исходное значение.</span><span class="sxs-lookup"><span data-stu-id="7ac24-112">Because the copy is created implicitly, developers might not be aware that they are mutating the copy, and not the original value.</span></span> <span data-ttu-id="7ac24-113">Кроме того, для некоторых языков (в частности динамических языков) есть проблемы с использованием изменяемых типов значений, так как даже локальные переменные при разыменовании приводят к созданию копии.</span><span class="sxs-lookup"><span data-stu-id="7ac24-113">Also, some languages (dynamic languages, in particular) have problems using mutable value types because even local variables, when dereferenced, cause a copy to be made.</span></span>

 <span data-ttu-id="7ac24-114">✔️ Убедитесь, что состояние, в котором все данные экземпляра имеют значение 0, false или NULL (по необходимости), допустимо.</span><span class="sxs-lookup"><span data-stu-id="7ac24-114">✔️ DO ensure that a state where all instance data is set to zero, false, or null (as appropriate) is valid.</span></span>

 <span data-ttu-id="7ac24-115">Это предотвратит случайное создание недопустимых экземпляров во время создания массива структур.</span><span class="sxs-lookup"><span data-stu-id="7ac24-115">This prevents accidental creation of invalid instances when an array of the structs is created.</span></span>

 <span data-ttu-id="7ac24-116">✔️ РЕАЛИЗУЙТЕ <xref:System.IEquatable%601> для типов значений.</span><span class="sxs-lookup"><span data-stu-id="7ac24-116">✔️ DO implement <xref:System.IEquatable%601> on value types.</span></span>

 <span data-ttu-id="7ac24-117">Метод <xref:System.Object.Equals%2A?displayProperty=nameWithType> для типов значений приводит к тому, что упаковка-преобразование и реализация по умолчанию не очень эффективны, так как используется отражение.</span><span class="sxs-lookup"><span data-stu-id="7ac24-117">The <xref:System.Object.Equals%2A?displayProperty=nameWithType> method on value types causes boxing, and its default implementation is not very efficient, because it uses reflection.</span></span> <span data-ttu-id="7ac24-118">Метод <xref:System.IEquatable%601.Equals%2A> может иметь гораздо более высокую производительность. Его можно реализовать таким образом, чтобы избежать упаковки-преобразования.</span><span class="sxs-lookup"><span data-stu-id="7ac24-118"><xref:System.IEquatable%601.Equals%2A> can have much better performance and can be implemented so that it will not cause boxing.</span></span>

 <span data-ttu-id="7ac24-119">❌ НЕ расширяйте явным образом <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="7ac24-119">❌ DO NOT explicitly extend <xref:System.ValueType>.</span></span> <span data-ttu-id="7ac24-120">На самом деле это не рекомендуется для большинства языков.</span><span class="sxs-lookup"><span data-stu-id="7ac24-120">In fact, most languages prevent this.</span></span>

 <span data-ttu-id="7ac24-121">Как правило, структуры могут быть очень полезными, но их следует использовать только для небольших, отдельных, неизменяемых значений, которые не будут часто упаковываться.</span><span class="sxs-lookup"><span data-stu-id="7ac24-121">In general, structs can be very useful but should only be used for small, single, immutable values that will not be boxed frequently.</span></span>

 <span data-ttu-id="7ac24-122">*Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="7ac24-122">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="7ac24-123">*Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="7ac24-123">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="7ac24-124">См. также</span><span class="sxs-lookup"><span data-stu-id="7ac24-124">See also</span></span>

- [<span data-ttu-id="7ac24-125">Рекомендации по разработке типов</span><span class="sxs-lookup"><span data-stu-id="7ac24-125">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="7ac24-126">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="7ac24-126">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="7ac24-127">Выбор между классом и структурой</span><span class="sxs-lookup"><span data-stu-id="7ac24-127">Choosing Between Class and Struct</span></span>](choosing-between-class-and-struct.md)
