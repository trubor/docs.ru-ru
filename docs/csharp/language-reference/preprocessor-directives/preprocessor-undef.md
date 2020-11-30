---
description: '#undef. Справочник по C#'
title: '#undef. Справочник по C#'
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: 7db79be7ea9d8462e09b6ae874bf0ae7d265afe2
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "91150561"
---
# <a name="undef-c-reference"></a><span data-ttu-id="1415d-103">#undef (Справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="1415d-103">#undef (C# Reference)</span></span>

<span data-ttu-id="1415d-104">`#undef` позволяет отменить определение символа таким образом, чтобы при использовании этого символа в качестве выражения в директиве [#if](./preprocessor-if.md) возвращалось значение `false`.</span><span class="sxs-lookup"><span data-stu-id="1415d-104">`#undef` lets you undefine a symbol, such that, by using the symbol as the expression in a [#if](./preprocessor-if.md) directive, the expression will evaluate to `false`.</span></span>  
  
 <span data-ttu-id="1415d-105">Символ можно определить с помощью директивы [#define](./preprocessor-define.md) или параметра компилятора [-define](../compiler-options/define-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="1415d-105">A symbol can be defined either with the [#define](./preprocessor-define.md) directive or the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="1415d-106">Директива `#undef` должна находиться в файле перед использованием любых инструкций, которые также не являются директивами.</span><span class="sxs-lookup"><span data-stu-id="1415d-106">The `#undef` directive must appear in the file before you use any statements that are not also directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1415d-107">Пример</span><span class="sxs-lookup"><span data-stu-id="1415d-107">Example</span></span>  

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

<span data-ttu-id="1415d-108">**DEBUG не определено**</span><span class="sxs-lookup"><span data-stu-id="1415d-108">**DEBUG is not defined**</span></span>

## <a name="see-also"></a><span data-ttu-id="1415d-109">См. также</span><span class="sxs-lookup"><span data-stu-id="1415d-109">See also</span></span>

- [<span data-ttu-id="1415d-110">Справочник по C#</span><span class="sxs-lookup"><span data-stu-id="1415d-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1415d-111">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="1415d-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1415d-112">Директивы препроцессора C#</span><span class="sxs-lookup"><span data-stu-id="1415d-112">C# Preprocessor Directives</span></span>](./index.md)
