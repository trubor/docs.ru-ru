---
description: Дополнительные сведения о новом операторе (Visual Basic)
title: Оператор New
ms.date: 07/20/2015
f1_keywords:
- vb.new
- vb.NewConstraint
helpviewer_keywords:
- constraints, Visual Basic generic types
- generics [Visual Basic], constraints
- constraints, New keyword [Visual Basic]
- New constraint
- New keyword [Visual Basic]
ms.assetid: d7d566d7-fe0e-4336-91f7-641a542de4d0
ms.openlocfilehash: f52dd7606127c7587173de8a78e618ceb3e4681d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665384"
---
# <a name="new-operator-visual-basic"></a><span data-ttu-id="52a8b-103">Оператор New (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52a8b-103">New Operator (Visual Basic)</span></span>

<span data-ttu-id="52a8b-104">Вводит `New` предложение для создания нового экземпляра объекта, задает ограничение конструктора для параметра типа или определяет `Sub` процедуру как конструктор класса.</span><span class="sxs-lookup"><span data-stu-id="52a8b-104">Introduces a `New` clause to create a new object instance, specifies a constructor constraint on a type parameter, or identifies a `Sub` procedure as a class constructor.</span></span>

## <a name="remarks"></a><span data-ttu-id="52a8b-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="52a8b-105">Remarks</span></span>

<span data-ttu-id="52a8b-106">В объявлении или операторе присваивания в `New` предложении необходимо указать определенный класс, из которого можно создать экземпляр.</span><span class="sxs-lookup"><span data-stu-id="52a8b-106">In a declaration or assignment statement, a `New` clause must specify a defined class from which the instance can be created.</span></span> <span data-ttu-id="52a8b-107">Это означает, что класс должен предоставлять один или несколько конструкторов, к которым вызывающий код может получить доступ.</span><span class="sxs-lookup"><span data-stu-id="52a8b-107">This means that the class must expose one or more constructors that the calling code can access.</span></span>

<span data-ttu-id="52a8b-108">Предложение можно использовать `New` в операторе объявления или в операторе присваивания.</span><span class="sxs-lookup"><span data-stu-id="52a8b-108">You can use a `New` clause in a declaration statement or an assignment statement.</span></span> <span data-ttu-id="52a8b-109">При выполнении инструкции вызывается соответствующий конструктор указанного класса, передавая все предоставленные аргументы.</span><span class="sxs-lookup"><span data-stu-id="52a8b-109">When the statement runs, it calls the appropriate constructor of the specified class, passing any arguments you have supplied.</span></span> <span data-ttu-id="52a8b-110">В следующем примере демонстрируется создание экземпляров `Customer` класса, который имеет два конструктора, один из которых не принимает параметры и один принимает строковый параметр:</span><span class="sxs-lookup"><span data-stu-id="52a8b-110">The following example demonstrates this by creating instances of a `Customer` class that has two constructors, one that takes no parameters and one that takes a string parameter:</span></span>

[!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]

<span data-ttu-id="52a8b-111">Поскольку массивы являются классами, `New` может создать новый экземпляр массива, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="52a8b-111">Since arrays are classes, `New` can create a new array instance, as shown in the following example:</span></span>

[!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]

<span data-ttu-id="52a8b-112">Среда CLR выдает <xref:System.OutOfMemoryException> ошибку, если недостаточно памяти для создания нового экземпляра.</span><span class="sxs-lookup"><span data-stu-id="52a8b-112">The common language runtime (CLR) throws an <xref:System.OutOfMemoryException> error if there is insufficient memory to create the new instance.</span></span>

> [!NOTE]
> <span data-ttu-id="52a8b-113">`New`Ключевое слово также используется в списках параметров типов, чтобы указать, что предоставленный тип должен предоставлять доступный конструктор без параметров.</span><span class="sxs-lookup"><span data-stu-id="52a8b-113">The `New` keyword is also used in type parameter lists to specify that the supplied type must expose an accessible parameterless constructor.</span></span> <span data-ttu-id="52a8b-114">Дополнительные сведения о параметрах типа и ограничениях см. в разделе [Type List](../statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="52a8b-114">For more information about type parameters and constraints, see [Type List](../statements/type-list.md).</span></span>

<span data-ttu-id="52a8b-115">Чтобы создать процедуру конструктора для класса, задайте в качестве имени `Sub` процедуры `New` ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="52a8b-115">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="52a8b-116">Дополнительные сведения см. в разделе [время существования объекта: как создаются и уничтожаются объекты](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="52a8b-116">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

<span data-ttu-id="52a8b-117">Ключевое слово `New` можно использовать в следующих контекстах:</span><span class="sxs-lookup"><span data-stu-id="52a8b-117">The `New` keyword can be used in these contexts:</span></span>

- [<span data-ttu-id="52a8b-118">Оператор Dim</span><span class="sxs-lookup"><span data-stu-id="52a8b-118">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="52a8b-119">Окна</span><span class="sxs-lookup"><span data-stu-id="52a8b-119">Of</span></span>](../statements/of-clause.md)
- [<span data-ttu-id="52a8b-120">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="52a8b-120">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="52a8b-121">См. также</span><span class="sxs-lookup"><span data-stu-id="52a8b-121">See also</span></span>

- <xref:System.OutOfMemoryException>
- [<span data-ttu-id="52a8b-122">Ключевые слова</span><span class="sxs-lookup"><span data-stu-id="52a8b-122">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="52a8b-123">Type List</span><span class="sxs-lookup"><span data-stu-id="52a8b-123">Type List</span></span>](../statements/type-list.md)
- [<span data-ttu-id="52a8b-124">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="52a8b-124">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="52a8b-125">Время существования: создание и уничтожение объектов</span><span class="sxs-lookup"><span data-stu-id="52a8b-125">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
