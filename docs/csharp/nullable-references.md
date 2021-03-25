---
title: Ссылочные типы, допускающие значение null
description: В этой статье представлен обзор ссылочных типов, допускающих значение NULL, добавленных в C# 8.0. Вы узнаете, как эта функция обеспечивает безопасность от исключений, связанных со ссылочными типами, допускающими значение NULL, в новых и существующих проектах.
ms.technology: csharp-null-safety
ms.date: 04/21/2020
ms.openlocfilehash: 36078031eebc1890edf04744475c330c2ba31f96
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103480104"
---
# <a name="nullable-reference-types"></a><span data-ttu-id="2da9d-104">Ссылочные типы, допускающие значение null</span><span class="sxs-lookup"><span data-stu-id="2da9d-104">Nullable reference types</span></span>

<span data-ttu-id="2da9d-105">C# 8.0 представляет **ссылочные типы, допускающие значение NULL** и **ссылочные типы, не допускающие значение NULL**, которые позволяют делать важные заявления о свойствах для переменных ссылочного типа:</span><span class="sxs-lookup"><span data-stu-id="2da9d-105">C# 8.0 introduces **nullable reference types** and **non-nullable reference types** that enable you to make important statements about the properties for reference type variables:</span></span>

- <span data-ttu-id="2da9d-106">**Ссылка не должна иметь значение NULL**.</span><span class="sxs-lookup"><span data-stu-id="2da9d-106">**A reference isn't supposed to be null**.</span></span> <span data-ttu-id="2da9d-107">Когда переменные не должны иметь значение NULL, компилятор принудительно применяет правила, которые гарантируют, что можно разыменовать эти переменные без предварительной проверки того, что они не имеют значение NULL:</span><span class="sxs-lookup"><span data-stu-id="2da9d-107">When variables aren't supposed to be null, the compiler enforces rules that ensure it's safe to dereference these variables without first checking that it isn't null:</span></span>
  - <span data-ttu-id="2da9d-108">Переменную необходимо инициализировать со значением, отличным от NULL.</span><span class="sxs-lookup"><span data-stu-id="2da9d-108">The variable must be initialized to a non-null value.</span></span>
  - <span data-ttu-id="2da9d-109">Переменной не может быть присвоено значение `null`.</span><span class="sxs-lookup"><span data-stu-id="2da9d-109">The variable can never be assigned the value `null`.</span></span>
- <span data-ttu-id="2da9d-110">**Ссылка может иметь значение NULL**.</span><span class="sxs-lookup"><span data-stu-id="2da9d-110">**A reference may be null**.</span></span> <span data-ttu-id="2da9d-111">Когда переменные могут иметь значение NULL, компилятор применяет различные правила, чтобы убедиться, что вы правильно проверили наличие пустой ссылки:</span><span class="sxs-lookup"><span data-stu-id="2da9d-111">When variables may be null, the compiler enforces different rules to ensure that you've correctly checked for a null reference:</span></span>
  - <span data-ttu-id="2da9d-112">Переменная может быть разыменована только в том случае, когда компилятор может гарантировать, что значение не равно NULL.</span><span class="sxs-lookup"><span data-stu-id="2da9d-112">The variable may only be dereferenced when the compiler can guarantee that the value isn't null.</span></span>
  - <span data-ttu-id="2da9d-113">Эти переменные могут быть инициализированы со значением по умолчанию `null`, и им можно присвоить значение `null` в другом коде.</span><span class="sxs-lookup"><span data-stu-id="2da9d-113">These variables may be initialized with the default `null` value and may be assigned the value `null` in other code.</span></span>

<span data-ttu-id="2da9d-114">Эта новая функция предоставляет значительные преимущества по сравнению с обработкой ссылочных переменных в более ранних версиях C#, где назначение кода невозможно было определить по объявлению переменной.</span><span class="sxs-lookup"><span data-stu-id="2da9d-114">This new feature provides significant benefits over the handling of reference variables in earlier versions of C# where the design intent can't be determined from the variable declaration.</span></span> <span data-ttu-id="2da9d-115">Компилятор не обеспечивает безопасность от исключений, связанных с пустой ссылкой, для ссылочных типов:</span><span class="sxs-lookup"><span data-stu-id="2da9d-115">The compiler didn't provide safety against null reference exceptions for reference types:</span></span>

- <span data-ttu-id="2da9d-116">**Ссылка может иметь значение NULL**.</span><span class="sxs-lookup"><span data-stu-id="2da9d-116">**A reference can be null**.</span></span> <span data-ttu-id="2da9d-117">Компилятор не выдает предупреждения, если переменная ссылочного типа инициализируется со значением `null` либо позднее получает значение `null`.</span><span class="sxs-lookup"><span data-stu-id="2da9d-117">The compiler doesn't issue warnings when a reference-type variable is initialized to `null`, or later assigned `null`.</span></span> <span data-ttu-id="2da9d-118">Компилятор выдает предупреждения при разыменовании этих переменных без проверки значений NULL.</span><span class="sxs-lookup"><span data-stu-id="2da9d-118">The compiler issues warnings when these variables are dereferenced without null checks.</span></span>
- <span data-ttu-id="2da9d-119">**Предполагается, что ссылка не имеет значение NULL**.</span><span class="sxs-lookup"><span data-stu-id="2da9d-119">**A reference is assumed to be not null**.</span></span> <span data-ttu-id="2da9d-120">Компилятор не выдает предупреждения, когда ссылочные типы разыменованы.</span><span class="sxs-lookup"><span data-stu-id="2da9d-120">The compiler doesn't issue any warnings when reference types are dereferenced.</span></span> <span data-ttu-id="2da9d-121">Компилятор выдает предупреждения, если в качестве значения переменной задано выражение, которое может иметь значение NULL.</span><span class="sxs-lookup"><span data-stu-id="2da9d-121">The compiler issues warnings if a variable is set to an expression that may be null.</span></span>

