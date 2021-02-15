---
description: Дополнительные сведения о том, как сгруппировать связанные значения констант (Visual Basic).
title: Практическое руководство. Группирование значений связанных констант
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: ddd60696d2c751810e49ecbcb537589bedc58abf
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471595"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a><span data-ttu-id="bdaf2-103">Практическое руководство. Группирование значений связанных констант (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bdaf2-103">How to: Group Related Constant Values Together (Visual Basic)</span></span>

<span data-ttu-id="bdaf2-104">Перечисление — это лучший способ сгруппировать связанные константы.</span><span class="sxs-lookup"><span data-stu-id="bdaf2-104">An enumeration is the best way to group related constants together.</span></span> <span data-ttu-id="bdaf2-105">Перечисление создается с помощью `Enum` инструкции в разделе Declarations класса или модуля.</span><span class="sxs-lookup"><span data-stu-id="bdaf2-105">You create an enumeration with the `Enum` statement in the declarations section of a class or a module.</span></span> <span data-ttu-id="bdaf2-106">Дополнительные сведения см. [в разделе инструкции. Объявление перечисления](how-to-declare-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="bdaf2-106">For more information, see [How to: Declare an Enumeration](how-to-declare-enumerations.md).</span></span>  
  
### <a name="to-group-related-constant-values"></a><span data-ttu-id="bdaf2-107">Группирование связанных значений констант</span><span class="sxs-lookup"><span data-stu-id="bdaf2-107">To group related constant values</span></span>  
  
1. <span data-ttu-id="bdaf2-108">Напишите объявление, которое включает уровень доступа к коду, `Enum` ключевое слово и допустимое имя.</span><span class="sxs-lookup"><span data-stu-id="bdaf2-108">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name.</span></span> <span data-ttu-id="bdaf2-109">В этом примере создается `Private` Перечисление `temperatureValues` .</span><span class="sxs-lookup"><span data-stu-id="bdaf2-109">This example creates the `Private` enumeration, `temperatureValues`.</span></span>  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2. <span data-ttu-id="bdaf2-110">Определите константы в перечислении.</span><span class="sxs-lookup"><span data-stu-id="bdaf2-110">Define the constants in the enumeration.</span></span> <span data-ttu-id="bdaf2-111">В этом примере создается `Public` Перечисление `temperatureValues` , и ему присваиваются значения.</span><span class="sxs-lookup"><span data-stu-id="bdaf2-111">This example creates the `Public` enumeration `temperatureValues` and assigns its values.</span></span>  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="bdaf2-112">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="bdaf2-112">See also</span></span>

- [<span data-ttu-id="bdaf2-113">Перечисления и уточнение имен</span><span class="sxs-lookup"><span data-stu-id="bdaf2-113">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="bdaf2-114">Практическое руководство. Ссылка на элемент перечисления</span><span class="sxs-lookup"><span data-stu-id="bdaf2-114">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="bdaf2-115">Когда следует использовать перечисление</span><span class="sxs-lookup"><span data-stu-id="bdaf2-115">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="bdaf2-116">Общие сведения о константах</span><span class="sxs-lookup"><span data-stu-id="bdaf2-116">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="bdaf2-117">Типы данных констант и литералов</span><span class="sxs-lookup"><span data-stu-id="bdaf2-117">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="bdaf2-118">Константы и перечисления</span><span class="sxs-lookup"><span data-stu-id="bdaf2-118">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
