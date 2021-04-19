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
# <a name="var-c-reference"></a>var (справочник по C#)

Начиная с Visual C# 3 переменные, объявленные в области действия метода, получают неявный "тип" `var`. Неявно типизированные локальные переменные является строго типизированными, как если бы вы объявили тип самостоятельно, однако его определяет компилятор. Следующие два объявления `i` функционально эквивалентны:

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

> [!IMPORTANT]
> При использовании `var` с включенными [ссылочными типами, допускающими значение NULL](../builtin-types/nullable-reference-types.md), всегда подразумевается ссылочный тип, допускающий значение NULL, даже если тип выражения не допускает значения NULL.

Ключевое слово `var` обычно используется с выражениями вызова конструктора. Использование `var` позволяет вам не повторять имя типа при объявлении переменной и создании экземпляра объекта, как показано в следующем примере:

```csharp
var xs = new List<int>();
```

Начиная с C# 9.0 вы можете использовать [выражение `new` с целевым типом](../operators/new-operator.md) в качестве альтернативы:

```csharp
List<int> xs = new();
List<int>? ys = new();
```

При сопоставлении шаблонов в [шаблоне`var` ](../operators/patterns.md#var-pattern) используется ключевое слово `var`.

## <a name="example"></a>Пример

В следующем примере показаны два выражения запросов. В первом выражении использование `var` разрешено, но не является обязательным, поскольку тип результата запроса может быть задан явно как `IEnumerable<string>`. Однако во втором выражении благодаря `var` результат может быть коллекцией анонимных типов, и имя этого типа доступно только для компилятора. Использование `var` делает создание нового класса для результата необязательным. Обратите внимание на то, что во втором примере переменная итерации `foreach``item` также типизирована неявно.

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a>См. также

- [справочник по C#](../index.md)
- [Неявно типизированные локальные переменные](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
- [Связи типов в операциях запросов LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)
