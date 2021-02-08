---
description: Дополнительные сведения о операторе TypeOf (Visual Basic)
title: Оператор TypeOf
ms.date: 07/20/2015
f1_keywords:
- TypeOf
- vb.TypeOf
helpviewer_keywords:
- types [Visual Basic], compatible
- comparison operators [Visual Basic]
- TypeOf...Is expression
- data types [Visual Basic], compatible
- TypeOf operator [Visual Basic]
- compatible data types [Visual Basic]
ms.assetid: 33f65296-659a-4b9a-9a29-c2a91cff68b2
ms.openlocfilehash: 59a03095b2abbaa304221b30402b9a058954db63
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795239"
---
# <a name="typeof-operator-visual-basic"></a><span data-ttu-id="530be-103">Оператор TypeOf (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="530be-103">TypeOf Operator (Visual Basic)</span></span>

<span data-ttu-id="530be-104">Проверяет, совместим ли тип среды выполнения результата выражения с указанным типом.</span><span class="sxs-lookup"><span data-stu-id="530be-104">Checks whether the runtime type of an expression's result is type-compatible with the specified type.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="530be-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="530be-105">Syntax</span></span>  
  
```vb  
result = TypeOf objectexpression Is typename  
```  
  
```vb  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a><span data-ttu-id="530be-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="530be-106">Parts</span></span>  

 `result`  
 <span data-ttu-id="530be-107">Возвращено.</span><span class="sxs-lookup"><span data-stu-id="530be-107">Returned.</span></span> <span data-ttu-id="530be-108">Значение `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="530be-108">A `Boolean` value.</span></span>  
  
 `objectexpression`  
 <span data-ttu-id="530be-109">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="530be-109">Required.</span></span> <span data-ttu-id="530be-110">Любое выражение, результатом которого является тип ссылки.</span><span class="sxs-lookup"><span data-stu-id="530be-110">Any expression that evaluates to a reference type.</span></span>  
  
 `typename`  
 <span data-ttu-id="530be-111">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="530be-111">Required.</span></span> <span data-ttu-id="530be-112">Любое имя типа данных.</span><span class="sxs-lookup"><span data-stu-id="530be-112">Any data type name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="530be-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="530be-113">Remarks</span></span>  

 <span data-ttu-id="530be-114">Оператор `TypeOf` определяет, совместим ли тип времени выполнения `objectexpression` с `typename`.</span><span class="sxs-lookup"><span data-stu-id="530be-114">The `TypeOf` operator determines whether the run-time type of `objectexpression` is compatible with `typename`.</span></span> <span data-ttu-id="530be-115">Совместимость зависит от категории типа `typename`.</span><span class="sxs-lookup"><span data-stu-id="530be-115">The compatibility depends on the type category of `typename`.</span></span> <span data-ttu-id="530be-116">В следующей таблице показано, как определяется совместимость.</span><span class="sxs-lookup"><span data-stu-id="530be-116">The following table shows how compatibility is determined.</span></span>  
  
