---
title: Руководство по программированию на C#. Константы
description: Константы в C# — это литеральные значения, которые известны во время компиляции и не изменяются после компиляции программы. Константами могут быть только встроенные типы C#.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
ms.openlocfilehash: 4783aff8e9424c90e46cb52692a3e645e995d914
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899078"
---
# <a name="constants-c-programming-guide"></a><span data-ttu-id="7d5f7-104">Константы (Руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="7d5f7-104">Constants (C# Programming Guide)</span></span>

<span data-ttu-id="7d5f7-105">Константы — это постоянные значения, которые известны во время компиляции и не изменяются во время выполнения программы.</span><span class="sxs-lookup"><span data-stu-id="7d5f7-105">Constants are immutable values which are known at compile time and do not change for the life of the program.</span></span> <span data-ttu-id="7d5f7-106">Константы должны объявляться с модификатором [const](../../language-reference/keywords/const.md).</span><span class="sxs-lookup"><span data-stu-id="7d5f7-106">Constants are declared with the [const](../../language-reference/keywords/const.md) modifier.</span></span> <span data-ttu-id="7d5f7-107">Только [встроенные типы](../../language-reference/builtin-types/built-in-types.md) C# (за исключением <xref:System.Object?displayProperty=nameWithType>) могут быть объявлены как `const`.</span><span class="sxs-lookup"><span data-stu-id="7d5f7-107">Only the C# [built-in types](../../language-reference/builtin-types/built-in-types.md) (excluding <xref:System.Object?displayProperty=nameWithType>) may be declared as `const`.</span></span> <span data-ttu-id="7d5f7-108">Пользовательские типы, включая классы, структуры и массивы, не могут объявляться как `const`.</span><span class="sxs-lookup"><span data-stu-id="7d5f7-108">User-defined types, including classes, structs, and arrays, cannot be `const`.</span></span> <span data-ttu-id="7d5f7-109">Модификатор [readonly](../../language-reference/keywords/readonly.md) позволяет создать класс, структуру или массив, которые инициализируются один раз (например, в конструкторе), и впоследствии изменить их нельзя.</span><span class="sxs-lookup"><span data-stu-id="7d5f7-109">Use the [readonly](../../language-reference/keywords/readonly.md) modifier to create a class, struct, or array that is initialized one time at runtime (for example in a constructor) and thereafter cannot be changed.</span></span>  
  
 <span data-ttu-id="7d5f7-110">C# не поддерживает методы, свойства или события `const`.</span><span class="sxs-lookup"><span data-stu-id="7d5f7-110">C# does not support `const` methods, properties, or events.</span></span>  
  
 <span data-ttu-id="7d5f7-111">Тип перечисления позволяет определять именованные константы для целочисленных встроенных типов (например `int`, `uint`, `long` и т. д.).</span><span class="sxs-lookup"><span data-stu-id="7d5f7-111">The enum type enables you to define named constants for integral built-in types (for example `int`, `uint`, `long`, and so on).</span></span> <span data-ttu-id="7d5f7-112">Дополнительные сведения см. в разделе [Перечисление](../../language-reference/builtin-types/enum.md).</span><span class="sxs-lookup"><span data-stu-id="7d5f7-112">For more information, see [enum](../../language-reference/builtin-types/enum.md).</span></span>  
  
 <span data-ttu-id="7d5f7-113">Константы должны инициализироваться сразу после объявления.</span><span class="sxs-lookup"><span data-stu-id="7d5f7-113">Constants must be initialized as they are declared.</span></span> <span data-ttu-id="7d5f7-114">Пример:</span><span class="sxs-lookup"><span data-stu-id="7d5f7-114">For example:</span></span>  
  
 [!code-csharp[Calendar#1](snippets/constants/Calendar.cs#1)]
  
 <span data-ttu-id="7d5f7-115">В этом примере константа `Months` всегда имеет значение 12, и его не может изменить даже сам класс.</span><span class="sxs-lookup"><span data-stu-id="7d5f7-115">In this example, the constant `Months` is always 12, and it cannot be changed even by the class itself.</span></span> <span data-ttu-id="7d5f7-116">На самом деле в случае, если компилятор встречает идентификатор константы в исходном коде C# (например, `Months`), он подставляет значение литерала непосредственно в создаваемый им промежуточный язык (IL).</span><span class="sxs-lookup"><span data-stu-id="7d5f7-116">In fact, when the compiler encounters a constant identifier in C# source code (for example, `Months`), it substitutes the literal value directly into the intermediate language (IL) code that it produces.</span></span> <span data-ttu-id="7d5f7-117">Поскольку с константой в среде выполнения не связан адрес ни одной переменной, поля `const` не могут передаваться по ссылке и отображаться в выражении как левостороннее значение.</span><span class="sxs-lookup"><span data-stu-id="7d5f7-117">Because there is no variable address associated with a constant at run time, `const` fields cannot be passed by reference and cannot appear as an l-value in an expression.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7d5f7-118">Будьте внимательны, ссылаясь на постоянные значения, определенные в другом коде, например, в DLL.</span><span class="sxs-lookup"><span data-stu-id="7d5f7-118">Use caution when you refer to constant values defined in other code such as DLLs.</span></span> <span data-ttu-id="7d5f7-119">Если в новой версии DLL для константы определяется новое значение, старое значение литерала хранится в вашей программе вплоть до повторной компиляции для новой версии.</span><span class="sxs-lookup"><span data-stu-id="7d5f7-119">If a new version of the DLL defines a new value for the constant, your program will still hold the old literal value until it is recompiled against the new version.</span></span>  
  
 <span data-ttu-id="7d5f7-120">Несколько констант одного типа можно объявить одновременно, например:</span><span class="sxs-lookup"><span data-stu-id="7d5f7-120">Multiple constants of the same type can be declared at the same time, for example:</span></span>  
  
 [!code-csharp[Calendar#2](snippets/constants/Calendar.cs#2)]
  
 <span data-ttu-id="7d5f7-121">Выражение, которое используется для инициализации константы, может ссылаться на другую константу, если не создает циклическую ссылку.</span><span class="sxs-lookup"><span data-stu-id="7d5f7-121">The expression that is used to initialize a constant can refer to another constant if it does not create a circular reference.</span></span> <span data-ttu-id="7d5f7-122">Пример:</span><span class="sxs-lookup"><span data-stu-id="7d5f7-122">For example:</span></span>  
  
 [!code-csharp[Calendar#3](snippets/constants/Calendar.cs#3)]
  
 <span data-ttu-id="7d5f7-123">Константы могут иметь пометку [public](../../language-reference/keywords/public.md), [private](../../language-reference/keywords/private.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md) или [private protected](../../language-reference/keywords/private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="7d5f7-123">Constants can be marked as [public](../../language-reference/keywords/public.md), [private](../../language-reference/keywords/private.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="7d5f7-124">Эти модификаторы доступа определяют, каким образом пользователи класса смогут получать доступ к константе.</span><span class="sxs-lookup"><span data-stu-id="7d5f7-124">These access modifiers define how users of the class can access the constant.</span></span> <span data-ttu-id="7d5f7-125">Дополнительные сведения см. в разделе [Модификаторы доступа](./access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="7d5f7-125">For more information, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
 <span data-ttu-id="7d5f7-126">Доступ к константам осуществляется так, как если бы они были [статическими](../../language-reference/keywords/static.md) полями, поскольку значение константы одинаково для всех экземпляров типа.</span><span class="sxs-lookup"><span data-stu-id="7d5f7-126">Constants are accessed as if they were [static](../../language-reference/keywords/static.md) fields because the value of the constant is the same for all instances of the type.</span></span> <span data-ttu-id="7d5f7-127">Для их объявления используйте ключевое слово `static`.</span><span class="sxs-lookup"><span data-stu-id="7d5f7-127">You do not use the `static` keyword to declare them.</span></span> <span data-ttu-id="7d5f7-128">Выражения, которые не относятся к классу, определяющему константу, должны включать имя класса, период и имя константы для доступа к этой константе.</span><span class="sxs-lookup"><span data-stu-id="7d5f7-128">Expressions that are not in the class that defines the constant must use the class name, a period, and the name of the constant to access the constant.</span></span> <span data-ttu-id="7d5f7-129">Пример:</span><span class="sxs-lookup"><span data-stu-id="7d5f7-129">For example:</span></span>  
  
 [!code-csharp[Calendar#4](snippets/constants/Calendar.cs#4)]
  
## <a name="c-language-specification"></a><span data-ttu-id="7d5f7-130">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="7d5f7-130">C# Language Specification</span></span>  

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7d5f7-131">См. также</span><span class="sxs-lookup"><span data-stu-id="7d5f7-131">See also</span></span>

- [<span data-ttu-id="7d5f7-132">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="7d5f7-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7d5f7-133">Классы и структуры</span><span class="sxs-lookup"><span data-stu-id="7d5f7-133">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="7d5f7-134">Свойства</span><span class="sxs-lookup"><span data-stu-id="7d5f7-134">Properties</span></span>](./properties.md)
- [<span data-ttu-id="7d5f7-135">Типы</span><span class="sxs-lookup"><span data-stu-id="7d5f7-135">Types</span></span>](../types/index.md)
- [<span data-ttu-id="7d5f7-136">readonly</span><span class="sxs-lookup"><span data-stu-id="7d5f7-136">readonly</span></span>](../../language-reference/keywords/readonly.md)
- <span data-ttu-id="7d5f7-137">[Immutability in C# Part One: Kinds of Immutability](/archive/blogs/ericlippert/immutability-in-c-part-one-kinds-of-immutability) (Неизменность в C#, часть 1. Виды неизменности)</span><span class="sxs-lookup"><span data-stu-id="7d5f7-137">[Immutability in C# Part One: Kinds of Immutability](/archive/blogs/ericlippert/immutability-in-c-part-one-kinds-of-immutability)</span></span>
