---
description: 'Дополнительные сведения: все поля ширины полей, за исключением последнего элемента, должны быть больше нуля'
title: Все поля, за исключением последнего элемента, должны иметь ширину больше нуля
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_FieldWidthsMustPositive
ms.assetid: 41d8c661-a749-4c89-be56-905c6e7c3c9d
ms.openlocfilehash: cf2edb21f017031c7dd333893d554353eceebe73
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787387"
---
# <a name="all-field-widths-except-the-last-element-must-be-greater-than-zero"></a><span data-ttu-id="d230d-103">Все поля, за исключением последнего элемента, должны иметь ширину больше нуля</span><span class="sxs-lookup"><span data-stu-id="d230d-103">All field widths, except the last element, must be greater than zero</span></span>

<span data-ttu-id="d230d-104">Все поля, за исключением последнего элемента, должны иметь ширину больше нуля.</span><span class="sxs-lookup"><span data-stu-id="d230d-104">All field widths, except the last element, must be greater than zero.</span></span> <span data-ttu-id="d230d-105">Ширина поля, меньшая или равная нулю в последнем элементе, указывает, что поле имеет переменную длину.</span><span class="sxs-lookup"><span data-stu-id="d230d-105">A field width less than or equal to zero in the last element indicates the last field is of variable length.</span></span>  
  
 <span data-ttu-id="d230d-106">Операция не была выполнена, так как ширина поля, отличного от последнего элемента, задана равной нулю или меньше.</span><span class="sxs-lookup"><span data-stu-id="d230d-106">The operation has failed because a field width other than the last element is set to zero or less.</span></span> <span data-ttu-id="d230d-107">Ширина поля, меньшая или равная нулю, может использоваться в последнем элементе для указания на то, что последнее поле имеет переменную длину, но не может использоваться как любой другой элемент.</span><span class="sxs-lookup"><span data-stu-id="d230d-107">A field width less than or equal to zero can be used as the last element to indicate that the last field is of variable length, but it cannot be used as any other element.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d230d-108">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="d230d-108">To correct this error</span></span>  
  
- <span data-ttu-id="d230d-109">Задайте для ширины поля корректное значение.</span><span class="sxs-lookup"><span data-stu-id="d230d-109">Set the field width to the correct length.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d230d-110">См. также</span><span class="sxs-lookup"><span data-stu-id="d230d-110">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetFieldWidths%2A?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.FieldWidths>
- [<span data-ttu-id="d230d-111">Практическое руководство. Чтение из текстовых файлов с полями фиксированного размера</span><span class="sxs-lookup"><span data-stu-id="d230d-111">How to: Read From Fixed-width Text Files</span></span>](../developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="d230d-112">TextFieldParser Object</span><span class="sxs-lookup"><span data-stu-id="d230d-112">TextFieldParser Object</span></span>](../language-reference/objects/textfieldparser-object.md)
