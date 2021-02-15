---
description: Дополнительные сведения см. в статье как объявить структуру (Visual Basic)
title: Практическое руководство. Объявление структуры
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: 7560f22db70fd5804ca309720d32477bcb9a3782
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100436933"
---
# <a name="how-to-declare-a-structure-visual-basic"></a><span data-ttu-id="a7c8f-103">Практическое руководство. Объявление структуры (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7c8f-103">How to: Declare a Structure (Visual Basic)</span></span>

<span data-ttu-id="a7c8f-104">Объявление структуры начинается с [оператора Structure](../../../language-reference/statements/structure-statement.md)и заканчивается `End Structure` инструкцией.</span><span class="sxs-lookup"><span data-stu-id="a7c8f-104">You begin a structure declaration with the [Structure Statement](../../../language-reference/statements/structure-statement.md), and you end it with the `End Structure` statement.</span></span> <span data-ttu-id="a7c8f-105">Между этими двумя операторами необходимо объявить хотя бы один *элемент*.</span><span class="sxs-lookup"><span data-stu-id="a7c8f-105">Between these two statements you must declare at least one *element*.</span></span> <span data-ttu-id="a7c8f-106">Элементы могут иметь любой тип данных, но хотя бы один из них должен быть либо необщей переменной, либо нестандартным, ненастраиваемым событием.</span><span class="sxs-lookup"><span data-stu-id="a7c8f-106">The elements can be of any data type, but at least one must be either a nonshared variable or a nonshared, noncustom event.</span></span>  
  
 <span data-ttu-id="a7c8f-107">Нельзя инициализировать какие либо элементы структуры в объявлении структуры.</span><span class="sxs-lookup"><span data-stu-id="a7c8f-107">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="a7c8f-108">При объявлении переменной, имеющей тип структуры, необходимо назначить значения элементам, обращаясь к ним через переменную.</span><span class="sxs-lookup"><span data-stu-id="a7c8f-108">When you declare a variable to be of a structure type, you assign values to the elements by accessing them through the variable.</span></span>  
  
 <span data-ttu-id="a7c8f-109">Обсуждение различий между структурами и классами см. в разделе [структуры и классы](structures-and-classes.md).</span><span class="sxs-lookup"><span data-stu-id="a7c8f-109">For a discussion of the differences between structures and classes, see [Structures and Classes](structures-and-classes.md).</span></span>  
  
 <span data-ttu-id="a7c8f-110">В демонстрационных целях рассмотрим ситуацию, когда необходимо отследить имя сотрудника, телефонное расширение и заработную плату.</span><span class="sxs-lookup"><span data-stu-id="a7c8f-110">For demonstration purposes, consider a situation where you want to keep track of an employee's name, telephone extension, and salary.</span></span> <span data-ttu-id="a7c8f-111">Структура позволяет сделать это в одной переменной.</span><span class="sxs-lookup"><span data-stu-id="a7c8f-111">A structure allows you to do this in a single variable.</span></span>  
  
### <a name="to-declare-a-structure"></a><span data-ttu-id="a7c8f-112">Объявление структуры</span><span class="sxs-lookup"><span data-stu-id="a7c8f-112">To declare a structure</span></span>  
  
1. <span data-ttu-id="a7c8f-113">Создайте начальную и конечную инструкции для структуры.</span><span class="sxs-lookup"><span data-stu-id="a7c8f-113">Create the beginning and ending statements for the structure.</span></span>  
  
     <span data-ttu-id="a7c8f-114">Можно указать уровень доступа структуры с помощью ключевого слова [Public](../../../language-reference/modifiers/public.md), [protected](../../../language-reference/modifiers/protected.md), [Friend](../../../language-reference/modifiers/friend.md)или [Private](../../../language-reference/modifiers/private.md) , либо можно разрешить по умолчанию использовать `Public` .</span><span class="sxs-lookup"><span data-stu-id="a7c8f-114">You can specify the access level of a structure using the [Public](../../../language-reference/modifiers/public.md), [Protected](../../../language-reference/modifiers/protected.md), [Friend](../../../language-reference/modifiers/friend.md), or [Private](../../../language-reference/modifiers/private.md) keyword, or you can let it default to `Public`.</span></span>  
  
    ```vb  
    Private Structure employee  
    End Structure  
    ```  
  
