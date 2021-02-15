---
description: 'Дополнительные сведения: перечисления и квалификация имени (Visual Basic)'
title: Перечисления и уточнение имен
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- Imports statement [Visual Basic], namespace declarations
- declaring namespaces [Visual Basic], enumerations
- name collisions
- ambiguous names [Visual Basic], enumerations
- enumerations [Visual Basic], name qualification
- names [Visual Basic], avoiding conflicts
- namespaces [Visual Basic], declaring
- naming conflicts, enumerations
- naming conflicts, qualifying names
- declaring enumerations
- references [Visual Basic], enumeration members
- naming conventions [Visual Basic], naming conflicts
- declarations [Visual Basic], namespaces
ms.assetid: 08ba2738-df52-4140-bc55-f57c871c9b73
ms.openlocfilehash: 83f5b894dad821fea920386be905de0b51f9c42f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100477480"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a><span data-ttu-id="c6911-103">Перечисления и уточнение имен (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6911-103">Enumerations and Name Qualification (Visual Basic)</span></span>

<span data-ttu-id="c6911-104">Обычно при ссылке на член перечисления необходимо уточнить имя члена с помощью имени перечисления.</span><span class="sxs-lookup"><span data-stu-id="c6911-104">Normally, when referring to a member of an enumeration, you must qualify the member name with the enumeration name.</span></span> <span data-ttu-id="c6911-105">Например, для ссылки на `Sunday` член `Days` перечисления используется следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="c6911-105">For example, to refer to the `Sunday` member of your `Days` enumeration, you would use the following syntax:</span></span>  
  
 [!code-vb[VbEnumsTask#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#18)]  
  
## <a name="using-the-imports-statement"></a><span data-ttu-id="c6911-106">Использование оператора Imports</span><span class="sxs-lookup"><span data-stu-id="c6911-106">Using the Imports Statement</span></span>  

 <span data-ttu-id="c6911-107">Можно избежать использования полных имен, добавив `Imports` инструкцию в раздел кода объявлений пространств имен, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="c6911-107">You can avoid using fully qualified names by adding an `Imports` statement to the namespace declarations section of your code, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 <span data-ttu-id="c6911-108">`Imports`Оператор импортирует имена пространств имен из проектов и сборок, на которые имеются ссылки, и из того же проекта, в котором находится модуль, в котором находится инструкция.</span><span class="sxs-lookup"><span data-stu-id="c6911-108">An `Imports` statement imports namespace names from referenced projects and assemblies and from within the same project as the module in which the statement appears.</span></span> <span data-ttu-id="c6911-109">После добавления этой инструкции можно ссылаться на члены перечисления без уточнения, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="c6911-109">Once this statement is added, you can refer to your enumeration members without qualification, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#24)]  
  
 <span data-ttu-id="c6911-110">Организуя наборы связанных констант в перечисления, можно использовать одни и те же имена констант в разных контекстах.</span><span class="sxs-lookup"><span data-stu-id="c6911-110">By organizing sets of related constants in enumerations, you can use the same constant names in different contexts.</span></span> <span data-ttu-id="c6911-111">Например, можно использовать те же имена для констант дня недели в `Days` `WorkDays` перечислениях и.</span><span class="sxs-lookup"><span data-stu-id="c6911-111">For example, you can use the same names for the weekday constants in the `Days` and `WorkDays` enumerations.</span></span> <span data-ttu-id="c6911-112">При использовании `Imports` оператора с перечислениями необходимо избегать неоднозначных ссылок.</span><span class="sxs-lookup"><span data-stu-id="c6911-112">If you use the `Imports` statement with your enumerations, you must be careful to avoid ambiguous references.</span></span> <span data-ttu-id="c6911-113">Рассмотрим следующий пример.</span><span class="sxs-lookup"><span data-stu-id="c6911-113">Consider the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 [!code-vb[VbEnumsTask#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#25)]  
  
 <span data-ttu-id="c6911-114">Если предположить, что `Monday` является членом `Days` перечисления и `Workdays` перечисления, этот код создает ошибку компилятора.</span><span class="sxs-lookup"><span data-stu-id="c6911-114">Assuming that `Monday` is a member of both the `Days` enumeration and the `Workdays` enumeration, this code generates a compiler error.</span></span> <span data-ttu-id="c6911-115">Чтобы избежать неоднозначных ссылок при ссылке на отдельную константу, уточните имя константы с его перечислением.</span><span class="sxs-lookup"><span data-stu-id="c6911-115">To avoid ambiguous references when referring to an individual constant, qualify the constant name with its enumeration.</span></span> <span data-ttu-id="c6911-116">Следующий код ссылается на `Saturday` константы в `Days` `WorkDays` перечислениях и.</span><span class="sxs-lookup"><span data-stu-id="c6911-116">The following code refers to the `Saturday` constants in the `Days` and `WorkDays` enumerations.</span></span>  
  
 [!code-vb[VbEnumsTask#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="c6911-117">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c6911-117">See also</span></span>

- [<span data-ttu-id="c6911-118">Константы и перечисления</span><span class="sxs-lookup"><span data-stu-id="c6911-118">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="c6911-119">Практическое руководство. Объявление перечисления</span><span class="sxs-lookup"><span data-stu-id="c6911-119">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="c6911-120">Практическое руководство. Ссылка на элемент перечисления</span><span class="sxs-lookup"><span data-stu-id="c6911-120">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="c6911-121">Практическое руководство. Перебор элементов перечисления в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c6911-121">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="c6911-122">Практическое руководство. Определение строки, связанной со значением из перечисления</span><span class="sxs-lookup"><span data-stu-id="c6911-122">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="c6911-123">Когда следует использовать перечисление</span><span class="sxs-lookup"><span data-stu-id="c6911-123">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="c6911-124">Типы данных констант и литералов</span><span class="sxs-lookup"><span data-stu-id="c6911-124">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="c6911-125">Оператор Enum</span><span class="sxs-lookup"><span data-stu-id="c6911-125">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
- [<span data-ttu-id="c6911-126">Оператор Imports (пространство имен .NET и тип)</span><span class="sxs-lookup"><span data-stu-id="c6911-126">Imports Statement (.NET Namespace and Type)</span></span>](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="c6911-127">Типы данных</span><span class="sxs-lookup"><span data-stu-id="c6911-127">Data Types</span></span>](../../../language-reference/data-types/index.md)
