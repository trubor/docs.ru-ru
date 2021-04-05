---
description: Справочник по C#. Метод partial
title: Справочник по C#. Метод partial
ms.date: 03/23/2021
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: 240ad6f2f5792e4db9b032e36991f3c398f1d2f9
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105111014"
---
# <a name="partial-method-c-reference"></a>Метод partial (Справочник по C#)

Сигнатура разделяемого метода определяется в одной части разделяемого типа, а его реализация — в другой части этого типа. С помощью разделяемых методов разработчики классов могут при необходимости реализовывать ловушки методов, которые схожи с обработчиками событий. Если реализация не предоставлена, компилятор удаляет сигнатуру во время компиляции. В отношении разделяемых методов применяются следующие условия:

- Объявления должны начинаться с контекстного ключевого слова [partial](../../language-reference/keywords/partial-type.md).

- Сигнатуры в обеих частях разделяемого типа должны совпадать.

Разделяемый метод может не иметь реализацию в следующих случаях.

- У него нет модификаторов доступа (включая [private](../../language-reference/keywords/private.md) по умолчанию).

- Он возвращает значение [void](../../language-reference/builtin-types/void.md).

- У него нет параметров [out](../../language-reference/keywords/out-parameter-modifier.md).

- У него нет ни одного из следующих модификаторов: [virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md), [sealed](../../language-reference/keywords/sealed.md), [new](../../language-reference/keywords/new-modifier.md) или [extern](../../language-reference/keywords/extern.md).

Любой метод, не соответствующий всем этим ограничениям (например, метод `public virtual partial void`), должен предоставлять реализацию.

В следующем примере показан разделяемый метод, определенный в двух частях разделяемого класса:

[!code-csharp[csrefKeywordsContextual#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#9)]

Разделяемые методы также могут быть удобны в сочетании с генераторами источника. Например, можно определить регулярное выражение, используя следующий шаблон.

```csharp
[RegexGenerated("(dog|cat|fish)")]
partial bool IsPetMatch(string input);
```

Дополнительные сведения см. в разделе [Разделяемые классы и методы](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).

## <a name="see-also"></a>См. также

- [Справочник по C#](../index.md)
- [Тип partial](partial-type.md)
