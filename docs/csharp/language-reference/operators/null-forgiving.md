---
description: '!  — оператор (допускающий значение NULL) — справочник по C#'
title: '!  — оператор (допускающий значение NULL) — справочник по C#'
ms.date: 11/13/2020
f1_keywords:
- nullForgiving_CSharpKeyword
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 14bc4501dfed515e162a6e30137c9def89bb3651
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105111079"
---
# <a name="-null-forgiving-operator-c-reference"></a><span data-ttu-id="927a5-105">!</span><span class="sxs-lookup"><span data-stu-id="927a5-105">!</span></span> <span data-ttu-id="927a5-106"> — оператор (допускающий значение NULL) (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="927a5-106">(null-forgiving) operator (C# reference)</span></span>

<span data-ttu-id="927a5-107">Унарный постфиксный оператор `!`, доступный в C# 8.0 и более поздних версиях, может допускать или не допускать значение NULL.</span><span class="sxs-lookup"><span data-stu-id="927a5-107">Available in C# 8.0 and later, the unary postfix `!` operator is the null-forgiving, or null-suppression, operator.</span></span> <span data-ttu-id="927a5-108">При включенном [контексте аннотаций с поддержкой значения NULL](../../nullable-references.md#nullable-annotation-context) можно использовать оператор, допускающий значение NULL, чтобы объявить, что выражение `x` для ссылочного типа, допускающего значение NULL, не равно `null`: `x!`.</span><span class="sxs-lookup"><span data-stu-id="927a5-108">In an enabled [nullable annotation context](../../nullable-references.md#nullable-annotation-context), you use the null-forgiving operator to declare that expression `x` of a reference type isn't `null`: `x!`.</span></span> <span data-ttu-id="927a5-109">Унарный префиксный оператор `!` является [оператором логического отрицания](boolean-logical-operators.md#logical-negation-operator-).</span><span class="sxs-lookup"><span data-stu-id="927a5-109">The unary prefix `!` operator is the [logical negation operator](boolean-logical-operators.md#logical-negation-operator-).</span></span>

<span data-ttu-id="927a5-110">Оператор, допускающий NULL, ни на что не влияет во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="927a5-110">The null-forgiving operator has no effect at run time.</span></span> <span data-ttu-id="927a5-111">Он влияет только на статический анализ потока компилятора путем изменения состояния NULL выражения.</span><span class="sxs-lookup"><span data-stu-id="927a5-111">It only affects the compiler's static flow analysis by changing the null state of the expression.</span></span> <span data-ttu-id="927a5-112">Во время выполнения выражение `x!` сравнивается с результатом базового выражения `x`.</span><span class="sxs-lookup"><span data-stu-id="927a5-112">At run time, expression `x!` evaluates to the result of the underlying expression `x`.</span></span>

