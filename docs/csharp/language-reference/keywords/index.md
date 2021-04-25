---
description: Ключевые слова C#
title: Ключевые слова C#
ms.date: 03/17/2021
f1_keywords:
- cs.keywords
helpviewer_keywords:
- keywords [C#]
- C# language, keywords
- Visual C#, keywords
- '@ keyword'
ms.custom: updateeachrelease
ms.openlocfilehash: 08bcfcdf4f27e9b2b772db37566f03b4b174a5f5
ms.sourcegitcommit: 02cc87f02c46e603ea5925de95af746b7ab46a35
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/25/2021
ms.locfileid: "107954514"
---
# <a name="c-keywords"></a>Ключевые слова C#

Ключевые слова — это предварительно определенные зарезервированные идентификаторы, которые имеют специальные значения для компилятора. Их нельзя использовать как идентификаторы в программах без префикса `@`. Например, допустимым идентификатором является `@if`, но не `if`, поскольку `if` является ключевым словом.  
  
 В первой таблице этой статьи перечислены ключевые слова, которые нельзя использовать как идентификаторы в любой части программы C#. Во второй таблице этой статьи перечислены контекстные ключевые слова C#. Контекстные ключевые слова имеют особое значение только в определенном контексте программы, а за пределами этого контекста могут использоваться в качестве идентификаторов. Как правило, новые ключевые слова добавляются в язык C# в качестве контекстных ключевых слов, чтобы не нарушать работу программ, созданных в предыдущих версиях.  
  
|||||  
|---|---|---|---|  
|[abstract](abstract.md)|[as](../operators/type-testing-and-cast.md#as-operator)|[base](base.md)|[bool](../builtin-types/bool.md)|
|[break](break.md)|[byte](../builtin-types/integral-numeric-types.md)|[case](switch.md)|[catch](try-catch.md)|
|[char](../builtin-types/char.md)|[checked](checked.md)|[class](class.md)|[const](const.md)|
|[continue](continue.md)|[decimal](../builtin-types/floating-point-numeric-types.md)|[default](default.md)|[delegate](../builtin-types/reference-types.md)|
|[do](do.md)|[double](../builtin-types/floating-point-numeric-types.md)|[else](if-else.md)|[enum](../builtin-types/enum.md)|
|[event](event.md)|[explicit](../operators/user-defined-conversion-operators.md)|[extern](extern.md)|[false](../builtin-types/bool.md)|
|[finally](try-finally.md)|[fixed](fixed-statement.md)|[float](../builtin-types/floating-point-numeric-types.md)|[for](for.md)|
|[foreach](foreach-in.md)|[goto](goto.md)|[if](if-else.md)|[implicit](../operators/user-defined-conversion-operators.md)|
|[in](in.md)|[int](../builtin-types/integral-numeric-types.md)|[interface](interface.md)|[internal](internal.md)|
|[is](../operators/is.md)|[lock](lock-statement.md)|[long](../builtin-types/integral-numeric-types.md)|[namespace](namespace.md)|
|[new](../operators/new-operator.md)|[null](null.md)|[object](../builtin-types/reference-types.md)|[operator](../operators/operator-overloading.md)|
|[out](out.md)|[override](override.md)|[params](params.md)|[private](private.md)|
|[protected](protected.md)|[public](public.md)|[readonly](readonly.md)|[ref](ref.md)|
|[return](return.md)|[sbyte](../builtin-types/integral-numeric-types.md)|[sealed](sealed.md)|[short](../builtin-types/integral-numeric-types.md)|
|[sizeof](../operators/sizeof.md)|[stackalloc](../operators/stackalloc.md)|[static](static.md)|[string](../builtin-types/reference-types.md)|
|[struct](../builtin-types/struct.md)|[switch](switch.md)|[this](this.md)|[throw](throw.md)|
|[true](../builtin-types/bool.md)|[try](try-catch.md)|[typeof](../operators/type-testing-and-cast.md#typeof-operator)|[uint](../builtin-types/integral-numeric-types.md)|
|[ulong](../builtin-types/integral-numeric-types.md)|[unchecked](unchecked.md)|[unsafe](unsafe.md)|[ushort](../builtin-types/integral-numeric-types.md)|
|[using](using.md)|[virtual](virtual.md)|[void](../builtin-types/void.md)|[volatile](volatile.md)|
|[while](while.md)||||

## <a name="contextual-keywords"></a>Контекстные ключевые слова

 Контекстное ключевое слово используется для предоставления конкретного значения в коде, но оно не является зарезервированным словом в C#. Некоторые контекстные ключевые слова, например `partial` и `where`, имеют особое значение в двух или более контекстах.  
  
||||  
|---|---|---|  
|[add](add.md)|[and](../operators/patterns.md#logical-patterns)|[alias](extern-alias.md)|
|[ascending](ascending.md)|[async](async.md)|[await](../operators/await.md)|
|[by](by.md)|[descending](descending.md)|[dynamic](../builtin-types/reference-types.md)|
|[equals](equals.md)|[from](from-clause.md)|[get](get.md)|
|[global](../operators/namespace-alias-qualifier.md)|[group](group-clause.md)|[init](init.md)|
|[into](into.md)|[join](join-clause.md)|[let](let-clause.md)|
|[nameof](../operators/nameof.md)|[nint](../builtin-types/nint-nuint.md)|[not](../operators/patterns.md#logical-patterns) (не);|
|[notnull](../../programming-guide/generics/constraints-on-type-parameters.md#notnull-constraint)|[nuint](../builtin-types/nint-nuint.md)|[on](on.md)|
|[или диспетчер конфигурации служб](../operators/patterns.md#logical-patterns)|[orderby](orderby-clause.md)|[partial (тип)](partial-type.md)|
|[partial (метод)](partial-method.md)|[record](../../programming-guide/classes-and-structs/records.md)|[remove](remove.md)|
|[select](select-clause.md)|[set](set.md)|[unmanaged (ограничение универсального типа)](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint)|
|[value](value.md)|[var](var.md)|[when (условие фильтра)](when.md)|
|[where (ограничение универсального типа)](where-generic-type-constraint.md)|[where (предложение запроса)](where-clause.md)|[with](../operators/with-expression.md)|
|[yield](yield.md)|||

## <a name="see-also"></a>См. также

- [справочник по C#](../index.md)