<span data-ttu-id="2da9d-122">Эти предупреждения выдаются во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="2da9d-122">These warnings are emitted at compile time.</span></span> <span data-ttu-id="2da9d-123">Компилятор не добавляет никаких проверок значений NULL или других конструкций среды выполнения в контексте, допускающем значение NULL.</span><span class="sxs-lookup"><span data-stu-id="2da9d-123">The compiler doesn't add any null checks or other runtime constructs in a nullable context.</span></span> <span data-ttu-id="2da9d-124">Во время выполнения ссылка, допускающая значение NULL, и ссылка, не допускающая значения NULL, являются эквивалентными.</span><span class="sxs-lookup"><span data-stu-id="2da9d-124">At runtime, a nullable reference and a non-nullable reference are equivalent.</span></span>

<span data-ttu-id="2da9d-125">С появлением ссылочных типов, допускающих значение NULL, вы можете более четко объявить свое намерение.</span><span class="sxs-lookup"><span data-stu-id="2da9d-125">With the addition of nullable reference types, you can declare your intent more clearly.</span></span> <span data-ttu-id="2da9d-126">Значение `null` — это правильный способ представить, что переменная не ссылается на значение.</span><span class="sxs-lookup"><span data-stu-id="2da9d-126">The `null` value is the correct way to represent that a variable doesn't refer to a value.</span></span> <span data-ttu-id="2da9d-127">Эта функция не предназначена для удаления всех значений `null` из кода.</span><span class="sxs-lookup"><span data-stu-id="2da9d-127">Don't use this feature to remove all `null` values from your code.</span></span> <span data-ttu-id="2da9d-128">Вместо этого следует объявить свое намерение компилятору и другим разработчикам, которые читают ваш код.</span><span class="sxs-lookup"><span data-stu-id="2da9d-128">Rather, you should declare your intent to the compiler and other developers that read your code.</span></span> <span data-ttu-id="2da9d-129">Если вы объявите свое намерение, компилятор сообщит, когда ваш код не соответствует этому намерению.</span><span class="sxs-lookup"><span data-stu-id="2da9d-129">By declaring your intent, the compiler informs you when you write code that is inconsistent with that intent.</span></span>

<span data-ttu-id="2da9d-130">**Ссылочный тип, допускающий значение NULL** использует тот же синтаксис, что и [тип значения, допускающего значение NULL](language-reference/builtin-types/nullable-value-types.md): к типу переменной добавляется `?`.</span><span class="sxs-lookup"><span data-stu-id="2da9d-130">A **nullable reference type** is noted using the same syntax as [nullable value types](language-reference/builtin-types/nullable-value-types.md): a `?` is appended to the type of the variable.</span></span> <span data-ttu-id="2da9d-131">Например, следующее объявление переменной представляет строковую переменную, допускающую значение NULL, `name`:</span><span class="sxs-lookup"><span data-stu-id="2da9d-131">For example, the following variable declaration represents a nullable string variable, `name`:</span></span>

```csharp
string? name;
```

<span data-ttu-id="2da9d-132">Любая переменная, где `?` не добавляется к имени типа, является **ссылочным типом, не допускающим значение NULL**.</span><span class="sxs-lookup"><span data-stu-id="2da9d-132">Any variable where the `?` isn't appended to the type name is a **non-nullable reference type**.</span></span> <span data-ttu-id="2da9d-133">Сюда входят все переменные ссылочных типов в существующем коде, если вы включили эту функцию.</span><span class="sxs-lookup"><span data-stu-id="2da9d-133">That includes all reference type variables in existing code when you've enabled this feature.</span></span>

<span data-ttu-id="2da9d-134">Компилятор использует статический анализ, чтобы определить, что ссылка, допускающая значение NULL, имеет значение, отличное от NULL.</span><span class="sxs-lookup"><span data-stu-id="2da9d-134">The compiler uses static analysis to determine if a nullable reference is known to be non-null.</span></span> <span data-ttu-id="2da9d-135">Компилятор выдает предупреждение, если вы разыменовываете ссылку, допускающую значение NULL, когда она может иметь значение NULL.</span><span class="sxs-lookup"><span data-stu-id="2da9d-135">The compiler warns you if you dereference a nullable reference when it may be null.</span></span> <span data-ttu-id="2da9d-136">Это поведение можно переопределить с помощью [оператора `!`, допускающего значение NULL](language-reference/operators/null-forgiving.md), следующего после имени переменной.</span><span class="sxs-lookup"><span data-stu-id="2da9d-136">You can override this behavior by using the [null-forgiving operator](language-reference/operators/null-forgiving.md) `!` following a variable name.</span></span> <span data-ttu-id="2da9d-137">Например, если вы знаете, что переменная `name` не имеет значение NULL, а компилятор выдает предупреждение, напишите следующий код, чтобы переопределить анализ компилятора:</span><span class="sxs-lookup"><span data-stu-id="2da9d-137">For example, if you know the `name` variable isn't null but the compiler issues a warning, you can write the following code to override the compiler's analysis:</span></span>

