---
description: Дополнительные сведения о переменных в Visual Basic
title: Переменные
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
ms.openlocfilehash: d00907e451fa09c6e9b6be990a24a4d39b386622
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481718"
---
# <a name="variables-in-visual-basic"></a><span data-ttu-id="365b3-103">Переменные в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="365b3-103">Variables in Visual Basic</span></span>

<span data-ttu-id="365b3-104">При выполнении вычислений с Visual Basic часто приходится сохранять значения.</span><span class="sxs-lookup"><span data-stu-id="365b3-104">You often have to store values when you perform calculations with Visual Basic.</span></span> <span data-ttu-id="365b3-105">Например, может потребоваться вычислить несколько значений, сравнить их и (в зависимости от результата сравнения) выполнить с ними различные операции.</span><span class="sxs-lookup"><span data-stu-id="365b3-105">For example, you might want to calculate several values, compare them, and perform different operations on them, depending on the result of the comparison.</span></span> <span data-ttu-id="365b3-106">Чтобы сравнить значения, их необходимо сохранить.</span><span class="sxs-lookup"><span data-stu-id="365b3-106">You have to retain the values if you want to compare them.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="365b3-107">Использование</span><span class="sxs-lookup"><span data-stu-id="365b3-107">Usage</span></span>  

 <span data-ttu-id="365b3-108">Visual Basic, как и большинство языков программирования, использует переменные для хранения значений.</span><span class="sxs-lookup"><span data-stu-id="365b3-108">Visual Basic, just like most programming languages, uses variables for storing values.</span></span> <span data-ttu-id="365b3-109">*Переменная* имеет имя (слово, которое используется для ссылки на содержащееся в переменной значение).</span><span class="sxs-lookup"><span data-stu-id="365b3-109">A *variable* has a name (the word that you use to refer to the value that the variable contains).</span></span> <span data-ttu-id="365b3-110">Переменная также имеет тип данных (который определяет, какие данные можно хранить в переменной).</span><span class="sxs-lookup"><span data-stu-id="365b3-110">A variable also has a data type (which determines the kind of data that the variable can store).</span></span> <span data-ttu-id="365b3-111">Переменная может представлять массив, если она должна хранить индексированный набор близко связанных элементов данных.</span><span class="sxs-lookup"><span data-stu-id="365b3-111">A variable can represent an array if it has to store an indexed set of closely related data items.</span></span>  
  
 <span data-ttu-id="365b3-112">Вывод локального типа позволяет объявлять переменные без явного указания типа данных.</span><span class="sxs-lookup"><span data-stu-id="365b3-112">Local type inference enables you to declare variables without explicitly stating a data type.</span></span> <span data-ttu-id="365b3-113">Вместо этого компилятор выводит тип переменной из типа инициализирующего выражения.</span><span class="sxs-lookup"><span data-stu-id="365b3-113">Instead, the compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="365b3-114">Дополнительные сведения см. в разделах [Вывод локального типа](local-type-inference.md) и [Оператор Option Infer](../../../language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="365b3-114">For more information, see [Local Type Inference](local-type-inference.md) and [Option Infer Statement](../../../language-reference/statements/option-infer-statement.md).</span></span>  
  
## <a name="assigning-values"></a><span data-ttu-id="365b3-115">Назначение значений</span><span class="sxs-lookup"><span data-stu-id="365b3-115">Assigning Values</span></span>  

 <span data-ttu-id="365b3-116">Для выполнения вычислений и присвоения результата переменной используются операторы присваивания, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="365b3-116">You use assignment statements to perform calculations and assign the result to a variable, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrVariables#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrVariables/VB/Class1.vb#1)]  
  
> [!NOTE]
> <span data-ttu-id="365b3-117">В этом примере знак равенства (`=`) является оператором присваивания, а не оператором равенства.</span><span class="sxs-lookup"><span data-stu-id="365b3-117">The equal sign (`=`) in this example is an assignment operator, not an equality operator.</span></span> <span data-ttu-id="365b3-118">Значение присваивается переменной `applesSold`.</span><span class="sxs-lookup"><span data-stu-id="365b3-118">The value is being assigned to the variable `applesSold`.</span></span>  
  
 <span data-ttu-id="365b3-119">Подробнее см. в разделе [Практическое руководство. Запись данных в переменную и их извлечение из переменной](how-to-move-data-into-and-out-of-a-variable.md).</span><span class="sxs-lookup"><span data-stu-id="365b3-119">For more information, see [How to: Move Data Into and Out of a Variable](how-to-move-data-into-and-out-of-a-variable.md).</span></span>  
  
## <a name="variables-and-properties"></a><span data-ttu-id="365b3-120">Переменные и свойства</span><span class="sxs-lookup"><span data-stu-id="365b3-120">Variables and Properties</span></span>  

 <span data-ttu-id="365b3-121">Как и переменная, *свойство* соответствует значению, к которому можно получить доступ.</span><span class="sxs-lookup"><span data-stu-id="365b3-121">Like a variable, a *property* represents a value that you can access.</span></span> <span data-ttu-id="365b3-122">Но оно является более сложным, чем переменная.</span><span class="sxs-lookup"><span data-stu-id="365b3-122">However, it is more complex than a variable.</span></span> <span data-ttu-id="365b3-123">Свойство использует блоки кода, определяющие способ задания и получения его значения.</span><span class="sxs-lookup"><span data-stu-id="365b3-123">A property uses code blocks that control how to set and retrieve its value.</span></span> <span data-ttu-id="365b3-124">Подробнее см. в разделе [Различия между свойствами и переменными в Visual Basic](../procedures/differences-between-properties-and-variables.md).</span><span class="sxs-lookup"><span data-stu-id="365b3-124">For more information, see [Differences Between Properties and Variables in Visual Basic](../procedures/differences-between-properties-and-variables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="365b3-125">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="365b3-125">See also</span></span>

- [<span data-ttu-id="365b3-126">Объявление переменной</span><span class="sxs-lookup"><span data-stu-id="365b3-126">Variable Declaration</span></span>](variable-declaration.md)
- [<span data-ttu-id="365b3-127">Объектные переменные</span><span class="sxs-lookup"><span data-stu-id="365b3-127">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="365b3-128">Устранение неполадок, связанных с переменными</span><span class="sxs-lookup"><span data-stu-id="365b3-128">Troubleshooting Variables</span></span>](troubleshooting-variables.md)
- [<span data-ttu-id="365b3-129">Практическое руководство. Запись данных в переменную и их извлечение из переменной</span><span class="sxs-lookup"><span data-stu-id="365b3-129">How to: Move Data Into and Out of a Variable</span></span>](how-to-move-data-into-and-out-of-a-variable.md)
- [<span data-ttu-id="365b3-130">Различия между свойствами и переменными в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="365b3-130">Differences Between Properties and Variables in Visual Basic</span></span>](../procedures/differences-between-properties-and-variables.md)
- [<span data-ttu-id="365b3-131">Вывод локального типа</span><span class="sxs-lookup"><span data-stu-id="365b3-131">Local Type Inference</span></span>](local-type-inference.md)
