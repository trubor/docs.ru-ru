---
description: Дополнительные сведения о операторе "IsFalse" (Visual Basic)
title: Оператор IsFalse
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: 190399dd29ba2d643bd26dfe4f6191211c9a3740
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665709"
---
# <a name="isfalse-operator-visual-basic"></a><span data-ttu-id="6bba2-103">Оператор IsFalse (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6bba2-103">IsFalse Operator (Visual Basic)</span></span>

<span data-ttu-id="6bba2-104">Определяет, является ли выражение `False` .</span><span class="sxs-lookup"><span data-stu-id="6bba2-104">Determines whether an expression is `False`.</span></span>  
  
 <span data-ttu-id="6bba2-105">`IsFalse`В коде нельзя вызывать явным образом, но компилятор Visual Basic может использовать его для создания кода из `AndAlso` предложений.</span><span class="sxs-lookup"><span data-stu-id="6bba2-105">You cannot call `IsFalse` explicitly in your code, but the Visual Basic compiler can use it to generate code from `AndAlso` clauses.</span></span> <span data-ttu-id="6bba2-106">Если вы определяете класс или структуру, а затем используете переменную этого типа в `AndAlso` предложении, необходимо определить `IsFalse` для этого класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="6bba2-106">If you define a class or structure and then use a variable of that type in an `AndAlso` clause, you must define `IsFalse` on that class or structure.</span></span>  
  
 <span data-ttu-id="6bba2-107">Компилятор рассматривает `IsFalse` операторы и `IsTrue` как *парную пару*.</span><span class="sxs-lookup"><span data-stu-id="6bba2-107">The compiler considers the `IsFalse` and `IsTrue` operators as a *matched pair*.</span></span> <span data-ttu-id="6bba2-108">Это означает, что при определении одного из них необходимо также определить другой.</span><span class="sxs-lookup"><span data-stu-id="6bba2-108">This means that if you define one of them, you must also define the other one.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6bba2-109">`IsFalse`Оператор можно *перегрузить*, что означает, что класс или структура может переопределить свое поведение, если его операнд имеет тип этого класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="6bba2-109">The `IsFalse` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="6bba2-110">Если код использует этот оператор для такого класса или структуры, убедитесь, что вы понимаете его переопределенное поведение.</span><span class="sxs-lookup"><span data-stu-id="6bba2-110">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="6bba2-111">Для получения дополнительной информации см. [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="6bba2-111">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bba2-112">Пример</span><span class="sxs-lookup"><span data-stu-id="6bba2-112">Example</span></span>  

 <span data-ttu-id="6bba2-113">В следующем примере кода определяется структура структуры, включающей определения для `IsFalse` `IsTrue` операторов и.</span><span class="sxs-lookup"><span data-stu-id="6bba2-113">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="6bba2-114">См. также</span><span class="sxs-lookup"><span data-stu-id="6bba2-114">See also</span></span>

- [<span data-ttu-id="6bba2-115">Оператор IsTrue</span><span class="sxs-lookup"><span data-stu-id="6bba2-115">IsTrue Operator</span></span>](istrue-operator.md)
- [<span data-ttu-id="6bba2-116">Практическое руководство. Определение оператора</span><span class="sxs-lookup"><span data-stu-id="6bba2-116">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="6bba2-117">Оператор AndAlso</span><span class="sxs-lookup"><span data-stu-id="6bba2-117">AndAlso Operator</span></span>](andalso-operator.md)