```csharp
name!.Length;
```

## <a name="nullability-of-types"></a><span data-ttu-id="2da9d-138">Допустимость значений NULL для типов</span><span class="sxs-lookup"><span data-stu-id="2da9d-138">Nullability of types</span></span>

<span data-ttu-id="2da9d-139">Любой ссылочный тип может иметь один из четырех уровней *допустимости значений NULL*, который описывает, когда создаются предупреждения:</span><span class="sxs-lookup"><span data-stu-id="2da9d-139">Any reference type can have one of four *nullabilities*, which describes when warnings are generated:</span></span>

- <span data-ttu-id="2da9d-140">*Не допускает значения NULL*: значение NULL нельзя присвоить переменным этого типа.</span><span class="sxs-lookup"><span data-stu-id="2da9d-140">*Nonnullable*: Null can't be assigned to variables of this type.</span></span> <span data-ttu-id="2da9d-141">Переменные этого типа не нужно проверять на значение NULL перед разыменованием.</span><span class="sxs-lookup"><span data-stu-id="2da9d-141">Variables of this type don't need to be null-checked before dereferencing.</span></span>
- <span data-ttu-id="2da9d-142">*Допускает значение NULL*: значение NULL можно присвоить переменным этого типа.</span><span class="sxs-lookup"><span data-stu-id="2da9d-142">*Nullable*: Null can be assigned to variables of this type.</span></span> <span data-ttu-id="2da9d-143">Разыменование переменных этого типа без предварительной проверки `null` вызывает предупреждение.</span><span class="sxs-lookup"><span data-stu-id="2da9d-143">Dereferencing variables of this type without first checking for `null` causes a warning.</span></span>
- <span data-ttu-id="2da9d-144">*Игнорировать*: существовало до версии C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="2da9d-144">*Oblivious*: Oblivious is the pre-C# 8.0 state.</span></span> <span data-ttu-id="2da9d-145">Переменные этого типа можно разыменовать или назначить без предупреждения.</span><span class="sxs-lookup"><span data-stu-id="2da9d-145">Variables of this type can be dereferenced or assigned without warnings.</span></span>
- <span data-ttu-id="2da9d-146">*Неизвестно*: обычно относится к параметрам типа, где ограничения не сообщают компилятору, что тип должен *допускать* или *не допускать значение NULL*.</span><span class="sxs-lookup"><span data-stu-id="2da9d-146">*Unknown*: Unknown is generally for type parameters where constraints don't tell the compiler that the type must be *nullable* or *nonnullable*.</span></span>

<span data-ttu-id="2da9d-147">Допустимость значений NULL для типа в объявлении переменной управляется *контекстом допустимости значения NULL*, в котором объявлена переменная.</span><span class="sxs-lookup"><span data-stu-id="2da9d-147">The nullability of a type in a variable declaration is controlled by the *nullable context* in which the variable is declared.</span></span>

## <a name="nullable-contexts"></a><span data-ttu-id="2da9d-148">Контексты допустимости значения NULL</span><span class="sxs-lookup"><span data-stu-id="2da9d-148">Nullable contexts</span></span>

<span data-ttu-id="2da9d-149">Контексты допустимости значения NULL детально контролируют, как компилятор интерпретирует переменные ссылочного типа.</span><span class="sxs-lookup"><span data-stu-id="2da9d-149">Nullable contexts enable fine-grained control for how the compiler interprets reference type variables.</span></span> <span data-ttu-id="2da9d-150">**Контекст с заметками о допустимости значения NULL** любой исходной строки включен или отключен.</span><span class="sxs-lookup"><span data-stu-id="2da9d-150">The **nullable annotation context** of any given source line is either enabled or disabled.</span></span> <span data-ttu-id="2da9d-151">Представьте себе, что компилятор до версии C# 8.0 компилирует весь код в контексте, допускающем значения NULL: все ссылочные типы могут иметь значение NULL.</span><span class="sxs-lookup"><span data-stu-id="2da9d-151">You can think of the pre-C# 8.0 compiler as compiling all your code in a disabled nullable context: any reference type may be null.</span></span> <span data-ttu-id="2da9d-152">**Контекст с предупреждениями о допустимости значения NULL** также может быть включен или отключен.</span><span class="sxs-lookup"><span data-stu-id="2da9d-152">The **nullable warnings context** may also be enabled or disabled.</span></span> <span data-ttu-id="2da9d-153">Контекст с предупреждениями о допустимости значения NULL указывает предупреждения, созданные компилятором с помощью анализа потока.</span><span class="sxs-lookup"><span data-stu-id="2da9d-153">The nullable warnings context specifies the warnings generated by the compiler using its flow analysis.</span></span>

<span data-ttu-id="2da9d-154">Контекст с заметками о допустимости значения NULL и контекст с предупреждениями о допустимости значения NULL можно задать для проекта с помощью элемента `Nullable` в файле *CSPROJ*.</span><span class="sxs-lookup"><span data-stu-id="2da9d-154">The nullable annotation context and nullable warning context can be set for a project using the `Nullable` element in your *.csproj* file.</span></span> <span data-ttu-id="2da9d-155">Этот элемент настраивает, как компилятор интерпретирует допустимость значений NULL для типов и какие предупреждения создаются.</span><span class="sxs-lookup"><span data-stu-id="2da9d-155">This element configures how the compiler interprets the nullability of types and what warnings are generated.</span></span> <span data-ttu-id="2da9d-156">Допустимые значения:</span><span class="sxs-lookup"><span data-stu-id="2da9d-156">Valid settings are:</span></span>

