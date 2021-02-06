---
description: 'Дополнительные сведения: Key (Visual Basic)'
title: Клавиши
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousKey
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
ms.openlocfilehash: 5ec918da661144053824ca2a734cdec11873b0e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640801"
---
# <a name="key-visual-basic"></a><span data-ttu-id="37d30-103">Key (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37d30-103">Key (Visual Basic)</span></span>

<span data-ttu-id="37d30-104">`Key`Ключевое слово позволяет задать поведение для свойств анонимных типов.</span><span class="sxs-lookup"><span data-stu-id="37d30-104">The `Key` keyword enables you to specify behavior for properties of anonymous types.</span></span> <span data-ttu-id="37d30-105">Только свойства, указанные в качестве ключевых свойств, участвуют в тестах равенства между экземплярами анонимного типа или вычислении значений хэш-кода.</span><span class="sxs-lookup"><span data-stu-id="37d30-105">Only properties you designate as key properties participate in tests of equality between anonymous type instances, or calculation of hash code values.</span></span> <span data-ttu-id="37d30-106">Значения ключевых свойств нельзя изменить.</span><span class="sxs-lookup"><span data-stu-id="37d30-106">The values of key properties cannot be changed.</span></span>  
  
 <span data-ttu-id="37d30-107">Вы назначаете свойство анонимного типа в качестве ключевого свойства, помещая ключевое слово `Key` перед его объявлением в списке инициализации.</span><span class="sxs-lookup"><span data-stu-id="37d30-107">You designate a property of an anonymous type as a key property by placing the keyword `Key` in front of its declaration in the initialization list.</span></span> <span data-ttu-id="37d30-108">В следующем примере `Airline` и `FlightNo` являются ключевыми свойствами, но `Gate` не.</span><span class="sxs-lookup"><span data-stu-id="37d30-108">In the following example, `Airline` and `FlightNo` are key properties, but `Gate` is not.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#26)]  
  
 <span data-ttu-id="37d30-109">При создании нового анонимного типа он наследуется непосредственно от <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="37d30-109">When a new anonymous type is created, it inherits directly from <xref:System.Object>.</span></span> <span data-ttu-id="37d30-110">Компилятор переопределяет три наследуемых члена: <xref:System.Object.Equals%2A> , <xref:System.Object.GetHashCode%2A> и <xref:System.Object.ToString%2A> .</span><span class="sxs-lookup"><span data-stu-id="37d30-110">The compiler overrides three inherited members: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="37d30-111">Код переопределения, созданный для <xref:System.Object.Equals%2A> и <xref:System.Object.GetHashCode%2A> , основан на ключевых свойствах.</span><span class="sxs-lookup"><span data-stu-id="37d30-111">The override code that is produced for <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> is based on key properties.</span></span> <span data-ttu-id="37d30-112">Значение, если в типе нет ключевых свойств <xref:System.Object.GetHashCode%2A> и <xref:System.Object.Equals%2A> они не переопределяются.</span><span class="sxs-lookup"><span data-stu-id="37d30-112">If there are no key properties in the type, <xref:System.Object.GetHashCode%2A> and <xref:System.Object.Equals%2A> are not overridden.</span></span>  
  
