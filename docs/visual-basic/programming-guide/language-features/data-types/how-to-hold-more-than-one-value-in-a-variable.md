---
description: Дополнительные сведения см. в статье как хранить более одного значения в переменной (Visual Basic)
title: Практическое руководство. Хранение нескольких значений в переменной
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- arrays [Visual Basic], compilation errors
- types [Visual Basic], composite
ms.assetid: 5fe0e558-aac2-4a40-b7f2-7cfea7336917
ms.openlocfilehash: 5248bc29f58cccf3b8ced95d3fba8f0d39033a83
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100484006"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a><span data-ttu-id="90013-103">Практическое руководство. Хранение нескольких значений в переменной (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90013-103">How to: Hold More Than One Value in a Variable (Visual Basic)</span></span>

<span data-ttu-id="90013-104">Переменная содержит более одного значения, если объявить ее для *составного типа данных*.</span><span class="sxs-lookup"><span data-stu-id="90013-104">A variable holds more than one value if you declare it to be of a *composite data type*.</span></span>

<span data-ttu-id="90013-105">[Составные типы данных](composite-data-types.md) включают структуры, массивы и классы.</span><span class="sxs-lookup"><span data-stu-id="90013-105">[Composite Data Types](composite-data-types.md) include structures, arrays, and classes.</span></span> <span data-ttu-id="90013-106">Переменная составного типа данных может содержать сочетание простейших типов данных и других составных типов.</span><span class="sxs-lookup"><span data-stu-id="90013-106">A variable of a composite data type can hold a combination of elementary data types and other composite types.</span></span> <span data-ttu-id="90013-107">Структуры и классы могут содержать код и данные.</span><span class="sxs-lookup"><span data-stu-id="90013-107">Structures and classes can hold code as well as data.</span></span>

## <a name="to-hold-more-than-one-value-in-a-variable"></a><span data-ttu-id="90013-108">Хранение более одного значения в переменной</span><span class="sxs-lookup"><span data-stu-id="90013-108">To hold more than one value in a variable</span></span>

1. <span data-ttu-id="90013-109">Определите составной тип данных, который будет использоваться для переменной.</span><span class="sxs-lookup"><span data-stu-id="90013-109">Determine what composite data type you want to use for your variable.</span></span>

2. <span data-ttu-id="90013-110">Если составной тип данных еще не определен, определите его, чтобы переменная могла его использовать.</span><span class="sxs-lookup"><span data-stu-id="90013-110">If the composite data type is not already defined, define it so that your variable can use it.</span></span>

    - <span data-ttu-id="90013-111">Определите структуру с помощью [оператора Structure](../../../language-reference/statements/structure-statement.md).</span><span class="sxs-lookup"><span data-stu-id="90013-111">Define a structure with a [Structure Statement](../../../language-reference/statements/structure-statement.md).</span></span>

    - <span data-ttu-id="90013-112">Определите массив с помощью [оператора Dim](../../../language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="90013-112">Define an array with a [Dim Statement](../../../language-reference/statements/dim-statement.md).</span></span>

    - <span data-ttu-id="90013-113">Определите класс с помощью [оператора класса](../../../language-reference/statements/class-statement.md).</span><span class="sxs-lookup"><span data-stu-id="90013-113">Define a class with a [Class Statement](../../../language-reference/statements/class-statement.md).</span></span>

3. <span data-ttu-id="90013-114">Объявите переменную с помощью `Dim` оператора.</span><span class="sxs-lookup"><span data-stu-id="90013-114">Declare your variable with a `Dim` statement.</span></span>

4. <span data-ttu-id="90013-115">Подпишите имя переменной с помощью `As` предложения.</span><span class="sxs-lookup"><span data-stu-id="90013-115">Follow the variable name with an `As` clause.</span></span>

5. <span data-ttu-id="90013-116">Используйте `As` ключевое слово с именем соответствующего составного типа данных.</span><span class="sxs-lookup"><span data-stu-id="90013-116">Follow the `As` keyword with the name of the appropriate composite data type.</span></span>

## <a name="see-also"></a><span data-ttu-id="90013-117">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="90013-117">See also</span></span>

- [<span data-ttu-id="90013-118">Типы данных</span><span class="sxs-lookup"><span data-stu-id="90013-118">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="90013-119">Символы типов</span><span class="sxs-lookup"><span data-stu-id="90013-119">Type Characters</span></span>](type-characters.md)
- [<span data-ttu-id="90013-120">Составные типы данных</span><span class="sxs-lookup"><span data-stu-id="90013-120">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="90013-121">Структуры</span><span class="sxs-lookup"><span data-stu-id="90013-121">Structures</span></span>](structures.md)
- [<span data-ttu-id="90013-122">Массивы</span><span class="sxs-lookup"><span data-stu-id="90013-122">Arrays</span></span>](../arrays/index.md)
- [<span data-ttu-id="90013-123">Объекты и классы</span><span class="sxs-lookup"><span data-stu-id="90013-123">Objects and Classes</span></span>](../objects-and-classes/index.md)
- [<span data-ttu-id="90013-124">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="90013-124">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