- <span data-ttu-id="2da9d-157">`enable`. Контекст с заметками о допустимости значения NULL **включен**.</span><span class="sxs-lookup"><span data-stu-id="2da9d-157">`enable`: The nullable annotation context is **enabled**.</span></span> <span data-ttu-id="2da9d-158">Контекст с предупреждениями о допустимости значения NULL **включен**.</span><span class="sxs-lookup"><span data-stu-id="2da9d-158">The nullable warning context is **enabled**.</span></span>
  - <span data-ttu-id="2da9d-159">Переменные ссылочного типа, например `string`, не допускают значения NULL.</span><span class="sxs-lookup"><span data-stu-id="2da9d-159">Variables of a reference type, `string` for example, are non-nullable.</span></span>  <span data-ttu-id="2da9d-160">Все предупреждения о допустимости значений NULL включены.</span><span class="sxs-lookup"><span data-stu-id="2da9d-160">All nullability warnings are enabled.</span></span>
- <span data-ttu-id="2da9d-161">`warnings`. Контекст с заметками о допустимости значения NULL **отключен**.</span><span class="sxs-lookup"><span data-stu-id="2da9d-161">`warnings`: The nullable annotation context is **disabled**.</span></span> <span data-ttu-id="2da9d-162">Контекст с предупреждениями о допустимости значения NULL **включен**.</span><span class="sxs-lookup"><span data-stu-id="2da9d-162">The nullable warning context is **enabled**.</span></span>
  - <span data-ttu-id="2da9d-163">Переменные ссылочного типа игнорируют допустимость.</span><span class="sxs-lookup"><span data-stu-id="2da9d-163">Variables of a reference type are oblivious.</span></span> <span data-ttu-id="2da9d-164">Все предупреждения о допустимости значений NULL включены.</span><span class="sxs-lookup"><span data-stu-id="2da9d-164">All nullability warnings are enabled.</span></span>
- <span data-ttu-id="2da9d-165">`annotations`. Контекст с заметками о допустимости значения NULL **включен**.</span><span class="sxs-lookup"><span data-stu-id="2da9d-165">`annotations`: The nullable annotation context is **enabled**.</span></span> <span data-ttu-id="2da9d-166">Контекст с предупреждениями о допустимости значения NULL **отключен**.</span><span class="sxs-lookup"><span data-stu-id="2da9d-166">The nullable warning context is **disabled**.</span></span>
  - <span data-ttu-id="2da9d-167">Переменные ссылочного типа, например строка, не допускают значения NULL.</span><span class="sxs-lookup"><span data-stu-id="2da9d-167">Variables of a reference type, string for example, are non-nullable.</span></span> <span data-ttu-id="2da9d-168">Все предупреждения о допустимости значений NULL отключены.</span><span class="sxs-lookup"><span data-stu-id="2da9d-168">All nullability warnings are disabled.</span></span>
- <span data-ttu-id="2da9d-169">`disable`. Контекст с заметками о допустимости значения NULL **отключен**.</span><span class="sxs-lookup"><span data-stu-id="2da9d-169">`disable`: The nullable annotation context is **disabled**.</span></span> <span data-ttu-id="2da9d-170">Контекст с предупреждениями о допустимости значения NULL **отключен**.</span><span class="sxs-lookup"><span data-stu-id="2da9d-170">The nullable warning context is **disabled**.</span></span>
  - <span data-ttu-id="2da9d-171">Переменные ссылочного типа игнорируют допустимость, как и в более ранних версиях C#.</span><span class="sxs-lookup"><span data-stu-id="2da9d-171">Variables of a reference type are oblivious, just like earlier versions of C#.</span></span> <span data-ttu-id="2da9d-172">Все предупреждения о допустимости значений NULL отключены.</span><span class="sxs-lookup"><span data-stu-id="2da9d-172">All nullability warnings are disabled.</span></span>

<span data-ttu-id="2da9d-173">**Пример**:</span><span class="sxs-lookup"><span data-stu-id="2da9d-173">**Example**:</span></span>

```xml
<Nullable>enable</Nullable>
```

<span data-ttu-id="2da9d-174">Также можно использовать директивы для задания этих контекстов в любом месте в проекте:</span><span class="sxs-lookup"><span data-stu-id="2da9d-174">You can also use directives to set these same contexts anywhere in your project:</span></span>

