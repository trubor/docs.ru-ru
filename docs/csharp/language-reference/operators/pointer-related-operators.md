---
title: Операторы, связанные с указателем — справочник по C#
description: Дополнительные сведения об операторах C#, которые можно использовать при работе с указателями.
ms.date: 05/20/2019
author: pkulikov
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- pointer related operators [C#]
- address-of operator [C#]
- '& operator [C#]'
- pointer indirection operator [C#]
- dereference operator [C#]
- '* operator [C#]'
- pointer member access operator [C#]
- -> operator [C#]
- pointer element access [C#]
- '[] operator [C#]'
- pointer arithmetic [C#]
- pointer increment [C#]
- pointer decrement [C#]
- pointer comparison [C#]
ms.openlocfilehash: 2d522e9357fb6da7b8d66a663e99e8858c9dd521
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103480381"
---
# <a name="pointer-related-operators-c-reference"></a>Операторы, связанные с указателем (справочник по C#)

Для работы с указателями можно использовать следующие операторы:

- Унарный оператор [`&` (address-of)](#address-of-operator-): для получения адреса переменной
- Унарный оператор [`*` (косвенное обращение к указателю)](#pointer-indirection-operator-): для получения переменной, на которую указывает указатель
- Операторы [`->` (доступ к членам)](#pointer-member-access-operator--) и [`[]` (доступ к элементам)](#pointer-element-access-operator-)
- Арифметические операторы [`+`, `-`, `++` и `--`](#pointer-arithmetic-operators)
- Операторы сравнения [`==`, `!=`, `<`, `>`, `<=` и `>=`](#pointer-comparison-operators)

Сведения о типах указателей см. в разделе [Типы указателей](../../programming-guide/unsafe-code-pointers/pointer-types.md).

> [!NOTE]
> Для всех операций с указателями требуется [небезопасный](../keywords/unsafe.md) контекст. Код, содержащий небезопасные блоки, должен компилироваться с параметром компилятора [**AllowUnsafeBlocks**](../compiler-options/language.md#allowunsafeblocks).

## <a name="address-of-operator-amp"></a><a name="address-of-operator-"></a> Оператор address-of &amp;

Унарный оператор `&` возвращает адрес своего операнда:

[!code-csharp[address of local](snippets/shared/PointerOperators.cs#AddressOf)]

Операнд оператора `&` должен быть фиксированной переменной. *Фиксированные* переменные — это переменные в местах хранения, на которые не распространяется [сборка мусора](../../../standard/garbage-collection/index.md). В приведенном выше примере локальная переменная `number` — это фиксированная переменная, так как она находится в стеке. Переменные, которые находятся в местах хранения, обслуживаемых сборщиком мусора (например, перемещение), называются *перемещаемыми* переменными. Поля объекта и элементы массива являются примерами перемещаемых переменных. Вы можете получить адрес перемещаемой переменной, если зафиксируете или закрепите ее с помощью [ инструкции `fixed`](../keywords/fixed-statement.md). Полученный адрес действителен только в пределах блока инструкции `fixed`. В следующем примере показано, как использовать инструкцию `fixed` и оператор `&`:

[!code-csharp[address of fixed](snippets/shared/PointerOperators.cs#AddressOfFixed)]

Получить адрес константы или значения нельзя.

Дополнительные сведения о фиксированных и перемещаемых переменных см. в разделе [Фиксированные и перемещаемые переменные](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) в [спецификации языка C#](~/_csharplang/spec/introduction.md).

Бинарный оператор `&` вычисляет [логическое И](boolean-logical-operators.md#logical-and-operator-) своих логических операндов или [побитовое логическое И](bitwise-and-shift-operators.md#logical-and-operator-) своих целочисленных операндов.

## <a name="pointer-indirection-operator-"></a>Оператор косвенного обращения указателя *

Унарный оператор косвенного обращения указателя `*` получает переменную, на которую указывает операнд. Он также называется оператором разыменования. Операнд оператора `*` должен иметь тип указателя.

[!code-csharp[pointer indirection](snippets/shared/PointerOperators.cs#PointerIndirection)]

Невозможно применить оператор `*` к выражению типа `void*`.

Бинарный оператор `*` вычисляет [продукт](arithmetic-operators.md#multiplication-operator-) своих числовых операндов.

## <a name="pointer-member-access-operator--"></a>Оператор доступа к члену указателя ->

Оператор `->` объединяет [косвенное обращение к указателю](#pointer-indirection-operator-) и [доступ к члену](member-access-operators.md#member-access-expression-). То есть если `x` — это указатель типа `T*`, а `y` является доступным членом типа `T`, выражение формы

```csharp
x->y
```

эквивалентно

```csharp
(*x).y
```

В следующем примере иллюстрируется использование оператора `->`.

[!code-csharp[pointer member access](snippets/shared/PointerOperators.cs#MemberAccess)]

Невозможно применить оператор `->` к выражению типа `void*`.

## <a name="pointer-element-access-operator-"></a>Оператор доступа к элементу указателя []

Для выражения `p` типа указателя доступ к элементу указателя формы `p[n]` вычисляется как `*(p + n)`, где `n` должен иметь тип, неявно преобразуемый в `int`, `uint`, `long` или `ulong`. Сведения о поведении оператора `+` с указателями см. в разделе [Сложение целочисленного значения с указателем или его вычитание из указателя](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer).

Следующий пример демонстрирует доступ к элементам массива с указателем и оператором `[]`:

[!code-csharp[pointer element access](snippets/shared/PointerOperators.cs#ElementAccess)]

В предыдущем примере [выражение `stackalloc`](stackalloc.md) выделяет блок памяти в стеке.

> [!NOTE]
> Оператор доступа к элементу указателя не проверяет ошибки за пределами области.

Нельзя использовать `[]` для доступа к элементу указателя с помощью выражения типа `void*`.

Можно также использовать оператор `[]` для [доступа к элементу массива или индексатору](member-access-operators.md#indexer-operator-).

## <a name="pointer-arithmetic-operators"></a>Арифметические операторы указателя

Вы можете выполнить следующие арифметические операции с указателями:

- Сложение целочисленного значения с указателем или его вычитание из указателя
- Вычитание двух указателей
- Инкремент или декремент указателя

Невозможно выполнить эти операции с указателями типа `void*`.

Сведения о поддерживаемых арифметических операциях с числовыми типами см. в разделе [Арифметические операторы](arithmetic-operators.md).

### <a name="addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer"></a>Сложение целочисленного значения с указателем или его вычитание из указателя

Для указателя `p` типа `T*` и выражения `n` типа, неявно преобразуемого в `int`, `uint`, `long` или `ulong`, сложение и вычитание определяются следующим образом:

- Выражения `p + n` и `n + p` создают указатель типа `T*`, полученный добавлением `n * sizeof(T)` к адресу, предоставленному `p`.
- Выражение `p - n` создает указатель типа `T*`, полученный вычитанием `n * sizeof(T)` из адреса, предоставленного `p`.

[Оператор `sizeof`](sizeof.md) получает размер типа в байтах.

В следующем примере показано использование оператора `+` с указателем:

[!code-csharp[pointer addition](snippets/shared/PointerOperators.cs#AddNumber)]

### <a name="pointer-subtraction"></a>Вычитание указателей

Для двух указателей `p1` и `p2` типа `T*` выражение `p1 - p2` находит разность между адресами, предоставленными `p1` и `p2`, деленную на `sizeof(T)`. Результат имеет тип `long`. То есть `p1 - p2` вычисляется как `((long)(p1) - (long)(p2)) / sizeof(T)`.

В следующем примере показано вычитание указателей:

[!code-csharp[pointer subtraction](snippets/shared/PointerOperators.cs#SubtractPointers)]

### <a name="pointer-increment-and-decrement"></a>Инкремент и декремент указателя

Оператор инкремента `++`[добавляет](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 к своему операнду указателя. Оператор декремента `--`[вычитает](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 из своего операнда указателя.

Оба оператора поддерживаются в двух формах: постфикс (`p++` и `p--`) и префикс (`++p` и `--p`). Результат `p++` и `p--` — это значение `p` *перед* операцией. Результат `++p` и `--p` — это значение `p` *после* операции.

В следующем примере показано поведение постфиксных и префиксных операторов инкремента:

[!code-csharp[pointer increment](snippets/shared/PointerOperators.cs#Increment)]

## <a name="pointer-comparison-operators"></a>Операторы сравнения указателей

Вы можете использовать операторы `==`, `!=`, `<`, `>`, `<=` и `>=` для сравнения операндов любого типа указателя, включая `void*`. Эти операторы сравнивают адреса, предоставленные двумя операндами, как если бы они были целыми числами без знака.

Сведения о поведении этих операторов для операндов других типов см. в статьях [Операторы равенства](equality-operators.md) и [Операторы сравнения](comparison-operators.md).

## <a name="operator-precedence"></a>Приоритет операторов

В следующем списке операторы, связанные с указателями, упорядочены от самого высокого до самого низкого приоритета:

- Постфиксные операторы инкремента `x++` и декремента `x--` и операторы `->` и `[]`
- Префиксные операторы инкремента `++x` и декремента `--x` и операторы `&` и `*`
- Аддитивные операторы `+` и `-`
- Операторы сравнения `<`, `>`, `<=` и `>=`
- Операторы равенства `==` и `!=`

Используйте скобки `()`, чтобы изменить порядок вычисления, накладываемый приоритетом операторов.

Полный список операторов C#, упорядоченный по уровню приоритета, можно найти в разделе [Приоритет операторов](index.md#operator-precedence) статьи [Операторы C#](index.md).

## <a name="operator-overloadability"></a>Возможность перегрузки оператора

Определяемый пользователем тип не может перегружать операторы, связанные с указателем, `&`, `*`, `->` и `[]`.

## <a name="c-language-specification"></a>Спецификация языка C#

Дополнительные сведения см. в следующих разделах статьи [Спецификация языка C#](~/_csharplang/spec/introduction.md):

- [Фиксированные и перемещаемые переменные](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables)
- [Оператор address-of](~/_csharplang/spec/unsafe-code.md#the-address-of-operator)
- [Косвенное обращение к указателю](~/_csharplang/spec/unsafe-code.md#pointer-indirection)
- [Доступ к членам указателей](~/_csharplang/spec/unsafe-code.md#pointer-member-access)
- [Доступ к элементам указателей](~/_csharplang/spec/unsafe-code.md#pointer-element-access)
- [Расчеты указателей](~/_csharplang/spec/unsafe-code.md#pointer-arithmetic)
- [Инкремент и декремент указателя](~/_csharplang/spec/unsafe-code.md#pointer-increment-and-decrement)
- [Сравнение указателей](~/_csharplang/spec/unsafe-code.md#pointer-comparison)

## <a name="see-also"></a>См. также

- [справочник по C#](../index.md)
- [Операторы и выражения C#](index.md)
- [Типы указателей](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Ключевое слово unsafe](../keywords/unsafe.md)
- [Ключевое слово fixed](../keywords/fixed-statement.md)
- [stackalloc](stackalloc.md)
- [Оператор sizeof](sizeof.md)
