---
description: 'Дополнительные сведения о: BC36635: лямбда-выражения недопустимы в первом выражении оператора Select Case'
title: Лямбда-выражения недопустимы в первом выражении оператора Select Case
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: e0c388db7164f6c9f99ba917109593a796f7b23b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795941"
---
# <a name="bc36635-lambda-expressions-are-not-valid-in-the-first-expression-of-a-select-case-statement"></a><span data-ttu-id="6ecd7-103">BC36635: лямбда-выражения недопустимы в первом выражении оператора Select Case</span><span class="sxs-lookup"><span data-stu-id="6ecd7-103">BC36635: Lambda expressions are not valid in the first expression of a 'Select Case' statement</span></span>

<span data-ttu-id="6ecd7-104">Нельзя использовать лямбда-выражение для тестового выражения в `Select Case` инструкции.</span><span class="sxs-lookup"><span data-stu-id="6ecd7-104">You cannot use a lambda expression for the test expression in a `Select Case` statement.</span></span> <span data-ttu-id="6ecd7-105">Определения лямбда-выражений возвращают функции, а тестовое выражение `Select Case` инструкции должно иметь простейший тип данных.</span><span class="sxs-lookup"><span data-stu-id="6ecd7-105">Lambda expression definitions return functions, and the test expression of a `Select Case` statement must be an elementary data type.</span></span>

 <span data-ttu-id="6ecd7-106">Следующий код вызывает эту ошибку:</span><span class="sxs-lookup"><span data-stu-id="6ecd7-106">The following code causes this error:</span></span>

```vb
' Select Case (Function(arg) arg Is Nothing)
    ' List of the cases.
' End Select
```

 <span data-ttu-id="6ecd7-107">**Идентификатор ошибки:** BC36635</span><span class="sxs-lookup"><span data-stu-id="6ecd7-107">**Error ID:** BC36635</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="6ecd7-108">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="6ecd7-108">To correct this error</span></span>

- <span data-ttu-id="6ecd7-109">Проверьте свой код, чтобы определить, подойдет ли вам другая условная конструкция, например оператор `If...Then...Else` .</span><span class="sxs-lookup"><span data-stu-id="6ecd7-109">Examine your code to determine whether a different conditional construction, such as an `If...Then...Else` statement, would work for you.</span></span>

- <span data-ttu-id="6ecd7-110">Возможно, вы предполагали вызвать функцию, как показано в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="6ecd7-110">You may have intended to call the function, as shown in the following code:</span></span>

```vb
Dim num? As Integer
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))
    ' List of the cases
End Select
```

## <a name="see-also"></a><span data-ttu-id="6ecd7-111">См. также</span><span class="sxs-lookup"><span data-stu-id="6ecd7-111">See also</span></span>

- [<span data-ttu-id="6ecd7-112">Лямбда-выражения</span><span class="sxs-lookup"><span data-stu-id="6ecd7-112">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="6ecd7-113">Оператор If…Then…Else</span><span class="sxs-lookup"><span data-stu-id="6ecd7-113">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
- [<span data-ttu-id="6ecd7-114">Оператор Select…Case</span><span class="sxs-lookup"><span data-stu-id="6ecd7-114">Select...Case Statement</span></span>](../statements/select-case-statement.md)
