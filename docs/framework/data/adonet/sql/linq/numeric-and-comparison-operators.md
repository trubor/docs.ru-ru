---
description: 'Дополнительные сведения: числовые и операторы сравнения'
title: Числовые операторы и операторы сравнения
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: 5b17f19769436ac4e575ac974668eadc3b17b8f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695532"
---
# <a name="numeric-and-comparison-operators"></a><span data-ttu-id="546e4-103">Числовые операторы и операторы сравнения</span><span class="sxs-lookup"><span data-stu-id="546e4-103">Numeric and Comparison Operators</span></span>

<span data-ttu-id="546e4-104">Арифметические операторы и операторы сравнения работают в среде (CLR) соответствующим образом, за исключением следующих моментов.</span><span class="sxs-lookup"><span data-stu-id="546e4-104">Arithmetic and comparison operators work as expected in the common language runtime (CLR) except as follows:</span></span>

- <span data-ttu-id="546e4-105">SQL не поддерживает оператор modulus для чисел с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="546e4-105">SQL does not support the modulus operator on floating-point numbers.</span></span>

- <span data-ttu-id="546e4-106">SQL не поддерживает непроверяемые арифметические операции.</span><span class="sxs-lookup"><span data-stu-id="546e4-106">SQL does not support unchecked arithmetic.</span></span>

- <span data-ttu-id="546e4-107">Операторы инкремента или декремента вызывают побочные эффекты, если используются в выражениях, которые не могут быть реплицированы в SQL и поэтому не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="546e4-107">Increment and decrement operators cause side-effects when you use them in expressions that cannot be replicated in SQL and are, therefore, not supported.</span></span>

## <a name="supported-operators"></a><span data-ttu-id="546e4-108">Поддерживаемые операторы</span><span class="sxs-lookup"><span data-stu-id="546e4-108">Supported Operators</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="546e4-109">поддерживает следующие операторы.</span><span class="sxs-lookup"><span data-stu-id="546e4-109">supports the following operators.</span></span>

- <span data-ttu-id="546e4-110">Основные арифметические операторы</span><span class="sxs-lookup"><span data-stu-id="546e4-110">Basic arithmetic operators:</span></span>

  - `+`

  - <span data-ttu-id="546e4-111">`-` (вычитание)</span><span class="sxs-lookup"><span data-stu-id="546e4-111">`-` (subtraction)</span></span>

  - `*`

  - `/`

  - <span data-ttu-id="546e4-112">Оператор целочисленного деления Visual Basic (`\`)</span><span class="sxs-lookup"><span data-stu-id="546e4-112">Visual Basic integer division (`\`)</span></span>

  - <span data-ttu-id="546e4-113">`%` (Visual Basic `Mod`)</span><span class="sxs-lookup"><span data-stu-id="546e4-113">`%` (Visual Basic `Mod`)</span></span>

  - `<<`

  - `>>`

  - <span data-ttu-id="546e4-114">`-` (унарное отрицание)</span><span class="sxs-lookup"><span data-stu-id="546e4-114">`-` (unary negation)</span></span>

- <span data-ttu-id="546e4-115">Основные операторы сравнения</span><span class="sxs-lookup"><span data-stu-id="546e4-115">Basic comparison operators:</span></span>

  - <span data-ttu-id="546e4-116">Visual Basic `=` и C# `==`</span><span class="sxs-lookup"><span data-stu-id="546e4-116">Visual Basic `=` and C# `==`</span></span>

  - <span data-ttu-id="546e4-117">Visual Basic `<>` и C# `!=`</span><span class="sxs-lookup"><span data-stu-id="546e4-117">Visual Basic `<>` and C# `!=`</span></span>

  - <span data-ttu-id="546e4-118">Visual Basic `Is/IsNot`</span><span class="sxs-lookup"><span data-stu-id="546e4-118">Visual Basic `Is/IsNot`</span></span>

  - `<`

  - `<=`

  - `>`

  - `>=`

## <a name="see-also"></a><span data-ttu-id="546e4-119">См. также</span><span class="sxs-lookup"><span data-stu-id="546e4-119">See also</span></span>

- [<span data-ttu-id="546e4-120">Типы данных и функции</span><span class="sxs-lookup"><span data-stu-id="546e4-120">Data Types and Functions</span></span>](data-types-and-functions.md)
- [<span data-ttu-id="546e4-121">Операторы в C#</span><span class="sxs-lookup"><span data-stu-id="546e4-121">C# Operators</span></span>](../../../../../csharp/language-reference/operators/index.md)
- [<span data-ttu-id="546e4-122">Операторы</span><span class="sxs-lookup"><span data-stu-id="546e4-122">Operators</span></span>](../../../../../visual-basic/language-reference/operators/index.md)
