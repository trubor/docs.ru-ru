---
description: 'Дополнительные сведения о: WithEvents (Visual Basic)'
title: WithEvents
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: b27f84fe54aaa10bc9b2359cd74fad3d3ace1ad5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674770"
---
# <a name="withevents-visual-basic"></a><span data-ttu-id="17b4b-103">WithEvents (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17b4b-103">WithEvents (Visual Basic)</span></span>

<span data-ttu-id="17b4b-104">Указывает, что одна или несколько объявленных переменных-членов ссылаются на экземпляр класса, который может создавать события.</span><span class="sxs-lookup"><span data-stu-id="17b4b-104">Specifies that one or more declared member variables refer to an instance of a class that can raise events.</span></span>

## <a name="remarks"></a><span data-ttu-id="17b4b-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="17b4b-105">Remarks</span></span>

<span data-ttu-id="17b4b-106">Если переменная определена с помощью `WithEvents` , можно декларативно указать, что метод обрабатывает события переменной с помощью `Handles` ключевого слова.</span><span class="sxs-lookup"><span data-stu-id="17b4b-106">When a variable is defined using `WithEvents`, you can declaratively specify that a method handles the variable's events using the `Handles` keyword.</span></span>

<span data-ttu-id="17b4b-107">Можно использовать `WithEvents` только на уровне класса или модуля.</span><span class="sxs-lookup"><span data-stu-id="17b4b-107">You can use `WithEvents` only at class or module level.</span></span> <span data-ttu-id="17b4b-108">Это означает, что контекст объявления для `WithEvents` переменной должен быть классом или модулем и не может быть исходным файлом, пространством имен, структурой или процедурой.</span><span class="sxs-lookup"><span data-stu-id="17b4b-108">This means the declaration context for a `WithEvents` variable must be a class or module and cannot be a source file, namespace, structure, or procedure.</span></span>

<span data-ttu-id="17b4b-109">Нельзя использовать `WithEvents` в члене структуры.</span><span class="sxs-lookup"><span data-stu-id="17b4b-109">You cannot use `WithEvents` on a structure member.</span></span>

<span data-ttu-id="17b4b-110">Можно объявлять только отдельные переменные, а не массивы, с помощью `WithEvents` .</span><span class="sxs-lookup"><span data-stu-id="17b4b-110">You can declare only individual variables—not arrays—with `WithEvents`.</span></span>

## <a name="rules"></a><span data-ttu-id="17b4b-111">Правила</span><span class="sxs-lookup"><span data-stu-id="17b4b-111">Rules</span></span>

<span data-ttu-id="17b4b-112">**Типы элементов.**</span><span class="sxs-lookup"><span data-stu-id="17b4b-112">**Element Types.**</span></span> <span data-ttu-id="17b4b-113">Переменные должны быть объявлены как `WithEvents` переменные объекта, чтобы они могли принимать экземпляры класса.</span><span class="sxs-lookup"><span data-stu-id="17b4b-113">You must declare `WithEvents` variables to be object variables so that they can accept class instances.</span></span> <span data-ttu-id="17b4b-114">Однако их нельзя объявить как `Object` .</span><span class="sxs-lookup"><span data-stu-id="17b4b-114">However, you cannot declare them as `Object`.</span></span> <span data-ttu-id="17b4b-115">Их необходимо объявить в качестве конкретного класса, который может вызывать события.</span><span class="sxs-lookup"><span data-stu-id="17b4b-115">You must declare them as the specific class that can raise the events.</span></span>

<span data-ttu-id="17b4b-116">`WithEvents`Модификатор можно использовать в этом контексте: [оператор Dim](../statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="17b4b-116">The `WithEvents` modifier can be used in this context: [Dim Statement](../statements/dim-statement.md)</span></span>

## <a name="example"></a><span data-ttu-id="17b4b-117">Пример</span><span class="sxs-lookup"><span data-stu-id="17b4b-117">Example</span></span>

```vb
Dim WithEvents app As Application
```

## <a name="see-also"></a><span data-ttu-id="17b4b-118">См. также</span><span class="sxs-lookup"><span data-stu-id="17b4b-118">See also</span></span>

- [<span data-ttu-id="17b4b-119">Маркеры</span><span class="sxs-lookup"><span data-stu-id="17b4b-119">Handles</span></span>](../statements/handles-clause.md)
- [<span data-ttu-id="17b4b-120">Ключевые слова</span><span class="sxs-lookup"><span data-stu-id="17b4b-120">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="17b4b-121">События</span><span class="sxs-lookup"><span data-stu-id="17b4b-121">Events</span></span>](../../programming-guide/language-features/events/index.md)
