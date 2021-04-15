---
description: 'Дополнительные сведения: директивы #Disable и #Enable (Visual Basic)'
title: Включение и отключение директив
ms.date: 01/28/2021
helpviewer_keywords:
- directives, enable
- directives, disable
- disable directive
ms.openlocfilehash: 14f8fbd0ac49829f99643d3eb0ac3149ddd9d647
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494783"
---
# <a name="disable-and-enable-directives-visual-basic"></a><span data-ttu-id="da44b-103">Директивы #Disable и #Enable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da44b-103">#Disable and #Enable directives (Visual Basic)</span></span>

<span data-ttu-id="da44b-104">`#Disable` `#Enable` Директивы и являются Visual Basic директивами компилятора исходного кода.</span><span class="sxs-lookup"><span data-stu-id="da44b-104">The `#Disable` and `#Enable` directives are Visual Basic source code compiler directives.</span></span> <span data-ttu-id="da44b-105">Они используются для отключения и повторного включения всех или конкретных предупреждений для регионов кода.</span><span class="sxs-lookup"><span data-stu-id="da44b-105">They are used to disable and re-enable all or specific warnings for regions of code.</span></span>

```vb
    Dim variable1    'warning BC42024: Unused local variable: 'variable1'.
#Disable Warning
    Dim variable2    'no warning
#Enable Warning 
    Dim variable3    'warning BC42024: Unused local variable: 'variable3'.
```

```vb
' Suppress warning about no awaits in this method.
#Disable Warning BC42356
    Async Function TestAsync() As Task
        Console.WriteLine("testing")
    End Function
#Enable Warning BC42356
```

<span data-ttu-id="da44b-106">Можно также отключить и включить список кодов предупреждений с разделителями-запятыми.</span><span class="sxs-lookup"><span data-stu-id="da44b-106">You can also disable and enable a comma-separated list of warning codes.</span></span>

## <a name="see-also"></a><span data-ttu-id="da44b-107">См. также</span><span class="sxs-lookup"><span data-stu-id="da44b-107">See also</span></span>

- [<span data-ttu-id="da44b-108">Справочник по языку Visual Basic</span><span class="sxs-lookup"><span data-stu-id="da44b-108">Visual Basic Language Reference</span></span>](../index.md)
- [<span data-ttu-id="da44b-109">Отключение предупреждений анализа кода</span><span class="sxs-lookup"><span data-stu-id="da44b-109">How to suppress code analysis warnings</span></span>](../../../fundamentals/code-analysis/suppress-warnings.md)