- <span data-ttu-id="2da9d-175">`#nullable enable`. Устанавливает контекст с заметками о допустимости значений NULL и контекст с предупреждениями о допустимости значений NULL в режим **включен**.</span><span class="sxs-lookup"><span data-stu-id="2da9d-175">`#nullable enable`: Sets the nullable annotation context and nullable warning context to **enabled**.</span></span>
- <span data-ttu-id="2da9d-176">`#nullable disable`. Устанавливает контекст с заметками о допустимости значений NULL и контекст с предупреждениями о допустимости значений NULL в режим **отключен**.</span><span class="sxs-lookup"><span data-stu-id="2da9d-176">`#nullable disable`: Sets the nullable annotation context and nullable warning context to **disabled**.</span></span>
- <span data-ttu-id="2da9d-177">`#nullable restore`. Восстанавливает контекст с заметками о допустимости значений NULL и контекст с предупреждениями о допустимости значений NULL в соответствии с параметрами проекта.</span><span class="sxs-lookup"><span data-stu-id="2da9d-177">`#nullable restore`: Restores the nullable annotation context and nullable warning context to the project settings.</span></span>
- <span data-ttu-id="2da9d-178">`#nullable disable warnings`. Устанавливает контекст с предупреждениями о допустимости значения NULL в режим **отключен**.</span><span class="sxs-lookup"><span data-stu-id="2da9d-178">`#nullable disable warnings`: Set the nullable warning context to **disabled**.</span></span>
- <span data-ttu-id="2da9d-179">`#nullable enable warnings`. Устанавливает контекст с предупреждениями о допустимости значения NULL в режим **включен**.</span><span class="sxs-lookup"><span data-stu-id="2da9d-179">`#nullable enable warnings`: Set the nullable warning context to **enabled**.</span></span>
- <span data-ttu-id="2da9d-180">`#nullable restore warnings`. Восстанавливает контекст с предупреждениями о допустимости NULL в соответствии с параметрами проекта.</span><span class="sxs-lookup"><span data-stu-id="2da9d-180">`#nullable restore warnings`: Restores the nullable warning context to the project settings.</span></span>
- <span data-ttu-id="2da9d-181">`#nullable disable annotations`. Устанавливает контекст с заметками о допустимости значения NULL в режим **отключен**.</span><span class="sxs-lookup"><span data-stu-id="2da9d-181">`#nullable disable annotations`: Set the nullable annotation context to **disabled**.</span></span>
- <span data-ttu-id="2da9d-182">`#nullable enable annotations`. Устанавливает контекст с заметками о допустимости значения NULL в режим **включен**.</span><span class="sxs-lookup"><span data-stu-id="2da9d-182">`#nullable enable annotations`: Set the nullable annotation context to **enabled**.</span></span>
- <span data-ttu-id="2da9d-183">`#nullable restore annotations`. Восстанавливает контекст с предупреждениями о заметках в соответствии с параметрами проекта.</span><span class="sxs-lookup"><span data-stu-id="2da9d-183">`#nullable restore annotations`: Restores the annotation warning context to the project settings.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2da9d-184">Глобальный контекст, допускающий значения NULL, не применяется для созданных файлов кода.</span><span class="sxs-lookup"><span data-stu-id="2da9d-184">The global nullable context does not apply for generated code files.</span></span> <span data-ttu-id="2da9d-185">В любом случае контекст, допускающий значение NULL, *отключен* для любого исходного файла, помеченного как созданный.</span><span class="sxs-lookup"><span data-stu-id="2da9d-185">Under either strategy, the nullable context is *disabled* for any source file marked as generated.</span></span> <span data-ttu-id="2da9d-186">Это означает, что все интерфейсы API в создаваемых файлах не заносятся в заметки.</span><span class="sxs-lookup"><span data-stu-id="2da9d-186">This means any APIs in generated files are not annotated.</span></span> <span data-ttu-id="2da9d-187">Существует четыре способа пометки файла как созданного:</span><span class="sxs-lookup"><span data-stu-id="2da9d-187">There are four ways a file is marked as generated:</span></span>
>
> 1. <span data-ttu-id="2da9d-188">В файле. editorconfig укажите `generated_code = true` в разделе, который применяется к этому файлу.</span><span class="sxs-lookup"><span data-stu-id="2da9d-188">In the .editorconfig, specify `generated_code = true` in a section that applies to that file.</span></span>
> 1. <span data-ttu-id="2da9d-189">Вставьте `<auto-generated>` или `<auto-generated/>` в комментарий в верхней части файла.</span><span class="sxs-lookup"><span data-stu-id="2da9d-189">Put `<auto-generated>` or `<auto-generated/>` in a comment at the top of the file.</span></span> <span data-ttu-id="2da9d-190">Он может находиться в любой строке комментария, однако блок комментариев должен быть первым элементом в файле.</span><span class="sxs-lookup"><span data-stu-id="2da9d-190">It can be on any line in that comment, but the comment block must be the first element in the file.</span></span>
> 1. <span data-ttu-id="2da9d-191">Имя файла следует начинать с *TemporaryGeneratedFile_*</span><span class="sxs-lookup"><span data-stu-id="2da9d-191">Start the file name with *TemporaryGeneratedFile_*</span></span>
> 1. <span data-ttu-id="2da9d-192">В конце имени файла следует указать *.designer.cs*, *.generated.cs*, *.g.cs* или *.g.i.cs*.</span><span class="sxs-lookup"><span data-stu-id="2da9d-192">End the file name with *.designer.cs*, *.generated.cs*, *.g.cs*, or *.g.i.cs*.</span></span>
>
> <span data-ttu-id="2da9d-193">Генераторы могут явно использовать директиву препроцессора [`#nullable`](language-reference/preprocessor-directives/preprocessor-nullable.md).</span><span class="sxs-lookup"><span data-stu-id="2da9d-193">Generators can opt-in using the [`#nullable`](language-reference/preprocessor-directives/preprocessor-nullable.md) preprocessor directive.</span></span>

