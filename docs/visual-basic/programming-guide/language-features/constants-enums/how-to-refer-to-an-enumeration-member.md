---
description: Дополнительные сведения см. в разделе как ссылаться на элемент перечисления (Visual Basic).
title: Практическое руководство. Ссылка на элемент перечисления
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], referring to
- values [Visual Basic], associating constant values with names
- enumeration members
- constants [Visual Basic], enumerated
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
ms.openlocfilehash: 339ea8292eea1b39e2c6e5879b98a083800fb1fc
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471530"
---
# <a name="how-to-refer-to-an-enumeration-member-visual-basic"></a><span data-ttu-id="ad325-103">Практическое руководство. Ссылка на член перечисления (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad325-103">How to: Refer to an Enumeration Member (Visual Basic)</span></span>

<span data-ttu-id="ad325-104">Перечисления предоставляют удобный способ работы с наборами связанных констант и для связывания постоянных значений с именами.</span><span class="sxs-lookup"><span data-stu-id="ad325-104">Enumerations provide a convenient way to work with sets of related constants and to associate constant values with names.</span></span> <span data-ttu-id="ad325-105">Например, вы можете объявить перечисление для набора целочисленных констант, связанных с днями недели, а затем использовать в коде названия дней, а не числа.</span><span class="sxs-lookup"><span data-stu-id="ad325-105">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
 <span data-ttu-id="ad325-106">С помощью инструкции можно избежать использования полных имен `Imports` .</span><span class="sxs-lookup"><span data-stu-id="ad325-106">You can avoid using fully qualified names with the `Imports` statement.</span></span> <span data-ttu-id="ad325-107">Дополнительные сведения см. в разделе [перечисления и квалификация имени](enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="ad325-107">For more information, see [Enumerations and Name Qualification](enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-refer-to-an-enumeration-member"></a><span data-ttu-id="ad325-108">Ссылка на элемент перечисления</span><span class="sxs-lookup"><span data-stu-id="ad325-108">To refer to an enumeration member</span></span>  
  
- <span data-ttu-id="ad325-109">Уточните имя члена с помощью перечисления.</span><span class="sxs-lookup"><span data-stu-id="ad325-109">Qualify the member name with the enumeration.</span></span> <span data-ttu-id="ad325-110">Например, в следующем примере член перечисления присваивается `Saturday` `FirstDayOfWeek` переменной `DayValue` .</span><span class="sxs-lookup"><span data-stu-id="ad325-110">For example, the following example assigns the `Saturday` member of the `FirstDayOfWeek` enumeration to the variable `DayValue`.</span></span>  
  
     [!code-vb[VbEnumsTask#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="ad325-111">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="ad325-111">See also</span></span>

- [<span data-ttu-id="ad325-112">Практическое руководство. Объявление перечисления</span><span class="sxs-lookup"><span data-stu-id="ad325-112">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="ad325-113">Перечисления и уточнение имен</span><span class="sxs-lookup"><span data-stu-id="ad325-113">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="ad325-114">Практическое руководство. Перебор элементов перечисления в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ad325-114">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="ad325-115">Практическое руководство. Определение строки, связанной со значением из перечисления</span><span class="sxs-lookup"><span data-stu-id="ad325-115">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="ad325-116">Когда следует использовать перечисление</span><span class="sxs-lookup"><span data-stu-id="ad325-116">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
