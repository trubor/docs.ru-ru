---
description: Дополнительные сведения см. в статье как создать новую переменную (Visual Basic).
title: Практическое руководство. Создание новой переменной
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: b473a247bc5b4d9c1d65f4721ecba3621b232e27
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481965"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a><span data-ttu-id="d20d6-103">Практическое руководство. Создание новой переменной (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d20d6-103">How to: Create a New Variable (Visual Basic)</span></span>

<span data-ttu-id="d20d6-104">Переменная создается с помощью [оператора Dim](../../../language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d20d6-104">You create a variable with a [Dim Statement](../../../language-reference/statements/dim-statement.md).</span></span>

### <a name="to-create-a-new-variable"></a><span data-ttu-id="d20d6-105">Создание новой переменной</span><span class="sxs-lookup"><span data-stu-id="d20d6-105">To create a new variable</span></span>

1. <span data-ttu-id="d20d6-106">Объявите переменную в `Dim` операторе.</span><span class="sxs-lookup"><span data-stu-id="d20d6-106">Declare the variable in a `Dim` statement.</span></span>

    ```vb
    Dim newCustomer
    ```

2. <span data-ttu-id="d20d6-107">Включите спецификации для характеристик переменной, например [Private](../../../language-reference/modifiers/private.md), [static](../../../language-reference/modifiers/static.md), [Shadows](../../../language-reference/modifiers/shadows.md)или [WithEvents](../../../language-reference/modifiers/withevents.md).</span><span class="sxs-lookup"><span data-stu-id="d20d6-107">Include specifications for the variable's characteristics, such as [Private](../../../language-reference/modifiers/private.md), [Static](../../../language-reference/modifiers/static.md), [Shadows](../../../language-reference/modifiers/shadows.md), or [WithEvents](../../../language-reference/modifiers/withevents.md).</span></span> <span data-ttu-id="d20d6-108">Дополнительные сведения см. в разделе [Характеристики объявленных элементов](../declared-elements/declared-element-characteristics.md).</span><span class="sxs-lookup"><span data-stu-id="d20d6-108">For more information, see [Declared Element Characteristics](../declared-elements/declared-element-characteristics.md).</span></span>

    ```vb
    Public Static newCustomer
    ```

    <span data-ttu-id="d20d6-109">`Dim`Ключевое слово не требуется, если в объявлении используются другие ключевые слова.</span><span class="sxs-lookup"><span data-stu-id="d20d6-109">You do not need the `Dim` keyword if you use other keywords in the declaration.</span></span>

3. <span data-ttu-id="d20d6-110">Используйте спецификации с именем переменной, которое должно соответствовать правилам и соглашениям Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d20d6-110">Follow the specifications with the variable's name, which must follow Visual Basic rules and conventions.</span></span> <span data-ttu-id="d20d6-111">Дополнительные сведения см. в разделе [Имена объявленных элементов](../declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="d20d6-111">For more information, see [Declared Element Names](../declared-elements/declared-element-names.md).</span></span>

    ```vb
    Public Static newCustomer
    ```

4. <span data-ttu-id="d20d6-112">Чтобы указать тип данных переменной, используйте имя с предложением [as](../../../language-reference/statements/as-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="d20d6-112">Follow the name with the [As](../../../language-reference/statements/as-clause.md) clause to specify the variable's data type.</span></span>

    ```vb
    Public Static newCustomer As Customer
    ```

    <span data-ttu-id="d20d6-113">Если тип данных не указан, используется значение по умолчанию: `Object` .</span><span class="sxs-lookup"><span data-stu-id="d20d6-113">If you do not specify the data type, it uses the default: `Object`.</span></span>

5. <span data-ttu-id="d20d6-114">Следуйте `As` предложению со знаком равенства ( `=` ) и выполните знак равенства с начальным значением переменной.</span><span class="sxs-lookup"><span data-stu-id="d20d6-114">Follow the `As` clause with an equal sign (`=`) and follow the equal sign with the variable's initial value.</span></span>

    <span data-ttu-id="d20d6-115">Visual Basic назначает указанное значение переменной при каждом выполнении `Dim` инструкции.</span><span class="sxs-lookup"><span data-stu-id="d20d6-115">Visual Basic assigns the specified value to the variable every time it runs the `Dim` statement.</span></span> <span data-ttu-id="d20d6-116">Если не указать начальное значение, Visual Basic присваивает начальное значение по умолчанию для типа данных переменной при первом входе в код, содержащий `Dim` инструкцию.</span><span class="sxs-lookup"><span data-stu-id="d20d6-116">If you do not specify an initial value, Visual Basic assigns the default initial value for the variable's data type when it first enters the code that contains the `Dim` statement.</span></span>

    <span data-ttu-id="d20d6-117">Если переменная является ссылочным типом, можно создать экземпляр его класса, включив в предложение ключевое слово [New operator](../../../language-reference/operators/new-operator.md) `As` .</span><span class="sxs-lookup"><span data-stu-id="d20d6-117">If the variable is a reference type, you can create an instance of its class by including the [New Operator](../../../language-reference/operators/new-operator.md) keyword in the `As` clause.</span></span> <span data-ttu-id="d20d6-118">Если не используется `New` , начальное значение переменной равно [Nothing](../../../language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="d20d6-118">If you do not use `New`, the initial value of the variable is [Nothing](../../../language-reference/nothing.md).</span></span>

    ```vb
    Public Static newCustomer As New Customer
    ```

## <a name="see-also"></a><span data-ttu-id="d20d6-119">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="d20d6-119">See also</span></span>

- [<span data-ttu-id="d20d6-120">Переменные</span><span class="sxs-lookup"><span data-stu-id="d20d6-120">Variables</span></span>](index.md)
- [<span data-ttu-id="d20d6-121">Объявление переменной</span><span class="sxs-lookup"><span data-stu-id="d20d6-121">Variable Declaration</span></span>](variable-declaration.md)
- [<span data-ttu-id="d20d6-122">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="d20d6-122">Declared Element Names</span></span>](../declared-elements/declared-element-names.md)
- [<span data-ttu-id="d20d6-123">Характеристики объявленных элементов</span><span class="sxs-lookup"><span data-stu-id="d20d6-123">Declared Element Characteristics</span></span>](../declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="d20d6-124">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="d20d6-124">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="d20d6-125">Операторы</span><span class="sxs-lookup"><span data-stu-id="d20d6-125">Statements</span></span>](../../../language-reference/statements/index.md)
- [<span data-ttu-id="d20d6-126">Вывод локального типа</span><span class="sxs-lookup"><span data-stu-id="d20d6-126">Local Type Inference</span></span>](local-type-inference.md)
- [<span data-ttu-id="d20d6-127">Оператор Option Infer</span><span class="sxs-lookup"><span data-stu-id="d20d6-127">Option Infer Statement</span></span>](../../../language-reference/statements/option-infer-statement.md)
