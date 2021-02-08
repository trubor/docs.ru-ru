---
description: 'Дополнительные сведения: оператор AddressOf (Visual Basic)'
title: Оператор AddressOf
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: 2aba8c26aa9581fe1070574b8c408e09bf063d1f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774386"
---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="b9239-103">Оператор AddressOf (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9239-103">AddressOf Operator (Visual Basic)</span></span>

<span data-ttu-id="b9239-104">Создает экземпляр делегата, который ссылается на определенную процедуру.</span><span class="sxs-lookup"><span data-stu-id="b9239-104">Creates a delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9239-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b9239-105">Syntax</span></span>  
  
```vb  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="b9239-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="b9239-106">Parts</span></span>  

 `procedurename`  
 <span data-ttu-id="b9239-107">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="b9239-107">Required.</span></span> <span data-ttu-id="b9239-108">Задает процедуру, на которую ссылается только что созданный делегат.</span><span class="sxs-lookup"><span data-stu-id="b9239-108">Specifies the procedure to be referenced by the newly created delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9239-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="b9239-109">Remarks</span></span>  

 <span data-ttu-id="b9239-110">`AddressOf`Оператор создает делегат, указывающий на подпрограмму или функцию, заданную параметром `procedurename` .</span><span class="sxs-lookup"><span data-stu-id="b9239-110">The `AddressOf` operator creates a delegate that points to the sub or function specified by `procedurename`.</span></span> <span data-ttu-id="b9239-111">Если указанная процедура является методом экземпляра, то делегат ссылается на экземпляр и метод.</span><span class="sxs-lookup"><span data-stu-id="b9239-111">When the specified procedure is an instance method then the delegate refers to both the instance and the method.</span></span> <span data-ttu-id="b9239-112">Затем при вызове делегата вызывается указанный метод указанного экземпляра.</span><span class="sxs-lookup"><span data-stu-id="b9239-112">Then, when the  delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="b9239-113">`AddressOf`Оператор можно использовать в качестве операнда конструктора делегата или его можно использовать в контексте, в котором тип делегата может быть определен компилятором.</span><span class="sxs-lookup"><span data-stu-id="b9239-113">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9239-114">Пример</span><span class="sxs-lookup"><span data-stu-id="b9239-114">Example</span></span>  

 <span data-ttu-id="b9239-115">В этом примере `AddressOf` оператор используется для обозначения делегата, обрабатывающего `Click` событие кнопки.</span><span class="sxs-lookup"><span data-stu-id="b9239-115">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="b9239-116">Пример</span><span class="sxs-lookup"><span data-stu-id="b9239-116">Example</span></span>  

 <span data-ttu-id="b9239-117">В следующем примере оператор используется `AddressOf` для назначения функции Startup для потока.</span><span class="sxs-lookup"><span data-stu-id="b9239-117">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="b9239-118">См. также</span><span class="sxs-lookup"><span data-stu-id="b9239-118">See also</span></span>

- [<span data-ttu-id="b9239-119">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="b9239-119">Declare Statement</span></span>](../statements/declare-statement.md)
- [<span data-ttu-id="b9239-120">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="b9239-120">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="b9239-121">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="b9239-121">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="b9239-122">Делегаты</span><span class="sxs-lookup"><span data-stu-id="b9239-122">Delegates</span></span>](../../programming-guide/language-features/delegates/index.md)
