---
description: Дополнительные сведения о других структурах управления (Visual Basic)
title: Другие структуры управления
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: 39654b8c780369eeea043087c8a04e2ba1f928c2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100473580"
---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="2aa9b-103">Другие структуры управления (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2aa9b-103">Other Control Structures (Visual Basic)</span></span>

<span data-ttu-id="2aa9b-104">Visual Basic предоставляет управляющие структуры, которые помогают удалить ресурс или сократить количество повторных ссылок на объект.</span><span class="sxs-lookup"><span data-stu-id="2aa9b-104">Visual Basic provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="2aa9b-105">Использование... Завершить с помощью конструкции</span><span class="sxs-lookup"><span data-stu-id="2aa9b-105">Using...End Using Construction</span></span>  

 <span data-ttu-id="2aa9b-106">`Using...End Using`Конструкция устанавливает блок инструкций, в рамках которого используется ресурс, например соединение SQL.</span><span class="sxs-lookup"><span data-stu-id="2aa9b-106">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="2aa9b-107">При необходимости можно получить ресурс с помощью `Using` инструкции.</span><span class="sxs-lookup"><span data-stu-id="2aa9b-107">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="2aa9b-108">При выходе из `Using` блока Visual Basic автоматически уничтожает ресурс, чтобы он был доступен для использования другим кодом.</span><span class="sxs-lookup"><span data-stu-id="2aa9b-108">When you exit the `Using` block, Visual Basic automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="2aa9b-109">Ресурс должен быть локальным и удаляемым.</span><span class="sxs-lookup"><span data-stu-id="2aa9b-109">The resource must be local and disposable.</span></span> <span data-ttu-id="2aa9b-110">Дополнительные сведения см. в разделе [Оператор using](../../../language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2aa9b-110">For more information, see [Using Statement](../../../language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="2aa9b-111">С помощью... Завершить конструкцию</span><span class="sxs-lookup"><span data-stu-id="2aa9b-111">With...End With Construction</span></span>  

 <span data-ttu-id="2aa9b-112">`With...End With`Конструкция позволяет указать ссылку на объект один раз, а затем выполнить последовательность инструкций, обращающихся к ее членам.</span><span class="sxs-lookup"><span data-stu-id="2aa9b-112">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="2aa9b-113">Это может упростить код и повысить производительность, поскольку Visual Basic не придется повторно устанавливать ссылку для каждой инструкции, которая обращается к ней.</span><span class="sxs-lookup"><span data-stu-id="2aa9b-113">This can simplify your code and improve performance because Visual Basic does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="2aa9b-114">Дополнительные сведения см [. в разделе with... Конец оператора](../../../language-reference/statements/with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2aa9b-114">For more information, see [With...End With Statement](../../../language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2aa9b-115">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="2aa9b-115">See also</span></span>

- [<span data-ttu-id="2aa9b-116">Поток управления</span><span class="sxs-lookup"><span data-stu-id="2aa9b-116">Control Flow</span></span>](index.md)
- [<span data-ttu-id="2aa9b-117">Структуры решений</span><span class="sxs-lookup"><span data-stu-id="2aa9b-117">Decision Structures</span></span>](decision-structures.md)
- [<span data-ttu-id="2aa9b-118">Циклические структуры</span><span class="sxs-lookup"><span data-stu-id="2aa9b-118">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="2aa9b-119">Вложенные структуры управления</span><span class="sxs-lookup"><span data-stu-id="2aa9b-119">Nested Control Structures</span></span>](nested-control-structures.md)
- [<span data-ttu-id="2aa9b-120">Оператор Using</span><span class="sxs-lookup"><span data-stu-id="2aa9b-120">Using Statement</span></span>](../../../language-reference/statements/using-statement.md)
- [<span data-ttu-id="2aa9b-121">Оператор With…End With</span><span class="sxs-lookup"><span data-stu-id="2aa9b-121">With...End With Statement</span></span>](../../../language-reference/statements/with-end-with-statement.md)
