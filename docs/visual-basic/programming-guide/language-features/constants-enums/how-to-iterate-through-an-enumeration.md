---
description: Дополнительные сведения см. в статье как выполнить итерацию перечисления в Visual Basic
title: Практическое руководство. Перебор элементов перечисления
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: a14d65a33e8a2f7872203a6a332dec1e753704f8
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471569"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a><span data-ttu-id="d0618-103">Практическое руководство. Перебор элементов перечисления в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d0618-103">How to: Iterate Through An Enumeration in Visual Basic</span></span>

<span data-ttu-id="d0618-104">Перечисления — это удобный способ работать с наборами связанных констант и связывать постоянные значения с именами.</span><span class="sxs-lookup"><span data-stu-id="d0618-104">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="d0618-105">Чтобы выполнить итерацию по перечислению, можно переместить его в массив с помощью <xref:System.Enum.GetValues%2A> метода.</span><span class="sxs-lookup"><span data-stu-id="d0618-105">To iterate through an enumeration, you can move it into an array using the <xref:System.Enum.GetValues%2A> method.</span></span> <span data-ttu-id="d0618-106">Можно также выполнить итерацию перечисления с помощью `For...Each` инструкции, используя <xref:System.Enum.GetNames%2A> <xref:System.Enum.GetValues%2A> метод или для извлечения строкового или числового значения.</span><span class="sxs-lookup"><span data-stu-id="d0618-106">You could also iterate through an enumeration using a `For...Each` statement, using the <xref:System.Enum.GetNames%2A> or <xref:System.Enum.GetValues%2A> method to extract the string or numeric value.</span></span>  
  
### <a name="to-iterate-through-an-enumeration"></a><span data-ttu-id="d0618-107">Перебор перечислений</span><span class="sxs-lookup"><span data-stu-id="d0618-107">To iterate through an enumeration</span></span>  
  
- <span data-ttu-id="d0618-108">Объявите массив и преобразуйте перечисление в него с помощью <xref:System.Enum.GetValues%2A> метода, прежде чем передавать массив, как и любую другую переменную.</span><span class="sxs-lookup"><span data-stu-id="d0618-108">Declare an array and convert the enumeration to it with the <xref:System.Enum.GetValues%2A> method before passing the array as you would any other variable.</span></span> <span data-ttu-id="d0618-109">В следующем примере отображается каждый элемент перечисления по <xref:Microsoft.VisualBasic.FirstDayOfWeek> мере его итерации по перечислению.</span><span class="sxs-lookup"><span data-stu-id="d0618-109">The following example displays each member of the enumeration <xref:Microsoft.VisualBasic.FirstDayOfWeek> as it iterates through the enumeration.</span></span>  
  
     [!code-vb[VbEnumsTask#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="d0618-110">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="d0618-110">See also</span></span>

- [<span data-ttu-id="d0618-111">Общие сведения о перечислениях</span><span class="sxs-lookup"><span data-stu-id="d0618-111">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="d0618-112">Практическое руководство. Объявление перечисления</span><span class="sxs-lookup"><span data-stu-id="d0618-112">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="d0618-113">Когда следует использовать перечисление</span><span class="sxs-lookup"><span data-stu-id="d0618-113">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="d0618-114">Практическое руководство. Определение строки, связанной со значением из перечисления</span><span class="sxs-lookup"><span data-stu-id="d0618-114">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="d0618-115">Практическое руководство. Ссылка на элемент перечисления</span><span class="sxs-lookup"><span data-stu-id="d0618-115">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="d0618-116">Перечисления и уточнение имен</span><span class="sxs-lookup"><span data-stu-id="d0618-116">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="d0618-117">Массивы</span><span class="sxs-lookup"><span data-stu-id="d0618-117">Arrays</span></span>](../arrays/index.md)
