---
title: Руководство по программированию на C#. Массивы
description: Храните несколько переменных одного типа в структуре данных массива на C#. Объявите массив, указав тип или указав объект для хранения любого типа.
ms.date: 01/22/2021
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: d55e177d18c0dc483f3419966042e42f1e41ed26
ms.sourcegitcommit: 178ccefa8c454bfae844ce12ed222a54913df157
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2021
ms.locfileid: "107883310"
---
# <a name="arrays-c-programming-guide"></a>Массивы (Руководство по программированию на C#)

В структуре данных массива можно хранить несколько переменных одного типа. Чтобы объявить массив, следует указать тип его элементов. Если требуется, чтобы массив мог хранить элементы любого типа, можно указать `object` в качестве его типа. В унифицированной системе типов C# все типы, стандартные и определяемые пользователем, ссылочные типы и типы значений напрямую или косвенно наследуются из <xref:System.Object>.

```csharp
type[] arrayName;
```

## <a name="example"></a>Пример

В следующих примерах создаются одномерные массивы, многомерные массивы и массивы массивов:

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a>Общие сведения о массивах

Массив имеет следующие свойства:

- Массив может быть [одномерным](single-dimensional-arrays.md), [многомерным](multidimensional-arrays.md) или [массивом массивов](jagged-arrays.md).
- Количество измерений и длина каждого из измерений задаются, когда создается экземпляр массива. Эти значения нельзя изменить во время существования экземпляра.
- Используемые по умолчанию значения числовых элементов массива равны нулю, и элементам ссылки присвоено значение NULL.
- В массиве массивов элементы являются ссылочными типами и инициализируются значением `null`.
- Массивы индексируются от нуля: массив с `n` элементами индексируется от `0` до `n-1`.
- Элементы массива могут иметь любой тип, в том числе тип массива.
- Типы массивов — это [ссылочные типы](../../language-reference/keywords/reference-types.md), производные от абстрактного базового типа <xref:System.Array>. Все массивы реализуют <xref:System.Collections.IList> и <xref:System.Collections.IEnumerable>.  Вы можете использовать массивы итерации [foreach](../../language-reference/keywords/foreach-in.md) в C#,  так как одномерные массивы также реализуют <xref:System.Collections.Generic.IList%601> и <xref:System.Collections.Generic.IEnumerable%601>.

### <a name="arrays-as-objects"></a>Массивы как объекты

В C# массивы представляют собой реальные объекты, а не просто адресуемые области непрерывной памяти, как в C и C++. <xref:System.Array> — это абстрактный базовый тип для всех типов массивов. Вы можете использовать свойства и другие члены класса, входящие в <xref:System.Array>. Например, с помощью свойства <xref:System.Array.Length%2A> можно получить длину массива. В следующем коде значение длины массива `numbers` (`5`) присваивается переменной с именем `lengthOfNumbers`:

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

В классе <xref:System.Array> представлено множество других полезных методов и свойств для сортировки, поиска и копирования массивов. В следующем примере свойство <xref:System.Array.Rank%2A> используется для отображения количества измерений массива.

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a>См. также раздел

- [Как использовать одномерные массивы](single-dimensional-arrays.md)
- [Как использовать многомерные массивы](multidimensional-arrays.md)
- [Как использовать массивы массивов](jagged-arrays.md)
- [Использование оператора foreach с массивами](using-foreach-with-arrays.md)
- [Передача массивов в качестве аргументов](passing-arrays-as-arguments.md)
- [Неявно типизированные массивы](implicitly-typed-arrays.md)
- [Руководство по программированию на C#](../index.md)
- [Коллекции](../concepts/collections.md)

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
