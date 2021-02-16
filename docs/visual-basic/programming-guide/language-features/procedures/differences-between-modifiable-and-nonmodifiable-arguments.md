---
description: 'Подробнее: различия между изменяемыми и неизменяемыми аргументами (Visual Basic)'
title: Различия между изменяемыми и неизменяемыми аргументами
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
ms.openlocfilehash: 8d83802b4b8830a17412fdef44eabd2e5b8a7f2d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472635"
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a><span data-ttu-id="d873d-103">Различия между аргументами Modifiable и Nonmodifiable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d873d-103">Differences Between Modifiable and Nonmodifiable Arguments (Visual Basic)</span></span>

<span data-ttu-id="d873d-104">При вызове процедуры в нее обычно передается один или несколько аргументов.</span><span class="sxs-lookup"><span data-stu-id="d873d-104">When you call a procedure, you typically pass one or more arguments to it.</span></span> <span data-ttu-id="d873d-105">Каждый аргумент соответствует базовому программному элементу.</span><span class="sxs-lookup"><span data-stu-id="d873d-105">Each argument corresponds to an underlying programming element.</span></span> <span data-ttu-id="d873d-106">Как базовые элементы, так и сами аргументы могут быть либо изменяемыми, либо неизменяемыми.</span><span class="sxs-lookup"><span data-stu-id="d873d-106">Both the underlying elements and the arguments themselves can be either modifiable or nonmodifiable.</span></span>  
  
## <a name="modifiable-and-nonmodifiable-elements"></a><span data-ttu-id="d873d-107">Изменяемые и неизменяемые элементы</span><span class="sxs-lookup"><span data-stu-id="d873d-107">Modifiable and Nonmodifiable Elements</span></span>  

 <span data-ttu-id="d873d-108">Программным элементом может быть *изменяемый элемент*, для которого может быть изменено значение, или *неизменяемый элемент*, имеющий фиксированное значение после создания.</span><span class="sxs-lookup"><span data-stu-id="d873d-108">A programming element can be either a *modifiable element*, which can have its value changed, or a *nonmodifiable element*, which has a fixed value once it has been created.</span></span>  
  
 <span data-ttu-id="d873d-109">В следующей таблице перечислены изменяемые и неизменяемые элементы программирования.</span><span class="sxs-lookup"><span data-stu-id="d873d-109">The following table lists modifiable and nonmodifiable programming elements.</span></span>  
  
