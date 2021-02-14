---
description: 'Дополнительные сведения: повышение типа (Visual Basic)'
title: Повышение типа
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- Partial keyword [Visual Basic], unexpected results with type promotion
- scope [Visual Basic], declared elements
- scope [Visual Basic], Visual Basic
- type promotion
- declared elements [Visual Basic], visibility
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
ms.openlocfilehash: fd8a30fb7e442d82222ae55daabf70bd8e532138
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434723"
---
# <a name="type-promotion-visual-basic"></a><span data-ttu-id="54101-103">Повышение типа (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="54101-103">Type Promotion (Visual Basic)</span></span>

<span data-ttu-id="54101-104">При объявлении программного элемента в модуле Visual Basic повышает его область до пространства имен, содержащего модуль.</span><span class="sxs-lookup"><span data-stu-id="54101-104">When you declare a programming element in a module, Visual Basic promotes its scope to the namespace containing the module.</span></span> <span data-ttu-id="54101-105">Это называется *повышением типа*.</span><span class="sxs-lookup"><span data-stu-id="54101-105">This is known as *type promotion*.</span></span>  
  
 <span data-ttu-id="54101-106">В следующем примере показано определение каркаса для модуля и два члена этого модуля.</span><span class="sxs-lookup"><span data-stu-id="54101-106">The following example shows a skeleton definition of a module and two members of that module.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#1)]  
  
 <span data-ttu-id="54101-107">В `projModule` элементы программирования, объявленные на уровне модуля, помещаются в `projNamespace` .</span><span class="sxs-lookup"><span data-stu-id="54101-107">Within `projModule`, programming elements declared at module level are promoted to `projNamespace`.</span></span> <span data-ttu-id="54101-108">В предыдущем примере `basicEnum` и `innerClass` были повышены, но `numberSub` не являются, поскольку не объявлены на уровне модуля.</span><span class="sxs-lookup"><span data-stu-id="54101-108">In the preceding example, `basicEnum` and `innerClass` are promoted, but `numberSub` is not, because it is not declared at module level.</span></span>  
  
## <a name="effect-of-type-promotion"></a><span data-ttu-id="54101-109">Результат повышения типа</span><span class="sxs-lookup"><span data-stu-id="54101-109">Effect of Type Promotion</span></span>  

 <span data-ttu-id="54101-110">Результатом повышения типа является то, что Уточняющая строка не обязательно должна включать имя модуля.</span><span class="sxs-lookup"><span data-stu-id="54101-110">The effect of type promotion is that a qualification string does not need to include the module name.</span></span> <span data-ttu-id="54101-111">Следующий пример выполняет два вызова процедуры в предыдущем примере.</span><span class="sxs-lookup"><span data-stu-id="54101-111">The following example makes two calls to the procedure in the preceding example.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#2)]  
  
 <span data-ttu-id="54101-112">В предыдущем примере первый вызов использует полные строки квалификации.</span><span class="sxs-lookup"><span data-stu-id="54101-112">In the preceding example, the first call uses complete qualification strings.</span></span> <span data-ttu-id="54101-113">Однако это необязательно из-за продвижения типа.</span><span class="sxs-lookup"><span data-stu-id="54101-113">However, this is not necessary because of type promotion.</span></span> <span data-ttu-id="54101-114">Второй вызов также обращается к членам модуля, не включая `projModule` в строки квалификации.</span><span class="sxs-lookup"><span data-stu-id="54101-114">The second call also accesses the module's members without including `projModule` in the qualification strings.</span></span>  
  
