---
description: 'Дополнительные сведения: директивы #Disable и #Enable (Visual Basic)'
title: Включение и отключение директив
ms.date: 01/28/2021
helpviewer_keywords:
- directives, enable
- directives, disable
- disable directive
ms.openlocfilehash: d600cc959639a3f70bca5678fbc81aae0806c9cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797267"
---
# <a name="disable-and-enable-directives-visual-basic"></a><span data-ttu-id="07dce-103">Директивы #Disable и #Enable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07dce-103">#Disable and #Enable directives (Visual Basic)</span></span>

<span data-ttu-id="07dce-104">`#Disable` `#Enable` Директивы и являются Visual Basic директивами компилятора исходного кода.</span><span class="sxs-lookup"><span data-stu-id="07dce-104">The `#Disable` and `#Enable` directives are Visual Basic source code compiler directives.</span></span> <span data-ttu-id="07dce-105">Они используются для отключения и повторного включения конкретных предупреждений для регионов кода.</span><span class="sxs-lookup"><span data-stu-id="07dce-105">They are used to disable and re-enable specific warnings for regions of code.</span></span>

```vb
' Suppress warning about no awaits in this method.
#Disable Warning BC42356
    Async Function TestAsync() As Task
        Console.WriteLine("testing")
    End Function
#Enable Warning BC42356
```

<span data-ttu-id="07dce-106">Можно также отключить и включить список кодов предупреждений с разделителями-запятыми.</span><span class="sxs-lookup"><span data-stu-id="07dce-106">You can also disable and enable a comma-separated list of warning codes.</span></span>

## <a name="see-also"></a><span data-ttu-id="07dce-107">См. также</span><span class="sxs-lookup"><span data-stu-id="07dce-107">See also</span></span>

- [<span data-ttu-id="07dce-108">Справочник по языку Visual Basic</span><span class="sxs-lookup"><span data-stu-id="07dce-108">Visual Basic Language Reference</span></span>](../index.md)
- [<span data-ttu-id="07dce-109">Отключение предупреждений анализа кода</span><span class="sxs-lookup"><span data-stu-id="07dce-109">How to suppress code analysis warnings</span></span>](../../../fundamentals/code-analysis/suppress-warnings.md)
