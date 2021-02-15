---
description: Дополнительные сведения см. в статье как создать переменную, которая не изменяется в значении (Visual Basic)
title: Практическое руководство. Создание переменной, которая не изменяет значение
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
ms.openlocfilehash: 0392a27249de3bf604a73c8f8aaa16caf6f1c3e2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481939"
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a><span data-ttu-id="79a27-103">Практическое руководство. Создание переменной, которая не изменяет значение (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79a27-103">How to: Create a Variable that Does Not Change in Value (Visual Basic)</span></span>

<span data-ttu-id="79a27-104">Понятие переменной, которая не изменяет ее значение, может показаться противоречивым.</span><span class="sxs-lookup"><span data-stu-id="79a27-104">The notion of a variable that does not change its value might appear to be contradictory.</span></span> <span data-ttu-id="79a27-105">Но бывают ситуации, когда константа нецелесообразна и полезно иметь переменную с фиксированным значением.</span><span class="sxs-lookup"><span data-stu-id="79a27-105">But there are situations when a constant is not feasible and it is useful to have a variable with a fixed value.</span></span> <span data-ttu-id="79a27-106">В этом случае можно определить переменную-член с помощью ключевого слова [ReadOnly](../../../language-reference/modifiers/readonly.md) .</span><span class="sxs-lookup"><span data-stu-id="79a27-106">In such a case you can define a member variable with the [ReadOnly](../../../language-reference/modifiers/readonly.md) keyword.</span></span>

<span data-ttu-id="79a27-107">Нельзя использовать [оператор Const](../../../language-reference/statements/const-statement.md) для объявления и присваивания константного значения в следующих случаях.</span><span class="sxs-lookup"><span data-stu-id="79a27-107">You cannot use the [Const Statement](../../../language-reference/statements/const-statement.md) to declare and assign a constant value in the following circumstances:</span></span>

- <span data-ttu-id="79a27-108">`Const`Инструкция не принимает тип данных, который вы хотите использовать.</span><span class="sxs-lookup"><span data-stu-id="79a27-108">The `Const` statement does not accept the data type you want to use</span></span>

- <span data-ttu-id="79a27-109">Неизвестно значение во время компиляции</span><span class="sxs-lookup"><span data-stu-id="79a27-109">You do not know the value at compile time</span></span>

- <span data-ttu-id="79a27-110">Не удается вычислить постоянное значение во время компиляции</span><span class="sxs-lookup"><span data-stu-id="79a27-110">You are unable to compute the constant value at compile time</span></span>

### <a name="to-create-a-variable-that-does-not-change-in-value"></a><span data-ttu-id="79a27-111">Создание переменной, которая не изменяется в значении</span><span class="sxs-lookup"><span data-stu-id="79a27-111">To create a variable that does not change in value</span></span>

1. <span data-ttu-id="79a27-112">На уровне модуля объявите переменную-член с помощью [оператора Dim](../../../language-reference/statements/dim-statement.md)и включите ключевое слово [ReadOnly](../../../language-reference/modifiers/readonly.md) .</span><span class="sxs-lookup"><span data-stu-id="79a27-112">At module level, declare a member variable with the [Dim Statement](../../../language-reference/statements/dim-statement.md), and include the [ReadOnly](../../../language-reference/modifiers/readonly.md) keyword.</span></span>

    ```vb
    Dim ReadOnly timeStarted
    ```

    <span data-ttu-id="79a27-113">Можно указать `ReadOnly` только для переменной-члена.</span><span class="sxs-lookup"><span data-stu-id="79a27-113">You can specify `ReadOnly` only on a member variable.</span></span> <span data-ttu-id="79a27-114">Это означает, что необходимо определить переменную на уровне модуля вне любой процедуры.</span><span class="sxs-lookup"><span data-stu-id="79a27-114">This means you must define the variable at module level, outside of any procedure.</span></span>

2. <span data-ttu-id="79a27-115">Если значение можно вычислить в одной инструкции во время компиляции, используйте предложение инициализации в `Dim` инструкции.</span><span class="sxs-lookup"><span data-stu-id="79a27-115">If you can compute the value in a single statement at compile time, use an initialization clause in the `Dim` statement.</span></span> <span data-ttu-id="79a27-116">Используйте предложение [as](../../../language-reference/statements/as-clause.md) со знаком равенства ( `=` ), за которым следует выражение.</span><span class="sxs-lookup"><span data-stu-id="79a27-116">Follow the [As](../../../language-reference/statements/as-clause.md) clause with an equal sign (`=`), followed by an expression.</span></span> <span data-ttu-id="79a27-117">Убедитесь, что компилятор может вычислить это выражение до постоянного значения.</span><span class="sxs-lookup"><span data-stu-id="79a27-117">Be sure the compiler can evaluate this expression to a constant value.</span></span>

    ```vb
    Dim ReadOnly timeStarted As Date = Now
    ```

    <span data-ttu-id="79a27-118">Значение переменной можно присвоить `ReadOnly` только один раз.</span><span class="sxs-lookup"><span data-stu-id="79a27-118">You can assign a value to a `ReadOnly` variable only once.</span></span> <span data-ttu-id="79a27-119">После этого код не сможет изменить его значение.</span><span class="sxs-lookup"><span data-stu-id="79a27-119">Once you do so, no code can ever change its value.</span></span>

    <span data-ttu-id="79a27-120">Если значение неизвестно во время компиляции или не может быть вычислено во время компиляции в одной инструкции, вы все равно можете назначить его во время выполнения в конструкторе.</span><span class="sxs-lookup"><span data-stu-id="79a27-120">If you do not know the value at compile time, or cannot compute it at compile time in a single statement, you can still assign it at run time in a constructor.</span></span> <span data-ttu-id="79a27-121">Для этого необходимо объявить `ReadOnly` переменную на уровне класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="79a27-121">To do this, you must declare the `ReadOnly` variable at class or structure level.</span></span> <span data-ttu-id="79a27-122">В конструкторе для этого класса или структуры следует вычислить фиксированное значение переменной и присвоить его переменной перед возвратом из конструктора.</span><span class="sxs-lookup"><span data-stu-id="79a27-122">In the constructor for that class or structure, compute the variable's fixed value, and assign it to the variable before returning from the constructor.</span></span>

## <a name="see-also"></a><span data-ttu-id="79a27-123">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="79a27-123">See also</span></span>

- [<span data-ttu-id="79a27-124">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="79a27-124">WriteOnly</span></span>](../../../language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="79a27-125">Оператор Const</span><span class="sxs-lookup"><span data-stu-id="79a27-125">Const Statement</span></span>](../../../language-reference/statements/const-statement.md)
