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
ms.openlocfilehash: c61018444dd600d6f33765b104034355d0301667
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255240"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="ac600-103">Практическое руководство. Создание конструктора копий (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="ac600-103">How to write a copy constructor (C# Programming Guide)</span></span>

<span data-ttu-id="ac600-104">Для [записей](records.md) C# предоставляет конструктор копирования для объектов, но для классов его необходимо писать самостоятельно.</span><span class="sxs-lookup"><span data-stu-id="ac600-104">C# [records](records.md) provide a copy constructor for objects, but for classes you have to write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac600-105">Пример</span><span class="sxs-lookup"><span data-stu-id="ac600-105">Example</span></span>  

 <span data-ttu-id="ac600-106">В следующем примере [класс](../../language-reference/keywords/class.md)`Person` определяет конструктор копии, который использует экземпляр `Person`в качестве аргумента.</span><span class="sxs-lookup"><span data-stu-id="ac600-106">In the following example, the `Person`[class](../../language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="ac600-107">Значения свойств аргумента присваиваются свойствам нового экземпляра `Person`.</span><span class="sxs-lookup"><span data-stu-id="ac600-107">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="ac600-108">Код содержит дополнительный конструктор копии, который отправляет свойства `Name` и `Age` экземпляра, который необходимо скопировать конструктору экземпляра класса.</span><span class="sxs-lookup"><span data-stu-id="ac600-108">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[CopyConstructor](snippets/how-to-write-a-copy-constructor/Program.cs)]

## <a name="see-also"></a><span data-ttu-id="ac600-109">См. также</span><span class="sxs-lookup"><span data-stu-id="ac600-109">See also</span></span>

- <xref:System.ICloneable>
- [<span data-ttu-id="ac600-110">Записи</span><span class="sxs-lookup"><span data-stu-id="ac600-110">Records</span></span>](records.md)
- [<span data-ttu-id="ac600-111">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="ac600-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ac600-112">Классы и структуры</span><span class="sxs-lookup"><span data-stu-id="ac600-112">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="ac600-113">Конструкторы</span><span class="sxs-lookup"><span data-stu-id="ac600-113">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="ac600-114">Методы завершения</span><span class="sxs-lookup"><span data-stu-id="ac600-114">Finalizers</span></span>](./destructors.md)
