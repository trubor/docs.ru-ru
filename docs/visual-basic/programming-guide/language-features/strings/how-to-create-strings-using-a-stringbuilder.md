---
description: Дополнительные сведения см. в статье как создавать строки с помощью StringBuilder в Visual Basic
title: Инструкции. Создание строк с помощью StringBuilder
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: 6def32517f71ec3c2a7795c3395e3e572903ce1e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429823"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="cf463-103">Инструкции. Создание строк с помощью StringBuilder в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cf463-103">How to: create strings using a StringBuilder in Visual Basic</span></span>

<span data-ttu-id="cf463-104">В этом примере создается длинная строка из множества меньших строк с помощью <xref:System.Text.StringBuilder> класса.</span><span class="sxs-lookup"><span data-stu-id="cf463-104">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="cf463-105"><xref:System.Text.StringBuilder>Класс является более эффективным, чем `&=` оператор для сцепления многих строк.</span><span class="sxs-lookup"><span data-stu-id="cf463-105">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>

## <a name="example"></a><span data-ttu-id="cf463-106">Пример</span><span class="sxs-lookup"><span data-stu-id="cf463-106">Example</span></span>

<span data-ttu-id="cf463-107">В следующем примере создается экземпляр <xref:System.Text.StringBuilder> класса, добавляются строки 1 000 в этот экземпляр, а затем возвращается его строковое представление:</span><span class="sxs-lookup"><span data-stu-id="cf463-107">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation:</span></span>

 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]

## <a name="see-also"></a><span data-ttu-id="cf463-108">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="cf463-108">See also</span></span>

- <span data-ttu-id="cf463-109">[Using the StringBuilder class](../../../../standard/base-types/stringbuilder.md) (Использование класса StringBuilder)</span><span class="sxs-lookup"><span data-stu-id="cf463-109">[Using the StringBuilder Class](../../../../standard/base-types/stringbuilder.md)</span></span>
- [<span data-ttu-id="cf463-110"> Оператор&=</span><span class="sxs-lookup"><span data-stu-id="cf463-110">&= Operator</span></span>](../../../language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="cf463-111">Строки</span><span class="sxs-lookup"><span data-stu-id="cf463-111">Strings</span></span>](index.md)
- [<span data-ttu-id="cf463-112">Создание строк</span><span class="sxs-lookup"><span data-stu-id="cf463-112">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="cf463-113">Операции со строками</span><span class="sxs-lookup"><span data-stu-id="cf463-113">Manipulating Strings</span></span>](../../../../standard/base-types/best-practices-strings.md)