## <a name="equality"></a><span data-ttu-id="37d30-113">Равенство</span><span class="sxs-lookup"><span data-stu-id="37d30-113">Equality</span></span>  

 <span data-ttu-id="37d30-114">Два экземпляра анонимных типов равны, если они являются экземплярами одного типа и если значения их ключевых свойств равны.</span><span class="sxs-lookup"><span data-stu-id="37d30-114">Two anonymous type instances are equal if they are instances of the same type and if the values of their key properties are equal.</span></span> <span data-ttu-id="37d30-115">В следующих примерах `flight2` значение равно `flight1` из предыдущего примера, так как они являются экземплярами одного и того же анонимного типа и имеют совпадающие значения для их ключевых свойств.</span><span class="sxs-lookup"><span data-stu-id="37d30-115">In the following examples, `flight2` is equal to `flight1` from the previous example because they are instances of the same anonymous type and they have matching values for their key properties.</span></span> <span data-ttu-id="37d30-116">Однако `flight3` не равно, `flight1` поскольку имеет другое значение для ключевого свойства, `FlightNo` .</span><span class="sxs-lookup"><span data-stu-id="37d30-116">However, `flight3` is not equal to `flight1` because it has a different value for a key property, `FlightNo`.</span></span> <span data-ttu-id="37d30-117">Тип экземпляра отличается `flight4` от типа, `flight1` так как он определяет различные свойства в качестве ключевых свойств.</span><span class="sxs-lookup"><span data-stu-id="37d30-117">Instance `flight4` is not the same type as `flight1` because they designate different properties as key properties.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#27)]  
  
 <span data-ttu-id="37d30-118">Если два экземпляра объявляются только с неключевыми свойствами, идентичными в имени, типе, порядке и значении, два экземпляра не равны.</span><span class="sxs-lookup"><span data-stu-id="37d30-118">If two instances are declared with only non-key properties, identical in name, type, order, and value, the two instances are not equal.</span></span> <span data-ttu-id="37d30-119">Экземпляр без ключевых свойств равен только самому себе.</span><span class="sxs-lookup"><span data-stu-id="37d30-119">An instance without key properties is equal only to itself.</span></span>  
  
 <span data-ttu-id="37d30-120">Дополнительные сведения об условиях, при которых два экземпляра анонимных типов являются экземплярами одного и того же анонимного типа, см. в разделе [анонимные типы](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="37d30-120">For more information about the conditions under which two anonymous type instances are instances of the same anonymous type, see [Anonymous Types](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="hash-code-calculation"></a><span data-ttu-id="37d30-121">Вычисление хэш-кода</span><span class="sxs-lookup"><span data-stu-id="37d30-121">Hash Code Calculation</span></span>  

 <span data-ttu-id="37d30-122">Например <xref:System.Object.Equals%2A> , хэш-функция, определенная в <xref:System.Object.GetHashCode%2A> для анонимного типа, основана на ключевых свойствах типа.</span><span class="sxs-lookup"><span data-stu-id="37d30-122">Like <xref:System.Object.Equals%2A>, the hash function that is defined in <xref:System.Object.GetHashCode%2A> for an anonymous type is based on the key properties of the type.</span></span> <span data-ttu-id="37d30-123">В следующих примерах показано взаимодействие между ключевыми свойствами и значениями хэш-кода.</span><span class="sxs-lookup"><span data-stu-id="37d30-123">The following examples show the interaction between key properties and hash code values.</span></span>  
  
 <span data-ttu-id="37d30-124">Экземпляры анонимного типа, имеющие одинаковые значения для всех ключевых свойств, имеют одинаковое значение хэш-кода, даже если неключевые свойства не имеют совпадающих значений.</span><span class="sxs-lookup"><span data-stu-id="37d30-124">Instances of an anonymous type that have the same values for all key properties have the same hash code value, even if non-key properties do not have matching values.</span></span> <span data-ttu-id="37d30-125">Следующая инструкция возвращает значение `True`.</span><span class="sxs-lookup"><span data-stu-id="37d30-125">The following statement returns `True`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#37)]  
  
 <span data-ttu-id="37d30-126">Экземпляры анонимного типа, имеющие разные значения для одного или нескольких ключевых свойств, имеют разные значения хэш-кода.</span><span class="sxs-lookup"><span data-stu-id="37d30-126">Instances of an anonymous type that have different values for one or more key properties have different hash code values.</span></span> <span data-ttu-id="37d30-127">Следующая инструкция возвращает значение `False`.</span><span class="sxs-lookup"><span data-stu-id="37d30-127">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#38)]  
  
 <span data-ttu-id="37d30-128">Экземпляры анонимных типов, которые обозначают различные свойства в качестве ключевых свойств, не являются экземплярами одного типа.</span><span class="sxs-lookup"><span data-stu-id="37d30-128">Instances of anonymous types that designate different properties as key properties are not instances of the same type.</span></span> <span data-ttu-id="37d30-129">Они имеют разные значения хэш-кода, даже если имена и значения всех свойств одинаковы.</span><span class="sxs-lookup"><span data-stu-id="37d30-129">They have different hash code values even when the names and values of all properties are the same.</span></span> <span data-ttu-id="37d30-130">Следующая инструкция возвращает значение `False`.</span><span class="sxs-lookup"><span data-stu-id="37d30-130">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#39)]  
  
## <a name="read-only-values"></a><span data-ttu-id="37d30-131">Значения Read-Only</span><span class="sxs-lookup"><span data-stu-id="37d30-131">Read-Only Values</span></span>  

 <span data-ttu-id="37d30-132">Значения ключевых свойств нельзя изменить.</span><span class="sxs-lookup"><span data-stu-id="37d30-132">The values of key properties cannot be changed.</span></span> <span data-ttu-id="37d30-133">Например, в `flight1` предыдущих примерах `Airline` `FlightNo` поля и доступны только для чтения, но `Gate` могут быть изменены.</span><span class="sxs-lookup"><span data-stu-id="37d30-133">For example, in `flight1` in the earlier examples, the `Airline` and `FlightNo` fields are read-only, but `Gate` can be changed.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="37d30-134">См. также</span><span class="sxs-lookup"><span data-stu-id="37d30-134">See also</span></span>

- [<span data-ttu-id="37d30-135">Определение анонимного типа</span><span class="sxs-lookup"><span data-stu-id="37d30-135">Anonymous Type Definition</span></span>](../../programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [<span data-ttu-id="37d30-136">Практическое руководство. Выведение имен свойств и типов в объявлениях анонимных типов</span><span class="sxs-lookup"><span data-stu-id="37d30-136">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [<span data-ttu-id="37d30-137">Анонимные типы</span><span class="sxs-lookup"><span data-stu-id="37d30-137">Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
