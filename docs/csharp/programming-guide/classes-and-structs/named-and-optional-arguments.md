---
title: Руководство по программированию на C#. Именованные и необязательные аргументы
description: Именованные аргументы в C# указывают аргументы по имени, а не по позиции. Необязательные аргументы можно опустить.
ms.date: 09/25/2020
ms.custom: contperf-fy21q1
f1_keywords:
- namedParameter_CSharpKeyword
- cs_namedParameter
helpviewer_keywords:
- parameters [C#], named
- named arguments [C#]
- arguments [C#], named
- optional arguments [C#]
- arguments [C#], optional
- parameters [C#], optional
- named and optional arguments [C#]
ms.assetid: 839c960c-c2dc-4d05-af4d-ca5428e54008
ms.openlocfilehash: bb79d956124a610bac0de6825c1f42655789e98d
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513111"
---
# <a name="named-and-optional-arguments-c-programming-guide"></a><span data-ttu-id="30a60-104">Именованные и необязательные аргументы (Руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="30a60-104">Named and Optional Arguments (C# Programming Guide)</span></span>

<span data-ttu-id="30a60-105">C# 4 вводит именованные и необязательные аргументы.</span><span class="sxs-lookup"><span data-stu-id="30a60-105">C# 4 introduces named and optional arguments.</span></span> <span data-ttu-id="30a60-106">*Именованные аргументы* позволяют указать аргумент для параметра, связав этот аргумент с именем параметра, а не с его позицией в списке параметров.</span><span class="sxs-lookup"><span data-stu-id="30a60-106">*Named arguments* enable you to specify an argument for a parameter by matching the argument with its name rather than with its position in the parameter list.</span></span> <span data-ttu-id="30a60-107">*Необязательные аргументы* позволяют опускать аргументы для некоторых параметров.</span><span class="sxs-lookup"><span data-stu-id="30a60-107">*Optional arguments* enable you to omit arguments for some parameters.</span></span> <span data-ttu-id="30a60-108">Оба варианта можно использовать с методами, индексаторами, конструкторами и делегатами.</span><span class="sxs-lookup"><span data-stu-id="30a60-108">Both techniques can be used with methods, indexers, constructors, and delegates.</span></span>

<span data-ttu-id="30a60-109">При использовании именованных и необязательных аргументов аргументы оцениваются в том порядке, в котором они отображаются в списке аргументов, а не в списке параметров.</span><span class="sxs-lookup"><span data-stu-id="30a60-109">When you use named and optional arguments, the arguments are evaluated in the order in which they appear in the argument list, not the parameter list.</span></span>

<span data-ttu-id="30a60-110">Именованные и дополнительные параметры позволяют указать аргументы для выбранных параметров.</span><span class="sxs-lookup"><span data-stu-id="30a60-110">Named and optional parameters enable you to supply arguments for selected parameters.</span></span> <span data-ttu-id="30a60-111">Эта возможность значительно упрощает вызов интерфейсов COM, таких как API автоматизации Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="30a60-111">This capability greatly eases calls to COM interfaces such as the Microsoft Office Automation APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="30a60-112">Именованные аргументы</span><span class="sxs-lookup"><span data-stu-id="30a60-112">Named Arguments</span></span>

<span data-ttu-id="30a60-113">Именованные аргументы освобождают вас от необходимости сопоставлять порядок параметров в списках параметров вызванных методов.</span><span class="sxs-lookup"><span data-stu-id="30a60-113">Named arguments free you from matching the order of parameters in the parameter lists of called methods.</span></span> <span data-ttu-id="30a60-114">Параметр для каждого аргумента можно указать, используя имя параметра.</span><span class="sxs-lookup"><span data-stu-id="30a60-114">The parameter for each argument can be specified by parameter name.</span></span> <span data-ttu-id="30a60-115">Например, функция, которая выводит сведения о заказе (имя продавца, номер заказа и наименование товара и т. д.), может вызываться путем передачи аргументов по позиции в порядке, определяемом функцией.</span><span class="sxs-lookup"><span data-stu-id="30a60-115">For example, a function that prints order details (such as, seller name, order number & product name) can be called by sending arguments by position, in the order defined by the function.</span></span>

```csharp
PrintOrderDetails("Gift Shop", 31, "Red Mug");
```

<span data-ttu-id="30a60-116">Если вы не помните порядок параметров, но знаете их имена, можете передать аргументы в любом порядке.</span><span class="sxs-lookup"><span data-stu-id="30a60-116">If you don't remember the order of the parameters but know their names, you can send the arguments in any order.</span></span>

```csharp
PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");
PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);
```

<span data-ttu-id="30a60-117">Именованные аргументы также делают код более удобным для чтения, поскольку указывают, чему соответствует каждый аргумент.</span><span class="sxs-lookup"><span data-stu-id="30a60-117">Named arguments also improve the readability of your code by identifying what each argument represents.</span></span> <span data-ttu-id="30a60-118">В приведенном ниже примере метода `sellerName` не может быть равен NULL или пробелу.</span><span class="sxs-lookup"><span data-stu-id="30a60-118">In the example method below, the `sellerName` can't be null or white space.</span></span> <span data-ttu-id="30a60-119">Так как и `sellerName`, и `productName` являются строковыми типами, вместо передачи аргументов по позиции имеет смысл использовать именованные аргументы, чтобы устранить данную неоднозначность и сделать код более удобочитаемым.</span><span class="sxs-lookup"><span data-stu-id="30a60-119">As both `sellerName` and `productName` are string types, instead of sending arguments by position, it makes sense to use named arguments to disambiguate the two and reduce confusion for anyone reading the code.</span></span>
  
<span data-ttu-id="30a60-120">Именованные аргументы при использовании с позиционными аргументами допустимы при условии, что</span><span class="sxs-lookup"><span data-stu-id="30a60-120">Named arguments, when used with positional arguments, are valid as long as</span></span>

- <span data-ttu-id="30a60-121">за ними не следуют позиционные аргументы, либо,</span><span class="sxs-lookup"><span data-stu-id="30a60-121">they're not followed by any positional arguments, or</span></span>

    ```csharp
    PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");
    ```

- <span data-ttu-id="30a60-122">_начиная с C# 7.2_, они используются в правильной позиции.</span><span class="sxs-lookup"><span data-stu-id="30a60-122">_starting with C# 7.2_, they're used in the correct position.</span></span> <span data-ttu-id="30a60-123">В примере ниже параметр `orderNum` находится в правильной позиции, но не имеет явно заданного имени.</span><span class="sxs-lookup"><span data-stu-id="30a60-123">In the example below, the parameter `orderNum` is in the correct position but isn't explicitly named.</span></span>

    ```csharp
    PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");
    ```

<span data-ttu-id="30a60-124">Позиционные аргументы после внеочередных именованных аргументов недопустимы.</span><span class="sxs-lookup"><span data-stu-id="30a60-124">Positional arguments that follow any out-of-order named arguments are invalid.</span></span>

```csharp
// This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
```

## <a name="example"></a><span data-ttu-id="30a60-125">Пример</span><span class="sxs-lookup"><span data-stu-id="30a60-125">Example</span></span>

<span data-ttu-id="30a60-126">Приведенный ниже код реализует как примеры из этого раздела, так и некоторые дополнительные примеры.</span><span class="sxs-lookup"><span data-stu-id="30a60-126">The following code implements the examples from this section along with some additional ones.</span></span>  

[!code-csharp[csProgGuideNamedAndOptional#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/program.cs#1)]

## <a name="optional-arguments"></a><span data-ttu-id="30a60-127">Необязательные аргументы</span><span class="sxs-lookup"><span data-stu-id="30a60-127">Optional Arguments</span></span>

<span data-ttu-id="30a60-128">Определение метода, конструктора, индексатора или делегата может указывать, являются его параметры обязательными или нет.</span><span class="sxs-lookup"><span data-stu-id="30a60-128">The definition of a method, constructor, indexer, or delegate can specify its parameters are required or optional.</span></span> <span data-ttu-id="30a60-129">Любой вызов должен содержать аргументы для всех обязательных параметров; аргументы для необязательных параметров можно опустить.</span><span class="sxs-lookup"><span data-stu-id="30a60-129">Any call must provide arguments for all required parameters, but can omit arguments for optional parameters.</span></span>

<span data-ttu-id="30a60-130">Определение каждого необязательного параметра содержит его значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="30a60-130">Each optional parameter has a default value as part of its definition.</span></span> <span data-ttu-id="30a60-131">Если аргумент для параметра не передается, используется значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="30a60-131">If no argument is sent for that parameter, the default value is used.</span></span> <span data-ttu-id="30a60-132">Значением по умолчанию должен быть один из следующих типов выражений:</span><span class="sxs-lookup"><span data-stu-id="30a60-132">A default value must be one of the following types of expressions:</span></span>
  
- <span data-ttu-id="30a60-133">константное выражение;</span><span class="sxs-lookup"><span data-stu-id="30a60-133">a constant expression;</span></span>  
- <span data-ttu-id="30a60-134">выражение в форме `new ValType()`, где `ValType` — это тип значения, например, [enum](../../language-reference/builtin-types/enum.md) или [struct](../../language-reference/builtin-types/struct.md);</span><span class="sxs-lookup"><span data-stu-id="30a60-134">an expression of the form `new ValType()`, where `ValType` is a value type, such as an [enum](../../language-reference/builtin-types/enum.md) or a [struct](../../language-reference/builtin-types/struct.md);</span></span>
- <span data-ttu-id="30a60-135">выражение в форме [default(ValType)](../../language-reference/operators/default.md), где `ValType` — это тип значения.</span><span class="sxs-lookup"><span data-stu-id="30a60-135">an expression of the form [default(ValType)](../../language-reference/operators/default.md),  where `ValType` is a value type.</span></span>

<span data-ttu-id="30a60-136">Необязательные параметры определяются в конце списка параметров после всех обязательных параметров.</span><span class="sxs-lookup"><span data-stu-id="30a60-136">Optional parameters are defined at the end of the parameter list, after any required parameters.</span></span> <span data-ttu-id="30a60-137">Если вызывающий объект предоставляет аргумент для любого из последующих необязательных параметров, он должен содержать аргументы для всех предыдущих необязательных параметров.</span><span class="sxs-lookup"><span data-stu-id="30a60-137">If the caller provides an argument for any one of a succession of optional parameters, it must provide arguments for all preceding optional parameters.</span></span> <span data-ttu-id="30a60-138">Пробелы, разделенные запятыми, в списке аргументов не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="30a60-138">Comma-separated gaps in the argument list aren't supported.</span></span> <span data-ttu-id="30a60-139">Например, в следующем коде метод экземпляра `ExampleMethod` определяется одним обязательным и двумя необязательными параметрами.</span><span class="sxs-lookup"><span data-stu-id="30a60-139">For example, in the following code, instance method `ExampleMethod` is defined with one required and two optional parameters.</span></span>

[!code-csharp[csProgGuideNamedAndOptional#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#15)]

<span data-ttu-id="30a60-140">Следующий вызов `ExampleMethod` вызывает ошибку компилятора, поскольку аргумент предоставляется для третьего параметра, но не для второго.</span><span class="sxs-lookup"><span data-stu-id="30a60-140">The following call to `ExampleMethod` causes a compiler error, because an argument is provided for the third parameter but not for the second.</span></span>

```csharp
//anExample.ExampleMethod(3, ,4);
```

<span data-ttu-id="30a60-141">Если вы знаете имя третьего параметра, можете использовать для выполнения задачи именованный аргумент.</span><span class="sxs-lookup"><span data-stu-id="30a60-141">However, if you know the name of the third parameter, you can use a named argument to accomplish the task.</span></span>

```csharp
anExample.ExampleMethod(3, optionalint: 4);
```

<span data-ttu-id="30a60-142">В IntelliSense необязательные параметры заключаются в квадратные скобки, как показано на следующем рисунке:</span><span class="sxs-lookup"><span data-stu-id="30a60-142">IntelliSense uses brackets to indicate optional parameters, as shown in the following illustration:</span></span>

![Снимок экрана, показывающий краткие сведения IntelliSense для метода ExampleMethod.](./media/named-and-optional-arguments/optional-examplemethod-parameters.png)

> [!NOTE]
> <span data-ttu-id="30a60-144">Необязательные параметры также можно объявлять с помощью класса .NET <xref:System.Runtime.InteropServices.OptionalAttribute>.</span><span class="sxs-lookup"><span data-stu-id="30a60-144">You can also declare optional parameters by using the .NET <xref:System.Runtime.InteropServices.OptionalAttribute> class.</span></span> <span data-ttu-id="30a60-145">Для параметров `OptionalAttribute` значение по умолчанию не требуется.</span><span class="sxs-lookup"><span data-stu-id="30a60-145">`OptionalAttribute` parameters do not require a default value.</span></span>

## <a name="example"></a><span data-ttu-id="30a60-146">Пример</span><span class="sxs-lookup"><span data-stu-id="30a60-146">Example</span></span>

<span data-ttu-id="30a60-147">В следующем примере конструктор `ExampleClass` имеет один параметр, который является необязательным.</span><span class="sxs-lookup"><span data-stu-id="30a60-147">In the following example, the constructor for `ExampleClass` has one parameter, which is optional.</span></span> <span data-ttu-id="30a60-148">У метода экземпляра `ExampleMethod` есть один обязательный параметр, `required`, и два необязательных параметра, `optionalstr` и `optionalint`.</span><span class="sxs-lookup"><span data-stu-id="30a60-148">Instance method `ExampleMethod` has one required parameter, `required`, and two optional parameters, `optionalstr` and `optionalint`.</span></span> <span data-ttu-id="30a60-149">Код в `Main` демонстрирует различные способы, которые можно использовать для вызова конструктора и метода.</span><span class="sxs-lookup"><span data-stu-id="30a60-149">The code in `Main` shows the different ways in which the constructor and method can be invoked.</span></span>

[!code-csharp[csProgGuideNamedAndOptional#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#2)]

<span data-ttu-id="30a60-150">Приведенный выше код выводит число примеров с некорректно примененными необязательными параметрами.</span><span class="sxs-lookup"><span data-stu-id="30a60-150">The preceding code shows a number of examples where optional parameters aren't applied correctly.</span></span> <span data-ttu-id="30a60-151">Первый пример демонстрирует, что для первого параметра (обязательный) необходимо указать аргумент.</span><span class="sxs-lookup"><span data-stu-id="30a60-151">The first illustrates that an argument must be supplied for the first parameter, which is required.</span></span>
  
## <a name="com-interfaces"></a><span data-ttu-id="30a60-152">Интерфейсы COM</span><span class="sxs-lookup"><span data-stu-id="30a60-152">COM Interfaces</span></span>

<span data-ttu-id="30a60-153">Именованные и необязательные аргументы, а также поддержка динамических объектов значительно улучшают взаимодействие с API COM, такими как API автоматизации Office.</span><span class="sxs-lookup"><span data-stu-id="30a60-153">Named and optional arguments, along with support for dynamic objects, greatly improve interoperability with COM APIs, such as Office Automation APIs.</span></span>

<span data-ttu-id="30a60-154">Например, метод <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A>в интерфейсе Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> имеет семь параметров и все они необязательные.</span><span class="sxs-lookup"><span data-stu-id="30a60-154">For example, the <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> method in the Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Range> interface has seven parameters, all of which are optional.</span></span> <span data-ttu-id="30a60-155">Эти параметры показаны на следующем рисунке:</span><span class="sxs-lookup"><span data-stu-id="30a60-155">These parameters are shown in the following illustration:</span></span>

![Снимок экрана, показывающий краткие сведения IntelliSense для метода AutoFormat.](./media/named-and-optional-arguments/autoformat-method-parameters.png)

<span data-ttu-id="30a60-157">В C# 3.0 и более ранних версиях аргумент необходимо указывать для каждого параметра, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="30a60-157">In C# 3.0 and earlier versions, an argument is required for each parameter, as shown in the following example.</span></span>

[!code-csharp[csProgGuideNamedAndOptional#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#3)]

<span data-ttu-id="30a60-158">При этом вызов `AutoFormat` можно значительно упростить, используя именованные и необязательные аргументы, представленные в C# 4.0.</span><span class="sxs-lookup"><span data-stu-id="30a60-158">However, you can greatly simplify the call to `AutoFormat` by using named and optional arguments, introduced in C# 4.0.</span></span> <span data-ttu-id="30a60-159">Именованные и необязательные аргументы позволяют опускать аргументы для необязательных параметров, если значение параметра по умолчанию менять не нужно.</span><span class="sxs-lookup"><span data-stu-id="30a60-159">Named and optional arguments enable you to omit the argument for an optional parameter if you don't want to change the parameter's default value.</span></span> <span data-ttu-id="30a60-160">В следующем вызове значение задается только для одного из семи параметров.</span><span class="sxs-lookup"><span data-stu-id="30a60-160">In the following call, a value is specified for only one of the seven parameters.</span></span>

[!code-csharp[csProgGuideNamedAndOptional#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#13)]

<span data-ttu-id="30a60-161">См. сведения и примеры в руководствах по [использованию именованных и необязательных аргументов в программировании Office](./how-to-use-named-and-optional-arguments-in-office-programming.md) и [получению доступа к объектам взаимодействия Office с помощью функций языка C#](../interop/how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="30a60-161">For more information and examples, see [How to use named and optional arguments in Office programming](./how-to-use-named-and-optional-arguments-in-office-programming.md) and [How to access Office interop objects by using C# features](../interop/how-to-access-office-onterop-objects.md).</span></span>
  
## <a name="overload-resolution"></a><span data-ttu-id="30a60-162">Overload Resolution</span><span class="sxs-lookup"><span data-stu-id="30a60-162">Overload Resolution</span></span>

<span data-ttu-id="30a60-163">Использование именованных и необязательных аргументов влияет на разрешение перегрузки описанным ниже образом.</span><span class="sxs-lookup"><span data-stu-id="30a60-163">Use of named and optional arguments affects overload resolution in the following ways:</span></span>

- <span data-ttu-id="30a60-164">Метод, индексатор или конструктор является кандидатом на выполнение, если каждый из его параметров необязателен либо по имени или позиции соответствует одному и тому же аргументу в операторе вызова, и этот аргумент можно преобразовать в тип параметра.</span><span class="sxs-lookup"><span data-stu-id="30a60-164">A method, indexer, or constructor is a candidate for execution if each of its parameters either is optional or corresponds, by name or by position, to a single argument in the calling statement, and that argument can be converted to the type of the parameter.</span></span>  
- <span data-ttu-id="30a60-165">Если найдено более одного кандидата, правила разрешения перегрузки для предпочтительных преобразований применяются к аргументам, указанным явно.</span><span class="sxs-lookup"><span data-stu-id="30a60-165">If more than one candidate is found, overload resolution rules for preferred conversions are applied to the arguments that are explicitly specified.</span></span> <span data-ttu-id="30a60-166">Опущенные аргументы для необязательных параметров игнорируются.</span><span class="sxs-lookup"><span data-stu-id="30a60-166">Omitted arguments for optional parameters are ignored.</span></span>
- <span data-ttu-id="30a60-167">Если два кандидата определяются как равно подходящие, предпочтение отдается кандидату без необязательных параметров, аргументы которых в вызове были опущены.</span><span class="sxs-lookup"><span data-stu-id="30a60-167">If two candidates are judged to be equally good, preference goes to a candidate that doesn't have optional parameters for which arguments were omitted in the call.</span></span> <span data-ttu-id="30a60-168">При разрешении перегрузки обычно используются кандидаты с меньшим числом параметров.</span><span class="sxs-lookup"><span data-stu-id="30a60-168">Overload resolution generally prefers candidates that have fewer parameters.</span></span>
  
## <a name="c-language-specification"></a><span data-ttu-id="30a60-169">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="30a60-169">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
