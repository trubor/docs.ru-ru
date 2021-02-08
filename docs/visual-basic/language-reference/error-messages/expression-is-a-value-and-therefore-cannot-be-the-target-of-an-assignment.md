---
description: 'Дополнительные сведения о: BC30068: Expression является значением и поэтому не может быть целью назначения'
title: Нельзя присвоить значение выражению, поскольку оно является значением
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: 424ce9cb0183153454bc068e9da940948b737c47
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796370"
---
# <a name="bc30068-expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a><span data-ttu-id="95c88-103">BC30068: выражение является значением и поэтому не может быть целью назначения</span><span class="sxs-lookup"><span data-stu-id="95c88-103">BC30068: Expression is a value and therefore cannot be the target of an assignment</span></span>

<span data-ttu-id="95c88-104">Оператор пытается присвоить значение выражению.</span><span class="sxs-lookup"><span data-stu-id="95c88-104">A statement attempts to assign a value to an expression.</span></span> <span data-ttu-id="95c88-105">Значение можно назначить только переменной с возможностью записи, свойству или элементу массива во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="95c88-105">You can assign a value only to a writable variable, property, or array element at run time.</span></span> <span data-ttu-id="95c88-106">В следующем примере показано, как может произойти эта ошибка.</span><span class="sxs-lookup"><span data-stu-id="95c88-106">The following example illustrates how this error can occur.</span></span>

```vb
Dim yesterday As Integer
ReadOnly maximum As Integer = 45
yesterday + 1 = DatePart(DateInterval.Day, Now)
' The preceding line is an ERROR because of an expression on the left.
maximum = 50
' The preceding line is an ERROR because maximum is declared ReadOnly.
```

<span data-ttu-id="95c88-107">Аналогичные примеры могут применяться к свойствам и элементам массива.</span><span class="sxs-lookup"><span data-stu-id="95c88-107">Similar examples could apply to properties and array elements.</span></span>

<span data-ttu-id="95c88-108">**Косвенный доступ.**</span><span class="sxs-lookup"><span data-stu-id="95c88-108">**Indirect Access.**</span></span> <span data-ttu-id="95c88-109">Непрямой доступ через тип значения может также вызвать эту ошибку.</span><span class="sxs-lookup"><span data-stu-id="95c88-109">Indirect access through a value type can also generate this error.</span></span> <span data-ttu-id="95c88-110">Рассмотрим следующий пример кода, который пытается задать значение <xref:System.Drawing.Point> путем прямого доступа к нему через <xref:System.Windows.Forms.Control.Location%2A> .</span><span class="sxs-lookup"><span data-stu-id="95c88-110">Consider the following code example, which attempts to set the value of <xref:System.Drawing.Point> by accessing it indirectly through <xref:System.Windows.Forms.Control.Location%2A>.</span></span>

```vb
' Assume this code runs inside Form1.
Dim exitButton As New System.Windows.Forms.Button()
exitButton.Text = "Exit this form"
exitButton.Location.X = 140
' The preceding line is an ERROR because of no storage for Location.
```

<span data-ttu-id="95c88-111">Последняя инструкция из предыдущего примера завершается сбоем, так как создает только временное выделение для <xref:System.Drawing.Point> структуры, возвращаемой <xref:System.Windows.Forms.Control.Location%2A> свойством.</span><span class="sxs-lookup"><span data-stu-id="95c88-111">The last statement of the preceding example fails because it creates only a temporary allocation for the <xref:System.Drawing.Point> structure returned by the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span> <span data-ttu-id="95c88-112">Структура является типом значения, а временная структура не сохраняется после выполнения инструкции.</span><span class="sxs-lookup"><span data-stu-id="95c88-112">A structure is a value type, and the temporary structure is not retained after the statement runs.</span></span> <span data-ttu-id="95c88-113">Проблема решается путем объявления и использования переменной для <xref:System.Windows.Forms.Control.Location%2A> , которая создает более постоянное выделение для <xref:System.Drawing.Point> структуры.</span><span class="sxs-lookup"><span data-stu-id="95c88-113">The problem is resolved by declaring and using a variable for <xref:System.Windows.Forms.Control.Location%2A>, which creates a more permanent allocation for the <xref:System.Drawing.Point> structure.</span></span> <span data-ttu-id="95c88-114">В следующем примере показан код, который может заменить последнюю инструкцию из предыдущего примера.</span><span class="sxs-lookup"><span data-stu-id="95c88-114">The following example shows code that can replace the last statement of the preceding example.</span></span>

```vb
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)
exitButton.Location = exitLocation
```

<span data-ttu-id="95c88-115">**Идентификатор ошибки:** BC30068</span><span class="sxs-lookup"><span data-stu-id="95c88-115">**Error ID:** BC30068</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="95c88-116">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="95c88-116">To correct this error</span></span>

- <span data-ttu-id="95c88-117">Если оператор присваивает значение выражению, замените выражение одной записываемой переменной, свойством или элементом массива.</span><span class="sxs-lookup"><span data-stu-id="95c88-117">If the statement assigns a value to an expression, replace the expression with a single writable variable, property, or array element.</span></span>

- <span data-ttu-id="95c88-118">Если инструкция делает косвенный доступ через тип значения (обычно это структура), создайте переменную для хранения типа значения.</span><span class="sxs-lookup"><span data-stu-id="95c88-118">If the statement makes indirect access through a value type (usually a structure), create a variable to hold the value type.</span></span>

- <span data-ttu-id="95c88-119">Назначьте переменной соответствующую структуру (или другой тип значения).</span><span class="sxs-lookup"><span data-stu-id="95c88-119">Assign the appropriate structure (or other value type) to the variable.</span></span>

- <span data-ttu-id="95c88-120">Используйте переменную для доступа к свойству, чтобы присвоить ему значение.</span><span class="sxs-lookup"><span data-stu-id="95c88-120">Use the variable to access the property to assign it a value.</span></span>

## <a name="see-also"></a><span data-ttu-id="95c88-121">См. также</span><span class="sxs-lookup"><span data-stu-id="95c88-121">See also</span></span>

- [<span data-ttu-id="95c88-122">Операторы и выражения</span><span class="sxs-lookup"><span data-stu-id="95c88-122">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="95c88-123">Операторы</span><span class="sxs-lookup"><span data-stu-id="95c88-123">Statements</span></span>](../../programming-guide/language-features/statements.md)
- [<span data-ttu-id="95c88-124">Рекомендации по устранению неполадок</span><span class="sxs-lookup"><span data-stu-id="95c88-124">Troubleshooting Procedures</span></span>](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
