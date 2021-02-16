---
description: Дополнительные сведения см. в статье как получить значение из свойства (Visual Basic)
title: Практическое руководство. Получение значения из свойства
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
ms.openlocfilehash: 5626ad1a248c3bb51e0f80076628c8108e424186
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100427600"
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a><span data-ttu-id="ce6c8-103">Практическое руководство. Получение значения из свойства (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce6c8-103">How to: Get a Value from a Property (Visual Basic)</span></span>

<span data-ttu-id="ce6c8-104">Значение свойства извлекается путем включения имени свойства в выражение.</span><span class="sxs-lookup"><span data-stu-id="ce6c8-104">You retrieve a property's value by including the property name in an expression.</span></span>  
  
 <span data-ttu-id="ce6c8-105">`Get`Процедура свойства получает значение, но не вызывает его явно по имени.</span><span class="sxs-lookup"><span data-stu-id="ce6c8-105">The property's `Get` procedure retrieves the value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="ce6c8-106">Свойство используется так же, как и переменная.</span><span class="sxs-lookup"><span data-stu-id="ce6c8-106">You use the property just as you would use a variable.</span></span> <span data-ttu-id="ce6c8-107">Visual Basic выполняет вызовы процедур свойств.</span><span class="sxs-lookup"><span data-stu-id="ce6c8-107">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-retrieve-a-value-from-a-property"></a><span data-ttu-id="ce6c8-108">Получение значения из свойства</span><span class="sxs-lookup"><span data-stu-id="ce6c8-108">To retrieve a value from a property</span></span>  
  
1. <span data-ttu-id="ce6c8-109">Используйте имя свойства в выражении так же, как при использовании имени переменной.</span><span class="sxs-lookup"><span data-stu-id="ce6c8-109">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="ce6c8-110">Свойство можно использовать в любом месте, где можно использовать переменную или константу.</span><span class="sxs-lookup"><span data-stu-id="ce6c8-110">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="ce6c8-111">-или-</span><span class="sxs-lookup"><span data-stu-id="ce6c8-111">-or-</span></span>  
  
     <span data-ttu-id="ce6c8-112">Используйте имя свойства после знака равенства ( `=` ) в операторе присваивания.</span><span class="sxs-lookup"><span data-stu-id="ce6c8-112">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="ce6c8-113">В следующем примере считывается значение `Now` свойства Visual Basic, неявно вызывающего его `Get` процедуру.</span><span class="sxs-lookup"><span data-stu-id="ce6c8-113">The following example reads the value of the Visual Basic `Now` property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. <span data-ttu-id="ce6c8-114">Если свойство принимает аргументы, следует следовать имени свойства с круглыми скобками, чтобы заключить список аргументов.</span><span class="sxs-lookup"><span data-stu-id="ce6c8-114">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="ce6c8-115">Если аргументы отсутствуют, можно дополнительно опустить круглые скобки.</span><span class="sxs-lookup"><span data-stu-id="ce6c8-115">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="ce6c8-116">Поместите аргументы в список аргументов в круглых скобках, разделяя их запятыми.</span><span class="sxs-lookup"><span data-stu-id="ce6c8-116">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="ce6c8-117">Убедитесь, что аргументы указываются в том же порядке, в котором свойство определяет соответствующие параметры.</span><span class="sxs-lookup"><span data-stu-id="ce6c8-117">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="ce6c8-118">Значение свойства участвует в выражении точно так же, как переменная или константа, либо хранится в переменной или свойстве в левой части оператора присваивания.</span><span class="sxs-lookup"><span data-stu-id="ce6c8-118">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce6c8-119">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="ce6c8-119">See also</span></span>

- [<span data-ttu-id="ce6c8-120">Процедуры</span><span class="sxs-lookup"><span data-stu-id="ce6c8-120">Procedures</span></span>](./index.md)
- [<span data-ttu-id="ce6c8-121">Процедуры свойств</span><span class="sxs-lookup"><span data-stu-id="ce6c8-121">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="ce6c8-122">Параметры и аргументы процедуры</span><span class="sxs-lookup"><span data-stu-id="ce6c8-122">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="ce6c8-123">Property Statement</span><span class="sxs-lookup"><span data-stu-id="ce6c8-123">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="ce6c8-124">Различия между свойствами и переменными в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ce6c8-124">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="ce6c8-125">Практическое руководство. Создание свойства</span><span class="sxs-lookup"><span data-stu-id="ce6c8-125">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="ce6c8-126">Практическое руководство. Объявление свойства со смешанным уровнем доступа</span><span class="sxs-lookup"><span data-stu-id="ce6c8-126">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="ce6c8-127">Практическое руководство. Вызов процедуры свойства</span><span class="sxs-lookup"><span data-stu-id="ce6c8-127">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="ce6c8-128">Практическое руководство. Объявление и вызов свойства по умолчанию в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ce6c8-128">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="ce6c8-129">Практическое руководство. Запись значения в свойство</span><span class="sxs-lookup"><span data-stu-id="ce6c8-129">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
