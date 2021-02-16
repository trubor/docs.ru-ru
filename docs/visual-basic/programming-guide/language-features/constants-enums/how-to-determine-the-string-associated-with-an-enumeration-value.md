---
description: Дополнительные сведения см. в статье как определить строку, связанную со значением перечисления (Visual Basic).
title: Практическое руководство. Определение строки, связанной со значением из перечисления
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: 391cb097fa8163f7131cc30f85f8a4f85ba826a4
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471608"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a><span data-ttu-id="d8c50-103">Практическое руководство. Определение строки, связанной со значением из перечисления (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8c50-103">How to: Determine the String Associated with an Enumeration Value (Visual Basic)</span></span>

<span data-ttu-id="d8c50-104"><xref:System.Enum.GetValues%2A>Методы и <xref:System.Enum.GetNames%2A> позволяют определить строки и значения, связанные с элементами перечисления.</span><span class="sxs-lookup"><span data-stu-id="d8c50-104">The <xref:System.Enum.GetValues%2A> and <xref:System.Enum.GetNames%2A> methods allow you to determine the strings and values associated with enumeration members.</span></span>  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a><span data-ttu-id="d8c50-105">Определение строки, связанной с перечислением</span><span class="sxs-lookup"><span data-stu-id="d8c50-105">To determine the string associated with an enumeration</span></span>  
  
- <span data-ttu-id="d8c50-106">Используйте <xref:System.Enum.GetNames%2A> метод для получения строк, связанных с элементами перечисления.</span><span class="sxs-lookup"><span data-stu-id="d8c50-106">Use the <xref:System.Enum.GetNames%2A> method to retrieve the strings associated with the enumeration members.</span></span> <span data-ttu-id="d8c50-107">В этом примере объявляется перечисление, `flavorEnum` а затем используется <xref:System.Enum.GetNames%2A> метод для вывода строк, связанных с каждым элементом.</span><span class="sxs-lookup"><span data-stu-id="d8c50-107">This example declares an enumeration, `flavorEnum`, then uses the <xref:System.Enum.GetNames%2A> method to display the strings associated with each member.</span></span>  
  
     [!code-vb[VbEnumsTask#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d8c50-108">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="d8c50-108">See also</span></span>

- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [<span data-ttu-id="d8c50-109">Практическое руководство. Объявление перечисления</span><span class="sxs-lookup"><span data-stu-id="d8c50-109">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="d8c50-110">Практическое руководство. Ссылка на элемент перечисления</span><span class="sxs-lookup"><span data-stu-id="d8c50-110">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="d8c50-111">Перечисления и уточнение имен</span><span class="sxs-lookup"><span data-stu-id="d8c50-111">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="d8c50-112">Практическое руководство. Перебор элементов перечисления в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d8c50-112">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="d8c50-113">Когда следует использовать перечисление</span><span class="sxs-lookup"><span data-stu-id="d8c50-113">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="d8c50-114">Оператор Enum</span><span class="sxs-lookup"><span data-stu-id="d8c50-114">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
