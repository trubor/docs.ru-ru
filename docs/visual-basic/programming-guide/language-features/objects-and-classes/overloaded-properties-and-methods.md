---
description: 'Дополнительные сведения: перегруженные свойства и методы (Visual Basic)'
title: Перегруженные свойства и методы
ms.date: 07/20/2015
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names [Visual Basic], multiple procedures with same
- procedures [Visual Basic], multiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword [Visual Basic], overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
ms.openlocfilehash: fb46876d346ad5f391241aee0b07175df290e656
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100438779"
---
# <a name="overloaded-properties-and-methods-visual-basic"></a><span data-ttu-id="a79a4-103">Перегруженные свойства и методы (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a79a4-103">Overloaded properties and methods (Visual Basic)</span></span>

<span data-ttu-id="a79a4-104">Перегрузка — это создание более чем одной процедуры, конструктора экземпляра или свойства в классе с тем же именем, но разными типами аргументов.</span><span class="sxs-lookup"><span data-stu-id="a79a4-104">Overloading is the creation of more than one procedure, instance constructor, or property in a class with the same name but different argument types.</span></span>

## <a name="overloading-usage"></a><span data-ttu-id="a79a4-105">Перегрузка использования</span><span class="sxs-lookup"><span data-stu-id="a79a4-105">Overloading usage</span></span>

<span data-ttu-id="a79a4-106">Перегрузка особенно полезна, когда объектная модель определяет, что для процедур, которые работают с различными типами данных, используются одинаковые имена.</span><span class="sxs-lookup"><span data-stu-id="a79a4-106">Overloading is especially useful when your object model dictates that you employ identical names for procedures that operate on different data types.</span></span> <span data-ttu-id="a79a4-107">Например, класс, который может отображать несколько различных типов данных, может иметь `Display` процедуры, которые выглядят следующим образом:</span><span class="sxs-lookup"><span data-stu-id="a79a4-107">For example, a class that can display several different data types could have `Display` procedures that look like this:</span></span>

[!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]

<span data-ttu-id="a79a4-108">Без перегрузки необходимо создать разные имена для каждой процедуры, даже если они выполняют одно и то же действие, как показано далее:</span><span class="sxs-lookup"><span data-stu-id="a79a4-108">Without overloading, you would need to create distinct names for each procedure, even though they do the same thing, as shown next:</span></span>

[!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]

<span data-ttu-id="a79a4-109">Перегрузка упрощает использование свойств или методов, поскольку она предоставляет возможность выбора типов данных, которые можно использовать.</span><span class="sxs-lookup"><span data-stu-id="a79a4-109">Overloading makes it easier to use properties or methods because it provides a choice of data types that can be used.</span></span> <span data-ttu-id="a79a4-110">Например, перегруженный `Display` метод, описанный ранее, можно вызвать с помощью любой из следующих строк кода:</span><span class="sxs-lookup"><span data-stu-id="a79a4-110">For example, the overloaded `Display` method discussed previously can be called with any of the following lines of code:</span></span>

[!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]

<span data-ttu-id="a79a4-111">Во время выполнения Visual Basic вызывает правильную процедуру на основе типов данных указанных параметров.</span><span class="sxs-lookup"><span data-stu-id="a79a4-111">At run time, Visual Basic calls the correct procedure based on the data types of the parameters you specify.</span></span>

## <a name="overloading-rules"></a><span data-ttu-id="a79a4-112">Перегрузка правил</span><span class="sxs-lookup"><span data-stu-id="a79a4-112">Overloading rules</span></span>

 <span data-ttu-id="a79a4-113">Перегруженный член класса создается путем добавления двух или более свойств или методов с одинаковым именем.</span><span class="sxs-lookup"><span data-stu-id="a79a4-113">You create an overloaded member for a class by adding two or more properties or methods with the same name.</span></span> <span data-ttu-id="a79a4-114">За исключением перегруженных производных членов, каждый перегруженный член должен иметь разные списки параметров, и следующие элементы нельзя использовать в качестве отличительной функции при перегрузке свойства или процедуры:</span><span class="sxs-lookup"><span data-stu-id="a79a4-114">Except for overloaded derived members, each overloaded member must have different parameter lists, and the following items cannot be used as a differentiating feature when overloading a property or procedure:</span></span>

