---
description: 'Дополнительные сведения о: BC30982: тип " <variablename> " не может быть определен, так как границы цикла и переменная шага не расширяются до того же типа.'
title: Тип <variablename> не может быть выведен, поскольку для границ цикла и переменной шага нет расширяющего преобразования к одному типу
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: 399e021500813127df6ecede2534783df09ac8dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641165"
---
# <a name="bc30982-type-of-variablename-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a><span data-ttu-id="4a657-103">BC30982: тип " \<variablename> " не может быть определен, так как границы цикла и переменная шага не расширяются до того же типа</span><span class="sxs-lookup"><span data-stu-id="4a657-103">BC30982: Type of '\<variablename>' cannot be inferred because the loop bounds and the step variable do not widen to the same type</span></span>

<span data-ttu-id="4a657-104">Вы написали `For...Next` цикл, в котором компилятор не может определить тип данных для управляющей переменной цикла, так как выполняются следующие условия.</span><span class="sxs-lookup"><span data-stu-id="4a657-104">You have written a `For...Next` loop in which the compiler cannot infer a data type for the loop control variable because the following conditions are true:</span></span>

- <span data-ttu-id="4a657-105">Тип данных управляющей переменной цикла не указан с помощью выражения `As` .</span><span class="sxs-lookup"><span data-stu-id="4a657-105">The data type of the loop control variable is not specified with an `As` clause.</span></span>

- <span data-ttu-id="4a657-106">Границы цикла и переменная шага содержат по крайней мере два типа данных.</span><span class="sxs-lookup"><span data-stu-id="4a657-106">The loop bounds and step variable contain at least two data types.</span></span>

- <span data-ttu-id="4a657-107">Между типами данных не существует стандартных преобразований.</span><span class="sxs-lookup"><span data-stu-id="4a657-107">No standard conversions exist between the data types.</span></span>

 <span data-ttu-id="4a657-108">Таким образом, компилятор не может определить тип данных управляющей переменной цикла.</span><span class="sxs-lookup"><span data-stu-id="4a657-108">Therefore, the compiler cannot infer the data type of a loop's control variable.</span></span>

 <span data-ttu-id="4a657-109">В следующем примере переменная шага является символом, а границы цикла — обоими целыми числами.</span><span class="sxs-lookup"><span data-stu-id="4a657-109">In the following example, the step variable is a character and the loop bounds are both integers.</span></span> <span data-ttu-id="4a657-110">Так как нет стандартного преобразования между символами и целыми числами, возникает эта ошибка.</span><span class="sxs-lookup"><span data-stu-id="4a657-110">Because there is no standard conversion between characters and integers, this error is reported.</span></span>

```vb
Dim stepVar = "1"c
Dim m = 0
Dim n = 20

' Not valid.
' For i = 1 To 10 Step stepVar
    ' Loop processing
' Next
```

<span data-ttu-id="4a657-111">**Идентификатор ошибки:** BC30982</span><span class="sxs-lookup"><span data-stu-id="4a657-111">**Error ID:** BC30982</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="4a657-112">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="4a657-112">To correct this error</span></span>

- <span data-ttu-id="4a657-113">При необходимости измените типы границ цикла и переменной шага, чтобы по крайней мере один из них был типом, расширяющимся в.</span><span class="sxs-lookup"><span data-stu-id="4a657-113">Change the types of the loop bounds and step variable as necessary so that at least one of them is a type that the others widen to.</span></span> <span data-ttu-id="4a657-114">В предыдущем примере измените тип `stepVar` на `Integer` .</span><span class="sxs-lookup"><span data-stu-id="4a657-114">In the preceding example, change the type of `stepVar` to `Integer`.</span></span>

  ```vb
  Dim stepVar = 1
  ```

  <span data-ttu-id="4a657-115">-или-</span><span class="sxs-lookup"><span data-stu-id="4a657-115">-or-</span></span>

  ```vb
  Dim stepVar As Integer = 1
  ```

- <span data-ttu-id="4a657-116">Используйте явные функции преобразования для преобразования границ цикла и переменной Step в соответствующие типы.</span><span class="sxs-lookup"><span data-stu-id="4a657-116">Use explicit conversion functions to convert the loop bounds and step variable to the appropriate types.</span></span> <span data-ttu-id="4a657-117">В предыдущем примере примените `Val` функцию к `stepVar` .</span><span class="sxs-lookup"><span data-stu-id="4a657-117">In the preceding example, apply the `Val` function to `stepVar`.</span></span>

  ```vb
  For i = 1 To 10 Step Val(stepVar)
      ' Loop processing
  Next
  ```

## <a name="see-also"></a><span data-ttu-id="4a657-118">См. также</span><span class="sxs-lookup"><span data-stu-id="4a657-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [<span data-ttu-id="4a657-119">Оператор For…Next</span><span class="sxs-lookup"><span data-stu-id="4a657-119">For...Next Statement</span></span>](../statements/for-next-statement.md)
- [<span data-ttu-id="4a657-120">Явные и неявные преобразования</span><span class="sxs-lookup"><span data-stu-id="4a657-120">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="4a657-121">Вывод локального типа</span><span class="sxs-lookup"><span data-stu-id="4a657-121">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="4a657-122">Оператор Option Infer</span><span class="sxs-lookup"><span data-stu-id="4a657-122">Option Infer Statement</span></span>](../statements/option-infer-statement.md)
- [<span data-ttu-id="4a657-123">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="4a657-123">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="4a657-124">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="4a657-124">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
