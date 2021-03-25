---
description: Справочник по C#. Ключевое слово init
title: Справочник по C#. Ключевое слово init
ms.date: 03/03/2021
f1_keywords:
- init
- init_CSharpKeyword
helpviewer_keywords:
- init keyword [C#]
ms.openlocfilehash: 2271b5332c8bfd3223d0c034a44eca4e2ca0ca54
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190445"
---
# <a name="init-c-reference"></a>init (справочник по C#)

В C# 9 и более поздних версий ключевое слово `init` определяет *метод доступа* в свойстве или индексаторе. Метод задания только для инициализации присваивает значение свойству или элементу индексатора только во время создания объекта. Дополнительные сведения и примеры см. в разделах [Свойства](../../programming-guide/classes-and-structs/properties.md), [Автоматически реализуемые свойства](../../programming-guide/classes-and-structs/auto-implemented-properties.md) и [Индексаторы](../../programming-guide/indexers/index.md).

В приведенном ниже примере определен как метод доступа `get`, так и метод доступа `init` для свойства с именем `Seconds`. Для возвращения значения свойства в нем используется закрытое поле с именем `_seconds`.

[!code-csharp[init#1](snippets/InitExample1.cs)]

Метод доступа `init` часто состоит из одного оператора, который присваивает значение, как в предыдущем примере. Метод доступа `init` можно реализовывать как элемент, воплощающий выражение. В приведенном ниже примере методы доступа `get` и `init` реализуются как члены, воплощающие выражение.

[!code-csharp[init#3](snippets/InitExample3.cs)]
  
В простых случаях, когда методы доступа `get` и `init` свойства не выполняют никаких иных операций, кроме задания или извлечения значения в закрытом поле, можно использовать поддержку автоматически реализуемых свойств в компиляторе C#. В приведенном ниже примере `Hours` реализуется как автоматически реализуемое свойство.

[!code-csharp[init#2](snippets/InitExample2.cs)]
  
## <a name="c-language-specification"></a>Спецификация языка C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>См. также

- [Справочник по C#](../index.md)
- [Руководство по программированию на C#](../../programming-guide/index.md)
- [Ключевые слова в C#](index.md)
- [Свойства](../../programming-guide/classes-and-structs/properties.md)
