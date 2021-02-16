---
description: Дополнительные сведения см. в статье как объявить и вызвать свойство по умолчанию в Visual Basic
title: Практическое руководство. Объявление и вызов свойства по умолчанию
ms.date: 07/20/2015
helpviewer_keywords:
- defaults [Visual Basic], properties
- properties [Visual Basic], default
- procedures [Visual Basic], defining
- default properties [Visual Basic], in Visual Basic
- Visual Basic code, procedures
- Visual Basic code, properties
- default properties
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
ms.openlocfilehash: 2a0e82fe89bb89613996f613930ace1aa6e41b7f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472453"
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a><span data-ttu-id="03e30-103">Практическое руководство. Объявление и вызов свойства по умолчанию в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="03e30-103">How to: Declare and Call a Default Property in Visual Basic</span></span>

<span data-ttu-id="03e30-104">*Свойство по умолчанию* — это свойство класса или структуры, к которому код может получить доступ без указания этого свойства.</span><span class="sxs-lookup"><span data-stu-id="03e30-104">A *default property* is a class or structure property that your code can access without specifying it.</span></span> <span data-ttu-id="03e30-105">Если вызывающий код именует класс или структуру, но не свойство, и контекст разрешает доступ к свойству, Visual Basic разрешает доступ к свойству по умолчанию этого класса или структуры, если он существует.</span><span class="sxs-lookup"><span data-stu-id="03e30-105">When calling code names a class or structure but not a property, and the context allows access to a property, Visual Basic resolves the access to that class or structure's default property if one exists.</span></span>  
  
 <span data-ttu-id="03e30-106">Класс или структура может иметь не более одного свойства по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="03e30-106">A class or structure can have at most one default property.</span></span> <span data-ttu-id="03e30-107">Однако можно перегрузить свойство по умолчанию и иметь более одной версии.</span><span class="sxs-lookup"><span data-stu-id="03e30-107">However, you can overload a default property and have more than one version of it.</span></span>  
  
 <span data-ttu-id="03e30-108">Дополнительные сведения см. в разделе [Default](../../../language-reference/modifiers/default.md).</span><span class="sxs-lookup"><span data-stu-id="03e30-108">For more information, see [Default](../../../language-reference/modifiers/default.md).</span></span>  
  
### <a name="to-declare-a-default-property"></a><span data-ttu-id="03e30-109">Объявление свойства по умолчанию</span><span class="sxs-lookup"><span data-stu-id="03e30-109">To declare a default property</span></span>  
  
1. <span data-ttu-id="03e30-110">Объявите свойство обычным способом.</span><span class="sxs-lookup"><span data-stu-id="03e30-110">Declare the property in the normal way.</span></span> <span data-ttu-id="03e30-111">Не указывайте `Shared` `Private` ключевое слово или.</span><span class="sxs-lookup"><span data-stu-id="03e30-111">Do not specify the `Shared` or `Private` keyword.</span></span>  
  
2. <span data-ttu-id="03e30-112">Включите `Default` ключевое слово в объявление свойства.</span><span class="sxs-lookup"><span data-stu-id="03e30-112">Include the `Default` keyword in the property declaration.</span></span>  
  
3. <span data-ttu-id="03e30-113">Укажите по меньшей мере один параметр для свойства.</span><span class="sxs-lookup"><span data-stu-id="03e30-113">Specify at least one parameter for the property.</span></span> <span data-ttu-id="03e30-114">Нельзя определить свойство по умолчанию, которое не принимает по крайней мере один аргумент.</span><span class="sxs-lookup"><span data-stu-id="03e30-114">You cannot define a default property that does not take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#17)]  
  
### <a name="to-call-a-default-property"></a><span data-ttu-id="03e30-115">Вызов свойства по умолчанию</span><span class="sxs-lookup"><span data-stu-id="03e30-115">To call a default property</span></span>  
  