2. <span data-ttu-id="a7c8f-115">Добавьте элементы в текст структуры.</span><span class="sxs-lookup"><span data-stu-id="a7c8f-115">Add elements to the body of the structure.</span></span>  
  
     <span data-ttu-id="a7c8f-116">Структура должна содержать по крайней мере один элемент.</span><span class="sxs-lookup"><span data-stu-id="a7c8f-116">A structure must have at least one element.</span></span> <span data-ttu-id="a7c8f-117">Необходимо объявить каждый элемент и указать для него уровень доступа.</span><span class="sxs-lookup"><span data-stu-id="a7c8f-117">You must declare every element and specify an access level for it.</span></span> <span data-ttu-id="a7c8f-118">Если вы используете [инструкцию Dim](../../../language-reference/statements/dim-statement.md) без ключевых слов, для специальных возможностей по умолчанию используется значение `Public` .</span><span class="sxs-lookup"><span data-stu-id="a7c8f-118">If you use the [Dim Statement](../../../language-reference/statements/dim-statement.md) without any keywords, the accessibility defaults to `Public`.</span></span>  
  
    ```vb  
    Private Structure employee  
        Public givenName As String  
        Public familyName As String  
        Public phoneExtension As Long  
        Private salary As Decimal  
        Public Sub giveRaise(raise As Double)  
            salary *= raise  
        End Sub  
        Public Event salaryReviewTime()  
    End Structure  
    ```  
  
     <span data-ttu-id="a7c8f-119">`salary`Поле в предыдущем примере имеет значение `Private` , которое означает, что оно недоступно за пределами структуры, даже из содержащего класса.</span><span class="sxs-lookup"><span data-stu-id="a7c8f-119">The `salary` field in the preceding example is `Private`, which means it is inaccessible outside the structure, even from the containing class.</span></span> <span data-ttu-id="a7c8f-120">Однако `giveRaise` процедура является `Public` , поэтому ее можно вызывать извне структуры.</span><span class="sxs-lookup"><span data-stu-id="a7c8f-120">However, the `giveRaise` procedure is `Public`, so it can be called from outside the structure.</span></span> <span data-ttu-id="a7c8f-121">Аналогичным образом можно вызвать `salaryReviewTime` событие за пределами структуры.</span><span class="sxs-lookup"><span data-stu-id="a7c8f-121">Similarly, you can raise the `salaryReviewTime` event from outside the structure.</span></span>  
  
     <span data-ttu-id="a7c8f-122">Помимо переменных, процедур и `Sub` событий, в структуре можно также определять константы, `Function` процедуры и свойства.</span><span class="sxs-lookup"><span data-stu-id="a7c8f-122">In addition to variables, `Sub` procedures, and events, you can also define constants, `Function` procedures, and properties in a structure.</span></span> <span data-ttu-id="a7c8f-123">Можно назначить не более одного свойства в качестве *свойства по умолчанию* при условии, что оно принимает по крайней мере один аргумент.</span><span class="sxs-lookup"><span data-stu-id="a7c8f-123">You can designate at most one property as the *default property*, provided it takes at least one argument.</span></span> <span data-ttu-id="a7c8f-124">Можно выполнить обработку события с помощью [общей](../../../language-reference/modifiers/shared.md) `Sub` процедуры.</span><span class="sxs-lookup"><span data-stu-id="a7c8f-124">You can handle an event with a [Shared](../../../language-reference/modifiers/shared.md)`Sub` procedure.</span></span> <span data-ttu-id="a7c8f-125">Дополнительные сведения см. в разделе [инструкции. объявление и вызов свойства по умолчанию в Visual Basic](../procedures/how-to-declare-and-call-a-default-property.md).</span><span class="sxs-lookup"><span data-stu-id="a7c8f-125">For more information, see [How to: Declare and Call a Default Property in Visual Basic](../procedures/how-to-declare-and-call-a-default-property.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7c8f-126">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a7c8f-126">See also</span></span>

- [<span data-ttu-id="a7c8f-127">Типы данных</span><span class="sxs-lookup"><span data-stu-id="a7c8f-127">Data Types</span></span>](index.md)
- [<span data-ttu-id="a7c8f-128">Простые типы данных</span><span class="sxs-lookup"><span data-stu-id="a7c8f-128">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="a7c8f-129">Составные типы данных</span><span class="sxs-lookup"><span data-stu-id="a7c8f-129">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="a7c8f-130">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="a7c8f-130">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="a7c8f-131">Структуры</span><span class="sxs-lookup"><span data-stu-id="a7c8f-131">Structures</span></span>](structures.md)
- [<span data-ttu-id="a7c8f-132">Устранение неполадок, связанных с типами данных</span><span class="sxs-lookup"><span data-stu-id="a7c8f-132">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="a7c8f-133">Переменные структуры</span><span class="sxs-lookup"><span data-stu-id="a7c8f-133">Structure Variables</span></span>](structure-variables.md)
- [<span data-ttu-id="a7c8f-134">Структуры и другие элементы программирования</span><span class="sxs-lookup"><span data-stu-id="a7c8f-134">Structures and Other Programming Elements</span></span>](structures-and-other-programming-elements.md)
- [<span data-ttu-id="a7c8f-135">Структуры и классы</span><span class="sxs-lookup"><span data-stu-id="a7c8f-135">Structures and Classes</span></span>](structures-and-classes.md)
- [<span data-ttu-id="a7c8f-136">Тип данных, определенный пользователем</span><span class="sxs-lookup"><span data-stu-id="a7c8f-136">User-Defined Data Type</span></span>](../../../language-reference/data-types/user-defined-data-type.md)