## <a name="defeat-of-type-promotion"></a><span data-ttu-id="54101-115">Отмена повышения типа</span><span class="sxs-lookup"><span data-stu-id="54101-115">Defeat of Type Promotion</span></span>  

 <span data-ttu-id="54101-116">Если пространство имен уже содержит член с тем же именем, что и у члена модуля, повышение типа для этого члена модуля будет недоступно.</span><span class="sxs-lookup"><span data-stu-id="54101-116">If the namespace already has a member with the same name as a module member, type promotion is defeated for that module member.</span></span> <span data-ttu-id="54101-117">В следующем примере показано определение схемы перечисления и модуля в пределах одного пространства имен.</span><span class="sxs-lookup"><span data-stu-id="54101-117">The following example shows a skeleton definition of an enumeration and a module within the same namespace.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#3)]  
  
 <span data-ttu-id="54101-118">В предыдущем примере Visual Basic не может повысить уровень до класса, `abc` `thisNameSpace` так как на уровне пространства имен уже существует перечисление с тем же именем.</span><span class="sxs-lookup"><span data-stu-id="54101-118">In the preceding example, Visual Basic cannot promote class `abc` to `thisNameSpace` because there is already an enumeration with the same name at namespace level.</span></span> <span data-ttu-id="54101-119">Для доступа `abcSub` необходимо использовать полную строку квалификации `thisNamespace.thisModule.abc.abcSub` .</span><span class="sxs-lookup"><span data-stu-id="54101-119">To access `abcSub`, you must use the full qualification string `thisNamespace.thisModule.abc.abcSub`.</span></span> <span data-ttu-id="54101-120">Однако класс `xyz` по-прежнему становится более продвинутым, и к нему можно получить доступ `xyzSub` с помощью более короткой уточняющей строки `thisNamespace.xyz.xyzSub` .</span><span class="sxs-lookup"><span data-stu-id="54101-120">However, class `xyz` is still promoted, and you can access `xyzSub` with the shorter qualification string `thisNamespace.xyz.xyzSub`.</span></span>  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a><span data-ttu-id="54101-121">Отмена повышения типа для разделяемых типов</span><span class="sxs-lookup"><span data-stu-id="54101-121">Defeat of Type Promotion for Partial Types</span></span>  

 <span data-ttu-id="54101-122">Если класс или структура внутри модуля использует ключевое слово [partial](../../../language-reference/modifiers/partial.md) , то продвижение типов автоматически отменяется для этого класса или структуры, независимо от того, имеет ли пространство имен член с таким же именем.</span><span class="sxs-lookup"><span data-stu-id="54101-122">If a class or structure inside a module uses the [Partial](../../../language-reference/modifiers/partial.md) keyword, type promotion is automatically defeated for that class or structure, whether or not the namespace has a member with the same name.</span></span> <span data-ttu-id="54101-123">Другие элементы в модуле по-прежнему имеют право на повышение типа.</span><span class="sxs-lookup"><span data-stu-id="54101-123">Other elements in the module are still eligible for type promotion.</span></span>  
  
 <span data-ttu-id="54101-124">**Последствия.**</span><span class="sxs-lookup"><span data-stu-id="54101-124">**Consequences.**</span></span> <span data-ttu-id="54101-125">Отмена повышения типа частичного определения может привести к непредвиденным результатам и даже к ошибкам компилятора.</span><span class="sxs-lookup"><span data-stu-id="54101-125">Defeat of type promotion of a partial definition can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="54101-126">В следующем примере показана скелетная часть определений класса, один из которых находится внутри модуля.</span><span class="sxs-lookup"><span data-stu-id="54101-126">The following example shows skeleton partial definitions of a class, one of which is inside a module.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#4)]  
  
 <span data-ttu-id="54101-127">В предыдущем примере разработчик может ожидать, что компилятор объединит два разделяемых определения `sampleClass` .</span><span class="sxs-lookup"><span data-stu-id="54101-127">In the preceding example, the developer might expect the compiler to merge the two partial definitions of `sampleClass`.</span></span> <span data-ttu-id="54101-128">Однако компилятор не учитывает продвижение для частичного определения внутри `sampleModule` .</span><span class="sxs-lookup"><span data-stu-id="54101-128">However, the compiler does not consider promotion for the partial definition inside `sampleModule`.</span></span> <span data-ttu-id="54101-129">В результате он пытается скомпилировать два отдельных и разных класса с именами, `sampleClass` но с разными путями уточнения.</span><span class="sxs-lookup"><span data-stu-id="54101-129">As a result, it attempts to compile two separate and distinct classes, both named `sampleClass` but with different qualification paths.</span></span>  
  
 <span data-ttu-id="54101-130">Компилятор объединяет частичные определения, только если их полные пути идентичны.</span><span class="sxs-lookup"><span data-stu-id="54101-130">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="54101-131">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="54101-131">Recommendations</span></span>  

 <span data-ttu-id="54101-132">Следующие рекомендации являются хорошей практикой программирования.</span><span class="sxs-lookup"><span data-stu-id="54101-132">The following recommendations represent good programming practice.</span></span>  
  
