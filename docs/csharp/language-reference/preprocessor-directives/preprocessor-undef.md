---
description: '#undef. Справочник по C#'
title: '#undef. Справочник по C#'
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: ecbf8f5793e70c7dd6e602a3992ee3783a76c7ca
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477975"
---
# <a name="undef-c-reference"></a>#undef (Справочник по C#)

`#undef` позволяет отменить определение символа таким образом, чтобы при использовании этого символа в качестве выражения в директиве [#if](./preprocessor-if.md) возвращалось значение `false`.  
  
 Символ можно определить с помощью директивы [#define](./preprocessor-define.md) или параметра компилятора [**DefineConstants**](../compiler-options/language.md#defineconstants). Директива `#undef` должна находиться в файле перед использованием любых инструкций, которые также не являются директивами.  
  
## <a name="example"></a>Пример  

```csharp
// preprocessor_undef.cs  
// compile with: /d:DEBUG  
#undef DEBUG  
using System;  
class MyClass
{  
    static void Main()
    {  
#if DEBUG  
        Console.WriteLine("DEBUG is defined");  
#else  
        Console.WriteLine("DEBUG is not defined");  
#endif  
    }  
}  
```

**DEBUG не определено**

## <a name="see-also"></a>См. также

- [Справочник по C#](../index.md)
- [Руководство по программированию на C#](../../programming-guide/index.md)
- [Директивы препроцессора C#](./index.md)
