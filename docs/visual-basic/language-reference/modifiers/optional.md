---
description: 'Дополнительные сведения: необязательно (Visual Basic)'
title: Необязательно
ms.date: 07/20/2015
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
ms.openlocfilehash: d9a61371364d87745203363dbc0a641cec9660a2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666086"
---
# <a name="optional-visual-basic"></a><span data-ttu-id="7f630-103">Optional (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f630-103">Optional (Visual Basic)</span></span>

<span data-ttu-id="7f630-104">Указывает, что аргумент процедуры может быть пропущен при вызове процедуры.</span><span class="sxs-lookup"><span data-stu-id="7f630-104">Specifies that a procedure argument can be omitted when the procedure is called.</span></span>

## <a name="remarks"></a><span data-ttu-id="7f630-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="7f630-105">Remarks</span></span>

<span data-ttu-id="7f630-106">Для каждого необязательного параметра необходимо указать константное выражение в качестве значения по умолчанию для этого параметра.</span><span class="sxs-lookup"><span data-stu-id="7f630-106">For each optional parameter, you must specify a constant expression as the default value of that parameter.</span></span> <span data-ttu-id="7f630-107">Если результат вычисления выражения равен [Nothing](../nothing.md), в качестве значения по умолчанию для параметра используется значение по умолчанию типа данных value.</span><span class="sxs-lookup"><span data-stu-id="7f630-107">If the expression evaluates to [Nothing](../nothing.md), the default value of the value data type is used as the default value of the parameter.</span></span>

<span data-ttu-id="7f630-108">Если список параметров содержит необязательный параметр, то каждый параметр, следующий за ним, также должен быть необязательным.</span><span class="sxs-lookup"><span data-stu-id="7f630-108">If the parameter list contains an optional parameter, every parameter that follows it must also be optional.</span></span>

<span data-ttu-id="7f630-109">Модификатор `Optional` можно использовать в следующих контекстах:</span><span class="sxs-lookup"><span data-stu-id="7f630-109">The `Optional` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="7f630-110">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="7f630-110">Declare Statement</span></span>](../statements/declare-statement.md)

- [<span data-ttu-id="7f630-111">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="7f630-111">Function Statement</span></span>](../statements/function-statement.md)

- [<span data-ttu-id="7f630-112">Property Statement</span><span class="sxs-lookup"><span data-stu-id="7f630-112">Property Statement</span></span>](../statements/property-statement.md)

- [<span data-ttu-id="7f630-113">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="7f630-113">Sub Statement</span></span>](../statements/sub-statement.md)

> [!NOTE]
> <span data-ttu-id="7f630-114">При вызове процедуры с необязательными параметрами или без них можно передавать аргументы по положению или по имени.</span><span class="sxs-lookup"><span data-stu-id="7f630-114">When calling a procedure with or without optional parameters, you can pass arguments by position or by name.</span></span> <span data-ttu-id="7f630-115">Дополнительные сведения см. в разделе [Передача аргументов по положению и по имени](../../programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="7f630-115">For more information, see [Passing Arguments by Position and by Name](../../programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span></span>

> [!NOTE]
> <span data-ttu-id="7f630-116">Можно также определить процедуру с необязательными параметрами с помощью перегрузки.</span><span class="sxs-lookup"><span data-stu-id="7f630-116">You can also define a procedure with optional parameters by using overloading.</span></span> <span data-ttu-id="7f630-117">Если имеется один необязательный параметр, можно определить две перегруженные версии процедуры, одна из которых принимает параметр, а другая — нет.</span><span class="sxs-lookup"><span data-stu-id="7f630-117">If you have one optional parameter, you can define two overloaded versions of the procedure, one that accepts the parameter and one that doesn’t.</span></span> <span data-ttu-id="7f630-118">Дополнительные сведения см. в разделе [Procedure Overloading](../../programming-guide/language-features/procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="7f630-118">For more information, see [Procedure Overloading](../../programming-guide/language-features/procedures/procedure-overloading.md).</span></span>

## <a name="example"></a><span data-ttu-id="7f630-119">Пример</span><span class="sxs-lookup"><span data-stu-id="7f630-119">Example</span></span>

<span data-ttu-id="7f630-120">В следующем примере определяется процедура, имеющая необязательный параметр.</span><span class="sxs-lookup"><span data-stu-id="7f630-120">The following example defines a procedure that has an optional parameter.</span></span>

```vb
Public Function FindMatches(ByRef values As List(Of String),
                            ByVal searchString As String,
                            Optional ByVal matchCase As Boolean = False) As List(Of String)

    Dim results As IEnumerable(Of String)

    If matchCase Then
        results = From v In values
                  Where v.Contains(searchString)
    Else
        results = From v In values
                  Where UCase(v).Contains(UCase(searchString))
    End If

    Return results.ToList()
End Function
```

## <a name="example"></a><span data-ttu-id="7f630-121">Пример</span><span class="sxs-lookup"><span data-stu-id="7f630-121">Example</span></span>

<span data-ttu-id="7f630-122">В следующем примере показано, как вызвать процедуру с аргументами, передаваемыми по положению, и с аргументами, передаваемыми по имени.</span><span class="sxs-lookup"><span data-stu-id="7f630-122">The following example demonstrates how to call a procedure with arguments passed by position and with arguments passed by name.</span></span> <span data-ttu-id="7f630-123">Процедура имеет два необязательных параметра.</span><span class="sxs-lookup"><span data-stu-id="7f630-123">The procedure has two optional parameters.</span></span>

[!code-vb[VbVbalrKeywords#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class8.vb#21)]

## <a name="see-also"></a><span data-ttu-id="7f630-124">См. также</span><span class="sxs-lookup"><span data-stu-id="7f630-124">See also</span></span>

- [<span data-ttu-id="7f630-125">Список параметров</span><span class="sxs-lookup"><span data-stu-id="7f630-125">Parameter List</span></span>](../statements/parameter-list.md)
- [<span data-ttu-id="7f630-126">Необязательные параметры</span><span class="sxs-lookup"><span data-stu-id="7f630-126">Optional Parameters</span></span>](../../programming-guide/language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="7f630-127">Ключевые слова</span><span class="sxs-lookup"><span data-stu-id="7f630-127">Keywords</span></span>](../keywords/index.md)
