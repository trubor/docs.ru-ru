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
# <a name="init-c-reference"></a><span data-ttu-id="16e15-103">init (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="16e15-103">init (C# Reference)</span></span>

<span data-ttu-id="16e15-104">В C# 9 и более поздних версий ключевое слово `init` определяет *метод доступа* в свойстве или индексаторе.</span><span class="sxs-lookup"><span data-stu-id="16e15-104">In C# 9 and later, the `init` keyword defines an *accessor* method in a property or indexer.</span></span> <span data-ttu-id="16e15-105">Метод задания только для инициализации присваивает значение свойству или элементу индексатора только во время создания объекта.</span><span class="sxs-lookup"><span data-stu-id="16e15-105">An init-only setter assigns a value to the property or the indexer element only during object construction.</span></span> <span data-ttu-id="16e15-106">Дополнительные сведения и примеры см. в разделах [Свойства](../../programming-guide/classes-and-structs/properties.md), [Автоматически реализуемые свойства](../../programming-guide/classes-and-structs/auto-implemented-properties.md) и [Индексаторы](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="16e15-106">For more information and examples, see [Properties](../../programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md), and [Indexers](../../programming-guide/indexers/index.md).</span></span>

<span data-ttu-id="16e15-107">В приведенном ниже примере определен как метод доступа `get`, так и метод доступа `init` для свойства с именем `Seconds`.</span><span class="sxs-lookup"><span data-stu-id="16e15-107">The following example defines both a `get` and an `init` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="16e15-108">Для возвращения значения свойства в нем используется закрытое поле с именем `_seconds`.</span><span class="sxs-lookup"><span data-stu-id="16e15-108">It uses a private field named `_seconds` to back the property value.</span></span>

[!code-csharp[init#1](snippets/InitExample1.cs)]

<span data-ttu-id="16e15-109">Метод доступа `init` часто состоит из одного оператора, который присваивает значение, как в предыдущем примере.</span><span class="sxs-lookup"><span data-stu-id="16e15-109">Often, the `init` accessor consists of a single statement that assigns a value, as it did in the previous example.</span></span> <span data-ttu-id="16e15-110">Метод доступа `init` можно реализовывать как элемент, воплощающий выражение.</span><span class="sxs-lookup"><span data-stu-id="16e15-110">You can implement the `init` accessor as an expression-bodied member.</span></span> <span data-ttu-id="16e15-111">В приведенном ниже примере методы доступа `get` и `init` реализуются как члены, воплощающие выражение.</span><span class="sxs-lookup"><span data-stu-id="16e15-111">The following example implements both the `get` and the `init` accessors as expression-bodied members.</span></span>

[!code-csharp[init#3](snippets/InitExample3.cs)]
  
<span data-ttu-id="16e15-112">В простых случаях, когда методы доступа `get` и `init` свойства не выполняют никаких иных операций, кроме задания или извлечения значения в закрытом поле, можно использовать поддержку автоматически реализуемых свойств в компиляторе C#.</span><span class="sxs-lookup"><span data-stu-id="16e15-112">For simple cases in which a property's `get` and `init` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="16e15-113">В приведенном ниже примере `Hours` реализуется как автоматически реализуемое свойство.</span><span class="sxs-lookup"><span data-stu-id="16e15-113">The following example implements `Hours` as an auto-implemented property.</span></span>

[!code-csharp[init#2](snippets/InitExample2.cs)]
  
## <a name="c-language-specification"></a><span data-ttu-id="16e15-114">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="16e15-114">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="16e15-115">См. также</span><span class="sxs-lookup"><span data-stu-id="16e15-115">See also</span></span>

- [<span data-ttu-id="16e15-116">Справочник по C#</span><span class="sxs-lookup"><span data-stu-id="16e15-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="16e15-117">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="16e15-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="16e15-118">Ключевые слова в C#</span><span class="sxs-lookup"><span data-stu-id="16e15-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="16e15-119">Свойства</span><span class="sxs-lookup"><span data-stu-id="16e15-119">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)