<span data-ttu-id="2da9d-194">По умолчанию контексты с заметками и предупреждениями о допустимости значения NULL **отключены**, включая новые проекты.</span><span class="sxs-lookup"><span data-stu-id="2da9d-194">By default, nullable annotation and warning contexts are **disabled**, including new projects.</span></span> <span data-ttu-id="2da9d-195">Это означает, что существующий код компилируется без изменений и без создания новых предупреждений.</span><span class="sxs-lookup"><span data-stu-id="2da9d-195">That means that your existing code compiles without changes and without generating any new warnings.</span></span>

<span data-ttu-id="2da9d-196">Эти параметры предоставляют две отдельные стратегии для [обновления существующей базы кода](nullable-migration-strategies.md) так, чтобы она могла использовать ссылочные типы, допускающие значение NULL.</span><span class="sxs-lookup"><span data-stu-id="2da9d-196">These options provide two distinct strategies to [update an existing codebase](nullable-migration-strategies.md) to use nullable reference types.</span></span>

## <a name="nullable-annotation-context"></a><span data-ttu-id="2da9d-197">Контекст с заметками о допустимости значений NULL</span><span class="sxs-lookup"><span data-stu-id="2da9d-197">Nullable annotation context</span></span>

<span data-ttu-id="2da9d-198">Компилятор использует следующие правила в отключенном контексте с заметками о допустимости значения NULL:</span><span class="sxs-lookup"><span data-stu-id="2da9d-198">The compiler uses the following rules in a disabled nullable annotation context:</span></span>

- <span data-ttu-id="2da9d-199">Нельзя объявлять ссылки, допускающие значение NULL, в отключенном контексте.</span><span class="sxs-lookup"><span data-stu-id="2da9d-199">You can't declare nullable references in a disabled context.</span></span>
- <span data-ttu-id="2da9d-200">Всем ссылочным переменным можно присвоить значение NULL.</span><span class="sxs-lookup"><span data-stu-id="2da9d-200">All reference variables may be assigned a value of null.</span></span>
- <span data-ttu-id="2da9d-201">При разыменовании переменной ссылочного типа не выдаются предупреждения.</span><span class="sxs-lookup"><span data-stu-id="2da9d-201">No warnings are generated when a variable of a reference type is dereferenced.</span></span>
- <span data-ttu-id="2da9d-202">Оператор, допускающий NULL, нельзя использовать в отключенном контексте.</span><span class="sxs-lookup"><span data-stu-id="2da9d-202">The null-forgiving operator may not be used in a disabled context.</span></span>

<span data-ttu-id="2da9d-203">Это поведение аналогично предыдущим версиям C#.</span><span class="sxs-lookup"><span data-stu-id="2da9d-203">The behavior is the same as previous versions of C#.</span></span>

<span data-ttu-id="2da9d-204">Компилятор использует следующие правила во включенном контексте с заметками о допустимости значения NULL:</span><span class="sxs-lookup"><span data-stu-id="2da9d-204">The compiler uses the following rules in an enabled nullable annotation context:</span></span>

- <span data-ttu-id="2da9d-205">Любая переменная ссылочного типа является **ссылкой, не допускающей значение NULL**.</span><span class="sxs-lookup"><span data-stu-id="2da9d-205">Any variable of a reference type is a **non-nullable reference**.</span></span>
- <span data-ttu-id="2da9d-206">Любая ссылка, не допускающая значение NULL, может быть безопасно разыменована.</span><span class="sxs-lookup"><span data-stu-id="2da9d-206">Any non-nullable reference may be dereferenced safely.</span></span>
- <span data-ttu-id="2da9d-207">Любой ссылочный тип, допускающий значение NULL, (с `?` после типа в объявлении переменной) может иметь значение NULL.</span><span class="sxs-lookup"><span data-stu-id="2da9d-207">Any nullable reference type (noted by `?` after the type in the variable declaration) may be null.</span></span> <span data-ttu-id="2da9d-208">Статический анализ определяет, что значение не имеет значение NULL при разыменовывании.</span><span class="sxs-lookup"><span data-stu-id="2da9d-208">Static analysis determines if the value is known to be non-null when it's dereferenced.</span></span> <span data-ttu-id="2da9d-209">В противном случае компилятор выдает предупреждение.</span><span class="sxs-lookup"><span data-stu-id="2da9d-209">If not, the compiler warns you.</span></span>
- <span data-ttu-id="2da9d-210">Оператор допустимости значения NULL можно использовать для объявления того, что ссылка, допускающая значение NULL, не имеет значение NULL.</span><span class="sxs-lookup"><span data-stu-id="2da9d-210">You can use the null-forgiving operator to declare that a nullable reference isn't null.</span></span>

<span data-ttu-id="2da9d-211">Во включенном контексте с заметками о допустимости значения NULL символ `?`, добавленный к ссылочному типу, объявляет **ссылочный тип, допускающий значение NULL**.</span><span class="sxs-lookup"><span data-stu-id="2da9d-211">In an enabled nullable annotation context, the `?` character appended to a reference type declares a **nullable reference type**.</span></span> <span data-ttu-id="2da9d-212">**Оператор `!`, допускающий значение NULL**, можно добавить в выражение, чтобы объявить, что выражение не имеет значение NULL.</span><span class="sxs-lookup"><span data-stu-id="2da9d-212">The **null-forgiving operator** `!` may be appended to an expression to declare that the expression isn't null.</span></span>

## <a name="nullable-warning-context"></a><span data-ttu-id="2da9d-213">Контекст с предупреждениями о допустимости значений NULL</span><span class="sxs-lookup"><span data-stu-id="2da9d-213">Nullable warning context</span></span>

