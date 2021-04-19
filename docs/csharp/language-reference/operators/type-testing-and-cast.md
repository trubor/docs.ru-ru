---
title: Операторы проверки типа и выражения приведения — справочник по C#
description: Сведения об операторах C#, которые можно использовать для проверки типа результата выражения и преобразования его в другой тип, если потребуется.
ms.date: 06/21/2019
author: pkulikov
f1_keywords:
- is_CSharpKeyword
- as_CSharpKeyword
- ()_CSharpKeyword
- typeof_CSharpKeyword
- as
- typeof
helpviewer_keywords:
- type-testing operators [C#]
- conversion operators [C#]
- type conversion [C#]
- is operator [C#]
- as operator [C#]
- cast operator [C#]
- cast expression [C#]
- () operator [C#]
- typeof operator [C#]
ms.openlocfilehash: f47074fda20c1bc2eda75184dd26c9de1c0e3701
ms.sourcegitcommit: 4b7f6b348c986556ef805cb6baacfd5b9ec18ed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2021
ms.locfileid: "107075320"
---
# <a name="type-testing-operators-and-cast-expression-c-reference"></a>Операторы проверки типа и выражения приведения (справочник по C#)

Чтобы выполнить проверку или преобразование типов, можно использовать следующие операторы и выражения:

- [оператор is](#is-operator) проверяет, совместим ли тип среды выполнения для определенного выражения с указанным типом;
- [оператор as](#as-operator) явным образом преобразует выражение в указанный тип, если тип среды выполнения совместим с этим типом;
- [выражение приведения](#cast-expression) выполняет явное преобразование;
- [оператор typeof](#typeof-operator) получает экземпляр <xref:System.Type?displayProperty=nameWithType> указанного типа.

## <a name="is-operator"></a>Оператор is

Оператор `is` проверяет, совместим ли тип среды выполнения для результата определенного выражения с указанным типом. Начиная с версии C# 7.0, оператор `is` также проверяет соответствие результата выражения указанному шаблону.

Выражение с оператором проверки типа `is` имеет следующий вид:

```csharp
E is T
```

где `E` представляет выражение, возвращающее значение, а `T` содержит имя или параметр типа. `E` не может использоваться как анонимный метод или лямбда-выражение.

Выражение `E is T` возвращает значение `true`, если результат выражения `E` отличен от NULL и может быть преобразован в тип `T` путем преобразования ссылки, упаковки-преобразования или распаковки-преобразования. В противном случае он возвращает `false`. Оператор `is` не учитывает заданные пользователем преобразования.

В следующем примере показано, что оператор `is` возвращает `true`, если тип среды выполнения для результата выражения является производным от указанного типа, то есть между этими типами существует преобразование ссылки:

[!code-csharp[is with reference conversion](snippets/shared/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

В следующем примере показано, что оператор `is` учитывает упаковку-преобразование и распаковку-преобразование, но не учитывает [числовые преобразования](../builtin-types/numeric-conversions.md):

[!code-csharp-interactive[is with int](snippets/shared/TypeTestingAndConversionOperators.cs#IsWithInt)]

Дополнительные сведения о преобразованиях в C# см. в главе [о преобразованиях](~/_csharplang/spec/conversions.md) в [спецификации по языку C#](~/_csharplang/spec/introduction.md).

### <a name="type-testing-with-pattern-matching"></a>Тестирование типов с сопоставлением шаблонов

Начиная с версии C# 7.0, оператор `is` также проверяет соответствие результата выражения указанному шаблону. В следующем примере показано, как использовать [шаблон объявления](patterns.md#declaration-and-type-patterns) для проверки типа выражения в среде выполнения:

[!code-csharp-interactive[is with declaration pattern](snippets/shared/TypeTestingAndConversionOperators.cs#IsDeclarationPattern)]

Дополнительные сведения о поддерживаемых шаблонах см. в разделе [Шаблоны](patterns.md).

## <a name="as-operator"></a>Оператор as

Оператор `as` явным образом преобразует результат выражения в указанный ссылочный или поддерживающий значения NULL тип. Если такое преобразование невозможно, оператор `as` возвращает значение `null`. В отличие от [выражения приведения](#cast-expression), оператор `as` никогда не создает исключение.

Выражение имеет такой формат:

```csharp
E as T
```

где `E` представляет выражение, возвращающее значение, а `T` содержит имя или параметр типа. Результат такого выражения аналогичен результату этого:

```csharp
E is T ? (T)(E) : (T)null
```

за исключением того, что `E` вычисляется только один раз.

Оператор `as` рассматривает только преобразование ссылки, допускающие значение NULL преобразования, упаковку-преобразование и распаковку-преобразование. Нельзя использовать оператор `as` для определенного пользователем преобразования. Для этого используйте [выражение приведения](#cast-expression).

В следующем примере иллюстрируется использование оператора `as`.

[!code-csharp-interactive[as operator](snippets/shared/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> Как показано в примере выше, нужно сравнить результат выражения `as` со значением `null`, чтобы проверить, успешно ли выполнено преобразование. Начиная с версии C# 7.0, вы можете использовать [оператор is](#type-testing-with-pattern-matching) как для проверки успешного выполнения преобразования, так и для сохранения результата в переменной, если преобразование выполнено успешно.

## <a name="cast-expression"></a>Выражение приведения

Выражение приведения в формате `(T)E` выполняет явное преобразование значения выражения `E` в тип `T`. Если явного преобразования из типа `E` в тип `T` не существует, возникает ошибка времени компиляции. Во время выполнения явное преобразование может завершиться сбоем, и выражение приведения может вызвать исключение.

Приведенный ниже пример демонстрирует явное числовое преобразование и преобразование ссылки:

[!code-csharp-interactive[cast expression](snippets/shared/TypeTestingAndConversionOperators.cs#Cast)]

Сведения о поддерживаемых явных преобразованиях см. в разделе [о явных преобразованиях](~/_csharplang/spec/conversions.md#explicit-conversions) в [спецификации по языку C#](~/_csharplang/spec/introduction.md). Сведения о том, как определять пользовательские операторы явного или неявного преобразования, см. в разделе [Операторы пользовательского преобразования](user-defined-conversion-operators.md).

### <a name="other-usages-of-"></a>Другие данные об использовании ()

Используйте скобки, чтобы [вызвать метод или делегат](member-access-operators.md#invocation-expression-).

Кроме того, с помощью круглых скобок можно настраивать порядок выполнения операций в выражении. Дополнительные сведения см. в разделе [Операторы C#](index.md).

## <a name="typeof-operator"></a>typeof - оператор

Оператор `typeof` получает экземпляр <xref:System.Type?displayProperty=nameWithType> для указанного типа. Оператор `typeof` принимает в качестве аргумента имя типа или параметр типа, как показано в следующем примере:

[!code-csharp-interactive[typeof operator](snippets/shared/TypeTestingAndConversionOperators.cs#TypeOf)]

Кроме того, оператор `typeof` можно использовать с несвязанными универсальными типами. В имени несвязанного универсального типа должно содержаться правильное количество запятых, то есть на одну меньше, чем число параметров этого типа. В следующем примере показано использование оператора `typeof` с несвязанным универсальным типом:

[!code-csharp-interactive[typeof unbound generic](snippets/shared/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

Оператор `typeof` не может принимать выражения в качестве аргументов. Чтобы получить экземпляр <xref:System.Type?displayProperty=nameWithType> для типа среды выполнения результата выражения, используйте метод <xref:System.Object.GetType%2A?displayProperty=nameWithType>.

### <a name="type-testing-with-the-typeof-operator"></a>Тестирование типов с оператором `typeof`

Используйте оператор `typeof` для проверки, совместим ли тип среды выполнения для определенного выражения с указанным типом. В следующем примере показано различие между проверкой типов с помощью оператора `typeof` и [оператора is](#is-operator):

[!code-csharp[typeof vs is](snippets/shared/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a>Возможность перегрузки оператора

Операторы `is`, `as` и `typeof` перегрузить нельзя.

Определяемый пользователем тип нельзя использовать для перегрузки оператора `()`, но на его основе можно определить пользовательское преобразование типа и выполнить его с помощью выражения приведения. Дополнительные сведения см. в разделе [Операторы пользовательского преобразования](user-defined-conversion-operators.md).

## <a name="c-language-specification"></a>Спецификация языка C#

Дополнительные сведения см. в следующих разделах статьи [Спецификация языка C#](~/_csharplang/spec/introduction.md):

- [Оператор is](~/_csharplang/spec/expressions.md#the-is-operator)
- [Оператор as](~/_csharplang/spec/expressions.md#the-as-operator)
- [Выражения приведения](~/_csharplang/spec/expressions.md#cast-expressions)
- [Оператор typeof](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a>См. также

- [справочник по C#](../index.md)
- [Операторы и выражения C#](index.md)
- [Практическое руководство. Безопасное приведение с помощью сопоставления шаблонов, а также операторов is и as](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [Универсальные шаблоны в .NET](../../../standard/generics/index.md)