- <span data-ttu-id="a79a4-115">Модификаторы, такие как `ByVal` или `ByRef` , которые применяются к элементу или параметрам элемента.</span><span class="sxs-lookup"><span data-stu-id="a79a4-115">Modifiers, such as `ByVal` or `ByRef`, that apply to a member, or parameters of the member.</span></span>

- <span data-ttu-id="a79a4-116">Имена параметров</span><span class="sxs-lookup"><span data-stu-id="a79a4-116">Names of parameters</span></span>

- <span data-ttu-id="a79a4-117">Типы возвращаемых процедур</span><span class="sxs-lookup"><span data-stu-id="a79a4-117">Return types of procedures</span></span>

<span data-ttu-id="a79a4-118">`Overloads`Ключевое слово является необязательным при перегрузке, но если какой-либо перегруженный член использует `Overloads` ключевое слово, то все другие перегруженные члены с тем же именем также должны указывать это ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="a79a4-118">The `Overloads` keyword is optional when overloading, but if any overloaded member uses the `Overloads` keyword, then all other overloaded members with the same name must also specify this keyword.</span></span>

<span data-ttu-id="a79a4-119">Производные классы могут перегружать унаследованные члены с элементами, которые имеют одинаковые параметры и типы параметров, процесс, называемый *теневым именем и сигнатурой*.</span><span class="sxs-lookup"><span data-stu-id="a79a4-119">Derived classes can overload inherited members with members that have identical parameters and parameter types, a process known as *shadowing by name and signature*.</span></span> <span data-ttu-id="a79a4-120">Если `Overloads` ключевое слово используется при затенении по имени и сигнатуре, реализация члена в производном классе будет использоваться вместо реализации в базовом классе, а все другие перегрузки для этого члена будут доступны экземплярам производного класса.</span><span class="sxs-lookup"><span data-stu-id="a79a4-120">If the `Overloads` keyword is used when shadowing by name and signature, the derived class's implementation of the member will be used instead of the implementation in the base class, and all other overloads for that member will be available to instances of the derived class.</span></span>

<span data-ttu-id="a79a4-121">Если `Overloads` ключевое слово пропущено при перегрузке унаследованного члена с членом, имеющим идентичные параметры и типы параметров, перегрузка называется *тенью по имени*.</span><span class="sxs-lookup"><span data-stu-id="a79a4-121">If the `Overloads` keyword is omitted when overloading an inherited member with a member that has identical parameters and parameter types, then the overloading is called *shadowing by name*.</span></span> <span data-ttu-id="a79a4-122">Затенение по имени заменяет унаследованную реализацию члена и делает все другие перегрузки недоступными для экземпляров производного класса и его децедентс.</span><span class="sxs-lookup"><span data-stu-id="a79a4-122">Shadowing by name replaces the inherited implementation of a member, and it makes all other overloads unavailable to instances of the derived class and its decedents.</span></span>

<span data-ttu-id="a79a4-123">`Overloads` `Shadows` Модификаторы и не могут использоваться одновременно с одним свойством или методом.</span><span class="sxs-lookup"><span data-stu-id="a79a4-123">The `Overloads` and `Shadows` modifiers cannot both be used with the same property or method.</span></span>

### <a name="example"></a><span data-ttu-id="a79a4-124">Пример</span><span class="sxs-lookup"><span data-stu-id="a79a4-124">Example</span></span>

<span data-ttu-id="a79a4-125">В следующем примере создаются перегруженные методы, которые принимают `String` или `Decimal` представление суммы в долларе и возвращают строку, содержащую налог на продажу.</span><span class="sxs-lookup"><span data-stu-id="a79a4-125">The following example creates overloaded methods that accept either a `String` or `Decimal` representation of a dollar amount and return a string containing the sales tax.</span></span>

#### <a name="to-use-this-example-to-create-an-overloaded-method"></a><span data-ttu-id="a79a4-126">Использование этого примера для создания перегруженного метода</span><span class="sxs-lookup"><span data-stu-id="a79a4-126">To use this example to create an overloaded method</span></span>

1. <span data-ttu-id="a79a4-127">Откройте новый проект и добавьте класс с именем `TaxClass` .</span><span class="sxs-lookup"><span data-stu-id="a79a4-127">Open a new project and add a class named `TaxClass`.</span></span>

