---
description: Ссылочные типы. Справочник по C#
title: Ссылочные типы. Справочник по C#
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: ab8eb426a3f65fd2c59920e6baa9a67bdccad82c
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498559"
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="36afa-103">Ссылочные типы (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="36afa-103">Reference types (C# Reference)</span></span>

<span data-ttu-id="36afa-104">В C# существуют две разновидности типов: ссылочные типы и типы значений.</span><span class="sxs-lookup"><span data-stu-id="36afa-104">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="36afa-105">В переменных ссылочных типов хранятся ссылки на их данные (объекты), а переменные типа значений содержат свои данные непосредственно.</span><span class="sxs-lookup"><span data-stu-id="36afa-105">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="36afa-106">Две переменные ссылочного типа могут ссылаться на один и тот же объект, поэтому операции над одной переменной могут затрагивать объект, на который ссылается другая переменная.</span><span class="sxs-lookup"><span data-stu-id="36afa-106">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="36afa-107">Каждая переменная типа значения имеет собственную копию данных, и операции над одной переменной не могут затрагивать другую (за исключением переменных параметров in, ref и out; см. описание модификатора параметров [in](in-parameter-modifier.md), [ref](ref.md) и [out](out-parameter-modifier.md)).</span><span class="sxs-lookup"><span data-stu-id="36afa-107">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of in, ref and out parameter variables; see [in](in-parameter-modifier.md), [ref](ref.md) and [out](out-parameter-modifier.md) parameter modifier).</span></span>

 <span data-ttu-id="36afa-108">Для объявления ссылочных типов используются следующие ключевые слова:</span><span class="sxs-lookup"><span data-stu-id="36afa-108">The following keywords are used to declare reference types:</span></span>

- [<span data-ttu-id="36afa-109">class</span><span class="sxs-lookup"><span data-stu-id="36afa-109">class</span></span>](class.md)

- [<span data-ttu-id="36afa-110">interface</span><span class="sxs-lookup"><span data-stu-id="36afa-110">interface</span></span>](interface.md)

- [<span data-ttu-id="36afa-111">delegate</span><span class="sxs-lookup"><span data-stu-id="36afa-111">delegate</span></span>](../builtin-types/reference-types.md)
- [<span data-ttu-id="36afa-112">record</span><span class="sxs-lookup"><span data-stu-id="36afa-112">record</span></span>](../builtin-types/reference-types.md)

 <span data-ttu-id="36afa-113">В C# также предусмотрены следующие встроенные ссылочные типы:</span><span class="sxs-lookup"><span data-stu-id="36afa-113">C# also provides the following built-in reference types:</span></span>

- [<span data-ttu-id="36afa-114">dynamic</span><span class="sxs-lookup"><span data-stu-id="36afa-114">dynamic</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="36afa-115">object</span><span class="sxs-lookup"><span data-stu-id="36afa-115">object</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="36afa-116">строка</span><span class="sxs-lookup"><span data-stu-id="36afa-116">string</span></span>](../builtin-types/reference-types.md)

## <a name="see-also"></a><span data-ttu-id="36afa-117">См. также</span><span class="sxs-lookup"><span data-stu-id="36afa-117">See also</span></span>

- [<span data-ttu-id="36afa-118">Справочник по C#</span><span class="sxs-lookup"><span data-stu-id="36afa-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="36afa-119">Ключевые слова в C#</span><span class="sxs-lookup"><span data-stu-id="36afa-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="36afa-120">Типы указателей</span><span class="sxs-lookup"><span data-stu-id="36afa-120">Pointer types</span></span>](../unsafe-code.md#pointer-types)
- [<span data-ttu-id="36afa-121">Типы значений</span><span class="sxs-lookup"><span data-stu-id="36afa-121">Value types</span></span>](../builtin-types/value-types.md)
