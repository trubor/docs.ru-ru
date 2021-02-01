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
ms.openlocfilehash: db26b26ebcc51b57fdbe58ddaf92e5019cb69659
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899390"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="b40fa-103">Практическое руководство. Создание конструктора копий (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="b40fa-103">How to write a copy constructor (C# Programming Guide)</span></span>

<span data-ttu-id="b40fa-104">В C# не предусмотрен конструктор копии для объектов, однако его можно написать самостоятельно.</span><span class="sxs-lookup"><span data-stu-id="b40fa-104">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b40fa-105">Пример</span><span class="sxs-lookup"><span data-stu-id="b40fa-105">Example</span></span>  

 <span data-ttu-id="b40fa-106">В следующем примере [класс](../../language-reference/keywords/class.md)`Person` определяет конструктор копии, который использует экземпляр `Person`в качестве аргумента.</span><span class="sxs-lookup"><span data-stu-id="b40fa-106">In the following example, the `Person`[class](../../language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="b40fa-107">Значения свойств аргумента присваиваются свойствам нового экземпляра `Person`.</span><span class="sxs-lookup"><span data-stu-id="b40fa-107">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="b40fa-108">Код содержит дополнительный конструктор копии, который отправляет свойства `Name` и `Age` экземпляра, который необходимо скопировать конструктору экземпляра класса.</span><span class="sxs-lookup"><span data-stu-id="b40fa-108">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[CopyConstructor](snippets/how-to-write-a-copy-constructor/Program.cs)]
  
## <a name="see-also"></a><span data-ttu-id="b40fa-109">См. также</span><span class="sxs-lookup"><span data-stu-id="b40fa-109">See also</span></span>

- <xref:System.ICloneable>
- [<span data-ttu-id="b40fa-110">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="b40fa-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b40fa-111">Классы и структуры</span><span class="sxs-lookup"><span data-stu-id="b40fa-111">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="b40fa-112">Конструкторы</span><span class="sxs-lookup"><span data-stu-id="b40fa-112">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="b40fa-113">Методы завершения</span><span class="sxs-lookup"><span data-stu-id="b40fa-113">Finalizers</span></span>](./destructors.md)
