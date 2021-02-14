---
description: 'Узнайте подробнее о: Перегрузки операторов'
title: Перегрузки операторов
ms.date: 10/22/2008
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
ms.openlocfilehash: e6552f35081afa542e4dc14239206a63c7c1bd59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713329"
---
# <a name="operator-overloads"></a><span data-ttu-id="6425b-103">Перегрузки операторов</span><span class="sxs-lookup"><span data-stu-id="6425b-103">Operator Overloads</span></span>

<span data-ttu-id="6425b-104">Перегрузки операторов позволяют отображать типы платформ, как встроенные примитивы языка.</span><span class="sxs-lookup"><span data-stu-id="6425b-104">Operator overloads allow framework types to appear as if they were built-in language primitives.</span></span>

 <span data-ttu-id="6425b-105">Хотя в некоторых ситуациях это разрешено и полезно, перегрузки операторов следует использовать осторожно.</span><span class="sxs-lookup"><span data-stu-id="6425b-105">Although allowed and useful in some situations, operator overloads should be used cautiously.</span></span> <span data-ttu-id="6425b-106">Существует множество случаев злоупотреблений перегрузкой операторов. Например, когда конструкторы платформы использовали операторы для операций, которые должны быть простыми методами.</span><span class="sxs-lookup"><span data-stu-id="6425b-106">There are many cases in which operator overloading has been abused, such as when framework designers started to use operators for operations that should be simple methods.</span></span> <span data-ttu-id="6425b-107">Следующие рекомендации помогут решить, когда и как использовать перегрузку операторов.</span><span class="sxs-lookup"><span data-stu-id="6425b-107">The following guidelines should help you decide when and how to use operator overloading.</span></span>

 <span data-ttu-id="6425b-108">❌ НЕ определяйте перегрузки операторов, за исключением типов, которые должны быть похожи на примитивные (встроенные) типы.</span><span class="sxs-lookup"><span data-stu-id="6425b-108">❌ AVOID defining operator overloads, except in types that should feel like primitive (built-in) types.</span></span>

 <span data-ttu-id="6425b-109">✔️ РЕКОМЕНДУЕТСЯ определять перегрузки операторов в типе, который должен быть похож на примитивный тип.</span><span class="sxs-lookup"><span data-stu-id="6425b-109">✔️ CONSIDER defining operator overloads in a type that should feel like a primitive type.</span></span>

 <span data-ttu-id="6425b-110">Например, в <xref:System.String?displayProperty=nameWithType> определены `operator==` и `operator!=`.</span><span class="sxs-lookup"><span data-stu-id="6425b-110">For example, <xref:System.String?displayProperty=nameWithType> has `operator==` and `operator!=` defined.</span></span>

 <span data-ttu-id="6425b-111">✔️ РЕКОМЕНДУЕТСЯ️ определить перегрузки операторов в структурах, которые представляют числа (например, <xref:System.Decimal?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="6425b-111">✔️ DO define operator overloads in structs that represent numbers (such as <xref:System.Decimal?displayProperty=nameWithType>).</span></span>

 <span data-ttu-id="6425b-112">❌ ОТНЕСИТЕСЬ к определению перегрузки операторов серьезно.</span><span class="sxs-lookup"><span data-stu-id="6425b-112">❌ DO NOT be cute when defining operator overloads.</span></span>

 <span data-ttu-id="6425b-113">Перегрузка операторов полезна в случаях, когда сразу очевидно, каким будет результат операции.</span><span class="sxs-lookup"><span data-stu-id="6425b-113">Operator overloading is useful in cases in which it is immediately obvious what the result of the operation will be.</span></span> <span data-ttu-id="6425b-114">Например, есть смысл вычесть одно значение <xref:System.DateTime> из другого `DateTime` и получить <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="6425b-114">For example, it makes sense to be able to subtract one <xref:System.DateTime> from another `DateTime` and get a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="6425b-115">Однако не рекомендуется использовать оператор логического объединения, чтобы объединить два запроса к базе данных или использовать оператор сдвига для записи в поток.</span><span class="sxs-lookup"><span data-stu-id="6425b-115">However, it is not appropriate to use the logical union operator to union two database queries, or to use the shift operator to write to a stream.</span></span>

 <span data-ttu-id="6425b-116">❌ НЕ следует предоставлять перегрузки операторов, если по крайней мере один из операндов не относится к типу, определяющему перегрузку.</span><span class="sxs-lookup"><span data-stu-id="6425b-116">❌ DO NOT provide operator overloads unless at least one of the operands is of the type defining the overload.</span></span>

 <span data-ttu-id="6425b-117">✔️ ВЫПОЛНЯЙТЕ операторы перегрузки в симметричном режиме.</span><span class="sxs-lookup"><span data-stu-id="6425b-117">✔️ DO overload operators in a symmetric fashion.</span></span>

 <span data-ttu-id="6425b-118">Например, если перегрузить `operator==`, необходимо также перегрузить `operator!=`.</span><span class="sxs-lookup"><span data-stu-id="6425b-118">For example, if you overload the `operator==`, you should also overload the `operator!=`.</span></span> <span data-ttu-id="6425b-119">Аналогично если перегрузить `operator<`, то необходимо также перегрузить `operator>` и т. д.</span><span class="sxs-lookup"><span data-stu-id="6425b-119">Similarly, if you overload the `operator<`, you should also overload the `operator>`, and so on.</span></span>

 <span data-ttu-id="6425b-120">✔️️ ПОДБЕРИТЕ методы с понятными именами, которые соответствуют каждому перегруженному оператору.</span><span class="sxs-lookup"><span data-stu-id="6425b-120">✔️ CONSIDER providing methods with friendly names that correspond to each overloaded operator.</span></span>

 <span data-ttu-id="6425b-121">Многие языки не поддерживают перегрузку операторов.</span><span class="sxs-lookup"><span data-stu-id="6425b-121">Many languages do not support operator overloading.</span></span> <span data-ttu-id="6425b-122">По этой причине рекомендуется, чтобы типы с перегруженными операторами, включали дополнительный метод с соответствующим доменным именем, обеспечивающим эквивалентную функциональность.</span><span class="sxs-lookup"><span data-stu-id="6425b-122">For this reason, it is recommended that types that overload operators include a secondary method with an appropriate domain-specific name that provides equivalent functionality.</span></span>

 <span data-ttu-id="6425b-123">В следующей таблице приведен список операторов и соответствующие понятные имена методов.</span><span class="sxs-lookup"><span data-stu-id="6425b-123">The following table contains a list of operators and the corresponding friendly method names.</span></span>

|<span data-ttu-id="6425b-124">Символ оператора C#</span><span class="sxs-lookup"><span data-stu-id="6425b-124">C# Operator Symbol</span></span>|<span data-ttu-id="6425b-125">Имя метаданных</span><span class="sxs-lookup"><span data-stu-id="6425b-125">Metadata Name</span></span>|<span data-ttu-id="6425b-126">Понятное имя</span><span class="sxs-lookup"><span data-stu-id="6425b-126">Friendly Name</span></span>|
|-------------------------|-------------------|-------------------|
|`N/A`|`op_Implicit`|`To<TypeName>/From<TypeName>`|
|`N/A`|`op_Explicit`|`To<TypeName>/From<TypeName>`|
|`+ (binary)`|`op_Addition`|`Add`|
|`- (binary)`|`op_Subtraction`|`Subtract`|
|`* (binary)`|`op_Multiply`|`Multiply`|
|`/`|`op_Division`|`Divide`|
|`%`|`op_Modulus`|`Mod or Remainder`|
|`^`|`op_ExclusiveOr`|`Xor`|
|`& (binary)`|`op_BitwiseAnd`|`BitwiseAnd`|
|<code>&#124;</code>|`op_BitwiseOr`|`BitwiseOr`|
|`&&`|`op_LogicalAnd`|`And`|
|<code>&#124;&#124;</code>|`op_LogicalOr`|`Or`|
|`=`|`op_Assign`|`Assign`|
|`<<`|`op_LeftShift`|`LeftShift`|
|`>>`|`op_RightShift`|`RightShift`|
|`N/A`|`op_SignedRightShift`|`SignedRightShift`|
|`N/A`|`op_UnsignedRightShift`|`UnsignedRightShift`|
|`==`|`op_Equality`|`Equals`|
|`!=`|`op_Inequality`|`Equals`|
|`>`|`op_GreaterThan`|`CompareTo`|
|`<`|`op_LessThan`|`CompareTo`|
|`>=`|`op_GreaterThanOrEqual`|`CompareTo`|
|`<=`|`op_LessThanOrEqual`|`CompareTo`|
|`*=`|`op_MultiplicationAssignment`|`Multiply`|
|`-=`|`op_SubtractionAssignment`|`Subtract`|
|`^=`|`op_ExclusiveOrAssignment`|`Xor`|
|`<<=`|`op_LeftShiftAssignment`|`LeftShift`|
|`%=`|`op_ModulusAssignment`|`Mod`|
|`+=`|`op_AdditionAssignment`|`Add`|
|`&=`|`op_BitwiseAndAssignment`|`BitwiseAnd`|
|<code>&#124;=</code>|`op_BitwiseOrAssignment`|`BitwiseOr`|
|`,`|`op_Comma`|`Comma`|
|`/=`|`op_DivisionAssignment`|`Divide`|
|`--`|`op_Decrement`|`Decrement`|
|`++`|`op_Increment`|`Increment`|
|`- (unary)`|`op_UnaryNegation`|`Negate`|
|`+ (unary)`|`op_UnaryPlus`|`Plus`|
|`~`|`op_OnesComplement`|`OnesComplement`|

### <a name="overloading-operator-"></a><span data-ttu-id="6425b-127">Перегрузка оператора равенства ==</span><span class="sxs-lookup"><span data-stu-id="6425b-127">Overloading Operator ==</span></span>

 <span data-ttu-id="6425b-128">Перегрузка `operator ==` довольно сложная.</span><span class="sxs-lookup"><span data-stu-id="6425b-128">Overloading `operator ==` is quite complicated.</span></span> <span data-ttu-id="6425b-129">Семантика оператора должна быть совместима с несколькими другими элементами, например <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6425b-129">The semantics of the operator need to be compatible with several other members, such as <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span></span>

### <a name="conversion-operators"></a><span data-ttu-id="6425b-130">Операторы преобразования</span><span class="sxs-lookup"><span data-stu-id="6425b-130">Conversion Operators</span></span>

 <span data-ttu-id="6425b-131">Операторы преобразования — это унарные операторы, позволяющие выполнять преобразование из одного типа в другой.</span><span class="sxs-lookup"><span data-stu-id="6425b-131">Conversion operators are unary operators that allow conversion from one type to another.</span></span> <span data-ttu-id="6425b-132">Операторы должны быть определены как статические элементы либо как операнды или типы возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="6425b-132">The operators must be defined as static members on either the operand or the return type.</span></span> <span data-ttu-id="6425b-133">Существует два типа операторов преобразования: implicit и explicit.</span><span class="sxs-lookup"><span data-stu-id="6425b-133">There are two types of conversion operators: implicit and explicit.</span></span>

 <span data-ttu-id="6425b-134">❌ НЕ предоставляйте оператор преобразования, если пользователь явно не ожидает такое преобразование.</span><span class="sxs-lookup"><span data-stu-id="6425b-134">❌ DO NOT provide a conversion operator if such conversion is not clearly expected by the end users.</span></span>

 <span data-ttu-id="6425b-135">❌ НЕ определяйте операторы преобразования за пределами домена типа.</span><span class="sxs-lookup"><span data-stu-id="6425b-135">❌ DO NOT define conversion operators outside of a type’s domain.</span></span>

 <span data-ttu-id="6425b-136">Например, <xref:System.Int32>, <xref:System.Double> и <xref:System.Decimal> являются числовыми типами, а <xref:System.DateTime> — нет.</span><span class="sxs-lookup"><span data-stu-id="6425b-136">For example, <xref:System.Int32>, <xref:System.Double>, and <xref:System.Decimal> are all numeric types, whereas <xref:System.DateTime> is not.</span></span> <span data-ttu-id="6425b-137">Поэтому при преобразовании `Double(long)` в `DateTime` не должен использоваться оператор преобразования.</span><span class="sxs-lookup"><span data-stu-id="6425b-137">Therefore, there should be no conversion operator to convert a `Double(long)` to a `DateTime`.</span></span> <span data-ttu-id="6425b-138">В таком случае предпочтительнее использовать конструктор.</span><span class="sxs-lookup"><span data-stu-id="6425b-138">A constructor is preferred in such a case.</span></span>

 <span data-ttu-id="6425b-139">❌ НЕ предоставляйте неявный оператор преобразования, если преобразование может быть с потерями.</span><span class="sxs-lookup"><span data-stu-id="6425b-139">❌ DO NOT provide an implicit conversion operator if the conversion is potentially lossy.</span></span>

 <span data-ttu-id="6425b-140">Например, не существует неявного преобразования из `Double` в `Int32`, так как `Double`имеет более широкий диапазон, чем `Int32`.</span><span class="sxs-lookup"><span data-stu-id="6425b-140">For example, there should not be an implicit conversion from `Double` to `Int32` because `Double` has a wider range than `Int32`.</span></span> <span data-ttu-id="6425b-141">Явный оператор преобразования можно предоставить даже в том случае, если преобразование может быть с потерями.</span><span class="sxs-lookup"><span data-stu-id="6425b-141">An explicit conversion operator can be provided even if the conversion is potentially lossy.</span></span>

 <span data-ttu-id="6425b-142">❌ НЕ создавайте исключения из неявных приведений.</span><span class="sxs-lookup"><span data-stu-id="6425b-142">❌ DO NOT throw exceptions from implicit casts.</span></span>

 <span data-ttu-id="6425b-143">Пользователям очень сложно понять, что происходит, так как они могут не знать, что выполняется преобразование.</span><span class="sxs-lookup"><span data-stu-id="6425b-143">It is very difficult for end users to understand what is happening, because they might not be aware that a conversion is taking place.</span></span>

 <span data-ttu-id="6425b-144">✔️ РЕКОМЕНДУЕТСЯ создать <xref:System.InvalidCastException?displayProperty=nameWithType>, если вызов оператора приведения приводит к преобразованию с потерями, а контракт оператора не допускает этого.</span><span class="sxs-lookup"><span data-stu-id="6425b-144">✔️ DO throw <xref:System.InvalidCastException?displayProperty=nameWithType> if a call to a cast operator results in a lossy conversion and the contract of the operator does not allow lossy conversions.</span></span>

 <span data-ttu-id="6425b-145">*Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="6425b-145">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="6425b-146">*Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="6425b-146">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="6425b-147">См. также</span><span class="sxs-lookup"><span data-stu-id="6425b-147">See also</span></span>

- [<span data-ttu-id="6425b-148">Правила разработки членов</span><span class="sxs-lookup"><span data-stu-id="6425b-148">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="6425b-149">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="6425b-149">Framework Design Guidelines</span></span>](index.md)
