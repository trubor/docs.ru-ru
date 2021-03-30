---
title: Операторы и выражения для доступа к элементам. Справочник по C#
description: Дополнительные сведения об операторах C#, которые можно использовать для доступа к членам типа.
ms.date: 11/13/2020
author: pkulikov
f1_keywords:
- ._CSharpKeyword
- '[]_CSharpKeyword'
- ()_CSharpKeyword
- ^_CSharpKeyword
- .._CSharpKeyword
helpviewer_keywords:
- member access operators [C#]
- member access operator [C#]
- dot operator [C#]
- . operator [C#]
- subscript operator [C#]
- square brackets [] operator [C#]
- indexer operator [C#]
- '[] operator [C#]'
- null-conditional operators [C#]
- Elvis operator [C#]
- ?. operator [C#]
- ?[] operator [C#]
- invocation operator [C#]
- method call [C#]
- method invocation [C#]
- delegate invocation [C#]
- () operator [C#]
- ^ operator [C#]
- index from end operator [C#]
- hat operator [C#]
- .. operator [C#]
- range operator [C#]
ms.openlocfilehash: b3ba56c7485d27d2692a589e2a8e5b330ea0de85
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873904"
---
# <a name="member-access-operators-and-expressions-c-reference"></a>Операторы и выражения для доступа к элементам (справочник по C#)

При получении доступа к элементу типа можно использовать следующие операторы и выражения:

- [`.` (доступ к члену) ](#member-access-expression-): для доступа к члену пространства имен или типа;
- [`[]` (элемент массива или индексатор доступа) ](#indexer-operator-): для доступа к элементу массива или индексатору типа;
- [`?.` и `?[]` (null-условные операторы)](#null-conditional-operators--and-): для выполнения операции доступа члена или элемента только в том случае, если операнд не равен null;
- [`()` (вызов) ](#invocation-expression-): для вызова метода или делегата.
- [`^` (индекс от конца) ](#index-from-end-operator-): для определения того, что расположение элемента находится в конце последовательности.
- [`..` (диапазон)](#range-operator-): для определения диапазона индексов, которые можно использовать для получения диапазона элементов последовательности.

## <a name="member-access-expression-"></a>Выражение доступа к члену

Маркер `.` используется для обращения к члену пространства имен или типа, как в следующих примерах.

- Используйте `.` для обращения к пространству имен, вложенному в другое пространство имен, как показано в следующем примере [директивы `using`](../keywords/using-directive.md).

  [!code-csharp[nested namespaces](snippets/shared/MemberAccessOperators.cs#NestedNamespace)]

- Используйте `.` для создания *полного имени* для обращения к типу в пределах пространства имен, как показано в следующем коде:

  [!code-csharp[qualified name](snippets/shared/MemberAccessOperators.cs#QualifiedName)]

  Используйте [директиву `using`](../keywords/using-directive.md), чтобы сделать использование полных имен необязательным.

- Используйте `.` для обращения к [членам типов](../../programming-guide/classes-and-structs/index.md#members) (статическим и нестатическим), как показано в следующем коде:

  [!code-csharp-interactive[type members](snippets/shared/MemberAccessOperators.cs#TypeMemberAccess)]

Можно также использовать `.` для вызова [метода расширения](../../programming-guide/classes-and-structs/extension-methods.md).

## <a name="indexer-operator-"></a>Оператор индексатора []

Квадратные скобки, `[]`, обычно используются для доступа к элементам массива, индексатора или указателя.

### <a name="array-access"></a>Доступ к массиву

В приведенном ниже примере показано, как получить доступ к элементам массива.

[!code-csharp-interactive[array access](snippets/shared/MemberAccessOperators.cs#Arrays)]

Если индекс массива выходит за границы соответствующего измерения массива, возникает исключение <xref:System.IndexOutOfRangeException>.

Как показано в предыдущем примере, квадратные скобки также используются в объявлении типа массива и для создания экземпляров массива.

Дополнительные сведения см. в руководстве по работе с [массивами](../../programming-guide/arrays/index.md).

### <a name="indexer-access"></a>Доступ к индексатору

В приведенном ниже примере используется тип .NET <xref:System.Collections.Generic.Dictionary%602> для получения доступа к индексатору:

[!code-csharp-interactive[indexer access](snippets/shared/MemberAccessOperators.cs#Indexers)]

Индексаторы позволяют индексировать экземпляры определяемого пользователем типа аналогично индексации массива. В отличие от индексов массива, которые должны быть целым числом, параметры индексатора могут быть объявлены любым типом.

Дополнительные сведения см. в [руководстве по работе с индексаторами](../../programming-guide/indexers/index.md).

### <a name="other-usages-of-"></a>Другие данные об использовании []

Сведения о доступе к элементу указателя см. в разделе, посвященном [оператору доступа к элементу указателя []](pointer-related-operators.md#pointer-element-access-operator-), статьи [Операторы, связанные с указателем](pointer-related-operators.md).

Кроме того, с помощью квадратных скобок можно указывать [атрибуты](../../programming-guide/concepts/attributes/index.md).

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a>NULL-условные операторы: ?. и ?[]

В C# 6 и более поздних версий доступен оператор с условием null, который применяется для [доступа к членам](#member-access-expression-), `?.`, или [доступа к элементам](#indexer-operator-), `?[]`, к операнду только в том случае, если он имеет значение, отличное от NULL, в противном случае он возвращает `null`. Это означает следующее:

- Если `a` вычисляется как `null`, то результатом `a?.x` или `a?[x]` является `null`.
- Если `a` принимает значение, отличное от NULL, результат `a?.x` или `a?[x]` совпадает с результатом `a.x` или `a[x]`соответственно.

  > [!NOTE]
  > Если `a.x` или `a[x]` вызывает исключение, `a?.x` или `a?[x]` вызовут то же исключение для отличного от NULL `a`. Например, если `a` является экземпляром массива, не равным null, и `x` находится вне границ `a`, `a?[x]` вызовет <xref:System.IndexOutOfRangeException>.

Операторы с условием NULL предусматривают сокращенную обработку. То есть, если в цепочке операций условного доступа к элементу или члену одна из операций возвращает значение `null`, остальная цепочка не выполняется. В следующем примере `B` не вычисляется, если `A` принимает значение `null`, и `C` не вычисляется, если `A` или `B` принимает значение `null`.

```csharp
A?.B?.Do(C);
A?.B?[C];
```

В следующем примере иллюстрируется использование операторов `?.` и `?[]`.

[!code-csharp-interactive[null-conditional operators](snippets/shared/MemberAccessOperators.cs#NullConditional)]

В предыдущем примере также используется [оператор объединения со значением NULL `??`](null-coalescing-operator.md), чтобы указать альтернативное выражение для вычисления в случае, если результат выполнения условной операции NULL — это `null`.

Если `a.x` или `a[x]` является типом `T`, не допускающим значение NULL, `a?.x` или `a?[x]` является соответствующим [типом `T?`, допускающим значение NULL](../builtin-types/nullable-value-types.md). Если требуется выражение типа `T`, примените оператор объединения со значением NULL `??` к условному выражению NULL, как показано в следующем примере:

[!code-csharp-interactive[null-conditional with null-coalescing](snippets/shared/MemberAccessOperators.cs#NullConditionalWithNullCoalescing)]

Если в предыдущем примере оператор `??` не используется, `numbers?.Length < 2` вычисляется как `false`, если `numbers` имеет значение `null`.

Null-условный оператор доступа к элементу `?.` также называется элвис-оператором.

### <a name="thread-safe-delegate-invocation"></a>Потокобезопасный вызов делегата

Используйте оператор `?.` для проверки того, что делегат не равен null, и его вызова потокобезопасным способом (например, в том случае, когда вы собираетесь [породить событие](../../../standard/events/how-to-raise-and-consume-events.md)), как показано в следующем коде:

```csharp
PropertyChanged?.Invoke(…)
```

Этот код эквивалентен следующему коду, который будет использоваться в C# 5 или более ранней версии:

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

Этот потокобезопасный способ гарантирует, что вызывается только `handler`, не имеющий значения NULL. Так как экземпляры делегата являются неизменяемыми, ни один из потоков не может изменить объект, на который ссылается локальная переменная `handler`. В частности, если код, выполняемый другим потоком, отменяет подписку на событие `PropertyChanged` и событие `PropertyChanged` принимает значение `null` до вызова `handler`, объект, на который ссылается `handler`, остается неизменным. Оператор `?.` вычисляет левый операнд не более одного раза, гарантируя, что его нельзя изменить на `null` после того, как он пройдет проверку как не имеющий значение NULL.

## <a name="invocation-expression-"></a>Выражения вызова ()

Используйте скобки, `()`, чтобы вызвать [метод](../../programming-guide/classes-and-structs/methods.md) или [делегат](../../programming-guide/delegates/index.md).

Приведенный ниже пример демонстрирует вызов делегата и метода с аргументами или без них.

[!code-csharp-interactive[invocation with ()](snippets/shared/MemberAccessOperators.cs#Invocation)]

Круглые скобки также можно использовать при вызове [конструктора](../../programming-guide/classes-and-structs/constructors.md) с оператором [`new`](new-operator.md).

### <a name="other-usages-of-"></a>Другие данные об использовании ()

Кроме того, с помощью круглых скобок можно настраивать порядок выполнения операций в выражении. Дополнительные сведения см. в разделе [Операторы C#](index.md).

В [выражениях приведения](type-testing-and-cast.md#cast-expression), которые выполняют явные преобразования типов, также используйте круглые скобки.

## <a name="index-from-end-operator-"></a>Индекс от конца: оператор ^

Оператор `^`, доступный в C# 8.0 и последующих версиях, определяет расположение элемента от конца последовательности. Для последовательности длины `length``^n` указывает на элемент с `length - n` смещения от начала последовательности. Например, `^1` указывает на последний элемент последовательности, а `^length` — на первый элемент последовательности.

[!code-csharp[index from end](snippets/shared/MemberAccessOperators.cs#IndexFromEnd)]

В предыдущем примере выражение `^e` имеет тип <xref:System.Index?displayProperty=nameWithType>. В выражении `^e` результат `e` должен быть неявно преобразован в `int`.

Можно также использовать оператор `^` с [оператором диапазона](#range-operator-) для создания диапазона индексов. См. сведения в [руководстве по диапазонам и индексам](../../whats-new/tutorials/ranges-indexes.md).

## <a name="range-operator-"></a>Диапазон: оператор .

Оператор диапазона `..`, доступный в C# 8.0 и последующих версиях, определяет начало и конец диапазона индексов в качестве своих операндов. Левый операнд является *инклюзивным* началом диапазона. Правый операнд является *эксклюзивным* концом диапазона. Любой из операндов может быть индексом от начала или конца последовательности, как показано в следующем примере:

[!code-csharp[range examples](snippets/shared/MemberAccessOperators.cs#Ranges)]

В предыдущем примере выражение `a..b` имеет тип <xref:System.Range?displayProperty=nameWithType>. В выражении `a..b` результаты `a` и `b` должны быть неявно преобразованы в `int` или <xref:System.Index>.

Можно проигнорировать любой из операндов оператора `..`, чтобы получить открытый диапазон:

- `a..` — это эквивалент `a..^0`
- `..b` — это эквивалент `0..b`
- `..` — это эквивалент `0..^0`

[!code-csharp[ranges with omitted operands](snippets/shared/MemberAccessOperators.cs#RangesOptional)]

См. сведения в [руководстве по диапазонам и индексам](../../whats-new/tutorials/ranges-indexes.md).

## <a name="operator-overloadability"></a>Возможность перегрузки оператора

Операторы `.`, `()`, `^` и `..` перегрузить нельзя. Оператор `[]` также считается неперегружаемым. Используйте [индексаторы](../../programming-guide/indexers/index.md) для поддержки индексирования с помощью определяемых пользователем типов.

## <a name="c-language-specification"></a>Спецификация языка C#

Дополнительные сведения см. в следующих разделах статьи [Спецификация языка C#](~/_csharplang/spec/introduction.md):

- [Доступ к членам](~/_csharplang/spec/expressions.md#member-access)
- [Доступ к элементам](~/_csharplang/spec/expressions.md#element-access)
- [Null-условный оператор](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [Выражения вызова](~/_csharplang/spec/expressions.md#invocation-expressions)

См. сведения о индексах и диапазонах в [примечании к функциям](~/_csharplang/proposals/csharp-8.0/ranges.md).

## <a name="see-also"></a>См. также

- [справочник по C#](../index.md)
- [Операторы и выражения C#](index.md)
- [Оператор ?? (оператор объединения со значением NULL)](null-coalescing-operator.md)
- [Оператор ::](namespace-alias-qualifier.md)
