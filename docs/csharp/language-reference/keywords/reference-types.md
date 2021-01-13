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
ms.openlocfilehash: 075ec5ecd8f71f5cb85bab0e2baff56409709191
ms.sourcegitcommit: 88fbb019b84c2d044d11fb4f6004aec07f2b25b1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/05/2021
ms.locfileid: "97899617"
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="242ce-103">Ссылочные типы (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="242ce-103">Reference types (C# Reference)</span></span>

<span data-ttu-id="242ce-104">В C# существуют две разновидности типов: ссылочные типы и типы значений.</span><span class="sxs-lookup"><span data-stu-id="242ce-104">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="242ce-105">В переменных ссылочных типов хранятся ссылки на их данные (объекты), а переменные типа значений содержат свои данные непосредственно.</span><span class="sxs-lookup"><span data-stu-id="242ce-105">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="242ce-106">Две переменные ссылочного типа могут ссылаться на один и тот же объект, поэтому операции над одной переменной могут затрагивать объект, на который ссылается другая переменная.</span><span class="sxs-lookup"><span data-stu-id="242ce-106">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="242ce-107">Каждая переменная типа значения имеет собственную копию данных, и операции над одной переменной не могут затрагивать другую (за исключением переменных параметров in, ref и out; см. описание модификатора параметров [in](in-parameter-modifier.md), [ref](ref.md) и [out](out-parameter-modifier.md)).</span><span class="sxs-lookup"><span data-stu-id="242ce-107">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of in, ref and out parameter variables; see [in](in-parameter-modifier.md), [ref](ref.md) and [out](out-parameter-modifier.md) parameter modifier).</span></span>

 <span data-ttu-id="242ce-108">Для объявления ссылочных типов используются следующие ключевые слова:</span><span class="sxs-lookup"><span data-stu-id="242ce-108">The following keywords are used to declare reference types:</span></span>

- [<span data-ttu-id="242ce-109">class</span><span class="sxs-lookup"><span data-stu-id="242ce-109">class</span></span>](class.md)

- [<span data-ttu-id="242ce-110">interface</span><span class="sxs-lookup"><span data-stu-id="242ce-110">interface</span></span>](interface.md)

- [<span data-ttu-id="242ce-111">delegate</span><span class="sxs-lookup"><span data-stu-id="242ce-111">delegate</span></span>](../builtin-types/reference-types.md)
- [<span data-ttu-id="242ce-112">record</span><span class="sxs-lookup"><span data-stu-id="242ce-112">record</span></span>](../builtin-types/reference-types.md)

 <span data-ttu-id="242ce-113">В C# также предусмотрены следующие встроенные ссылочные типы:</span><span class="sxs-lookup"><span data-stu-id="242ce-113">C# also provides the following built-in reference types:</span></span>

- [<span data-ttu-id="242ce-114">dynamic</span><span class="sxs-lookup"><span data-stu-id="242ce-114">dynamic</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="242ce-115">object</span><span class="sxs-lookup"><span data-stu-id="242ce-115">object</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="242ce-116">строка</span><span class="sxs-lookup"><span data-stu-id="242ce-116">string</span></span>](../builtin-types/reference-types.md)

## <a name="see-also"></a><span data-ttu-id="242ce-117">См. также</span><span class="sxs-lookup"><span data-stu-id="242ce-117">See also</span></span>

- [<span data-ttu-id="242ce-118">Справочник по C#</span><span class="sxs-lookup"><span data-stu-id="242ce-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="242ce-119">Ключевые слова в C#</span><span class="sxs-lookup"><span data-stu-id="242ce-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="242ce-120">Типы указателей</span><span class="sxs-lookup"><span data-stu-id="242ce-120">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="242ce-121">Типы значений</span><span class="sxs-lookup"><span data-stu-id="242ce-121">Value types</span></span>](../builtin-types/value-types.md)
