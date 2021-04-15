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
# <a name="disable-and-enable-directives-visual-basic"></a>Директивы #Disable и #Enable (Visual Basic)

`#Disable` `#Enable` Директивы и являются Visual Basic директивами компилятора исходного кода. Они используются для отключения и повторного включения всех или конкретных предупреждений для регионов кода.

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

Можно также отключить и включить список кодов предупреждений с разделителями-запятыми.

## <a name="see-also"></a>См. также

- [Справочник по языку Visual Basic](../index.md)
- [Отключение предупреждений анализа кода](../../../fundamentals/code-analysis/suppress-warnings.md)