- <span data-ttu-id="54101-133">**Уникальные имена.**</span><span class="sxs-lookup"><span data-stu-id="54101-133">**Unique Names.**</span></span> <span data-ttu-id="54101-134">При наличии полного контроля над именованием программных элементов всегда рекомендуется использовать уникальные имена везде.</span><span class="sxs-lookup"><span data-stu-id="54101-134">When you have full control over the naming of programming elements, it is always a good idea to use unique names everywhere.</span></span> <span data-ttu-id="54101-135">Идентичные имена нуждаются в дополнительной квалификации и могут усложнить чтение кода.</span><span class="sxs-lookup"><span data-stu-id="54101-135">Identical names require extra qualification and can make your code harder to read.</span></span> <span data-ttu-id="54101-136">Они также могут привести к незначительным ошибкам и непредвиденным результатам.</span><span class="sxs-lookup"><span data-stu-id="54101-136">They can also lead to subtle errors and unexpected results.</span></span>  
  
- <span data-ttu-id="54101-137">**Полное уточнение.**</span><span class="sxs-lookup"><span data-stu-id="54101-137">**Full Qualification.**</span></span> <span data-ttu-id="54101-138">При работе с модулями и другими элементами в одном пространстве имен наиболее надежный подход заключается в том, чтобы всегда использовать полную квалификацию для всех программных элементов.</span><span class="sxs-lookup"><span data-stu-id="54101-138">When you are working with modules and other elements in the same namespace, the safest approach is to always use full qualification for all programming elements.</span></span> <span data-ttu-id="54101-139">Если повышение типа для члена модуля не используется и вы не полностью уточняете этот член, вы можете случайно получить доступ к другому программному элементу.</span><span class="sxs-lookup"><span data-stu-id="54101-139">If type promotion is defeated for a module member and you do not fully qualify that member, you could inadvertently access a different programming element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54101-140">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="54101-140">See also</span></span>

- [<span data-ttu-id="54101-141">Оператор Module</span><span class="sxs-lookup"><span data-stu-id="54101-141">Module Statement</span></span>](../../../language-reference/statements/module-statement.md)
- [<span data-ttu-id="54101-142">Оператор Namespace</span><span class="sxs-lookup"><span data-stu-id="54101-142">Namespace Statement</span></span>](../../../language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="54101-143">Partial</span><span class="sxs-lookup"><span data-stu-id="54101-143">Partial</span></span>](../../../language-reference/modifiers/partial.md)
- [<span data-ttu-id="54101-144">Область видимости в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="54101-144">Scope in Visual Basic</span></span>](scope.md)
- [<span data-ttu-id="54101-145">Практическое руководство. Управление областью действия переменной</span><span class="sxs-lookup"><span data-stu-id="54101-145">How to: Control the Scope of a Variable</span></span>](how-to-control-the-scope-of-a-variable.md)
- [<span data-ttu-id="54101-146">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="54101-146">References to Declared Elements</span></span>](references-to-declared-elements.md)