<span data-ttu-id="2da9d-214">Контекст с заметками о допустимости значений NULL отличается от контекста с предупреждениями.</span><span class="sxs-lookup"><span data-stu-id="2da9d-214">The nullable warning context is distinct from the nullable annotation context.</span></span> <span data-ttu-id="2da9d-215">Предупреждения можно включить даже в том случае, если заметки отключены.</span><span class="sxs-lookup"><span data-stu-id="2da9d-215">Warnings can be enabled even when the new annotations are disabled.</span></span> <span data-ttu-id="2da9d-216">Компилятор использует статический анализ потока для определения **состояния значения NULL** любой ссылки.</span><span class="sxs-lookup"><span data-stu-id="2da9d-216">The compiler uses static flow analysis to determine the **null state** of any reference.</span></span> <span data-ttu-id="2da9d-217">Состояние значения NULL может быть **не NULL** или **может быть NULL**, если *контекст с предупреждениями о допустимости значения NULL* не **отключен**.</span><span class="sxs-lookup"><span data-stu-id="2da9d-217">The null state is either **not null** or **maybe null** when the *nullable warning context* isn't **disabled**.</span></span> <span data-ttu-id="2da9d-218">Если вы пытаетесь разыменовать ссылку, когда компилятор определяет, что она может **иметь значение NULL**, компилятор выдает предупреждение.</span><span class="sxs-lookup"><span data-stu-id="2da9d-218">If you dereference a reference when the compiler has determined it's **maybe null**, the compiler warns you.</span></span> <span data-ttu-id="2da9d-219">Состояние ссылки — **может иметь значение NULL**, за тем исключением, если компилятор может определить одно из двух условий:</span><span class="sxs-lookup"><span data-stu-id="2da9d-219">The state of a reference is **maybe null** unless the compiler can determine one of two conditions:</span></span>

1. <span data-ttu-id="2da9d-220">Переменной определенно присвоено значение, отличное от NULL.</span><span class="sxs-lookup"><span data-stu-id="2da9d-220">The variable has been definitely assigned a non-null value.</span></span>
1. <span data-ttu-id="2da9d-221">Переменная или выражение проверены на значение NULL до разыменования.</span><span class="sxs-lookup"><span data-stu-id="2da9d-221">The variable or expression has been checked against null before de-referencing it.</span></span>

<span data-ttu-id="2da9d-222">Компилятор выдает предупреждения при каждом разыменовании переменной или выражения в состоянии **может иметь значение NULL** в допускающем значение NULL контексте с предупреждением.</span><span class="sxs-lookup"><span data-stu-id="2da9d-222">The compiler generates warnings when you dereference a variable or expression that is **maybe null** in a nullable warning context.</span></span> <span data-ttu-id="2da9d-223">Кроме того, компилятор создает предупреждения, когда переменной ссылочного типа, не допускающей значение NULL, присваивается переменная или выражение, **допускающие значение NULL**, во включенном контексте с заметками, допускающем значение NULL.</span><span class="sxs-lookup"><span data-stu-id="2da9d-223">Furthermore, the compiler generates warnings when a nonnullable reference-type variable is assigned a **maybe null** variable or expression in an enabled nullable annotation context.</span></span>

## <a name="attributes-describe-apis"></a><span data-ttu-id="2da9d-224">Атрибуты для описания API</span><span class="sxs-lookup"><span data-stu-id="2da9d-224">Attributes describe APIs</span></span>

<span data-ttu-id="2da9d-225">Атрибуты добавляются в API, которые предоставляют компилятору дополнительные сведения о том, когда аргументы или возвращаемые значения могут или не могут иметь значение NULL.</span><span class="sxs-lookup"><span data-stu-id="2da9d-225">You add attributes to APIs that provide the compiler more information about when arguments or return values can or can't be null.</span></span> <span data-ttu-id="2da9d-226">Дополнительные сведения об этих атрибутах см. в статье справочника по языку, где рассматриваются [атрибуты, допускающие значение NUL](language-reference/attributes/nullable-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="2da9d-226">You can learn more about these attributes in our article in the language reference covering the [nullable attributes](language-reference/attributes/nullable-analysis.md).</span></span> <span data-ttu-id="2da9d-227">Эти атрибуты добавляются в библиотеки .NET в текущих и будущих выпусках.</span><span class="sxs-lookup"><span data-stu-id="2da9d-227">These attributes are being added to .NET libraries over current and upcoming releases.</span></span> <span data-ttu-id="2da9d-228">Сначала обновляются наиболее часто используемые API.</span><span class="sxs-lookup"><span data-stu-id="2da9d-228">The most commonly used APIs are being updated first.</span></span>

## <a name="known-pitfalls"></a><span data-ttu-id="2da9d-229">Известные ошибки</span><span class="sxs-lookup"><span data-stu-id="2da9d-229">Known pitfalls</span></span>

<span data-ttu-id="2da9d-230">С массивами и структурами, содержащими ссылочные типы, связаны известные ошибки при использовании функции ссылочных типов, допускающих значения NULL.</span><span class="sxs-lookup"><span data-stu-id="2da9d-230">Arrays and structs that contain reference types are known pitfalls in nullable reference types feature.</span></span>

### <a name="structs"></a><span data-ttu-id="2da9d-231">Структуры</span><span class="sxs-lookup"><span data-stu-id="2da9d-231">Structs</span></span>

