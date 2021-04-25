---
description: Оператор ?:. Справочник по C#
title: Оператор ?:. Справочник по C#
ms.date: 09/17/2020
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 84a740f3afeca94a706b4120b8cd8f191f49a048
ms.sourcegitcommit: bbc724b72fb6c978905ac715e4033efa291f84dc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2021
ms.locfileid: "107369573"
---
# <a name="-operator-c-reference"></a>Оператор ?: (справочник по C#)

Условный оператор `?:`, также называемый тернарным, вычисляет логическое выражение и в зависимости от полученного значения `true` или `false` возвращает результат одного из двух соответствующих выражений, как показано в следующем примере.

:::code language="csharp" interactive="try-dotnet-method" source="snippets/shared/ConditionalOperator.cs" id="BasicExample":::

Как показано в предыдущем примере, синтаксис условного оператора выглядит следующим образом.

```csharp
condition ? consequent : alternative
```

Выражение `condition` должно принимать значение `true` или `false`. Если `condition` принимает значение `true`, вычисляется выражение `consequent`, а результат становится результатом операции. Если `condition` принимает значение `false`, вычисляется выражение `alternative`, а результат становится результатом операции. Вычисляется только выражение `consequent` или `alternative`.

Начиная с C# 9.0 условные выражения имеют целевой тип. Это значит, что если известен целевой тип условного выражения, типы `consequent` и `alternative` должны быть неявно преобразованы в целевой тип, как показано в следующем примере:

[!code-csharp[target-typed conditional](snippets/shared/ConditionalOperator.cs#TargetTyped)]

Если целевой тип условного выражения неизвестен (например, при использовании ключевого слова [`var`](../keywords/var.md)) или используются C# 8.0 и более ранние версии, типы `consequent` и `alternative` должны быть одинаковыми, либо должно поддерживаться неявное преобразование из одного типа в другой:

[!code-csharp[not target-typed conditional](snippets/shared/ConditionalOperator.cs#NotTargetTyped)]

Условный оператор имеет правую ассоциативность, то есть выражение формы.

```csharp
a ? b : c ? d : e
```

вычисляется как

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> Вы можете использовать следующий мнемонический прием, чтобы запомнить, как оценивается условный оператор:
>
> ```text
> is this condition true ? yes : no
> ```

## <a name="conditional-ref-expression"></a>Условное выражение REF

Начиная с версии C# 7.2 [локальные переменные REF](../keywords/ref.md#ref-locals) и [предназначенные только для чтения локальные переменные REF](../keywords/ref.md#ref-readonly-locals) можно присваивать условным образом с использованием условного выражения REF. Кроме того, условное выражение REF можно использовать как [возвращаемое ссылочное значение](../keywords/ref.md#reference-return-values) или как [аргумент метода `ref`](../keywords/ref.md#passing-an-argument-by-reference).

Для условного выражения REF используется следующий синтаксис:

```csharp
condition ? ref consequent : ref alternative
```

Подобно исходному условному оператору, условное выражение REF вычисляет только одно из двух выражений: `consequent` или `alternative`.

Для условного выражения REF типы `consequent` и `alternative` должны совпадать. Условные выражения REF не имеют целевого типа.

В следующем примере иллюстрируется использование условного выражения REF:

[!code-csharp-interactive[conditional ref](snippets/shared/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a>Условный оператор и оператор `if..else`

Если использовать условный оператор с оператором [if-else](../keywords/if-else.md), может получиться более лаконичный код в случаях, когда необходимо условно вычислить значение. В следующем примере иллюстрируются два вида классификации целого числа как положительного или отрицательного:

[!code-csharp[conditional and if-else](snippets/shared/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a>Возможность перегрузки оператора

Определяемый пользователем тип не может перегружать условный оператор.

## <a name="c-language-specification"></a>Спецификация языка C#

Дополнительные сведения см. в разделе [Условный оператор](~/_csharplang/spec/expressions.md#conditional-operator) статьи [Предварительная спецификация C# 6.0](~/_csharplang/spec/introduction.md).

Дополнительные сведения о функциях, добавленных в C# 7.2 и более поздние версии, см. в следующих заметках о функциях.

- [Условные выражения REF (C# 7.2)](~/_csharplang/proposals/csharp-7.2/conditional-ref.md)
- [Условное выражение с целевым типом (C# 9.0)](~/_csharplang/proposals/csharp-9.0/target-typed-conditional-expression.md)

## <a name="see-also"></a>См. также

- [справочник по C#](../index.md)
- [Операторы и выражения C#](index.md)
- [if-else (Справочник по C#)](../keywords/if-else.md)
- [Операторы ?. и ?[]](member-access-operators.md#null-conditional-operators--and-)
- [Операторы ?? и ??=](null-coalescing-operator.md)
- [Ключевое слово ref](../keywords/ref.md)
