---
description: выражение stackalloc справочнике по C#
title: выражение stackalloc справочнике по C#
ms.date: 03/13/2020
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc expression [C#]
ms.openlocfilehash: 42867ff1b5acffaf62639a31a5bdd3b4055e252a
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497467"
---
# <a name="stackalloc-expression-c-reference"></a>выражение stackalloc (справочник по C#)

Выражение `stackalloc` выделяет блок памяти в стеке. Выделенный в стеке блок памяти, который создает этот метод, автоматически удаляется по завершении выполнения метода. Вы не можете явным образом освободить память, выделенную `stackalloc`. Выделенный в стеке блок памяти не подвергается [сборке мусора](../../../standard/garbage-collection/index.md), поэтому его не нужно закреплять с помощью [инструкции `fixed`](../keywords/fixed-statement.md).

Результат выполнения выражения `stackalloc` можно присвоить переменной любого из следующих типов:

- Начиная с версии C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> или <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, как показано в следующем примере:

  [!code-csharp[stackalloc span](snippets/shared/StackallocOperator.cs#AssignToSpan)]

  Нет необходимости использовать [небезопасный](../keywords/unsafe.md) контекст при назначении выделенного в стеке блока памяти переменной <xref:System.Span%601> или <xref:System.ReadOnlySpan%601>.

  При работе с такими типами вы можете использовать выражение `stackalloc` в [условном](conditional-operator.md) выражении или выражении присваивания, как показано в следующем примере:

  [!code-csharp[stackalloc expression](snippets/shared/StackallocOperator.cs#AsExpression)]

  Начиная с версии C# 8.0, можно использовать выражение `stackalloc` внутри других выражений, если разрешена переменная <xref:System.Span%601> или <xref:System.ReadOnlySpan%601>, как показано в следующем примере:

  [!code-csharp[stackalloc in nested expressions](snippets/shared/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > Мы рекомендуем везде, где это возможно, использовать для работы с выделенной в стеке памятью типы <xref:System.Span%601> или <xref:System.ReadOnlySpan%601>.

- [Тип указателя](../unsafe-code.md#pointer-types), как показано в следующем примере.

  [!code-csharp[stackalloc pointer](snippets/shared/StackallocOperator.cs#AssignToPointer)]

  Как демонстрирует пример выше, при работе с типами указателей необходимо использовать контекст `unsafe`.

  В случае типов указателей можно использовать выражение `stackalloc` только в объявлении локальной переменной для инициализации переменной.

Объем доступной памяти в стеке ограничен. При выделении слишком большого объема памяти в стеке возникает исключение <xref:System.StackOverflowException>. Чтобы избежать этого, следуйте приведенным ниже правилам.

- Ограничьте объем памяти, выделенный `stackalloc`:

  [!code-csharp[limit stackalloc](snippets/shared/StackallocOperator.cs#LimitStackalloc)]

  Поскольку объем доступной памяти на стеке зависит от среды, в которой выполняется код, при определении фактического предельного значения следует использовать консервативное значение.

- Старайтесь не использовать `stackalloc` в циклах. Выделяйте блок памяти за пределами цикла и используйте его повторно внутри цикла.

Содержимое только что выделенной памяти не определено. Его следует инициализировать перед использованием. Например, вы можете использовать метод <xref:System.Span%601.Clear%2A?displayProperty=nameWithType>, который задает для всех элементов значение по умолчанию типа `T`.

Начиная с версии C# 7.3, вы можете использовать синтаксис инициализатора массива, чтобы определить содержимое для только что выделенной памяти. В следующем примере показано несколько способов сделать это:

[!code-csharp[stackalloc initialization](snippets/shared/StackallocOperator.cs#StackallocInit)]

В выражении `stackalloc T[E]` `T` должен иметь [неуправляемый тип](../builtin-types/unmanaged-types.md), а `E` — неотрицательное значение [int](../builtin-types/integral-numeric-types.md).

## <a name="security"></a>Безопасность

При использовании `stackalloc` в среде CLR автоматически включается контроль переполнения буфера. Если буфер переполнен, процесс незамедлительно прерывается — это позволяет минимизировать риск исполнения вредоносного кода.

## <a name="c-language-specification"></a>Спецификация языка C#

См. сведения о [выделении памяти в стеке](~/_csharplang/spec/unsafe-code.md#stack-allocation) в [спецификации языка C#](~/_csharplang/spec/introduction.md) и [разрешении `stackalloc` во вложенных контекстах](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) в примечании.

## <a name="see-also"></a>См. также

- [справочник по C#](../index.md)
- [Операторы и выражения C#](index.md)
- [Операторы, связанные с указателем](pointer-related-operators.md)
- [Типы указателей](../unsafe-code.md#pointer-types)
- [Типы, связанные с памятью и диапазонами](../../../standard/memory-and-spans/index.md)
- [Правила stackalloc](https://vcsjones.dev/2020/02/24/stackalloc/)