1. <span data-ttu-id="03e30-116">Объявите переменную содержащего класса или типа структуры.</span><span class="sxs-lookup"><span data-stu-id="03e30-116">Declare a variable of the containing class or structure type.</span></span>  
  
     [!code-vb[VbVbcnProcedures#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#16)]  
  
2. <span data-ttu-id="03e30-117">Используйте только имя переменной в выражении, в которое вы обычно включаете имя свойства.</span><span class="sxs-lookup"><span data-stu-id="03e30-117">Use the variable name alone in an expression where you would normally include the property name.</span></span>  
  
     [!code-vb[VbVbcnProcedures#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#21)]  
  
3. <span data-ttu-id="03e30-118">Используйте имя переменной со списком аргументов в круглых скобках.</span><span class="sxs-lookup"><span data-stu-id="03e30-118">Follow the variable name with an argument list in parentheses.</span></span> <span data-ttu-id="03e30-119">Свойство по умолчанию должно принимать по крайней мере один аргумент.</span><span class="sxs-lookup"><span data-stu-id="03e30-119">A default property must take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#20)]  
  
4. <span data-ttu-id="03e30-120">Чтобы получить значение свойства по умолчанию, используйте имя переменной со списком аргументов в выражении или после знака равенства ( `=` ) в операторе присваивания.</span><span class="sxs-lookup"><span data-stu-id="03e30-120">To retrieve the default property value, use the variable name, with an argument list, in an expression or following the equal (`=`) sign in an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#15)]  
  
5. <span data-ttu-id="03e30-121">Чтобы задать значение свойства по умолчанию, используйте имя переменной со списком аргументов в левой части оператора присваивания.</span><span class="sxs-lookup"><span data-stu-id="03e30-121">To set the default property value, use the variable name, with an argument list, on the left side of an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#14)]  
  
6. <span data-ttu-id="03e30-122">Вы всегда можете указать имя свойства по умолчанию вместе с именем переменной, как и при доступе к любому другому свойству.</span><span class="sxs-lookup"><span data-stu-id="03e30-122">You can always specify the default property name together with the variable name, just as you would do to access any other property.</span></span>  
  
     [!code-vb[VbVbcnProcedures#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#19)]  
  
## <a name="example"></a><span data-ttu-id="03e30-123">Пример</span><span class="sxs-lookup"><span data-stu-id="03e30-123">Example</span></span>  

 <span data-ttu-id="03e30-124">В следующем примере объявляется свойство по умолчанию для класса.</span><span class="sxs-lookup"><span data-stu-id="03e30-124">The following example declares a default property on a class.</span></span>  
  
 [!code-vb[VbVbcnProcedures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="03e30-125">Пример</span><span class="sxs-lookup"><span data-stu-id="03e30-125">Example</span></span>  

 <span data-ttu-id="03e30-126">В следующем примере показано, как вызвать свойство по умолчанию `myProperty` для класса `class1` .</span><span class="sxs-lookup"><span data-stu-id="03e30-126">The following example demonstrates how to call the default property `myProperty` on class `class1`.</span></span> <span data-ttu-id="03e30-127">Три оператора присваивания хранят значения в `myProperty` , а <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> вызов считывает значения.</span><span class="sxs-lookup"><span data-stu-id="03e30-127">The three assignment statements store values in `myProperty`, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> call reads the values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#13)]  
  
 <span data-ttu-id="03e30-128">Наиболее распространенным применением свойства по умолчанию является <xref:Microsoft.VisualBasic.Collection.Item%2A> свойство в различных классах коллекций.</span><span class="sxs-lookup"><span data-stu-id="03e30-128">The most common use of a default property is the <xref:Microsoft.VisualBasic.Collection.Item%2A> property on various collection classes.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="03e30-129">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="03e30-129">Robust Programming</span></span>  

 <span data-ttu-id="03e30-130">Свойства по умолчанию могут привести к небольшому сокращению количества символов в исходном коде, но они могут усложнить чтение кода.</span><span class="sxs-lookup"><span data-stu-id="03e30-130">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="03e30-131">Если вызывающий код не знаком с классом или структурой, то при создании ссылки на имя класса или структуры он не может определить, обращается ли эта ссылка к самому классу или структуре, или к свойству по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="03e30-131">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="03e30-132">Это может привести к ошибкам компилятора или незначительным логическим ошибкам времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="03e30-132">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="03e30-133">Можно немного уменьшить вероятность ошибок свойств по умолчанию, всегда используя [оператор Option строго](../../../language-reference/statements/option-strict-statement.md) , чтобы задать для проверки типа компилятора значение `On` .</span><span class="sxs-lookup"><span data-stu-id="03e30-133">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="03e30-134">Если вы планируете использовать в коде предопределенный класс или структуру, необходимо определить, имеет ли он свойство по умолчанию, и, если да, то, какое имя имеет значение.</span><span class="sxs-lookup"><span data-stu-id="03e30-134">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="03e30-135">Из-за этих недостатков рекомендуется не определять свойства по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="03e30-135">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="03e30-136">Для удобочитаемости кода следует также рассмотреть возможность явной ссылки на все свойства, даже свойства по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="03e30-136">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03e30-137">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="03e30-137">See also</span></span>

- [<span data-ttu-id="03e30-138">Процедуры свойств</span><span class="sxs-lookup"><span data-stu-id="03e30-138">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="03e30-139">Параметры и аргументы процедуры</span><span class="sxs-lookup"><span data-stu-id="03e30-139">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="03e30-140">Property Statement</span><span class="sxs-lookup"><span data-stu-id="03e30-140">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="03e30-141">Default</span><span class="sxs-lookup"><span data-stu-id="03e30-141">Default</span></span>](../../../language-reference/modifiers/default.md)
- [<span data-ttu-id="03e30-142">Различия между свойствами и переменными в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="03e30-142">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="03e30-143">Практическое руководство. Создание свойства</span><span class="sxs-lookup"><span data-stu-id="03e30-143">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="03e30-144">Практическое руководство. Объявление свойства со смешанным уровнем доступа</span><span class="sxs-lookup"><span data-stu-id="03e30-144">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="03e30-145">Практическое руководство. Вызов процедуры свойства</span><span class="sxs-lookup"><span data-stu-id="03e30-145">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="03e30-146">Практическое руководство. Запись значения в свойство</span><span class="sxs-lookup"><span data-stu-id="03e30-146">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="03e30-147">Практическое руководство. Получение значения из свойства</span><span class="sxs-lookup"><span data-stu-id="03e30-147">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
