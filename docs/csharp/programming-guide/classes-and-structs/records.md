---
title: Записи. Руководство по программированию в C#
description: Сведения о типах записей и их создании
ms.date: 02/26/2021
helpviewer_keywords:
- records [C#]
- C# language, records
ms.openlocfilehash: 99370e398d5e607def58334b33ae20aa59e21962
ms.sourcegitcommit: 872ca41d1c26f39d0aef57cc365d09503bac780d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/03/2021
ms.locfileid: "106288034"
---
# <a name="records-c-programming-guide"></a><span data-ttu-id="9212d-103">Записи (Руководство по программированию в C#)</span><span class="sxs-lookup"><span data-stu-id="9212d-103">Records (C# Programming Guide)</span></span>

<span data-ttu-id="9212d-104">[Запись](../../language-reference/builtin-types/record.md) — это [класс](../../language-reference/keywords/class.md), предоставляющий специальный синтаксис и поведение для работы с моделями данных.</span><span class="sxs-lookup"><span data-stu-id="9212d-104">A [record](../../language-reference/builtin-types/record.md) is a [class](../../language-reference/keywords/class.md) that provides special syntax and behavior for working with data models.</span></span> <span data-ttu-id="9212d-105">Дополнительные сведения о классах см. в разделе [Классы (руководство по программированию на C#)](classes.md).</span><span class="sxs-lookup"><span data-stu-id="9212d-105">For information about classes, see [Classes (C# Programming Guide)](classes.md).</span></span>

## <a name="when-to-use-records"></a><span data-ttu-id="9212d-106">Когда следует использовать записи</span><span class="sxs-lookup"><span data-stu-id="9212d-106">When to use records</span></span>

<span data-ttu-id="9212d-107">Рекомендуется использовать запись вместо класса в следующих сценариях.</span><span class="sxs-lookup"><span data-stu-id="9212d-107">Consider using a record in place of a class in the following scenarios:</span></span>

* <span data-ttu-id="9212d-108">Необходимо определить ссылочный тип, для которого объекты являются неизменяемыми.</span><span class="sxs-lookup"><span data-stu-id="9212d-108">You want to define a reference type for which objects are immutable.</span></span>
* <span data-ttu-id="9212d-109">Необходимо определить модель данных, зависящую от [равенства значений](../statements-expressions-operators/equality-comparisons.md#value-equality).</span><span class="sxs-lookup"><span data-stu-id="9212d-109">You want to define a data model that depends on [value equality](../statements-expressions-operators/equality-comparisons.md#value-equality).</span></span>

### <a name="immutability"></a><span data-ttu-id="9212d-110">Неизменяемость</span><span class="sxs-lookup"><span data-stu-id="9212d-110">Immutability</span></span>

<span data-ttu-id="9212d-111">Неизменяемый тип — это тип, который не позволяет изменять значения свойств или полей объекта после его создания.</span><span class="sxs-lookup"><span data-stu-id="9212d-111">An immutable type is one that prevents you from changing any property or field values of an object after it's instantiated.</span></span> <span data-ttu-id="9212d-112">Неизменность может быть полезной, если требуется обеспечить потокобезопасность типа или если существует зависимость от хэш-кода, остающегося неизменным в хэш-таблице.</span><span class="sxs-lookup"><span data-stu-id="9212d-112">Immutability can be useful when you need a type to be thread-safe or you're depending on a hash code remaining the same in a hash table.</span></span> <span data-ttu-id="9212d-113">Записи предоставляют краткий синтаксис для создания неизменяемых типов и работы с ними.</span><span class="sxs-lookup"><span data-stu-id="9212d-113">Records provide concise syntax for creating and working with immutable types.</span></span>

<span data-ttu-id="9212d-114">Неизменяемость подходит не для всех сценариев данных.</span><span class="sxs-lookup"><span data-stu-id="9212d-114">Immutability isn't appropriate for all data scenarios.</span></span> <span data-ttu-id="9212d-115">[Entity Framework Core](/ef/core/), например, не поддерживает обновление с неизменяемыми типами сущностей.</span><span class="sxs-lookup"><span data-stu-id="9212d-115">[Entity Framework Core](/ef/core/), for example, doesn't support updating with immutable entity types.</span></span>

### <a name="value-equality"></a><span data-ttu-id="9212d-116">Равенство значений</span><span class="sxs-lookup"><span data-stu-id="9212d-116">Value equality</span></span>

<span data-ttu-id="9212d-117">Для записей равенство значений означает, что две переменные типа "запись" равны, если совпадают типы и все значения свойств и полей.</span><span class="sxs-lookup"><span data-stu-id="9212d-117">For records, value equality means that two variables of a record type are equal if the types match and all property and field values match.</span></span> <span data-ttu-id="9212d-118">Для других ссылочных типов, таких как классы, равенство означает [равенство ссылок](../statements-expressions-operators/equality-comparisons.md#reference-equality).</span><span class="sxs-lookup"><span data-stu-id="9212d-118">For other reference types such as classes, equality means [reference equality](../statements-expressions-operators/equality-comparisons.md#reference-equality).</span></span> <span data-ttu-id="9212d-119">То есть две переменные типа "класс" равны, если они ссылаются на один и тот же объект.</span><span class="sxs-lookup"><span data-stu-id="9212d-119">That is, two variables of a class type are equal if they refer to the same object.</span></span> <span data-ttu-id="9212d-120">Методы и операторы, определяющие равенство двух экземпляров записи, используют равенство значений.</span><span class="sxs-lookup"><span data-stu-id="9212d-120">Methods and operators that determine equality of two record instances use value equality.</span></span>

<span data-ttu-id="9212d-121">Не все модели данных хорошо работают с равенством значений.</span><span class="sxs-lookup"><span data-stu-id="9212d-121">Not all data models work well with value equality.</span></span> <span data-ttu-id="9212d-122">Например, [Entity Framework Core](/ef/core/) опирается на равенство ссылок, чтобы гарантировать, что в нем используется только один экземпляр типа сущности для того, что является концептуально одной сущностью.</span><span class="sxs-lookup"><span data-stu-id="9212d-122">For example, [Entity Framework Core](/ef/core/) depends on reference equality to ensure that it uses only one instance of an entity type for what is conceptually one entity.</span></span> <span data-ttu-id="9212d-123">По этой причине типы записей не подходят для использования в качестве типов сущностей в Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="9212d-123">For this reason, record types aren't appropriate for use as entity types in Entity Framework Core.</span></span>

## <a name="how-records-differ-from-classes"></a><span data-ttu-id="9212d-124">Отличия записей от классов</span><span class="sxs-lookup"><span data-stu-id="9212d-124">How records differ from classes</span></span>

<span data-ttu-id="9212d-125">Тот же синтаксис, который [объявляет](classes.md#declaring-classes) и [создает экземпляры](classes.md#creating-objects) классов, можно использовать с записями.</span><span class="sxs-lookup"><span data-stu-id="9212d-125">The same syntax that [declares](classes.md#declaring-classes) and [instantiates](classes.md#creating-objects) classes can be used with records.</span></span> <span data-ttu-id="9212d-126">Просто замените ключевое слово `record` на `class`.</span><span class="sxs-lookup"><span data-stu-id="9212d-126">Just substitute the `record` keyword for the `class` keyword.</span></span> <span data-ttu-id="9212d-127">Аналогично, записями поддерживается тот же синтаксис для выражения связей наследования.</span><span class="sxs-lookup"><span data-stu-id="9212d-127">Likewise, the same syntax for expressing inheritance relationships is supported by records.</span></span> <span data-ttu-id="9212d-128">Записи отличаются от классов следующим образом.</span><span class="sxs-lookup"><span data-stu-id="9212d-128">Records differ from classes in the following ways:</span></span>

* <span data-ttu-id="9212d-129">Для объявления и создания экземпляра типа с неизменяемыми свойствами можно использовать [позиционные параметры](../../language-reference/builtin-types/record.md#positional-syntax-for-property-definition).</span><span class="sxs-lookup"><span data-stu-id="9212d-129">You can use [positional parameters](../../language-reference/builtin-types/record.md#positional-syntax-for-property-definition) to create and instantiate a type with immutable properties.</span></span>
* <span data-ttu-id="9212d-130">Те же методы и операторы, которые указывают на равенство или неравенство ссылок в классах (например <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> и `==`), указывают на [равенство или неравенство значений](../../language-reference/builtin-types/record.md#value-equality) в записях.</span><span class="sxs-lookup"><span data-stu-id="9212d-130">The same methods and operators that indicate reference equality or inequality in classes (such as <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> and `==`), indicate [value equality or inequality](../../language-reference/builtin-types/record.md#value-equality) in records.</span></span>
* <span data-ttu-id="9212d-131">Можно использовать [выражение `with`](../../language-reference/builtin-types/record.md#nondestructive-mutation) для создания копии неизменяемого объекта с новыми значениями в выбранных свойствах.</span><span class="sxs-lookup"><span data-stu-id="9212d-131">You can use a [`with` expression](../../language-reference/builtin-types/record.md#nondestructive-mutation) to create a copy of an immutable object with new values in selected properties.</span></span>
* <span data-ttu-id="9212d-132">Метод записи `ToString` создает форматированную строку, содержащую имя типа объекта, а также имена и значения всех его открытых свойств.</span><span class="sxs-lookup"><span data-stu-id="9212d-132">A record's `ToString` method creates a formatted string that shows an object's type name and the names and values of all its public properties.</span></span>
* <span data-ttu-id="9212d-133">Запись может [наследовать от другой записи](../../language-reference/builtin-types/record.md#inheritance).</span><span class="sxs-lookup"><span data-stu-id="9212d-133">A record can [inherit from another record](../../language-reference/builtin-types/record.md#inheritance).</span></span> <span data-ttu-id="9212d-134">Запись не может наследовать от класса, а класс не может наследовать от записи.</span><span class="sxs-lookup"><span data-stu-id="9212d-134">A record can't inherit from a class, and a class can't inherit from a record.</span></span>

## <a name="examples"></a><span data-ttu-id="9212d-135">Примеры</span><span class="sxs-lookup"><span data-stu-id="9212d-135">Examples</span></span>

<span data-ttu-id="9212d-136">В следующем примере определяется открытая запись, которая использует позиционные параметры для объявления и создания экземпляра.</span><span class="sxs-lookup"><span data-stu-id="9212d-136">The following example defines a public record that uses positional parameters to declare and instantiate a record.</span></span> <span data-ttu-id="9212d-137">Затем в нем выводятся имя типа и значения свойств:</span><span class="sxs-lookup"><span data-stu-id="9212d-137">It then prints out the type name and property values:</span></span>

:::code language="csharp" source="../../language-reference/builtin-types/snippets/shared/RecordType.cs" id="InstantiatePositional":::

<span data-ttu-id="9212d-138">В следующем примере демонстрируется равенство значений в записях:</span><span class="sxs-lookup"><span data-stu-id="9212d-138">The following example demonstrates value equality in records:</span></span>

:::code language="csharp" source="../../language-reference/builtin-types/snippets/shared/RecordType.cs" id="Equality":::

<span data-ttu-id="9212d-139">В следующем примере показано использование выражения `with` для копирования неизменяемого объекта и изменения одного из свойств:</span><span class="sxs-lookup"><span data-stu-id="9212d-139">The following example demonstrates use of a `with` expression to copy an immutable object and change one of the properties:</span></span>

:::code language="csharp" source="../../language-reference/builtin-types/snippets/shared/RecordType.cs" id="WithExpressions":::

<span data-ttu-id="9212d-140">Дополнительные сведения см. в разделе [Записи (справочник по C#)](../../language-reference/builtin-types/record.md).</span><span class="sxs-lookup"><span data-stu-id="9212d-140">For more information, see [Records (C# reference)](../../language-reference/builtin-types/record.md).</span></span>
  
## <a name="c-language-specification"></a><span data-ttu-id="9212d-141">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="9212d-141">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9212d-142">См. также</span><span class="sxs-lookup"><span data-stu-id="9212d-142">See also</span></span>

- [<span data-ttu-id="9212d-143">Классы (Руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="9212d-143">Classes (C# Programming Guide)</span></span>](classes.md)
- [<span data-ttu-id="9212d-144">Записи (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="9212d-144">Records (C# reference)</span></span>](../../language-reference/builtin-types/record.md)
- [<span data-ttu-id="9212d-145">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="9212d-145">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9212d-146">Объектно-ориентированное программирование</span><span class="sxs-lookup"><span data-stu-id="9212d-146">Object-Oriented Programming</span></span>](../../tutorials/intro-to-csharp/object-oriented-programming.md)
- [<span data-ttu-id="9212d-147">Полиморфизм</span><span class="sxs-lookup"><span data-stu-id="9212d-147">Polymorphism</span></span>](polymorphism.md)
- [<span data-ttu-id="9212d-148">Имена идентификаторов</span><span class="sxs-lookup"><span data-stu-id="9212d-148">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="9212d-149">Члены</span><span class="sxs-lookup"><span data-stu-id="9212d-149">Members</span></span>](members.md)
- [<span data-ttu-id="9212d-150">Методы</span><span class="sxs-lookup"><span data-stu-id="9212d-150">Methods</span></span>](methods.md)
- [<span data-ttu-id="9212d-151">Конструкторы</span><span class="sxs-lookup"><span data-stu-id="9212d-151">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="9212d-152">Методы завершения</span><span class="sxs-lookup"><span data-stu-id="9212d-152">Finalizers</span></span>](destructors.md)
- [<span data-ttu-id="9212d-153">Объекты</span><span class="sxs-lookup"><span data-stu-id="9212d-153">Objects</span></span>](objects.md)
