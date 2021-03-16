---
title: Записи. Руководство по программированию в C#
description: Сведения о типах записей и их создании
ms.date: 02/26/2021
helpviewer_keywords:
- records [C#]
- C# language, records
ms.openlocfilehash: a45ed08da18e58f11793d6874d7275d9f5216be4
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102260042"
---
# <a name="records-c-programming-guide"></a><span data-ttu-id="3511c-103">Записи (Руководство по программированию в C#)</span><span class="sxs-lookup"><span data-stu-id="3511c-103">Records (C# Programming Guide)</span></span>

<span data-ttu-id="3511c-104">[Запись](../../language-reference/builtin-types/record.md) — это [класс](../../language-reference/keywords/class.md), предоставляющий специальный синтаксис и поведение для работы с моделями данных.</span><span class="sxs-lookup"><span data-stu-id="3511c-104">A [record](../../language-reference/builtin-types/record.md) is a [class](../../language-reference/keywords/class.md) that provides special syntax and behavior for working with data models.</span></span> <span data-ttu-id="3511c-105">Дополнительные сведения о классах см. в разделе [Классы (руководство по программированию на C#)](classes.md).</span><span class="sxs-lookup"><span data-stu-id="3511c-105">For information about classes, see [Classes (C# Programming Guide)](classes.md).</span></span>

## <a name="when-to-use-records"></a><span data-ttu-id="3511c-106">Когда следует использовать записи</span><span class="sxs-lookup"><span data-stu-id="3511c-106">When to use records</span></span>

<span data-ttu-id="3511c-107">Рекомендуется использовать запись вместо класса в следующих сценариях.</span><span class="sxs-lookup"><span data-stu-id="3511c-107">Consider using a record in place of a class in the following scenarios:</span></span>

* <span data-ttu-id="3511c-108">Необходимо определить ссылочный тип, для которого объекты являются неизменяемыми.</span><span class="sxs-lookup"><span data-stu-id="3511c-108">You want to define a reference type for which objects are immutable.</span></span>
* <span data-ttu-id="3511c-109">Необходимо определить модель данных, зависящую от [равенства значений](../statements-expressions-operators/equality-comparisons.md#value-equality).</span><span class="sxs-lookup"><span data-stu-id="3511c-109">You want to define a data model that depends on [value equality](../statements-expressions-operators/equality-comparisons.md#value-equality).</span></span>

### <a name="immutability"></a><span data-ttu-id="3511c-110">Неизменяемость</span><span class="sxs-lookup"><span data-stu-id="3511c-110">Immutability</span></span>

<span data-ttu-id="3511c-111">Неизменяемый тип — это тип, который не позволяет изменять значения свойств или полей объекта после его создания.</span><span class="sxs-lookup"><span data-stu-id="3511c-111">An immutable type is one that prevents you from changing any property or field values of an object after it's instantiated.</span></span> <span data-ttu-id="3511c-112">Неизменность может быть полезной, если требуется обеспечить потокобезопасность типа или если существует зависимость от хэш-кода, остающегося неизменным в хэш-таблице.</span><span class="sxs-lookup"><span data-stu-id="3511c-112">Immutability can be useful when you need a type to be thread-safe or you're depending on a hash code remaining the same in a hash table.</span></span> <span data-ttu-id="3511c-113">Записи предоставляют краткий синтаксис для создания неизменяемых типов и работы с ними.</span><span class="sxs-lookup"><span data-stu-id="3511c-113">Records provide concise syntax for creating and working with immutable types.</span></span>

<span data-ttu-id="3511c-114">Неизменяемость подходит не для всех сценариев данных.</span><span class="sxs-lookup"><span data-stu-id="3511c-114">Immutability isn't appropriate for all data scenarios.</span></span> <span data-ttu-id="3511c-115">[Entity Framework Core](/ef/core/), например, не поддерживает обновление с неизменяемыми типами сущностей.</span><span class="sxs-lookup"><span data-stu-id="3511c-115">[Entity Framework Core](/ef/core/), for example, doesn't support updating with immutable entity types.</span></span>

### <a name="value-equality"></a><span data-ttu-id="3511c-116">Равенство значений</span><span class="sxs-lookup"><span data-stu-id="3511c-116">Value equality</span></span>

<span data-ttu-id="3511c-117">Для записей равенство значений означает, что две переменные типа "запись" равны, если совпадают типы и все значения свойств и полей.</span><span class="sxs-lookup"><span data-stu-id="3511c-117">For records, value equality means that two variables of a record type are equal if the types match and all property and field values match.</span></span> <span data-ttu-id="3511c-118">Для других ссылочных типов, таких как классы, равенство означает [равенство ссылок](../statements-expressions-operators/equality-comparisons.md#reference-equality).</span><span class="sxs-lookup"><span data-stu-id="3511c-118">For other reference types such as classes, equality means [reference equality](../statements-expressions-operators/equality-comparisons.md#reference-equality).</span></span> <span data-ttu-id="3511c-119">То есть две переменные типа "класс" равны, если они ссылаются на один и тот же объект.</span><span class="sxs-lookup"><span data-stu-id="3511c-119">That is, two variables of a class type are equal if they refer to the same object.</span></span> <span data-ttu-id="3511c-120">Методы и операторы, определяющие равенство двух экземпляров записи, используют равенство значений.</span><span class="sxs-lookup"><span data-stu-id="3511c-120">Methods and operators that determine equality of two record instances use value equality.</span></span>

<span data-ttu-id="3511c-121">Не все модели данных хорошо работают с равенством значений.</span><span class="sxs-lookup"><span data-stu-id="3511c-121">Not all data models work well with value equality.</span></span> <span data-ttu-id="3511c-122">Например, [Entity Framework Core](/ef/core/) опирается на равенство ссылок, чтобы гарантировать, что в нем используется только один экземпляр типа сущности для того, что является концептуально одной сущностью.</span><span class="sxs-lookup"><span data-stu-id="3511c-122">For example, [Entity Framework Core](/ef/core/) depends on reference equality to ensure that it uses only one instance of an entity type for what is conceptually one entity.</span></span> <span data-ttu-id="3511c-123">По этой причине типы записей не подходят для использования в качестве типов сущностей в Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="3511c-123">For this reason, record types aren't appropriate for use as entity types in Entity Framework Core.</span></span>

## <a name="how-records-differ-from-classes"></a><span data-ttu-id="3511c-124">Отличия записей от классов</span><span class="sxs-lookup"><span data-stu-id="3511c-124">How records differ from classes</span></span>

<span data-ttu-id="3511c-125">Тот же синтаксис, который [объявляет](classes.md#declaring-classes) и [создает экземпляры](classes.md#creating-objects) классов, можно использовать с записями.</span><span class="sxs-lookup"><span data-stu-id="3511c-125">The same syntax that [declares](classes.md#declaring-classes) and [instantiates](classes.md#creating-objects) classes can be used with records.</span></span> <span data-ttu-id="3511c-126">Просто замените ключевое слово `record` на `class`.</span><span class="sxs-lookup"><span data-stu-id="3511c-126">Just substitute the `record` keyword for the `class` keyword.</span></span> <span data-ttu-id="3511c-127">Аналогично, записями поддерживается тот же синтаксис для выражения связей наследования.</span><span class="sxs-lookup"><span data-stu-id="3511c-127">Likewise, the same syntax for expressing inheritance relationships is supported by records.</span></span> <span data-ttu-id="3511c-128">Записи отличаются от классов следующим образом.</span><span class="sxs-lookup"><span data-stu-id="3511c-128">Records differ from classes in the following ways:</span></span>

* <span data-ttu-id="3511c-129">Для объявления и создания экземпляра типа с неизменяемыми свойствами можно использовать [позиционные параметры](../../language-reference/builtin-types/record.md#positional-syntax-for-property-definition).</span><span class="sxs-lookup"><span data-stu-id="3511c-129">You can use [positional parameters](../../language-reference/builtin-types/record.md#positional-syntax-for-property-definition) to create and instantiate a type with immutable properties.</span></span>
* <span data-ttu-id="3511c-130">Те же методы и операторы, которые указывают на равенство или неравенство ссылок в классах (например <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> и `==`), указывают на [равенство или неравенство значений](../../language-reference/builtin-types/record.md#value-equality) в записях.</span><span class="sxs-lookup"><span data-stu-id="3511c-130">The same methods and operators that indicate reference equality or inequality in classes (such as <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> and `==`), indicate [value equality or inequality](../../language-reference/builtin-types/record.md#value-equality) in records.</span></span>
* <span data-ttu-id="3511c-131">Можно использовать [выражение `with`](../../language-reference/builtin-types/record.md#nondestructive-mutation) для создания копии неизменяемого объекта с новыми значениями в выбранных свойствах.</span><span class="sxs-lookup"><span data-stu-id="3511c-131">You can use a [`with` expression](../../language-reference/builtin-types/record.md#nondestructive-mutation) to create a copy of an immutable object with new values in selected properties.</span></span>
* <span data-ttu-id="3511c-132">Метод записи `ToString` создает форматированную строку, содержащую имя типа объекта, а также имена и значения всех его открытых свойств.</span><span class="sxs-lookup"><span data-stu-id="3511c-132">A record's `ToString` method creates a formatted string that shows an object's type name and the names and values of all its public properties.</span></span>
* <span data-ttu-id="3511c-133">Запись может [наследовать от другой записи](../../language-reference/builtin-types/record.md#inheritance).</span><span class="sxs-lookup"><span data-stu-id="3511c-133">A record can [inherit from another record](../../language-reference/builtin-types/record.md#inheritance).</span></span> <span data-ttu-id="3511c-134">Запись не может наследовать от класса, а класс не может наследовать от записи.</span><span class="sxs-lookup"><span data-stu-id="3511c-134">A record can't inherit from a class, and a class can't inherit from a record.</span></span>

## <a name="examples"></a><span data-ttu-id="3511c-135">Примеры</span><span class="sxs-lookup"><span data-stu-id="3511c-135">Examples</span></span>

<span data-ttu-id="3511c-136">В следующем примере определяется открытая запись, которая использует позиционные параметры для объявления и создания экземпляра.</span><span class="sxs-lookup"><span data-stu-id="3511c-136">The following example defines a public record that uses positional parameters to declare and instantiate a record.</span></span> <span data-ttu-id="3511c-137">Затем в нем выводятся имя типа и значения свойств:</span><span class="sxs-lookup"><span data-stu-id="3511c-137">It then prints out the type name and property values:</span></span>

:::code language="csharp" source="../../language-reference/builtin-types/snippets/shared/RecordType.cs" id="InstantiatePositional":::

<span data-ttu-id="3511c-138">В следующем примере демонстрируется равенство значений в записях:</span><span class="sxs-lookup"><span data-stu-id="3511c-138">The following example demonstrates value equality in records:</span></span>

:::code language="csharp" source="../../language-reference/builtin-types/snippets/shared/RecordType.cs" id="Equality":::

<span data-ttu-id="3511c-139">В следующем примере показано использование выражения `with` для копирования неизменяемого объекта и изменения одного из свойств:</span><span class="sxs-lookup"><span data-stu-id="3511c-139">The following example demonstrates use of a `with` expression to copy an immutable object and change one of the properties:</span></span>

:::code language="csharp" source="../../language-reference/builtin-types/snippets/shared/RecordType.cs" id="WithExpressions":::

<span data-ttu-id="3511c-140">Дополнительные сведения см. в разделе [Записи (справочник по C#)](../../language-reference/builtin-types/record.md).</span><span class="sxs-lookup"><span data-stu-id="3511c-140">For more information, see [Records (C# reference)](../../language-reference/builtin-types/record.md).</span></span>
  
## <a name="c-language-specification"></a><span data-ttu-id="3511c-141">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="3511c-141">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3511c-142">См. также</span><span class="sxs-lookup"><span data-stu-id="3511c-142">See also</span></span>

- [<span data-ttu-id="3511c-143">Классы (Руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="3511c-143">Classes (C# Programming Guide)</span></span>](classes.md)
- <span data-ttu-id="3511c-144">[Записи (справочник по C#)](../../language-reference/builtin-types/record.md).</span><span class="sxs-lookup"><span data-stu-id="3511c-144">[Records (C# reference)](../../language-reference/builtin-types/record.md).</span></span>
- [<span data-ttu-id="3511c-145">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="3511c-145">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3511c-146">Объектно-ориентированное программирование</span><span class="sxs-lookup"><span data-stu-id="3511c-146">Object-Oriented Programming</span></span>](../../tutorials/intro-to-csharp/object-oriented-programming.md)
- [<span data-ttu-id="3511c-147">Полиморфизм</span><span class="sxs-lookup"><span data-stu-id="3511c-147">Polymorphism</span></span>](polymorphism.md)
- [<span data-ttu-id="3511c-148">Имена идентификаторов</span><span class="sxs-lookup"><span data-stu-id="3511c-148">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="3511c-149">Члены</span><span class="sxs-lookup"><span data-stu-id="3511c-149">Members</span></span>](members.md)
- [<span data-ttu-id="3511c-150">Методы</span><span class="sxs-lookup"><span data-stu-id="3511c-150">Methods</span></span>](methods.md)
- [<span data-ttu-id="3511c-151">Конструкторы</span><span class="sxs-lookup"><span data-stu-id="3511c-151">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="3511c-152">Методы завершения</span><span class="sxs-lookup"><span data-stu-id="3511c-152">Finalizers</span></span>](destructors.md)
- [<span data-ttu-id="3511c-153">Объекты</span><span class="sxs-lookup"><span data-stu-id="3511c-153">Objects</span></span>](objects.md)
