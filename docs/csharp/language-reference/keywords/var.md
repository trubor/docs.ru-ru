---
description: var. Справочник по C#
title: var. Справочник по C#
ms.date: 10/02/2020
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: b3590ebbcff0894b7864cd4a227a6ea068de42a2
ms.sourcegitcommit: 4b7f6b348c986556ef805cb6baacfd5b9ec18ed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2021
ms.locfileid: "107075515"
---
# <a name="var-c-reference"></a><span data-ttu-id="297ea-103">var (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="297ea-103">var (C# reference)</span></span>

<span data-ttu-id="297ea-104">Начиная с Visual C# 3 переменные, объявленные в области действия метода, получают неявный "тип" `var`.</span><span class="sxs-lookup"><span data-stu-id="297ea-104">Beginning with C# 3, variables that are declared at method scope can have an implicit "type" `var`.</span></span> <span data-ttu-id="297ea-105">Неявно типизированные локальные переменные является строго типизированными, как если бы вы объявили тип самостоятельно, однако его определяет компилятор.</span><span class="sxs-lookup"><span data-stu-id="297ea-105">An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type.</span></span> <span data-ttu-id="297ea-106">Следующие два объявления `i` функционально эквивалентны:</span><span class="sxs-lookup"><span data-stu-id="297ea-106">The following two declarations of `i` are functionally equivalent:</span></span>

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

> [!IMPORTANT]
> <span data-ttu-id="297ea-107">При использовании `var` с включенными [ссылочными типами, допускающими значение NULL](../builtin-types/nullable-reference-types.md), всегда подразумевается ссылочный тип, допускающий значение NULL, даже если тип выражения не допускает значения NULL.</span><span class="sxs-lookup"><span data-stu-id="297ea-107">When `var` is used with [nullable reference types](../builtin-types/nullable-reference-types.md) enabled, it always implies a nullable reference type even if the expression type isn't nullable.</span></span>

<span data-ttu-id="297ea-108">Ключевое слово `var` обычно используется с выражениями вызова конструктора.</span><span class="sxs-lookup"><span data-stu-id="297ea-108">A common use of the `var` keyword is with constructor invocation expressions.</span></span> <span data-ttu-id="297ea-109">Использование `var` позволяет вам не повторять имя типа при объявлении переменной и создании экземпляра объекта, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="297ea-109">The use of `var` allows you to not repeat a type name in a variable declaration and object instantiation, as the following example shows:</span></span>

```csharp
var xs = new List<int>();
```

<span data-ttu-id="297ea-110">Начиная с C# 9.0 вы можете использовать [выражение `new` с целевым типом](../operators/new-operator.md) в качестве альтернативы:</span><span class="sxs-lookup"><span data-stu-id="297ea-110">Beginning with C# 9.0, you can use a target-typed [`new` expression](../operators/new-operator.md) as an alternative:</span></span>

```csharp
List<int> xs = new();
List<int>? ys = new();
```

<span data-ttu-id="297ea-111">При сопоставлении шаблонов в [шаблоне`var` ](../operators/patterns.md#var-pattern) используется ключевое слово `var`.</span><span class="sxs-lookup"><span data-stu-id="297ea-111">In pattern matching, the `var` keyword is used in a [`var` pattern](../operators/patterns.md#var-pattern).</span></span>

## <a name="example"></a><span data-ttu-id="297ea-112">Пример</span><span class="sxs-lookup"><span data-stu-id="297ea-112">Example</span></span>

<span data-ttu-id="297ea-113">В следующем примере показаны два выражения запросов.</span><span class="sxs-lookup"><span data-stu-id="297ea-113">The following example shows two query expressions.</span></span> <span data-ttu-id="297ea-114">В первом выражении использование `var` разрешено, но не является обязательным, поскольку тип результата запроса может быть задан явно как `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="297ea-114">In the first expression, the use of `var` is permitted but is not required, because the type of the query result can be stated explicitly as an `IEnumerable<string>`.</span></span> <span data-ttu-id="297ea-115">Однако во втором выражении благодаря `var` результат может быть коллекцией анонимных типов, и имя этого типа доступно только для компилятора.</span><span class="sxs-lookup"><span data-stu-id="297ea-115">However, in the second expression, `var` allows the result to be a collection of anonymous types, and the name of that type is not accessible except to the compiler itself.</span></span> <span data-ttu-id="297ea-116">Использование `var` делает создание нового класса для результата необязательным.</span><span class="sxs-lookup"><span data-stu-id="297ea-116">Use of `var` eliminates the requirement to create a new class for the result.</span></span> <span data-ttu-id="297ea-117">Обратите внимание на то, что во втором примере переменная итерации `foreach``item` также типизирована неявно.</span><span class="sxs-lookup"><span data-stu-id="297ea-117">Note that in Example #2, the `foreach` iteration variable `item` must also be implicitly typed.</span></span>

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a><span data-ttu-id="297ea-118">См. также</span><span class="sxs-lookup"><span data-stu-id="297ea-118">See also</span></span>

- [<span data-ttu-id="297ea-119">справочник по C#</span><span class="sxs-lookup"><span data-stu-id="297ea-119">C# reference</span></span>](../index.md)
- [<span data-ttu-id="297ea-120">Неявно типизированные локальные переменные</span><span class="sxs-lookup"><span data-stu-id="297ea-120">Implicitly typed local variables</span></span>](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
- [<span data-ttu-id="297ea-121">Связи типов в операциях запросов LINQ</span><span class="sxs-lookup"><span data-stu-id="297ea-121">Type relationships in LINQ query operations</span></span>](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)
