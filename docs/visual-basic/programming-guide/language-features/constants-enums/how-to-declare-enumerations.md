---
description: Дополнительные сведения см. в статье как объявлять перечисления (Visual Basic)
title: Практическое руководство. Объявление перечислений
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
ms.openlocfilehash: 10ce0b16a03b832c5afed4d7a310ffb729338e57
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471634"
---
# <a name="how-to-declare-enumerations-visual-basic"></a><span data-ttu-id="88835-103">Практическое руководство. Объявление перечисления (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88835-103">How to: Declare Enumerations (Visual Basic)</span></span>

<span data-ttu-id="88835-104">Перечисление создается с помощью `Enum` инструкции в разделе Declarations класса или модуля.</span><span class="sxs-lookup"><span data-stu-id="88835-104">You create an enumeration with the `Enum` statement in the declarations section of a class or module.</span></span> <span data-ttu-id="88835-105">Нельзя объявить перечисление в методе.</span><span class="sxs-lookup"><span data-stu-id="88835-105">You cannot declare an enumeration within a method.</span></span> <span data-ttu-id="88835-106">Чтобы указать соответствующий уровень доступа, используйте,, `Private` `Protected` `Friend` или `Public` .</span><span class="sxs-lookup"><span data-stu-id="88835-106">To specify the appropriate level of access, use `Private`, `Protected`, `Friend`, or `Public`.</span></span>  
  
 <span data-ttu-id="88835-107">`Enum`Тип имеет имя, базовый тип и набор полей, каждый из которых представляет константу.</span><span class="sxs-lookup"><span data-stu-id="88835-107">An `Enum` type has a name, an underlying type, and a set of fields, each representing a constant.</span></span> <span data-ttu-id="88835-108">Имя должно быть допустимым квалификатором Visual Basic .NET.</span><span class="sxs-lookup"><span data-stu-id="88835-108">The name must be a valid Visual Basic .NET qualifier.</span></span> <span data-ttu-id="88835-109">Базовый тип должен быть одним из целочисленных типов — `Byte` , `Short` `Long` или `Integer` .</span><span class="sxs-lookup"><span data-stu-id="88835-109">The underlying type must be one of the integer types—`Byte`, `Short`, `Long` or `Integer`.</span></span> <span data-ttu-id="88835-110">Значение по умолчанию — `Integer`.</span><span class="sxs-lookup"><span data-stu-id="88835-110">`Integer` is the default.</span></span> <span data-ttu-id="88835-111">Перечисления всегда являются строго типизированными и не взаимозаменяемы с целочисленными типами чисел.</span><span class="sxs-lookup"><span data-stu-id="88835-111">Enumerations are always strongly typed and are not interchangeable with integer number types.</span></span>  
  
 <span data-ttu-id="88835-112">Перечисления не могут иметь значения с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="88835-112">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="88835-113">Если перечислению присвоено значение с плавающей запятой `Option Strict On` , то это приведет к ошибке компилятора.</span><span class="sxs-lookup"><span data-stu-id="88835-113">If an enumeration is assigned a floating-point value with `Option Strict On`, a compiler error results.</span></span> <span data-ttu-id="88835-114">Если `Option Strict` равно `Off` , значение автоматически преобразуется в `Enum` тип.</span><span class="sxs-lookup"><span data-stu-id="88835-114">If `Option Strict` is `Off`, the value is automatically converted to the `Enum` type.</span></span>  
  
 <span data-ttu-id="88835-115">Сведения об именах и об использовании `Imports` инструкции для уточнения имен не нужны, см. в разделе [перечисления и квалификация имени](enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="88835-115">For information on names, and how to use the `Imports` statement to make name qualification unnecessary, see [Enumerations and Name Qualification](enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-declare-an-enumeration"></a><span data-ttu-id="88835-116">Объявление перечисления</span><span class="sxs-lookup"><span data-stu-id="88835-116">To declare an enumeration</span></span>  
  
1. <span data-ttu-id="88835-117">Напишите объявление, которое включает уровень доступа кода, `Enum` ключевое слово и допустимое имя, как в следующих примерах, каждый из которых объявляет другой `Enum` .</span><span class="sxs-lookup"><span data-stu-id="88835-117">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name, as in the following examples, each of which declares a different `Enum`.</span></span>  
  
     [!code-vb[VbEnumsTask#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#3)]  
  
2. <span data-ttu-id="88835-118">Определите константы в перечислении.</span><span class="sxs-lookup"><span data-stu-id="88835-118">Define the constants in the enumeration.</span></span> <span data-ttu-id="88835-119">По умолчанию первая константа в перечислении инициализируется в `0` , а последующие константы инициализируются значением, которое больше, чем предыдущая константа.</span><span class="sxs-lookup"><span data-stu-id="88835-119">By default, the first constant in an enumeration is initialized to `0`, and subsequent constants are initialized to a value of one more than the previous constant.</span></span> <span data-ttu-id="88835-120">Например, следующее перечисление `Days` содержит константу с именем, константу с именем и значением, `Sunday` `0` `Monday` `1` константу с именем `Tuesday` `2` и т. д.</span><span class="sxs-lookup"><span data-stu-id="88835-120">For example, the following enumeration, `Days`, contains a constant named `Sunday` with the value `0`, a constant named `Monday` with the value `1`, a constant named `Tuesday` with the value of `2`, and so on.</span></span>  
  
     [!code-vb[VbEnumsTask#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#4)]  
  
3. <span data-ttu-id="88835-121">Можно явно назначать значения константам в перечислении с помощью оператора присваивания.</span><span class="sxs-lookup"><span data-stu-id="88835-121">You can explicitly assign values to constants in an enumeration by using an assignment statement.</span></span> <span data-ttu-id="88835-122">Можно назначить любое целочисленное значение, включая отрицательные числа.</span><span class="sxs-lookup"><span data-stu-id="88835-122">You can assign any integer value, including negative numbers.</span></span> <span data-ttu-id="88835-123">Например, для представления ошибок могут потребоваться константы со значениями меньше нуля.</span><span class="sxs-lookup"><span data-stu-id="88835-123">For example, you may want constants with values less than zero to represent error conditions.</span></span> <span data-ttu-id="88835-124">В следующем перечислении константе `Invalid` явно присваивается значение `–1` , а константе `Sunday` присваивается значение `0` .</span><span class="sxs-lookup"><span data-stu-id="88835-124">In the following enumeration, the constant `Invalid` is explicitly assigned the value `–1`, and the constant `Sunday` is assigned the value `0`.</span></span> <span data-ttu-id="88835-125">Так как это первая константа в перечислении, она `Saturday` также инициализируется значением `0` .</span><span class="sxs-lookup"><span data-stu-id="88835-125">Because it is the first constant in the enumeration, `Saturday` is also initialized to the value `0`.</span></span> <span data-ttu-id="88835-126">Значение `Monday` равно `1` (на единицу больше, чем значение `Sunday` ); значение `Tuesday` равно `2` и т. д.</span><span class="sxs-lookup"><span data-stu-id="88835-126">The value of `Monday` is `1` (one more than the value of `Sunday`); the value of `Tuesday` is `2`, and so on.</span></span>  
  
     [!code-vb[VbEnumsTask#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#5)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a><span data-ttu-id="88835-127">Объявление перечисления в явном типе</span><span class="sxs-lookup"><span data-stu-id="88835-127">To declare an enumeration as an explicit type</span></span>  
  
- <span data-ttu-id="88835-128">Укажите тип перечисления с помощью `As` предложения, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="88835-128">Specify the type of the enum by using the `As` clause, as shown in the following example.</span></span>  
  
     [!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="88835-129">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="88835-129">See also</span></span>

- [<span data-ttu-id="88835-130">Перечисления и уточнение имен</span><span class="sxs-lookup"><span data-stu-id="88835-130">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="88835-131">Практическое руководство. Ссылка на элемент перечисления</span><span class="sxs-lookup"><span data-stu-id="88835-131">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="88835-132">Практическое руководство. Перебор элементов перечисления в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="88835-132">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="88835-133">Практическое руководство. Определение строки, связанной со значением из перечисления</span><span class="sxs-lookup"><span data-stu-id="88835-133">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="88835-134">Когда следует использовать перечисление</span><span class="sxs-lookup"><span data-stu-id="88835-134">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="88835-135">Общие сведения о константах</span><span class="sxs-lookup"><span data-stu-id="88835-135">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="88835-136">Типы данных констант и литералов</span><span class="sxs-lookup"><span data-stu-id="88835-136">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="88835-137">Константы и перечисления</span><span class="sxs-lookup"><span data-stu-id="88835-137">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
