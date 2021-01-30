---
title: Включение и отключение директив
ms.date: 01/28/2021
helpviewer_keywords:
- directives, enable
- directives, disable
- disable directive
ms.openlocfilehash: 3104b25c903465f3a650304f477b25a74591c8ba
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/30/2021
ms.locfileid: "99217242"
---
# <a name="disable-and-enable-directives-visual-basic"></a><span data-ttu-id="5e6fc-102">Директивы #Disable и #Enable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e6fc-102">#Disable and #Enable directives (Visual Basic)</span></span>

<span data-ttu-id="5e6fc-103">`#Disable` `#Enable` Директивы и являются Visual Basic директивами компилятора исходного кода.</span><span class="sxs-lookup"><span data-stu-id="5e6fc-103">The `#Disable` and `#Enable` directives are Visual Basic source code compiler directives.</span></span> <span data-ttu-id="5e6fc-104">Они используются для отключения и повторного включения конкретных предупреждений для регионов кода.</span><span class="sxs-lookup"><span data-stu-id="5e6fc-104">They are used to disable and re-enable specific warnings for regions of code.</span></span>

```vb
' Suppress warning about no awaits in this method.
#Disable Warning BC42356
    Async Function TestAsync() As Task
        Console.WriteLine("testing")
    End Function
#Enable Warning BC42356
```

<span data-ttu-id="5e6fc-105">Можно также отключить и включить список кодов предупреждений с разделителями-запятыми.</span><span class="sxs-lookup"><span data-stu-id="5e6fc-105">You can also disable and enable a comma-separated list of warning codes.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e6fc-106">См. также</span><span class="sxs-lookup"><span data-stu-id="5e6fc-106">See also</span></span>

- [<span data-ttu-id="5e6fc-107">Справочник по языку Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5e6fc-107">Visual Basic Language Reference</span></span>](../index.md)
- [<span data-ttu-id="5e6fc-108">Отключение предупреждений анализа кода</span><span class="sxs-lookup"><span data-stu-id="5e6fc-108">How to suppress code analysis warnings</span></span>](../../../fundamentals/code-analysis/suppress-warnings.md)
