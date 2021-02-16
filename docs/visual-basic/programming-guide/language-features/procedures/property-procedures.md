---
description: 'Дополнительные сведения: процедуры свойств (Visual Basic)'
title: Процедуры свойств
ms.date: 07/20/2015
helpviewer_keywords:
- Set statement [Visual Basic], Property procedures
- Visual Basic code, procedures
- return values [Visual Basic], Property procedures
- syntax [Visual Basic], Property procedures
- procedures [Visual Basic], property
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], custom
- property procedures
- Get statement [Visual Basic], property procedures
ms.assetid: 46a98379-e1a2-45dd-a48c-b51213f5ab07
ms.openlocfilehash: 55588278cdb8423a4f13a4e7ecc02f7ea692a618
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466592"
---
# <a name="property-procedures-visual-basic"></a><span data-ttu-id="a4d73-103">Процедуры свойств (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4d73-103">Property Procedures (Visual Basic)</span></span>

<span data-ttu-id="a4d73-104">Процедура свойства — это серия Visual Basic инструкций, которые управляют пользовательским свойством модуля, класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="a4d73-104">A property procedure is a series of Visual Basic statements that manipulate a custom property on a module, class, or structure.</span></span> <span data-ttu-id="a4d73-105">Процедуры свойств также называются свойствами *доступа к свойствам*.</span><span class="sxs-lookup"><span data-stu-id="a4d73-105">Property procedures are also known as *property accessors*.</span></span>

<span data-ttu-id="a4d73-106">Visual Basic предоставляет следующие процедуры свойств.</span><span class="sxs-lookup"><span data-stu-id="a4d73-106">Visual Basic provides for the following property procedures:</span></span>

- <span data-ttu-id="a4d73-107">`Get`Процедура возвращает значение свойства.</span><span class="sxs-lookup"><span data-stu-id="a4d73-107">A `Get` procedure returns the value of a property.</span></span> <span data-ttu-id="a4d73-108">Он вызывается при доступе к свойству в выражении.</span><span class="sxs-lookup"><span data-stu-id="a4d73-108">It is called when you access the property in an expression.</span></span>
- <span data-ttu-id="a4d73-109">`Set`Процедура задает для свойства значение, включая ссылку на объект.</span><span class="sxs-lookup"><span data-stu-id="a4d73-109">A `Set` procedure sets a property to a value, including an object reference.</span></span> <span data-ttu-id="a4d73-110">Он вызывается при присвоении значения свойству.</span><span class="sxs-lookup"><span data-stu-id="a4d73-110">It is called when you assign a value to the property.</span></span>

