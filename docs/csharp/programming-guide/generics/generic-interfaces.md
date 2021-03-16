---
title: Руководство по программированию на C#. Универсальные интерфейсы
description: Сведения об использовании универсальных интерфейсов при программировании на C#. Изучите примеры кода и ознакомьтесь с дополнительными ресурсами.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
ms.openlocfilehash: 6089e14bd2b13268a03d3600ef8bf78f9afa1c6d
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102206743"
---
# <a name="generic-interfaces-c-programming-guide"></a>Универсальные интерфейсы. (Руководство по программированию на C#)

Часто требуется определить интерфейсы для универсальных классов коллекций или для универсальных классов, представляющих элементы коллекции. Для универсальных классов предпочтительнее использовать универсальные интерфейсы, такие как <xref:System.IComparable%601>, вместо <xref:System.IComparable>, поскольку это позволяет избежать выполнения операция упаковки-преобразования и распаковки-преобразования для типов значений. В библиотеке классов .NET в пространстве имен <xref:System.Collections.Generic> определяется несколько универсальных интерфейсов для работы с классами коллекций.  
  
 Если интерфейс задан в качестве ограничения для параметра типа, можно использовать только типы, реализующие такой интерфейс. В следующем примере кода демонстрируется класс `SortedList<T>`, который является производным от класса `GenericList<T>`. Дополнительные сведения см. в разделе [Введение в универсальные шаблоны](./index.md). `SortedList<T>` добавляет ограничение `where T : IComparable<T>`. Это позволяет методу `BubbleSort` в `SortedList<T>` использовать универсальный метод <xref:System.IComparable%601.CompareTo%2A> в отношении элементов списка. В этом примере элементы списка относятся к простому классу `Person`, который реализует `IComparable<Person>`.  
  
 [!code-csharp[csProgGuideGenerics#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics2.cs#29)]  
  
 В качестве ограничений для одного типа можно задать несколько интерфейсов, как показано ниже:  
  
 [!code-csharp[csProgGuideGenerics#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#30)]  
  
 Интерфейс может определять несколько параметров типа, как показано ниже:  
  
 [!code-csharp[csProgGuideGenerics#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#31)]  
  
 Правила наследования, действующие в отношении классов, также применяются к интерфейсам:  
  
 [!code-csharp[csProgGuideGenerics#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#32)]  
  
 Универсальные интерфейсы могут наследоваться от неуниверсальных интерфейсов, если универсальный интерфейс является ковариантным (то есть использует в качестве возвращаемого значения только свой параметр типа). В библиотеке классов .NET <xref:System.Collections.Generic.IEnumerable%601> наследуется от <xref:System.Collections.IEnumerable>, поскольку <xref:System.Collections.Generic.IEnumerable%601> использует `T` только в возвращаемом значении <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> и в методе считывания свойства <xref:System.Collections.Generic.IEnumerator%601.Current%2A>.  
  
 Конкретные классы могут реализовывать закрытые сконструированные интерфейсы, как показано ниже:  
  
 [!code-csharp[csProgGuideGenerics#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#33)]  
  
 Универсальные классы могут реализовывать универсальные интерфейсы или закрытые сконструированные интерфейсы при условии, что в списке параметров класса заданы все аргументы, требуемые интерфейсом, как показано ниже:  
  
 [!code-csharp[csProgGuideGenerics#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#34)]  
  
 Правила, управляющие перегрузкой методов, одинаковы для методов с универсальными классами, структурами или интерфейсами. Дополнительные сведения см. в разделе [Универсальные методы](./generic-methods.md).  
  
## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../index.md)
- [Введение в универсальные шаблоны](./index.md)
- [interface](../../language-reference/keywords/interface.md)
- [Универсальные шаблоны](../../../standard/generics/index.md)
