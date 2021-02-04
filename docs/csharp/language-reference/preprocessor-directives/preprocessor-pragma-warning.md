---
description: '#Справочник по C#. #pragma warning'
title: '#Справочник по C#. #pragma warning'
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: 16582a74bd34f2c0d89950280f1d5fde25435eea
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/30/2021
ms.locfileid: "99215996"
---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="fb1da-103">#pragma warning (Справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="fb1da-103">#pragma warning (C# Reference)</span></span>

<span data-ttu-id="fb1da-104">`#pragma warning` может включать или отключать определенные предупреждения.</span><span class="sxs-lookup"><span data-stu-id="fb1da-104">`#pragma warning` can enable or disable certain warnings.</span></span>

## <a name="syntax"></a><span data-ttu-id="fb1da-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fb1da-105">Syntax</span></span>

```csharp
#pragma warning disable warning-list
#pragma warning restore warning-list
```

## <a name="parameters"></a><span data-ttu-id="fb1da-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="fb1da-106">Parameters</span></span>

 <span data-ttu-id="fb1da-107">`warning-list` Список номеров предупреждений с разделителем-запятой.</span><span class="sxs-lookup"><span data-stu-id="fb1da-107">`warning-list` A comma-separated list of warning numbers.</span></span> <span data-ttu-id="fb1da-108">Префикс CS является необязательным.</span><span class="sxs-lookup"><span data-stu-id="fb1da-108">The "CS" prefix is optional.</span></span>

 <span data-ttu-id="fb1da-109">Если номера предупреждений не указаны, `disable` отключает все предупреждения, а `restore` включает все предупреждения.</span><span class="sxs-lookup"><span data-stu-id="fb1da-109">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>

> [!NOTE]
> <span data-ttu-id="fb1da-110">Чтобы найти номера предупреждений в Visual Studio, выполните сборку проекта, а затем поиск номеров предупреждений в окне **Вывод**.</span><span class="sxs-lookup"><span data-stu-id="fb1da-110">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>

## <a name="example"></a><span data-ttu-id="fb1da-111">Пример</span><span class="sxs-lookup"><span data-stu-id="fb1da-111">Example</span></span>

```csharp
// pragma_warning.cs
using System;

#pragma warning disable 414, CS3021
[CLSCompliant(false)]
public class C
{
    int i = 1;
    static void Main()
    {
    }
}
#pragma warning restore CS3021
[CLSCompliant(false)]  // CS3021
public class D
{
    int i = 1;
    public static void F()
    {
    }
}
```

## <a name="see-also"></a><span data-ttu-id="fb1da-112">См. также</span><span class="sxs-lookup"><span data-stu-id="fb1da-112">See also</span></span>

- [<span data-ttu-id="fb1da-113">Справочник по C#</span><span class="sxs-lookup"><span data-stu-id="fb1da-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fb1da-114">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="fb1da-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="fb1da-115">Директивы препроцессора C#</span><span class="sxs-lookup"><span data-stu-id="fb1da-115">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="fb1da-116">Ошибки компилятора C#</span><span class="sxs-lookup"><span data-stu-id="fb1da-116">C# Compiler Errors</span></span>](../compiler-messages/index.md)
- [<span data-ttu-id="fb1da-117">Отключение предупреждений анализа кода</span><span class="sxs-lookup"><span data-stu-id="fb1da-117">How to suppress code analysis warnings</span></span>](../../../fundamentals/code-analysis/suppress-warnings.md)
