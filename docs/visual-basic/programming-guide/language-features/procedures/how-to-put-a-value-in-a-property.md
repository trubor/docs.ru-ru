---
description: Дополнительные сведения см. в статье как добавить значение в свойство (Visual Basic)
title: Практическое руководство. Запись значения в свойство
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: 62f5552f821fb98bd3a4695505aba5ff73b08fc7
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476206"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a><span data-ttu-id="8a284-103">Практическое руководство. Запись значения в свойство (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a284-103">How to: Put a Value in a Property (Visual Basic)</span></span>

<span data-ttu-id="8a284-104">Значение в свойстве сохраняется путем размещения имени свойства в левой части оператора присваивания.</span><span class="sxs-lookup"><span data-stu-id="8a284-104">You store a value in a property by putting the property name on the left side of an assignment statement.</span></span>  
  
 <span data-ttu-id="8a284-105">`Set`Процедура свойства сохраняет значение, но явно не вызывает его по имени.</span><span class="sxs-lookup"><span data-stu-id="8a284-105">The property's `Set` procedure stores a value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="8a284-106">Свойство используется так же, как и переменная.</span><span class="sxs-lookup"><span data-stu-id="8a284-106">You use the property just as you would use a variable.</span></span> <span data-ttu-id="8a284-107">Visual Basic выполняет вызовы процедур свойств.</span><span class="sxs-lookup"><span data-stu-id="8a284-107">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-store-a-value-in-a-property"></a><span data-ttu-id="8a284-108">Сохранение значения в свойстве</span><span class="sxs-lookup"><span data-stu-id="8a284-108">To store a value in a property</span></span>  
  
1. <span data-ttu-id="8a284-109">Используйте имя свойства в левой части оператора присваивания.</span><span class="sxs-lookup"><span data-stu-id="8a284-109">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="8a284-110">В следующем примере свойству Visual Basic присваивается значение `TimeOfDay` полдень, неявное вызов его `Set` процедуры.</span><span class="sxs-lookup"><span data-stu-id="8a284-110">The following example sets the value of the Visual Basic `TimeOfDay` property to noon, implicitly calling its `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. <span data-ttu-id="8a284-111">Если свойство принимает аргументы, следует следовать имени свойства с круглыми скобками, чтобы заключить список аргументов.</span><span class="sxs-lookup"><span data-stu-id="8a284-111">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="8a284-112">Если аргументы отсутствуют, можно дополнительно опустить круглые скобки.</span><span class="sxs-lookup"><span data-stu-id="8a284-112">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="8a284-113">Поместите аргументы в список аргументов в круглых скобках, разделяя их запятыми.</span><span class="sxs-lookup"><span data-stu-id="8a284-113">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="8a284-114">Убедитесь, что аргументы указываются в том же порядке, в котором свойство определяет соответствующие параметры.</span><span class="sxs-lookup"><span data-stu-id="8a284-114">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
4. <span data-ttu-id="8a284-115">Значение, созданное в правой части оператора присваивания, хранится в свойстве.</span><span class="sxs-lookup"><span data-stu-id="8a284-115">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a284-116">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="8a284-116">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>
- [<span data-ttu-id="8a284-117">Процедуры свойств</span><span class="sxs-lookup"><span data-stu-id="8a284-117">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="8a284-118">Параметры и аргументы процедуры</span><span class="sxs-lookup"><span data-stu-id="8a284-118">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="8a284-119">Property Statement</span><span class="sxs-lookup"><span data-stu-id="8a284-119">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="8a284-120">Различия между свойствами и переменными в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8a284-120">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="8a284-121">Практическое руководство. Создание свойства</span><span class="sxs-lookup"><span data-stu-id="8a284-121">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="8a284-122">Практическое руководство. Объявление свойства со смешанным уровнем доступа</span><span class="sxs-lookup"><span data-stu-id="8a284-122">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="8a284-123">Практическое руководство. Вызов процедуры свойства</span><span class="sxs-lookup"><span data-stu-id="8a284-123">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="8a284-124">Практическое руководство. Объявление и вызов свойства по умолчанию в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8a284-124">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="8a284-125">Практическое руководство. Получение значения из свойства</span><span class="sxs-lookup"><span data-stu-id="8a284-125">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
