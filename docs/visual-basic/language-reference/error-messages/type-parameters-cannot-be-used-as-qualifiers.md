---
description: 'Дополнительные сведения о: BC32098: параметры типа нельзя использовать в качестве квалификаторов'
title: Параметры типа нельзя использовать в качестве квалификаторов
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 61be8e81c9cf6c7a8339c7bbf0ad9566f582eb57
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675056"
---
# <a name="bc32098-type-parameters-cannot-be-used-as-qualifiers"></a><span data-ttu-id="38049-103">BC32098: параметры типа не могут использоваться в качестве квалификаторов</span><span class="sxs-lookup"><span data-stu-id="38049-103">BC32098: Type parameters cannot be used as qualifiers</span></span>

<span data-ttu-id="38049-104">Элемент программирования дополняется уточняющей строкой, включающей параметр типа.</span><span class="sxs-lookup"><span data-stu-id="38049-104">A programming element is qualified with a qualification string that includes a type parameter.</span></span>

<span data-ttu-id="38049-105">Параметр типа представляет требование для типа, который должен предоставляться при создании универсального типа.</span><span class="sxs-lookup"><span data-stu-id="38049-105">A type parameter represents a requirement for a type that is to be supplied when the generic type is constructed.</span></span> <span data-ttu-id="38049-106">Он не представляет определенный определенный тип.</span><span class="sxs-lookup"><span data-stu-id="38049-106">It does not represent a specific defined type.</span></span> <span data-ttu-id="38049-107">Уточняющая строка должна включать только те элементы, которые определены во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="38049-107">A qualification string must include only elements that are defined at compile time.</span></span>

<span data-ttu-id="38049-108">Следующий код может вызвать эту ошибку:</span><span class="sxs-lookup"><span data-stu-id="38049-108">The following code can generate this error:</span></span>

```vb
Public Function CheckText(Of c As System.Windows.Forms.Control)(
    badText As String) As Boolean

    Dim saveText As c.Text
    ' Insert code to look for badText within saveText.
End Function
```

 <span data-ttu-id="38049-109">**Идентификатор ошибки:** BC32098</span><span class="sxs-lookup"><span data-stu-id="38049-109">**Error ID:** BC32098</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="38049-110">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="38049-110">To correct this error</span></span>

1. <span data-ttu-id="38049-111">Удалите параметр типа из строки квалификации или замените его определенным типом.</span><span class="sxs-lookup"><span data-stu-id="38049-111">Remove the type parameter from the qualification string, or replace it with a defined type.</span></span>

2. <span data-ttu-id="38049-112">Если необходимо использовать сконструированный тип для нахождение квалифицированного программного элемента, необходимо использовать дополнительную логику программы.</span><span class="sxs-lookup"><span data-stu-id="38049-112">If you need to use a constructed type to locate the programming element being qualified, you must use additional program logic.</span></span>

## <a name="see-also"></a><span data-ttu-id="38049-113">См. также</span><span class="sxs-lookup"><span data-stu-id="38049-113">See also</span></span>

- [<span data-ttu-id="38049-114">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="38049-114">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="38049-115">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="38049-115">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="38049-116">Type List</span><span class="sxs-lookup"><span data-stu-id="38049-116">Type List</span></span>](../statements/type-list.md)
