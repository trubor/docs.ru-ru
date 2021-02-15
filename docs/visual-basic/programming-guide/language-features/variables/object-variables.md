---
description: 'Подробнее: объектные переменные в Visual Basic'
title: Объектные переменные
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: 7c50dcbac32cdc841e513765d62f6ee711fc6049
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100478845"
---
# <a name="object-variables-in-visual-basic"></a><span data-ttu-id="15aed-103">Объектные переменные в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="15aed-103">Object Variables in Visual Basic</span></span>

<span data-ttu-id="15aed-104">Помимо непосредственного хранения значений, переменная может ссылаться на объект.</span><span class="sxs-lookup"><span data-stu-id="15aed-104">In addition to storing values directly, a variable can refer to an object.</span></span> <span data-ttu-id="15aed-105">Объект присваивается переменной по тем же причинам, что вы присваиваете переменной значение.</span><span class="sxs-lookup"><span data-stu-id="15aed-105">You assign an object to a variable for the same reasons you assign any value to a variable:</span></span>

- <span data-ttu-id="15aed-106">Имя переменной часто короче и проще в запоминании, чем полный путь к методам и свойствам, необходимым для доступа к самому объекту.</span><span class="sxs-lookup"><span data-stu-id="15aed-106">A variable name is often shorter and easier to remember than the full path of methods and properties necessary to access the object itself.</span></span>

- <span data-ttu-id="15aed-107">Использование переменной, ссылающейся на объект, является более эффективным, чем многократный доступ к самому объекту через необходимые методы или свойства.</span><span class="sxs-lookup"><span data-stu-id="15aed-107">Using a variable that refers to an object is more efficient than repeatedly accessing the object itself through the necessary methods or properties.</span></span>

- <span data-ttu-id="15aed-108">Вы можете изменить переменную, чтобы она ссылалась на другие объекты во время выполнения кода.</span><span class="sxs-lookup"><span data-stu-id="15aed-108">You can change a variable to refer to other objects while your code is running.</span></span>

## <a name="making-code-shorter"></a><span data-ttu-id="15aed-109">Сокращение кода</span><span class="sxs-lookup"><span data-stu-id="15aed-109">Making Code Shorter</span></span>

<span data-ttu-id="15aed-110">Переменные объекта можно использовать для сокращения кода, который необходимо ввести.</span><span class="sxs-lookup"><span data-stu-id="15aed-110">You can use object variables to shorten the code you have to type.</span></span> <span data-ttu-id="15aed-111">В следующем примере используется полный путь к методам и свойствам для доступа к <xref:System.Windows.Forms.Control> объекту.</span><span class="sxs-lookup"><span data-stu-id="15aed-111">The following example uses the full path of methods and properties to access a <xref:System.Windows.Forms.Control> object.</span></span>

```vb
' Assume Me is a valid Form, or replace Me with a valid Form.
Me.ActiveForm.ActiveControl.Text = "Test"
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)
Me.ActiveForm.ActiveControl.Show()
```

<span data-ttu-id="15aed-112">Этот код можно сократить и ускорить выполнение, если для элемента управления используется объектная переменная.</span><span class="sxs-lookup"><span data-stu-id="15aed-112">You can shorten this code, and speed up execution, if you use an object variable for the control.</span></span> <span data-ttu-id="15aed-113">Необходимо объявить объектную переменную с конкретным классом, который вы хотите присвоить ему ( `Control` в данном случае).</span><span class="sxs-lookup"><span data-stu-id="15aed-113">You should declare the object variable with the specific class that you intend to assign to it (`Control` in this case).</span></span> <span data-ttu-id="15aed-114">После присвоения объекта переменной ее можно обрабатывать точно так же, как и объект, к которому он относится.</span><span class="sxs-lookup"><span data-stu-id="15aed-114">Once you assign an object to the variable, you can treat it exactly the same as you treat the object to which it refers.</span></span> <span data-ttu-id="15aed-115">Можно задать или получить свойства объекта или использовать любой из его методов.</span><span class="sxs-lookup"><span data-stu-id="15aed-115">You can set or retrieve the properties of the object or use any of its methods.</span></span> <span data-ttu-id="15aed-116">В следующем примере используется объектная переменная для упрощения кода в предыдущем примере.</span><span class="sxs-lookup"><span data-stu-id="15aed-116">The following example uses an object variable to simplify the code in the preceding example.</span></span>

```vb
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl
ctrlActv.Text = "Test"
ctrlActv.Location = New Point(100, 100)
ctrlActv.Show()
```

## <a name="see-also"></a><span data-ttu-id="15aed-117">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="15aed-117">See also</span></span>

- [<span data-ttu-id="15aed-118">Объявление переменной</span><span class="sxs-lookup"><span data-stu-id="15aed-118">Variable Declaration</span></span>](variable-declaration.md)
- [<span data-ttu-id="15aed-119">Практическое руководство. Увеличение скорости доступа к объекту с длинным классификационным путем</span><span class="sxs-lookup"><span data-stu-id="15aed-119">How to: Speed Up Access to an Object with a Long Qualification Path</span></span>](how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)
- [<span data-ttu-id="15aed-120">Объявление объектной переменной</span><span class="sxs-lookup"><span data-stu-id="15aed-120">Object Variable Declaration</span></span>](object-variable-declaration.md)
- [<span data-ttu-id="15aed-121">Присваивание объектных переменных</span><span class="sxs-lookup"><span data-stu-id="15aed-121">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="15aed-122">Значения объектных переменных</span><span class="sxs-lookup"><span data-stu-id="15aed-122">Object Variable Values</span></span>](object-variable-values.md)