<span data-ttu-id="a4d73-111">Обычно процедуры свойств определяются парами с помощью `Get` `Set` инструкций и, но можно определить только одну процедуру, если свойство доступно только для чтения ([Инструкция Get](../../../language-reference/statements/get-statement.md)) или только для записи ([инструкция SET](../../../language-reference/statements/set-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="a4d73-111">You usually define property procedures in pairs, using the `Get` and `Set` statements, but you can define either procedure alone if the property is read-only ([Get Statement](../../../language-reference/statements/get-statement.md)) or write-only ([Set Statement](../../../language-reference/statements/set-statement.md)).</span></span>

<span data-ttu-id="a4d73-112">Процедуру и можно опустить `Get` `Set` при использовании автоматического реализуемого свойства.</span><span class="sxs-lookup"><span data-stu-id="a4d73-112">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="a4d73-113">Дополнительные сведения см. в разделе [Автоматически реализуемые свойства](./auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="a4d73-113">For more information, see [Auto-Implemented Properties](./auto-implemented-properties.md).</span></span>

<span data-ttu-id="a4d73-114">Свойства можно определить в классах, структурах и модулях.</span><span class="sxs-lookup"><span data-stu-id="a4d73-114">You can define properties in classes, structures, and modules.</span></span> <span data-ttu-id="a4d73-115">Свойства по `Public` умолчанию. Это означает, что их можно вызывать из любого места в приложении, которое может получить доступ к контейнеру свойства.</span><span class="sxs-lookup"><span data-stu-id="a4d73-115">Properties are `Public` by default, which means you can call them from anywhere in your application that can access the property's container.</span></span>

<span data-ttu-id="a4d73-116">Сравнение свойств и переменных см. [в разделе различия между свойствами и переменными в Visual Basic](differences-between-properties-and-variables.md).</span><span class="sxs-lookup"><span data-stu-id="a4d73-116">For a comparison of properties and variables, see [Differences Between Properties and Variables in Visual Basic](differences-between-properties-and-variables.md).</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="a4d73-117">Синтаксис объявления</span><span class="sxs-lookup"><span data-stu-id="a4d73-117">Declaration syntax</span></span>

<span data-ttu-id="a4d73-118">Само свойство определяется блоком кода, заключенным в [Оператор Property](../../../language-reference/statements/property-statement.md) и `End Property` оператор.</span><span class="sxs-lookup"><span data-stu-id="a4d73-118">A property itself is defined by a block of code enclosed within the [Property Statement](../../../language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="a4d73-119">Внутри этого блока каждая процедура свойства отображается как внутренний блок, заключенный в оператор объявления ( `Get` или `Set` ) и в объявление сопоставления `End` .</span><span class="sxs-lookup"><span data-stu-id="a4d73-119">Inside this block, each property procedure appears as an internal block enclosed within a declaration statement (`Get` or `Set`) and the matching `End` declaration.</span></span>

<span data-ttu-id="a4d73-120">Синтаксис объявления свойства и его процедур выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="a4d73-120">The syntax for declaring a property and its procedures is as follows:</span></span>

```vb
[Default] [Modifiers] Property PropertyName[(ParameterList)] [As DataType]
    [AccessLevel] Get
        ' Statements of the Get procedure.
        ' The following statement returns an expression as the property's value.
        Return Expression
    End Get
    [AccessLevel] Set[(ByVal NewValue As DataType)]
        ' Statements of the Set procedure.
        ' The following statement assigns newvalue as the property's value.
        LValue = NewValue
    End Set
End Property
' - or -
[Default] [Modifiers] Property PropertyName [(ParameterList)] [As DataType]
```

<span data-ttu-id="a4d73-121">В `Modifiers` можно указать уровень доступа и сведения о перегрузке, переопределении, совместном использовании и затенении, а также о том, доступно ли свойство только для чтения или только для записи.</span><span class="sxs-lookup"><span data-stu-id="a4d73-121">The `Modifiers` can specify access level and information regarding overloading, overriding, sharing, and shadowing, as well as whether the property is read-only or write-only.</span></span> <span data-ttu-id="a4d73-122">В `AccessLevel` `Get` `Set` процедуре или может быть любой уровень, который более четкий, чем уровень доступа, заданный для самого свойства.</span><span class="sxs-lookup"><span data-stu-id="a4d73-122">The `AccessLevel` on the `Get` or `Set` procedure can be any level that is more restrictive than the access level specified for the property itself.</span></span> <span data-ttu-id="a4d73-123">Дополнительные сведения см. в разделе [Оператор Property](../../../language-reference/statements/property-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a4d73-123">For more information, see [Property Statement](../../../language-reference/statements/property-statement.md).</span></span>

### <a name="data-type"></a><span data-ttu-id="a4d73-124">Тип данных</span><span class="sxs-lookup"><span data-stu-id="a4d73-124">Data Type</span></span>

<span data-ttu-id="a4d73-125">Тип данных свойства и основной уровень доступа определяются в `Property` инструкции, а не в процедурах свойства.</span><span class="sxs-lookup"><span data-stu-id="a4d73-125">A property's data type and principal access level are defined in the `Property` statement, not in the property procedures.</span></span> <span data-ttu-id="a4d73-126">Свойство может иметь только один тип данных.</span><span class="sxs-lookup"><span data-stu-id="a4d73-126">A property can have only one data type.</span></span> <span data-ttu-id="a4d73-127">Например, нельзя определить свойство для хранения `Decimal` значения, но получить `Double` значение.</span><span class="sxs-lookup"><span data-stu-id="a4d73-127">For example, you cannot define a property to store a `Decimal` value but retrieve a `Double` value.</span></span>

### <a name="access-level"></a><span data-ttu-id="a4d73-128">Уровень доступа</span><span class="sxs-lookup"><span data-stu-id="a4d73-128">Access Level</span></span>

<span data-ttu-id="a4d73-129">Однако можно определить основной уровень доступа для свойства и дополнительно ограничить уровень доступа в одной из его процедур свойств.</span><span class="sxs-lookup"><span data-stu-id="a4d73-129">However, you can define a principal access level for a property and further restrict the access level in one of its property procedures.</span></span> <span data-ttu-id="a4d73-130">Например, можно определить `Public` свойство, а затем определить `Private Set` процедуру.</span><span class="sxs-lookup"><span data-stu-id="a4d73-130">For example, you can define a `Public` property and then define a `Private Set` procedure.</span></span> <span data-ttu-id="a4d73-131">`Get`Процедура остается `Public` .</span><span class="sxs-lookup"><span data-stu-id="a4d73-131">The `Get` procedure remains `Public`.</span></span> <span data-ttu-id="a4d73-132">Уровень доступа можно изменить только в одной из процедур свойства, и его можно сделать более узким, чем основной уровень доступа.</span><span class="sxs-lookup"><span data-stu-id="a4d73-132">You can change the access level in only one of a property's procedures, and you can only make it more restrictive than the principal access level.</span></span> <span data-ttu-id="a4d73-133">Дополнительные сведения см. [в разделе инструкции. объявление свойства со смешанными уровнями доступа](how-to-declare-a-property-with-mixed-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="a4d73-133">For more information, see [How to: Declare a Property with Mixed Access Levels](how-to-declare-a-property-with-mixed-access-levels.md).</span></span>

## <a name="parameter-declaration"></a><span data-ttu-id="a4d73-134">Объявление параметра</span><span class="sxs-lookup"><span data-stu-id="a4d73-134">Parameter declaration</span></span>

<span data-ttu-id="a4d73-135">Каждый параметр объявляется так же, как и для [процедур подразделов](sub-procedures.md), за исключением того, что механизм передачи должен быть `ByVal` .</span><span class="sxs-lookup"><span data-stu-id="a4d73-135">You declare each parameter the same way you do for [Sub Procedures](sub-procedures.md), except that the passing mechanism must be `ByVal`.</span></span>

<span data-ttu-id="a4d73-136">Для каждого параметра в списке параметров используется следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="a4d73-136">The syntax for each parameter in the parameter list is as follows:</span></span>

```vb
[Optional] ByVal [ParamArray] parametername As datatype
```

<span data-ttu-id="a4d73-137">Если параметр является необязательным, необходимо также указать значение по умолчанию в составе объявления.</span><span class="sxs-lookup"><span data-stu-id="a4d73-137">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="a4d73-138">Для указания значения по умолчанию используется следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="a4d73-138">The syntax for specifying a default value is as follows:</span></span>

```vb
Optional ByVal parametername As datatype = defaultvalue
```

## <a name="property-value"></a><span data-ttu-id="a4d73-139">Значение свойства</span><span class="sxs-lookup"><span data-stu-id="a4d73-139">Property value</span></span>

<span data-ttu-id="a4d73-140">В `Get` процедуре возвращаемое значение предоставляется вызывающему выражению как значение свойства.</span><span class="sxs-lookup"><span data-stu-id="a4d73-140">In a `Get` procedure, the return value is supplied to the calling expression as the value of the property.</span></span>

<span data-ttu-id="a4d73-141">В `Set` процедуре новое значение свойства передается в параметр `Set` инструкции.</span><span class="sxs-lookup"><span data-stu-id="a4d73-141">In a `Set` procedure, the new property value is passed to the parameter of the `Set` statement.</span></span> <span data-ttu-id="a4d73-142">При явном объявлении параметра необходимо объявить его с тем же типом данных, что и свойство.</span><span class="sxs-lookup"><span data-stu-id="a4d73-142">If you explicitly declare a parameter, you must declare it with the same data type as the property.</span></span> <span data-ttu-id="a4d73-143">Если параметр не объявлен, компилятор использует неявный параметр `Value` для представления нового значения, присваиваемого свойству.</span><span class="sxs-lookup"><span data-stu-id="a4d73-143">If you do not declare a parameter, the compiler uses the implicit parameter `Value` to represent the new value to be assigned to the property.</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="a4d73-144">Синтаксис вызова</span><span class="sxs-lookup"><span data-stu-id="a4d73-144">Calling syntax</span></span>

<span data-ttu-id="a4d73-145">Процедура свойства вызывается неявно путем создания ссылки на свойство.</span><span class="sxs-lookup"><span data-stu-id="a4d73-145">You invoke a property procedure implicitly by making reference to the property.</span></span> <span data-ttu-id="a4d73-146">Имя свойства используется так же, как имя переменной, за исключением того, что необходимо указать значения для всех аргументов, которые не являются необязательными, а список аргументов необходимо заключить в круглые скобки.</span><span class="sxs-lookup"><span data-stu-id="a4d73-146">You use the name of the property the same way you would use the name of a variable, except that you must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="a4d73-147">Если аргументы не указаны, можно дополнительно опустить круглые скобки.</span><span class="sxs-lookup"><span data-stu-id="a4d73-147">If no arguments are supplied, you can optionally omit the parentheses.</span></span>

<span data-ttu-id="a4d73-148">Для неявного вызова `Set` процедуры используется следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="a4d73-148">The syntax for an implicit call to a `Set` procedure is as follows:</span></span>

```vb
propertyname[(argumentlist)] = expression
```

<span data-ttu-id="a4d73-149">Для неявного вызова `Get` процедуры используется следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="a4d73-149">The syntax for an implicit call to a `Get` procedure is as follows:</span></span>

```vb
lvalue = propertyname[(argumentlist)]
Do While (propertyname[(argumentlist)] > expression)
```

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="a4d73-150">Иллюстрация объявления и вызова</span><span class="sxs-lookup"><span data-stu-id="a4d73-150">Illustration of declaration and call</span></span>

<span data-ttu-id="a4d73-151">Следующее свойство сохраняет полное имя как два составных имени: имя и фамилия.</span><span class="sxs-lookup"><span data-stu-id="a4d73-151">The following property stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="a4d73-152">При чтении вызывающего кода `fullName` `Get` процедура объединяет два составных имени и возвращает полное имя.</span><span class="sxs-lookup"><span data-stu-id="a4d73-152">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="a4d73-153">Когда вызывающий код присваивает новое полное имя, `Set` процедура попытается разбить ее на два составных имени.</span><span class="sxs-lookup"><span data-stu-id="a4d73-153">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="a4d73-154">Если не удается найти пробел, он сохраняется как первое имя.</span><span class="sxs-lookup"><span data-stu-id="a4d73-154">If it does not find a space, it stores it all as the first name.</span></span>

[!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]

<span data-ttu-id="a4d73-155">В следующем примере показаны типичные вызовы процедур свойств `fullName` :</span><span class="sxs-lookup"><span data-stu-id="a4d73-155">The following example shows typical calls to the property procedures of `fullName`:</span></span>

[!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]

## <a name="see-also"></a><span data-ttu-id="a4d73-156">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a4d73-156">See also</span></span>

- [<span data-ttu-id="a4d73-157">Процедуры</span><span class="sxs-lookup"><span data-stu-id="a4d73-157">Procedures</span></span>](index.md)
- [<span data-ttu-id="a4d73-158">Процедуры функций</span><span class="sxs-lookup"><span data-stu-id="a4d73-158">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="a4d73-159">Процедуры операторов</span><span class="sxs-lookup"><span data-stu-id="a4d73-159">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="a4d73-160">Параметры и аргументы процедуры</span><span class="sxs-lookup"><span data-stu-id="a4d73-160">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="a4d73-161">Различия между свойствами и переменными в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a4d73-161">Differences Between Properties and Variables in Visual Basic</span></span>](differences-between-properties-and-variables.md)
- [<span data-ttu-id="a4d73-162">Практическое руководство. Создание свойства</span><span class="sxs-lookup"><span data-stu-id="a4d73-162">How to: Create a Property</span></span>](how-to-create-a-property.md)
- [<span data-ttu-id="a4d73-163">Практическое руководство. Вызов процедуры свойства</span><span class="sxs-lookup"><span data-stu-id="a4d73-163">How to: Call a Property Procedure</span></span>](how-to-call-a-property-procedure.md)
- [<span data-ttu-id="a4d73-164">Практическое руководство. Объявление и вызов свойства по умолчанию в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a4d73-164">How to: Declare and Call a Default Property in Visual Basic</span></span>](how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="a4d73-165">Практическое руководство. Запись значения в свойство</span><span class="sxs-lookup"><span data-stu-id="a4d73-165">How to: Put a Value in a Property</span></span>](how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="a4d73-166">Практическое руководство. Получение значения из свойства</span><span class="sxs-lookup"><span data-stu-id="a4d73-166">How to: Get a Value from a Property</span></span>](how-to-get-a-value-from-a-property.md)