|<span data-ttu-id="d873d-110">Изменяемые элементы</span><span class="sxs-lookup"><span data-stu-id="d873d-110">Modifiable elements</span></span>|<span data-ttu-id="d873d-111">Неизменяемые элементы</span><span class="sxs-lookup"><span data-stu-id="d873d-111">Nonmodifiable elements</span></span>|  
|-------------------------|----------------------------|  
|<span data-ttu-id="d873d-112">Локальные переменные (объявленные в процедурах), включая переменные объекта, за исключением только для чтения</span><span class="sxs-lookup"><span data-stu-id="d873d-112">Local variables (declared inside procedures), including object variables, except for read-only</span></span>|<span data-ttu-id="d873d-113">Переменные, поля и свойства только для чтения</span><span class="sxs-lookup"><span data-stu-id="d873d-113">Read-only variables, fields, and properties</span></span>|  
|<span data-ttu-id="d873d-114">Поля (переменные-члены модулей, классов и структур), кроме только для чтения</span><span class="sxs-lookup"><span data-stu-id="d873d-114">Fields (member variables of modules, classes, and structures), except for read-only</span></span>|<span data-ttu-id="d873d-115">Константы и литералы</span><span class="sxs-lookup"><span data-stu-id="d873d-115">Constants and literals</span></span>|  
|<span data-ttu-id="d873d-116">Свойства, кроме "только для чтения"</span><span class="sxs-lookup"><span data-stu-id="d873d-116">Properties, except for read-only</span></span>|<span data-ttu-id="d873d-117">Члены перечисления</span><span class="sxs-lookup"><span data-stu-id="d873d-117">Enumeration members</span></span>|  
|<span data-ttu-id="d873d-118">Элементы массива</span><span class="sxs-lookup"><span data-stu-id="d873d-118">Array elements</span></span>|<span data-ttu-id="d873d-119">Выражения (даже если их элементы являются изменяемыми)</span><span class="sxs-lookup"><span data-stu-id="d873d-119">Expressions (even if their elements are modifiable)</span></span>|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a><span data-ttu-id="d873d-120">Изменяемые и неизменяемые аргументы</span><span class="sxs-lookup"><span data-stu-id="d873d-120">Modifiable and Nonmodifiable Arguments</span></span>  

 <span data-ttu-id="d873d-121">*Изменяемый аргумент* — это один из изменяемых базовых элементов.</span><span class="sxs-lookup"><span data-stu-id="d873d-121">A *modifiable argument* is one with a modifiable underlying element.</span></span> <span data-ttu-id="d873d-122">Вызывающий код может сохранить новое значение в любое время, и при передаче аргумента [ByRef](../../../language-reference/modifiers/byref.md)код в процедуре также может изменить базовый элемент в вызывающем коде.</span><span class="sxs-lookup"><span data-stu-id="d873d-122">The calling code can store a new value at any time, and if you pass the argument [ByRef](../../../language-reference/modifiers/byref.md), the code in the procedure can also modify the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="d873d-123">*Неизменяемый аргумент* либо имеет неизменяемый базовый элемент, либо передается [ByVal](../../../language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="d873d-123">A *nonmodifiable argument* either has a nonmodifiable underlying element or is passed [ByVal](../../../language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="d873d-124">Процедура не может изменить базовый элемент в вызывающем коде, даже если это изменяемый элемент.</span><span class="sxs-lookup"><span data-stu-id="d873d-124">The procedure cannot modify the underlying element in the calling code, even if it is a modifiable element.</span></span> <span data-ttu-id="d873d-125">Если это неизменяемый элемент, то сам вызывающий код не может изменить его.</span><span class="sxs-lookup"><span data-stu-id="d873d-125">If it is a nonmodifiable element, the calling code itself cannot modify it.</span></span>  
  
 <span data-ttu-id="d873d-126">Вызванная процедура может изменить свою локальную копию неизменяемого аргумента, но это изменение не влияет на базовый элемент в вызывающем коде.</span><span class="sxs-lookup"><span data-stu-id="d873d-126">The called procedure might modify its local copy of a nonmodifiable argument, but that modification does not affect the underlying element in the calling code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d873d-127">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="d873d-127">See also</span></span>

- [<span data-ttu-id="d873d-128">Процедуры</span><span class="sxs-lookup"><span data-stu-id="d873d-128">Procedures</span></span>](./index.md)
- [<span data-ttu-id="d873d-129">Параметры и аргументы процедуры</span><span class="sxs-lookup"><span data-stu-id="d873d-129">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="d873d-130">Практическое руководство. Передача аргументов в процедуру</span><span class="sxs-lookup"><span data-stu-id="d873d-130">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="d873d-131">Передача аргументов по значению и по ссылке</span><span class="sxs-lookup"><span data-stu-id="d873d-131">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="d873d-132">Различия между передачей аргумента по значению и по ссылке</span><span class="sxs-lookup"><span data-stu-id="d873d-132">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="d873d-133">Практическое руководство. Изменение значения аргумента процедуры</span><span class="sxs-lookup"><span data-stu-id="d873d-133">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="d873d-134">Практическое руководство. Защита аргумента процедуры от изменений значения</span><span class="sxs-lookup"><span data-stu-id="d873d-134">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="d873d-135">Практическое руководство. Принудительная передача аргумента по значению</span><span class="sxs-lookup"><span data-stu-id="d873d-135">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="d873d-136">Передача аргументов по позиции и по имени</span><span class="sxs-lookup"><span data-stu-id="d873d-136">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="d873d-137">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="d873d-137">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