<span data-ttu-id="927a5-113">Дополнительные сведения о ссылочных типах, допускающих значения NULL, см. в разделе [Ссылочные типы, допускающие значение NULL](../builtin-types/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="927a5-113">For more information about the nullable reference types feature, see [Nullable reference types](../builtin-types/nullable-reference-types.md).</span></span>

## <a name="examples"></a><span data-ttu-id="927a5-114">Примеры</span><span class="sxs-lookup"><span data-stu-id="927a5-114">Examples</span></span>

<span data-ttu-id="927a5-115">Один из вариантов использования оператора, допускающего значение NULL, — тестирование логики проверки аргументов.</span><span class="sxs-lookup"><span data-stu-id="927a5-115">One of the use cases of the null-forgiving operator is in testing the argument validation logic.</span></span> <span data-ttu-id="927a5-116">Например, рассмотрим следующий класс.</span><span class="sxs-lookup"><span data-stu-id="927a5-116">For example, consider the following class:</span></span>

[!code-csharp[Person class](snippets/shared/NullForgivingOperator.cs#PersonClass)]

<span data-ttu-id="927a5-117">С помощью [платформы тестирования MSTest](../../../core/testing/unit-testing-with-mstest.md) можно создать следующий тест для логики проверки в конструкторе:</span><span class="sxs-lookup"><span data-stu-id="927a5-117">Using the [MSTest test framework](../../../core/testing/unit-testing-with-mstest.md), you can create the following test for the validation logic in the constructor:</span></span>

[!code-csharp[Person test](snippets/shared/NullForgivingOperator.cs#TestPerson)]

<span data-ttu-id="927a5-118">Без оператора, допускающего значение NULL, компилятор создает следующее предупреждение для предыдущего кода: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span><span class="sxs-lookup"><span data-stu-id="927a5-118">Without the null-forgiving operator, the compiler generates the following warning for the preceding code: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span></span> <span data-ttu-id="927a5-119">Используя оператор, допускающий значение NULL, вы сообщаете компилятору, что передача `null` ожидается и что о ней не нужно предупреждать.</span><span class="sxs-lookup"><span data-stu-id="927a5-119">By using the null-forgiving operator, you inform the compiler that passing `null` is expected and shouldn't be warned about.</span></span>

<span data-ttu-id="927a5-120">Можно также использовать оператор, допускающий значение NULL, если вы точно знаете, что выражение не может быть `null`, но компилятор не распознает это.</span><span class="sxs-lookup"><span data-stu-id="927a5-120">You can also use the null-forgiving operator when you definitely know that an expression cannot be `null` but the compiler doesn't manage to recognize that.</span></span> <span data-ttu-id="927a5-121">В следующем примере, если метод `IsValid` возвращает `true`, его аргумент не является `null`, и вы можете безопасно отменить его ссылку:</span><span class="sxs-lookup"><span data-stu-id="927a5-121">In the following example, if the `IsValid` method returns `true`, its argument is not `null` and you can safely dereference it:</span></span>

[!code-csharp[Use null-forgiving operator](snippets/shared/NullForgivingOperator.cs#UseNullForgiving)]

<span data-ttu-id="927a5-122">Без оператора, допускающего значение NULL, компилятор создает следующее предупреждение для кода `p.Name`: `Warning CS8602: Dereference of a possibly null reference`.</span><span class="sxs-lookup"><span data-stu-id="927a5-122">Without the null-forgiving operator, the compiler generates the following warning for the `p.Name` code: `Warning CS8602: Dereference of a possibly null reference`.</span></span>

<span data-ttu-id="927a5-123">Если вы можете изменить метод `IsValid`, можно использовать атрибут [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute), чтобы сообщить компилятору, что аргумент метода `IsValid` не может быть `null`, когда метод возвращает `true`:</span><span class="sxs-lookup"><span data-stu-id="927a5-123">If you can modify the `IsValid` method, you can use the [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) attribute to inform the compiler that an argument of the `IsValid` method cannot be `null` when the method returns `true`:</span></span>

[!code-csharp[Use an attribute](snippets/shared/NullForgivingOperator.cs#UseAttribute)]

<span data-ttu-id="927a5-124">В предыдущем примере не нужно использовать оператор, допускающий значение NULL, поскольку компилятор содержит достаточно информации, чтобы определить, что `p` не может быть `null` внутри `if`.</span><span class="sxs-lookup"><span data-stu-id="927a5-124">In the preceding example, you don't need to use the null-forgiving operator because the compiler has enough information to find out that `p` cannot be `null` inside the `if` statement.</span></span> <span data-ttu-id="927a5-125">См. сведения об атрибутах, позволяющих указать дополнительную информацию о состоянии NULL для переменной, в руководстве по [включению в API атрибутов для определения ожидаемых значений NULL](../attributes/nullable-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="927a5-125">For more information about the attributes that allow you to provide additional information about the null state of a variable, see [Upgrade APIs with attributes to define null expectations](../attributes/nullable-analysis.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="927a5-126">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="927a5-126">C# language specification</span></span>

<span data-ttu-id="927a5-127">См. сведения об [операторе, допускающем значение NULL](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md#the-null-forgiving-operator), в [черновике спецификации по ссылочным типам допускающим значение NULL](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md).</span><span class="sxs-lookup"><span data-stu-id="927a5-127">For more information, see [The null-forgiving operator](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md#the-null-forgiving-operator) section of the [draft of the nullable reference types specification](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="927a5-128">См. также</span><span class="sxs-lookup"><span data-stu-id="927a5-128">See also</span></span>

- [<span data-ttu-id="927a5-129">справочник по C#</span><span class="sxs-lookup"><span data-stu-id="927a5-129">C# reference</span></span>](../index.md)
- [<span data-ttu-id="927a5-130">Операторы и выражения C#</span><span class="sxs-lookup"><span data-stu-id="927a5-130">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="927a5-131">Учебник. Разработка с использованием ссылочных типов, допускающих значение NULL</span><span class="sxs-lookup"><span data-stu-id="927a5-131">Tutorial: Design with nullable reference types</span></span>](../../whats-new/tutorials/nullable-reference-types.md)
