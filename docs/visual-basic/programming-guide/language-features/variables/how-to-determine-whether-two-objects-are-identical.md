---
description: Дополнительные сведения см. в статье как определить идентичность двух объектов (Visual Basic)
title: Практическое руководство. Определение идентичности двух объектов
ms.date: 07/20/2015
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
ms.openlocfilehash: 91f431b5a7e4cf51135c060ca0aebf1b3b968b25
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481900"
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a><span data-ttu-id="06805-103">Практическое руководство. Определение идентичности двух объектов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06805-103">How to: Determine Whether Two Objects Are Identical (Visual Basic)</span></span>

<span data-ttu-id="06805-104">В Visual Basic две ссылки на переменные считаются идентичными, если их указатели одинаковы, то есть если обе переменные указывают на один и тот же экземпляр класса в памяти.</span><span class="sxs-lookup"><span data-stu-id="06805-104">In Visual Basic, two variable references are considered identical if their pointers are the same, that is, if both variables point to the same class instance in memory.</span></span> <span data-ttu-id="06805-105">Например, в Windows Forms приложении может потребоваться выполнить сравнение, чтобы определить, совпадает ли текущий экземпляр ( `Me` ) с конкретным экземпляром, например `Form2` .</span><span class="sxs-lookup"><span data-stu-id="06805-105">For example, in a Windows Forms application, you might want to make a comparison to determine whether the current instance (`Me`) is the same as a particular instance, such as `Form2`.</span></span>  
  
 <span data-ttu-id="06805-106">Visual Basic предоставляет два оператора для сравнения указателей.</span><span class="sxs-lookup"><span data-stu-id="06805-106">Visual Basic provides two operators to compare pointers.</span></span> <span data-ttu-id="06805-107">[Оператор is](../../../language-reference/operators/is-operator.md) возвращает значение `True` , если объекты идентичны, и [оператор IsNot](../../../language-reference/operators/isnot-operator.md) возвращает значение, `True` если это не так.</span><span class="sxs-lookup"><span data-stu-id="06805-107">The [Is Operator](../../../language-reference/operators/is-operator.md) returns `True` if the objects are identical, and the [IsNot Operator](../../../language-reference/operators/isnot-operator.md) returns `True` if they are not.</span></span>  
  
## <a name="determining-if-two-objects-are-identical"></a><span data-ttu-id="06805-108">Определение идентичности двух объектов</span><span class="sxs-lookup"><span data-stu-id="06805-108">Determining if Two Objects Are Identical</span></span>  
  
#### <a name="to-determine-if-two-objects-are-identical"></a><span data-ttu-id="06805-109">Определение идентичности двух объектов</span><span class="sxs-lookup"><span data-stu-id="06805-109">To determine if two objects are identical</span></span>  
  
1. <span data-ttu-id="06805-110">Настройте `Boolean` выражение для проверки двух объектов.</span><span class="sxs-lookup"><span data-stu-id="06805-110">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2. <span data-ttu-id="06805-111">В тестовом выражении используйте `Is` оператор с двумя объектами в качестве операндов.</span><span class="sxs-lookup"><span data-stu-id="06805-111">In your testing expression, use the `Is` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="06805-112">`Is` Возвращает значение `True` , если объекты указывают на один и тот же экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="06805-112">`Is` returns `True` if the objects point to the same class instance.</span></span>  
  
## <a name="determining-if-two-objects-are-not-identical"></a><span data-ttu-id="06805-113">Определение того, что два объекта не идентичны</span><span class="sxs-lookup"><span data-stu-id="06805-113">Determining if Two Objects Are Not Identical</span></span>  

 <span data-ttu-id="06805-114">Иногда требуется выполнить действие, если эти два объекта не идентичны, и, например, могут быть неудобными для объединения `Not` и `Is` `If Not obj1 Is obj2` .</span><span class="sxs-lookup"><span data-stu-id="06805-114">Sometimes you want to perform an action if the two objects are not identical, and it can be awkward to combine `Not` and `Is`, for example `If Not obj1 Is obj2`.</span></span> <span data-ttu-id="06805-115">В этом случае можно использовать `IsNot` оператор.</span><span class="sxs-lookup"><span data-stu-id="06805-115">In such a case you can use the `IsNot` operator.</span></span>  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a><span data-ttu-id="06805-116">Определение того, что два объекта не идентичны</span><span class="sxs-lookup"><span data-stu-id="06805-116">To determine if two objects are not identical</span></span>  
  
1. <span data-ttu-id="06805-117">Настройте `Boolean` выражение для проверки двух объектов.</span><span class="sxs-lookup"><span data-stu-id="06805-117">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2. <span data-ttu-id="06805-118">В тестовом выражении используйте `IsNot` оператор с двумя объектами в качестве операндов.</span><span class="sxs-lookup"><span data-stu-id="06805-118">In your testing expression, use the `IsNot` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="06805-119">`IsNot` Возвращает значение `True` , если объекты не указывают на один и тот же экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="06805-119">`IsNot` returns `True` if the objects do not point to the same class instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06805-120">Пример</span><span class="sxs-lookup"><span data-stu-id="06805-120">Example</span></span>  

 <span data-ttu-id="06805-121">В следующем примере показано `Object` , как проверить пары переменных, чтобы определить, указывают ли они на один и тот же экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="06805-121">The following example tests pairs of `Object` variables to see if they point to the same class instance.</span></span>  
  
 [!code-vb[VbVbalrKeywords#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#14)]  
  
 <span data-ttu-id="06805-122">В предыдущем примере отображаются следующие выходные данные.</span><span class="sxs-lookup"><span data-stu-id="06805-122">The preceding example displays the following output.</span></span>  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a><span data-ttu-id="06805-123">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="06805-123">See also</span></span>

- [<span data-ttu-id="06805-124">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="06805-124">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="06805-125">Объектные переменные</span><span class="sxs-lookup"><span data-stu-id="06805-125">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="06805-126">Значения объектных переменных</span><span class="sxs-lookup"><span data-stu-id="06805-126">Object Variable Values</span></span>](object-variable-values.md)
- [<span data-ttu-id="06805-127">Оператор Is</span><span class="sxs-lookup"><span data-stu-id="06805-127">Is Operator</span></span>](../../../language-reference/operators/is-operator.md)
- [<span data-ttu-id="06805-128">Оператор IsNot</span><span class="sxs-lookup"><span data-stu-id="06805-128">IsNot Operator</span></span>](../../../language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="06805-129">Практическое руководство. Определение наличия связи между двумя объектами</span><span class="sxs-lookup"><span data-stu-id="06805-129">How to: Determine Whether Two Objects Are Related</span></span>](how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="06805-130">Me, My, MyBase и MyClass</span><span class="sxs-lookup"><span data-stu-id="06805-130">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