2. <span data-ttu-id="a79a4-128">Добавьте в класс `TaxClass` приведенный далее код.</span><span class="sxs-lookup"><span data-stu-id="a79a4-128">Add the following code to the `TaxClass` class.</span></span>

    [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]

3. <span data-ttu-id="a79a4-129">Добавьте следующую процедуру в форму.</span><span class="sxs-lookup"><span data-stu-id="a79a4-129">Add the following procedure to your form.</span></span>

    [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]

4. <span data-ttu-id="a79a4-130">Добавьте в форму кнопку и вызовите `ShowTax` процедуру из `Button1_Click` события кнопки.</span><span class="sxs-lookup"><span data-stu-id="a79a4-130">Add a button to your form and call the `ShowTax` procedure from the `Button1_Click` event of the button.</span></span>

5. <span data-ttu-id="a79a4-131">Запустите проект и нажмите кнопку в форме, чтобы проверить перегруженную `ShowTax` процедуру.</span><span class="sxs-lookup"><span data-stu-id="a79a4-131">Run the project and click the button on the form to test the overloaded `ShowTax` procedure.</span></span>

<span data-ttu-id="a79a4-132">Во время выполнения компилятор выбирает подходящую перегруженную функцию, которая соответствует используемым параметрам.</span><span class="sxs-lookup"><span data-stu-id="a79a4-132">At run time, the compiler chooses the appropriate overloaded function that matches the parameters being used.</span></span> <span data-ttu-id="a79a4-133">При нажатии кнопки перегруженный метод вызывается первым с `Price` параметром, который является строкой, и сообщением «Price — это строка.</span><span class="sxs-lookup"><span data-stu-id="a79a4-133">When you click the button, the overloaded method is called first with a `Price` parameter that is a string and the message, "Price is a String.</span></span> <span data-ttu-id="a79a4-134">Налог — $5,12 ".</span><span class="sxs-lookup"><span data-stu-id="a79a4-134">Tax is $5.12" is displayed.</span></span> <span data-ttu-id="a79a4-135">`TaxAmount` вызывается со `Decimal` значением второй раз и сообщением "Price является десятичным числом.</span><span class="sxs-lookup"><span data-stu-id="a79a4-135">`TaxAmount` is called with a `Decimal` value the second time and the message, "Price is a Decimal.</span></span> <span data-ttu-id="a79a4-136">Налог — $5,12 ".</span><span class="sxs-lookup"><span data-stu-id="a79a4-136">Tax is $5.12" is displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="a79a4-137">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a79a4-137">See also</span></span>

- [<span data-ttu-id="a79a4-138">Объекты и классы</span><span class="sxs-lookup"><span data-stu-id="a79a4-138">Objects and Classes</span></span>](index.md)
- [<span data-ttu-id="a79a4-139">Сокрытие в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a79a4-139">Shadowing in Visual Basic</span></span>](../declared-elements/shadowing.md)
- [<span data-ttu-id="a79a4-140">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="a79a4-140">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="a79a4-141">Основы наследования</span><span class="sxs-lookup"><span data-stu-id="a79a4-141">Inheritance Basics</span></span>](inheritance-basics.md)
- [<span data-ttu-id="a79a4-142">Shadows</span><span class="sxs-lookup"><span data-stu-id="a79a4-142">Shadows</span></span>](../../../language-reference/modifiers/shadows.md)
- [<span data-ttu-id="a79a4-143">ByVal</span><span class="sxs-lookup"><span data-stu-id="a79a4-143">ByVal</span></span>](../../../language-reference/modifiers/byval.md)
- [<span data-ttu-id="a79a4-144">ByRef</span><span class="sxs-lookup"><span data-stu-id="a79a4-144">ByRef</span></span>](../../../language-reference/modifiers/byref.md)
- [<span data-ttu-id="a79a4-145">Перегрузки</span><span class="sxs-lookup"><span data-stu-id="a79a4-145">Overloads</span></span>](../../../language-reference/modifiers/overloads.md)
- [<span data-ttu-id="a79a4-146">Shadows</span><span class="sxs-lookup"><span data-stu-id="a79a4-146">Shadows</span></span>](../../../language-reference/modifiers/shadows.md)