|<span data-ttu-id="530be-117">Категория типа `typename`</span><span class="sxs-lookup"><span data-stu-id="530be-117">Type category of `typename`</span></span>|<span data-ttu-id="530be-118">Критерий совместимости</span><span class="sxs-lookup"><span data-stu-id="530be-118">Compatibility criterion</span></span>|  
|---------------------------------|-----------------------------|  
|<span data-ttu-id="530be-119">Class</span><span class="sxs-lookup"><span data-stu-id="530be-119">Class</span></span>|<span data-ttu-id="530be-120">`objectexpression` типа `typename` или наследует от `typename`</span><span class="sxs-lookup"><span data-stu-id="530be-120">`objectexpression` is of type `typename` or inherits from `typename`</span></span>|  
|<span data-ttu-id="530be-121">structure</span><span class="sxs-lookup"><span data-stu-id="530be-121">Structure</span></span>|<span data-ttu-id="530be-122">`objectexpression` типа `typename`</span><span class="sxs-lookup"><span data-stu-id="530be-122">`objectexpression` is of type `typename`</span></span>|  
|<span data-ttu-id="530be-123">Интерфейс</span><span class="sxs-lookup"><span data-stu-id="530be-123">Interface</span></span>|<span data-ttu-id="530be-124">`objectexpression` реализует `typename` или наследует от класса, реализующего `typename`</span><span class="sxs-lookup"><span data-stu-id="530be-124">`objectexpression` implements `typename` or inherits from a class that implements `typename`</span></span>|  
  
 <span data-ttu-id="530be-125">Если тип времени выполнения `objectexpression` удовлетворяет критерию совместимости, `result` является `True`.</span><span class="sxs-lookup"><span data-stu-id="530be-125">If the run-time type of `objectexpression` satisfies the compatibility criterion, `result` is `True`.</span></span> <span data-ttu-id="530be-126">В противном случае `result` является `False`.</span><span class="sxs-lookup"><span data-stu-id="530be-126">Otherwise, `result` is `False`.</span></span>  <span data-ttu-id="530be-127">Если `objectexpression` имеет значение null, то `TypeOf`...`Is` возвращает `False`, а ...`IsNot` возвращает `True`.</span><span class="sxs-lookup"><span data-stu-id="530be-127">If `objectexpression` is null, then `TypeOf`...`Is` returns `False`, and ...`IsNot` returns `True`.</span></span>  
  
 <span data-ttu-id="530be-128">`TypeOf` всегда используется с ключевым словом `Is` для создания выражения `TypeOf`...`Is` или с ключевым словом `IsNot` для создания выражения `TypeOf`...`IsNot`.</span><span class="sxs-lookup"><span data-stu-id="530be-128">`TypeOf` is always used with the `Is` keyword to construct a `TypeOf`...`Is` expression, or with the `IsNot` keyword to construct a `TypeOf`...`IsNot` expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="530be-129">Пример</span><span class="sxs-lookup"><span data-stu-id="530be-129">Example</span></span>  

 <span data-ttu-id="530be-130">В следующем примере выражение `TypeOf`...`Is` используется для проверки на совместимость типов двух переменных ссылок на объекты с различными типами данных.</span><span class="sxs-lookup"><span data-stu-id="530be-130">The following example uses `TypeOf`...`Is` expressions to test the type compatibility of two object reference variables with various data types.</span></span>  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 <span data-ttu-id="530be-131">Переменная `refInteger` имеет тип времени выполнения `Integer`.</span><span class="sxs-lookup"><span data-stu-id="530be-131">The variable `refInteger` has a run-time type of `Integer`.</span></span> <span data-ttu-id="530be-132">Она совместима с `Integer`, но не с `Double`.</span><span class="sxs-lookup"><span data-stu-id="530be-132">It is compatible with `Integer` but not with `Double`.</span></span> <span data-ttu-id="530be-133">Переменная `refForm` имеет тип времени выполнения <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="530be-133">The variable `refForm` has a run-time type of <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="530be-134">Она совместима с <xref:System.Windows.Forms.Form>, так как это ее тип, с <xref:System.Windows.Forms.Control>, так как <xref:System.Windows.Forms.Form> наследует от <xref:System.Windows.Forms.Control>, и с <xref:System.ComponentModel.IComponent>, так как <xref:System.Windows.Forms.Form> наследует от <xref:System.ComponentModel.Component>, который реализует <xref:System.ComponentModel.IComponent>.</span><span class="sxs-lookup"><span data-stu-id="530be-134">It is compatible with <xref:System.Windows.Forms.Form> because that is its type, with <xref:System.Windows.Forms.Control> because <xref:System.Windows.Forms.Form> inherits from <xref:System.Windows.Forms.Control>, and with <xref:System.ComponentModel.IComponent> because <xref:System.Windows.Forms.Form> inherits from <xref:System.ComponentModel.Component>, which implements <xref:System.ComponentModel.IComponent>.</span></span> <span data-ttu-id="530be-135">Однако `refForm` несовместима с <xref:System.Windows.Forms.Label>.</span><span class="sxs-lookup"><span data-stu-id="530be-135">However, `refForm` is not compatible with <xref:System.Windows.Forms.Label>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="530be-136">См. также</span><span class="sxs-lookup"><span data-stu-id="530be-136">See also</span></span>

- [<span data-ttu-id="530be-137">Оператор Is</span><span class="sxs-lookup"><span data-stu-id="530be-137">Is Operator</span></span>](is-operator.md)
- [<span data-ttu-id="530be-138">Оператор IsNot</span><span class="sxs-lookup"><span data-stu-id="530be-138">IsNot Operator</span></span>](isnot-operator.md)
- [<span data-ttu-id="530be-139">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="530be-139">Comparison Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="530be-140">Порядок применения операторов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="530be-140">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="530be-141">Список операторов, сгруппированных по функциональному назначению</span><span class="sxs-lookup"><span data-stu-id="530be-141">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="530be-142">Операторы и выражения</span><span class="sxs-lookup"><span data-stu-id="530be-142">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
