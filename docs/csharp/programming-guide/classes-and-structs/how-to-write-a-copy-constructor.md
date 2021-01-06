---
title: Практическое руководство. Создание конструктора копий (руководство по программированию на C#)
description: Узнайте, как создать конструктор копий в C#, который принимает экземпляр класса и возвращает новый экземпляр со значениями входных данных.
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: dfc702bfe183b3712b20c64f9e82d2d3c3edd6d5
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512376"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="61cf0-103">Практическое руководство. Создание конструктора копий (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="61cf0-103">How to write a copy constructor (C# Programming Guide)</span></span>

<span data-ttu-id="61cf0-104">В C# не предусмотрен конструктор копии для объектов, однако его можно написать самостоятельно.</span><span class="sxs-lookup"><span data-stu-id="61cf0-104">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61cf0-105">Пример</span><span class="sxs-lookup"><span data-stu-id="61cf0-105">Example</span></span>  

 <span data-ttu-id="61cf0-106">В следующем примере [класс](../../language-reference/keywords/class.md)`Person` определяет конструктор копии, который использует экземпляр `Person`в качестве аргумента.</span><span class="sxs-lookup"><span data-stu-id="61cf0-106">In the following example, the `Person`[class](../../language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="61cf0-107">Значения свойств аргумента присваиваются свойствам нового экземпляра `Person`.</span><span class="sxs-lookup"><span data-stu-id="61cf0-107">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="61cf0-108">Код содержит дополнительный конструктор копии, который отправляет свойства `Name` и `Age` экземпляра, который необходимо скопировать конструктору экземпляра класса.</span><span class="sxs-lookup"><span data-stu-id="61cf0-108">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a><span data-ttu-id="61cf0-109">См. также</span><span class="sxs-lookup"><span data-stu-id="61cf0-109">See also</span></span>

- <xref:System.ICloneable>
- [<span data-ttu-id="61cf0-110">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="61cf0-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="61cf0-111">Классы и структуры</span><span class="sxs-lookup"><span data-stu-id="61cf0-111">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="61cf0-112">Конструкторы</span><span class="sxs-lookup"><span data-stu-id="61cf0-112">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="61cf0-113">Методы завершения</span><span class="sxs-lookup"><span data-stu-id="61cf0-113">Finalizers</span></span>](./destructors.md)