<span data-ttu-id="2da9d-232">Структуре, которая содержит ссылочные типы, не допускающие значения NULL, может быть присвоено значение `default` без предупреждения.</span><span class="sxs-lookup"><span data-stu-id="2da9d-232">A struct that contains non-nullable reference types allows assigning `default` for it without any warnings.</span></span> <span data-ttu-id="2da9d-233">Рассмотрим следующий пример.</span><span class="sxs-lookup"><span data-stu-id="2da9d-233">Consider the following example:</span></span>

```csharp
using System;

#nullable enable

public struct Student
{
    public string FirstName;
    public string? MiddleName;
    public string LastName;
}

public static class Program
{
    public static void PrintStudent(Student student)
    {
        Console.WriteLine($"First name: {student.FirstName.ToUpper()}");
        Console.WriteLine($"Middle name: {student.MiddleName.ToUpper()}");
        Console.WriteLine($"Last name: {student.LastName.ToUpper()}");
    }

    public static void Main() => PrintStudent(default);
}
```

<span data-ttu-id="2da9d-234">В предыдущем примере в `PrintStudent(default)` не возвращается предупреждение, хотя ссылочные типы `FirstName` и `LastName`, не допускающие значения NULL, имеют значение NULL.</span><span class="sxs-lookup"><span data-stu-id="2da9d-234">In the preceding example, there is no warning in `PrintStudent(default)` while the non-nullable reference types `FirstName` and `LastName` are null.</span></span>

<span data-ttu-id="2da9d-235">Еще один более распространенный случай связан с работой с универсальными структурами.</span><span class="sxs-lookup"><span data-stu-id="2da9d-235">Another more common case is when you deal with generic structs.</span></span> <span data-ttu-id="2da9d-236">Рассмотрим следующий пример.</span><span class="sxs-lookup"><span data-stu-id="2da9d-236">Consider the following example:</span></span>

```csharp
#nullable enable

public struct Foo<T>
{
    public T Bar { get; set; }
}

public static class Program
{
    public static void Main()
    {
        string s = default(Foo<string>).Bar;
    }
}
```

<span data-ttu-id="2da9d-237">В предыдущем примере свойство `Bar` во время выполнения будет иметь значение `null` и присваивается строке, не допускающей значения NULL. При этом предупреждения не возвращаются.</span><span class="sxs-lookup"><span data-stu-id="2da9d-237">In the preceding example, the property `Bar` is going to be `null` at runtime, and it's assigned to non-nullable string without any warnings.</span></span>

### <a name="arrays"></a><span data-ttu-id="2da9d-238">Массивы</span><span class="sxs-lookup"><span data-stu-id="2da9d-238">Arrays</span></span>

<span data-ttu-id="2da9d-239">При использовании ссылочных типов, допускающих значения NULL, также могут возникать известные ошибки, связанные с массивами.</span><span class="sxs-lookup"><span data-stu-id="2da9d-239">Arrays are also a known pitfall in nullable reference types.</span></span> <span data-ttu-id="2da9d-240">Рассмотрим следующий пример, в котором не выдаются предупреждения:</span><span class="sxs-lookup"><span data-stu-id="2da9d-240">Consider the following example which doesn't produce any warnings:</span></span>

```csharp
using System;

#nullable enable

public static class Program
{
    public static void Main()
    {
        string[] values = new string[10];
        string s = values[0];
        Console.WriteLine(s.ToUpper());
    }
}
```

<span data-ttu-id="2da9d-241">В предыдущем примере объявление массива показывает, что он содержит строки, не допускающие значения NULL, а все элементы инициализируются с использованием значения NULL.</span><span class="sxs-lookup"><span data-stu-id="2da9d-241">In the preceding example, the declaration of the array shows it holds non-nullable strings, while its elements are all initialized to null.</span></span> <span data-ttu-id="2da9d-242">После этого переменной `s` присваивается значение NULL (первый элемент массива).</span><span class="sxs-lookup"><span data-stu-id="2da9d-242">Then, the variable `s` is assigned a null value (the first element of the array).</span></span> <span data-ttu-id="2da9d-243">Наконец, переменная `s` разыменовывается, в результате чего во время выполнения возникает исключение.</span><span class="sxs-lookup"><span data-stu-id="2da9d-243">Finally, the variable `s` is dereferenced causing a runtime exception.</span></span>

## <a name="see-also"></a><span data-ttu-id="2da9d-244">См. также</span><span class="sxs-lookup"><span data-stu-id="2da9d-244">See also</span></span>

- [<span data-ttu-id="2da9d-245">Ссылочные типы, допускающие значение NULL. Черновик спецификации</span><span class="sxs-lookup"><span data-stu-id="2da9d-245">Draft nullable reference types specification</span></span>](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md)
- [<span data-ttu-id="2da9d-246">Учебник "Введение в ссылки, допускающие значения NULL"</span><span class="sxs-lookup"><span data-stu-id="2da9d-246">Intro to nullable references tutorial</span></span>](tutorials/nullable-reference-types.md)
- [<span data-ttu-id="2da9d-247">Перенос существующей базы кода на ссылки, допускающие значение NULL</span><span class="sxs-lookup"><span data-stu-id="2da9d-247">Migrate an existing codebase to nullable references</span></span>](tutorials/upgrade-to-nullable-references.md)
- [<span data-ttu-id="2da9d-248">**Nullable** (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="2da9d-248">**Nullable** (C# Compiler option)</span></span>](language-reference/compiler-options/language.md#nullable)
