---
title: Методы. Руководство по программированию на C#
description: Метод в C# — это блок кода, содержащий ряд инструкций. Программа выполняет инструкции путем вызова метода и указания аргументов.
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#]
- C# language, methods
ms.assetid: cc738f07-e8cd-4683-9585-9f40c0667c37
ms.openlocfilehash: 879e57cfbce82f1aa77f8810e23d6a61a6ea5bc8
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899455"
---
# <a name="methods-c-programming-guide"></a><span data-ttu-id="e3c79-104">Методы (Руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="e3c79-104">Methods (C# Programming Guide)</span></span>

<span data-ttu-id="e3c79-105">Метод — это блок кода, содержащий ряд инструкций.</span><span class="sxs-lookup"><span data-stu-id="e3c79-105">A method is a code block that contains a series of statements.</span></span> <span data-ttu-id="e3c79-106">Программа инициирует выполнение инструкций, вызывая метод и указывая все аргументы, необходимые для этого метода.</span><span class="sxs-lookup"><span data-stu-id="e3c79-106">A program causes the statements to be executed by calling the method and specifying any required method arguments.</span></span> <span data-ttu-id="e3c79-107">В C# все инструкции выполняются в контексте метода.</span><span class="sxs-lookup"><span data-stu-id="e3c79-107">In C#, every executed instruction is performed in the context of a method.</span></span> <span data-ttu-id="e3c79-108">Метод `Main` является точкой входа для каждого приложения C# и вызывается общеязыковой средой выполнения (CLR) при запуске программы.</span><span class="sxs-lookup"><span data-stu-id="e3c79-108">The `Main` method is the entry point for every C# application and it's called by the common language runtime (CLR) when the program is started.</span></span>

> [!NOTE]
> <span data-ttu-id="e3c79-109">В этой статье рассматриваются названные методы.</span><span class="sxs-lookup"><span data-stu-id="e3c79-109">This article discusses named methods.</span></span> <span data-ttu-id="e3c79-110">Сведения об анонимных функциях см. в разделе [Анонимные функции](../statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="e3c79-110">For information about anonymous functions, see [Anonymous Functions](../statements-expressions-operators/anonymous-functions.md).</span></span>

## <a name="method-signatures"></a><span data-ttu-id="e3c79-111">Сигнатуры методов</span><span class="sxs-lookup"><span data-stu-id="e3c79-111">Method signatures</span></span>

<span data-ttu-id="e3c79-112">Методы объявляются в [классе](../../language-reference/keywords/class.md), [структуре](../../language-reference/builtin-types/struct.md) или [интерфейсе](../interfaces/index.md) путем указания уровня доступа, такого как `public` или `private`, необязательных модификаторов, таких как `abstract` или `sealed`, возвращаемого значения, имени метода и всех параметров этого метода.</span><span class="sxs-lookup"><span data-stu-id="e3c79-112">Methods are declared in a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md), or [interface](../interfaces/index.md) by specifying the access level such as `public` or `private`, optional modifiers such as `abstract` or `sealed`, the return value, the name of the method, and any method parameters.</span></span> <span data-ttu-id="e3c79-113">Все эти части вместе представляют собой сигнатуру метода.</span><span class="sxs-lookup"><span data-stu-id="e3c79-113">These parts together are the signature of the method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e3c79-114">Тип возврата метода не является частью сигнатуры метода в целях перегрузки метода.</span><span class="sxs-lookup"><span data-stu-id="e3c79-114">A return type of a method is not part of the signature of the method for the purposes of method overloading.</span></span> <span data-ttu-id="e3c79-115">Однако он является частью сигнатуры метода при определении совместимости между делегатом и методом, который он указывает.</span><span class="sxs-lookup"><span data-stu-id="e3c79-115">However, it is part of the signature of the method when determining the compatibility between a delegate and the method that it points to.</span></span>

<span data-ttu-id="e3c79-116">Параметры метода заключаются в скобки и разделяются запятыми.</span><span class="sxs-lookup"><span data-stu-id="e3c79-116">Method parameters are enclosed in parentheses and are separated by commas.</span></span> <span data-ttu-id="e3c79-117">Пустые скобки указывают, что параметры методу не требуются.</span><span class="sxs-lookup"><span data-stu-id="e3c79-117">Empty parentheses indicate that the method requires no parameters.</span></span> <span data-ttu-id="e3c79-118">Этот класс содержит четыре метода:</span><span class="sxs-lookup"><span data-stu-id="e3c79-118">This class contains four methods:</span></span>

[!code-csharp[DifferentModifiersOnMethods#1](snippets/methods/Program.cs#1)]

## <a name="method-access"></a><span data-ttu-id="e3c79-119">Доступ к методу</span><span class="sxs-lookup"><span data-stu-id="e3c79-119">Method access</span></span>

<span data-ttu-id="e3c79-120">Вызов метода в объекте аналогичен доступу к полю.</span><span class="sxs-lookup"><span data-stu-id="e3c79-120">Calling a method on an object is like accessing a field.</span></span> <span data-ttu-id="e3c79-121">После имени объекта добавьте точку, имя метода и круглые скобки.</span><span class="sxs-lookup"><span data-stu-id="e3c79-121">After the object name, add a period, the name of the method, and parentheses.</span></span> <span data-ttu-id="e3c79-122">Аргументы перечисляются в этих скобках и разделяются запятыми.</span><span class="sxs-lookup"><span data-stu-id="e3c79-122">Arguments are listed within the parentheses, and are separated by commas.</span></span> <span data-ttu-id="e3c79-123">Таким образом, методы класса `Motorcycle` могут вызываться, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="e3c79-123">The methods of the `Motorcycle` class can therefore be called as in the following example:</span></span>

[!code-csharp[CallingMethods#2](snippets/methods/Program.cs#2)]

## <a name="method-parameters-vs-arguments"></a><span data-ttu-id="e3c79-124">Параметры и аргументы метода</span><span class="sxs-lookup"><span data-stu-id="e3c79-124">Method parameters vs. arguments</span></span>

<span data-ttu-id="e3c79-125">Определение метода задает имена и типы всех необходимых параметров.</span><span class="sxs-lookup"><span data-stu-id="e3c79-125">The method definition specifies the names and types of any parameters that are required.</span></span> <span data-ttu-id="e3c79-126">Когда вызывающий код вызывает метод, он предоставляет конкретные значения, называемые аргументами, для каждого параметра.</span><span class="sxs-lookup"><span data-stu-id="e3c79-126">When calling code calls the method, it provides concrete values called arguments for each parameter.</span></span> <span data-ttu-id="e3c79-127">Аргументы должны быть совместимы с типом параметра, но имя аргумента (если есть), используемое в вызывающем коде, не обязательно должно совпадать с именем параметра, указанным в методе.</span><span class="sxs-lookup"><span data-stu-id="e3c79-127">The arguments must be compatible with the parameter type but the argument name (if any) used in the calling code doesn't have to be the same as the parameter named defined in the method.</span></span> <span data-ttu-id="e3c79-128">Пример:</span><span class="sxs-lookup"><span data-stu-id="e3c79-128">For example:</span></span>

[!code-csharp[MethodExamples#3](snippets/methods/Program.cs#3)]

## <a name="passing-by-reference-vs-passing-by-value"></a><span data-ttu-id="e3c79-129">Передача по ссылке и передача по значению</span><span class="sxs-lookup"><span data-stu-id="e3c79-129">Passing by reference vs. passing by value</span></span>

<span data-ttu-id="e3c79-130">По умолчанию при передаче в метод экземпляра [типа значения](../../language-reference/builtin-types/value-types.md) вместо самого этого экземпляра передается его копия.</span><span class="sxs-lookup"><span data-stu-id="e3c79-130">By default, when an instance of a [value type](../../language-reference/builtin-types/value-types.md) is passed to a method, its copy is passed instead of the instance itself.</span></span> <span data-ttu-id="e3c79-131">Поэтому изменения в аргументе не оказывают влияния на исходный экземпляр в вызывающем методе.</span><span class="sxs-lookup"><span data-stu-id="e3c79-131">Therefore, changes to the argument have no effect on the original instance in the calling method.</span></span> <span data-ttu-id="e3c79-132">Чтобы передать экземпляр типа значения по ссылке, используйте ключевое слово `ref`.</span><span class="sxs-lookup"><span data-stu-id="e3c79-132">To pass a value-type instance by reference, use the `ref` keyword.</span></span> <span data-ttu-id="e3c79-133">Дополнительные сведения см. в разделе [Передача параметров типа значения](./passing-value-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e3c79-133">For more information, see [Passing Value-Type Parameters](./passing-value-type-parameters.md).</span></span>

<span data-ttu-id="e3c79-134">При передаче в метод объекта ссылочного типа передается ссылка на этот объект.</span><span class="sxs-lookup"><span data-stu-id="e3c79-134">When an object of a reference type is passed to a method, a reference to the object is passed.</span></span> <span data-ttu-id="e3c79-135">То есть метод получает не сам объект, а аргумент, который указывает расположение объекта.</span><span class="sxs-lookup"><span data-stu-id="e3c79-135">That is, the method receives not the object itself but an argument that indicates the location of the object.</span></span> <span data-ttu-id="e3c79-136">При изменении члена объекта с помощью этой ссылки это изменение отражается в аргументе в вызывающем методе, даже если объект передается по значению.</span><span class="sxs-lookup"><span data-stu-id="e3c79-136">If you change a member of the object by using this reference, the change is reflected in the argument in the calling method, even if you pass the object by value.</span></span>

<span data-ttu-id="e3c79-137">Ссылочный тип создается с помощью ключевого слова `class`, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="e3c79-137">You create a reference type by using the `class` keyword, as the following example shows:</span></span>

[!code-csharp[SampleRefTypeClass#4](snippets/methods/Program.cs#4)]

<span data-ttu-id="e3c79-138">Теперь, если передать объект, основанный на этом типе, в метод, то будет передана ссылка на объект.</span><span class="sxs-lookup"><span data-stu-id="e3c79-138">Now, if you pass an object that is based on this type to a method, a reference to the object is passed.</span></span> <span data-ttu-id="e3c79-139">В следующем примере объект типа `SampleRefType` передается в метод `ModifyObject`:</span><span class="sxs-lookup"><span data-stu-id="e3c79-139">The following example passes an object of type `SampleRefType` to method `ModifyObject`:</span></span>

[!code-csharp[PassingAReferenceType#5](snippets/methods/Program.cs#5)]

<span data-ttu-id="e3c79-140">В этом примере, в сущности, делается то же, что и в предыдущем примере, — аргумент по значению передается в метод.</span><span class="sxs-lookup"><span data-stu-id="e3c79-140">The example does essentially the same thing as the previous example in that it passes an argument by value to a method.</span></span> <span data-ttu-id="e3c79-141">Но поскольку здесь используется ссылочный тип, результат будет другим.</span><span class="sxs-lookup"><span data-stu-id="e3c79-141">But, because a reference type is used, the result is different.</span></span> <span data-ttu-id="e3c79-142">В данном случае в методе `ModifyObject` изменено поле `value` параметра `obj`, а также изменено поле `value` аргумента, `rt`в методе `TestRefType` .</span><span class="sxs-lookup"><span data-stu-id="e3c79-142">The modification that is made in `ModifyObject` to the `value` field of the parameter, `obj`, also changes the `value` field of the argument, `rt`, in the `TestRefType` method.</span></span> <span data-ttu-id="e3c79-143">В качестве выходных данных метод `TestRefType` отображает 33.</span><span class="sxs-lookup"><span data-stu-id="e3c79-143">The `TestRefType` method displays 33 as the output.</span></span>

<span data-ttu-id="e3c79-144">Дополнительные сведения о передаче ссылочных типов по ссылке и по значению см. в разделах [Передача параметров ссылочного типа](./passing-reference-type-parameters.md) и [Ссылочные типы](../../language-reference/keywords/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="e3c79-144">For more information about how to pass reference types by reference and by value, see [Passing Reference-Type Parameters](./passing-reference-type-parameters.md) and [Reference Types](../../language-reference/keywords/reference-types.md).</span></span>

## <a name="return-values"></a><span data-ttu-id="e3c79-145">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="e3c79-145">Return values</span></span>

<span data-ttu-id="e3c79-146">Методы могут возвращать значение вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="e3c79-146">Methods can return a value to the caller.</span></span> <span data-ttu-id="e3c79-147">Если тип возврата, указываемый перед именем метода, не `void`, этот метод может возвращать значение с помощью ключевого слова `return` .</span><span class="sxs-lookup"><span data-stu-id="e3c79-147">If the return type, the type listed before the method name, is not `void`, the method can return the value by using the `return` keyword.</span></span> <span data-ttu-id="e3c79-148">Инструкция с ключевым словом `return` , за которым следует значение, соответствующее типу возврата, будет возвращать это значение объекту, вызвавшему метод.</span><span class="sxs-lookup"><span data-stu-id="e3c79-148">A statement with the `return` keyword followed by a value that matches the return type will return that value to the method caller.</span></span>

<span data-ttu-id="e3c79-149">Значение может возвращаться вызывающему объекту по значению или, начиная с C# версии 7.0, [по ссылке](ref-returns.md).</span><span class="sxs-lookup"><span data-stu-id="e3c79-149">The value can be returned to the caller by value or, starting with C# 7.0, [by reference](ref-returns.md).</span></span> <span data-ttu-id="e3c79-150">Значения возвращаются вызывающему объекту по ссылке, если ключевое слово `ref` используется в сигнатуре метода и указывается после каждого ключевого слова `return`.</span><span class="sxs-lookup"><span data-stu-id="e3c79-150">Values are returned to the caller by reference if the `ref` keyword is used in the method signature and it follows each `return` keyword.</span></span> <span data-ttu-id="e3c79-151">Например, следующая сигнатура метода и оператор return указывают, что метод возвращает имена переменных `estDistance` вызывающему объекту по ссылке.</span><span class="sxs-lookup"><span data-stu-id="e3c79-151">For example, the following method signature and return statement indicate that the method returns a variable names `estDistance` by reference to the caller.</span></span>

```csharp
public ref double GetEstimatedDistance()
{
    return ref estDistance;
}
```

<span data-ttu-id="e3c79-152">Ключевое слове `return` также останавливает выполнение метода.</span><span class="sxs-lookup"><span data-stu-id="e3c79-152">The `return` keyword also stops the execution of the method.</span></span> <span data-ttu-id="e3c79-153">Если тип возврата — `void`, инструкцию `return` без значения по-прежнему можно использовать для завершения выполнения метода.</span><span class="sxs-lookup"><span data-stu-id="e3c79-153">If the return type is `void`, a `return` statement without a value is still useful to stop the execution of the method.</span></span> <span data-ttu-id="e3c79-154">Без ключевого слова `return` этот метод будет останавливать выполнение при достижении конца блока кода.</span><span class="sxs-lookup"><span data-stu-id="e3c79-154">Without the `return` keyword, the method will stop executing when it reaches the end of the code block.</span></span> <span data-ttu-id="e3c79-155">Методы с типом возврата, отличным от void, должны использовать ключевое слово `return` для возврата значения.</span><span class="sxs-lookup"><span data-stu-id="e3c79-155">Methods with a non-void return type are required to use the `return` keyword to return a value.</span></span> <span data-ttu-id="e3c79-156">Например, в следующих двух методах ключевое слово `return` используется для возврата целочисленных значений.</span><span class="sxs-lookup"><span data-stu-id="e3c79-156">For example, these two methods use the `return` keyword to return integers:</span></span>

[!code-csharp[SimpleMathClass#6](snippets/methods/Program.cs#6)]

<span data-ttu-id="e3c79-157">Чтобы использовать значение, возвращаемое из метода, вызывающий метод может применять сам вызов метода везде, где будет достаточно значения того же типа.</span><span class="sxs-lookup"><span data-stu-id="e3c79-157">To use a value returned from a method, the calling method can use the method call itself anywhere a value of the same type would be sufficient.</span></span> <span data-ttu-id="e3c79-158">Можно также назначить возвращаемое значение переменной.</span><span class="sxs-lookup"><span data-stu-id="e3c79-158">You can also assign the return value to a variable.</span></span> <span data-ttu-id="e3c79-159">Например, следующие два примера кода достигают одной и той же цели.</span><span class="sxs-lookup"><span data-stu-id="e3c79-159">For example, the following two code examples accomplish the same goal:</span></span>

[!code-csharp[SquareANumberWithAddTwoNumbersUsingLocalVariable#7](snippets/methods/Program.cs#7)]

[!code-csharp[SquareANumberWithAddTwoNumbersInTheSameLine#8](snippets/methods/Program.cs#8)]

<span data-ttu-id="e3c79-160">Использование локальной переменной, в данном случае `result`, для сохранения значения является необязательным.</span><span class="sxs-lookup"><span data-stu-id="e3c79-160">Using a local variable, in this case, `result`, to store a value is optional.</span></span> <span data-ttu-id="e3c79-161">Это может улучшить читаемость кода или может оказаться необходимым, если нужно сохранить исходное значение аргумента для всей области метода.</span><span class="sxs-lookup"><span data-stu-id="e3c79-161">It may help the readability of the code, or it may be necessary if you need to store the original value of the argument for the entire scope of the method.</span></span>

<span data-ttu-id="e3c79-162">Чтобы использовать значение, возвращаемое по ссылке из метода, необходимо объявить [локальную ссылочную переменную](ref-returns.md#ref-locals), если планируется изменение значения.</span><span class="sxs-lookup"><span data-stu-id="e3c79-162">To use a value returned by reference from a method, you must declare a [ref local](ref-returns.md#ref-locals) variable if you intend to modify its value.</span></span> <span data-ttu-id="e3c79-163">Например, если метод `Planet.GetEstimatedDistance` возвращает значение <xref:System.Double> по ссылке, можно определить его как локальную ссылочную переменную с использованием кода следующего вида:</span><span class="sxs-lookup"><span data-stu-id="e3c79-163">For example, if the `Planet.GetEstimatedDistance` method returns a <xref:System.Double> value by reference, you can define it as a ref local variable with code like the following:</span></span>

```csharp
ref int distance = plant
```

<span data-ttu-id="e3c79-164">Возвращать многомерный массив из метода `M`, который изменяет содержимое массива, необязательно, если вызывающая функция передает массив в `M`.</span><span class="sxs-lookup"><span data-stu-id="e3c79-164">Returning a multi-dimensional array from a method, `M`, that modifies the array's contents is not necessary if the calling function passed the array into `M`.</span></span>  <span data-ttu-id="e3c79-165">В целях оптимизации можно возвращать полученный массив из `M` или функциональный поток значений, однако это необязательно. Это связано с тем, что C# передает все ссылочные типы по значению, а значение ссылки на массив представляет собой указатель на массив.</span><span class="sxs-lookup"><span data-stu-id="e3c79-165">You may return the resulting array from `M` for good style or functional flow of values, but it is not necessary because C# passes all reference types by value, and the value of an array reference is the pointer to the array.</span></span> <span data-ttu-id="e3c79-166">В методе `M` любые изменения содержимого массива отслеживаются любым кодом, имеющим ссылку на массив, как показано в приведенном ниже примере:</span><span class="sxs-lookup"><span data-stu-id="e3c79-166">In the method `M`, any changes to the array's contents are observable by any code that has a reference to the array, as shown in the following example:</span></span>

```csharp
static void Main(string[] args)
{
    int[,] matrix = new int[2, 2];
    FillMatrix(matrix);
    // matrix is now full of -1
}

public static void FillMatrix(int[,] matrix)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        for (int j = 0; j < matrix.GetLength(1); j++)
        {
            matrix[i, j] = -1;
        }
    }
}
```

<span data-ttu-id="e3c79-167">Для получения дополнительной информации см. [return](../../language-reference/keywords/return.md).</span><span class="sxs-lookup"><span data-stu-id="e3c79-167">For more information, see [return](../../language-reference/keywords/return.md).</span></span>

## <a name="async-methods"></a><span data-ttu-id="e3c79-168">Асинхронные методы</span><span class="sxs-lookup"><span data-stu-id="e3c79-168">Async methods</span></span>

<span data-ttu-id="e3c79-169">С помощью функции async можно вызывать асинхронные методы, не прибегая к использованию явных обратных вызовов или ручному разделению кода между несколькими методами или лямбда-выражениями.</span><span class="sxs-lookup"><span data-stu-id="e3c79-169">By using the async feature, you can invoke asynchronous methods without using explicit callbacks or manually splitting your code across multiple methods or lambda expressions.</span></span>

<span data-ttu-id="e3c79-170">Если пометить метод с помощью модификатора [async](../../language-reference/keywords/async.md) , можно использовать в этом методе инструкцию [await](../../language-reference/operators/await.md) .</span><span class="sxs-lookup"><span data-stu-id="e3c79-170">If you mark a method with the [async](../../language-reference/keywords/async.md) modifier, you can use the [await](../../language-reference/operators/await.md) operator in the method.</span></span> <span data-ttu-id="e3c79-171">Когда управление достигает выражения await в асинхронном методе, управление возвращается вызывающему объекту и выполнение метода приостанавливается до завершения выполнения ожидающей задачи.</span><span class="sxs-lookup"><span data-stu-id="e3c79-171">When control reaches an await expression in the async method, control returns to the caller, and progress in the method is suspended until the awaited task completes.</span></span> <span data-ttu-id="e3c79-172">После завершения задачи можно возобновить выполнение в методе.</span><span class="sxs-lookup"><span data-stu-id="e3c79-172">When the task is complete, execution can resume in the method.</span></span>

> [!NOTE]
> <span data-ttu-id="e3c79-173">Асинхронный метод возвращается в вызывающий объект, когда он встречает первый ожидаемый объект, выполнение которого еще не завершено, или когда выполнение асинхронного метода доходит до конца — в зависимости от того, что происходит раньше.</span><span class="sxs-lookup"><span data-stu-id="e3c79-173">An async method returns to the caller when either it encounters the first awaited object that's not yet complete or it gets to the end of the async method, whichever occurs first.</span></span>

<span data-ttu-id="e3c79-174">Асинхронный метод может иметь тип возврата <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>или void.</span><span class="sxs-lookup"><span data-stu-id="e3c79-174">An async method can have a return type of <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, or void.</span></span> <span data-ttu-id="e3c79-175">Тип возврата void в основном используется для определения обработчиков событий, где требуется тип возврата void.</span><span class="sxs-lookup"><span data-stu-id="e3c79-175">The void return type is used primarily to define event handlers, where a void return type is required.</span></span> <span data-ttu-id="e3c79-176">Асинхронный метод, который возвращает тип void, не может быть ожидающим. Вызывающий объект метода, возвращающего значение типа void, не может перехватывать исключения, которые выдает этот метод.</span><span class="sxs-lookup"><span data-stu-id="e3c79-176">An async method that returns void can't be awaited, and the caller of a void-returning method can't catch exceptions that the method throws.</span></span>

<span data-ttu-id="e3c79-177">В следующем примере `DelayAsync` является асинхронным методом с типом возврата <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="e3c79-177">In the following example, `DelayAsync` is an async method that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="e3c79-178">`DelayAsync` имеет инструкцию `return` , которая возвращает целое число.</span><span class="sxs-lookup"><span data-stu-id="e3c79-178">`DelayAsync` has a `return` statement that returns an integer.</span></span> <span data-ttu-id="e3c79-179">Поэтому объявление метода `DelayAsync` должно иметь тип возврата `Task<int>`.</span><span class="sxs-lookup"><span data-stu-id="e3c79-179">Therefore the method declaration of `DelayAsync` must have a return type of `Task<int>`.</span></span> <span data-ttu-id="e3c79-180">Поскольку тип возврата — `Task<int>`, вычисление выражения `await` в `DoSomethingAsync` создает целое число, как показывает следующая инструкция: `int result = await delayTask`.</span><span class="sxs-lookup"><span data-stu-id="e3c79-180">Because the return type is `Task<int>`, the evaluation of the `await` expression in `DoSomethingAsync` produces an integer as the following statement demonstrates: `int result = await delayTask`.</span></span>

<span data-ttu-id="e3c79-181">В следующем примере метод `Main` служит примером асинхронного метода с типом возврата <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="e3c79-181">The `Main` method is an example of an async method that has a return type of <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="e3c79-182">Он переходит к методу `DoSomethingAsync` и, поскольку он выражается в одной строке, он может опустить ключевые слова `async` и `await`.</span><span class="sxs-lookup"><span data-stu-id="e3c79-182">It goes to the `DoSomethingAsync` method, and because it is expressed with a single line, it can omit the `async` and `await` keywords.</span></span> <span data-ttu-id="e3c79-183">Поскольку `DoSomethingAsync` является асинхронным методом, задача для вызова `DoSomethingAsync` должна быть ожидаемой, как показывает следующая инструкция: `await DoSomethingAsync();`.</span><span class="sxs-lookup"><span data-stu-id="e3c79-183">Because `DoSomethingAsync` is an async method, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `await DoSomethingAsync();`.</span></span>

:::code language="csharp" source="snippets/classes-and-structs/methods/Program.cs":::

<span data-ttu-id="e3c79-184">Асинхронный метод не может объявить все параметры [ref](../../language-reference/keywords/ref.md) или [out](../../language-reference/keywords/out-parameter-modifier.md) , но может вызывать методы, которые имеют такие параметры.</span><span class="sxs-lookup"><span data-stu-id="e3c79-184">An async method can't declare any [ref](../../language-reference/keywords/ref.md) or [out](../../language-reference/keywords/out-parameter-modifier.md) parameters, but it can call methods that have such parameters.</span></span>

<span data-ttu-id="e3c79-185">Дополнительные сведения об асинхронных методах см. в разделах [Асинхронное программирование с использованием ключевых слов async и await (C#)](../concepts/async/index.md) и [Типы возвращаемых значений асинхронных операций](../concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="e3c79-185">For more information about async methods, see [Asynchronous programming with async and await](../concepts/async/index.md) and [Async return types](../concepts/async/async-return-types.md).</span></span>

## <a name="expression-body-definitions"></a><span data-ttu-id="e3c79-186">Определения текста выражений</span><span class="sxs-lookup"><span data-stu-id="e3c79-186">Expression body definitions</span></span>

<span data-ttu-id="e3c79-187">Часто используются определения методов, которые просто немедленно возвращаются с результатом выражения или которые имеют единственную инструкцию в тексте метода.</span><span class="sxs-lookup"><span data-stu-id="e3c79-187">It is common to have method definitions that simply return immediately with the result of an expression, or that have a single statement as the body of the method.</span></span> <span data-ttu-id="e3c79-188">Для определения таких методов существует сокращенный синтаксис с использованием `=>`:</span><span class="sxs-lookup"><span data-stu-id="e3c79-188">There is a syntax shortcut for defining such methods using `=>`:</span></span>

```csharp
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);
public void Print() => Console.WriteLine(First + " " + Last);
// Works with operators, properties, and indexers too.
public static Complex operator +(Complex a, Complex b) => a.Add(b);
public string Name => First + " " + Last;
public Customer this[long id] => store.LookupCustomer(id);
```

<span data-ttu-id="e3c79-189">Если метод возвращает `void` или является асинхронным методом, то текст метода должен быть выражением инструкции (так же, как при использовании лямбда-выражений).</span><span class="sxs-lookup"><span data-stu-id="e3c79-189">If the method returns `void` or is an async method, then the body of the method must be a statement expression (same as with lambdas).</span></span> <span data-ttu-id="e3c79-190">Свойства и индексаторы должны быть только для чтения, и вы не должны использовать ключевое слово `get` метода доступа.</span><span class="sxs-lookup"><span data-stu-id="e3c79-190">For properties and indexers, they must be read only, and you don't use the `get` accessor keyword.</span></span>

## <a name="iterators"></a><span data-ttu-id="e3c79-191">Iterators</span><span class="sxs-lookup"><span data-stu-id="e3c79-191">Iterators</span></span>

<span data-ttu-id="e3c79-192">Итератор выполняет настраиваемую итерацию по коллекции, например по списку или массиву.</span><span class="sxs-lookup"><span data-stu-id="e3c79-192">An iterator performs a custom iteration over a collection, such as a list or an array.</span></span> <span data-ttu-id="e3c79-193">Итератор использует инструкцию [yield return](../../language-reference/keywords/yield.md) для возврата всех элементов по одному.</span><span class="sxs-lookup"><span data-stu-id="e3c79-193">An iterator uses the [yield return](../../language-reference/keywords/yield.md) statement to return each element one at a time.</span></span> <span data-ttu-id="e3c79-194">Когда достигается инструкция [yield return](../../language-reference/keywords/yield.md) , текущее расположение в коде запоминается.</span><span class="sxs-lookup"><span data-stu-id="e3c79-194">When a [yield return](../../language-reference/keywords/yield.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="e3c79-195">При следующем вызове итератора выполнение возобновляется с этого места.</span><span class="sxs-lookup"><span data-stu-id="e3c79-195">Execution is restarted from that location when the iterator is called the next time.</span></span>

<span data-ttu-id="e3c79-196">Итератор вызывается из клиентского кода с помощью инструкции [foreach](../../language-reference/keywords/foreach-in.md) .</span><span class="sxs-lookup"><span data-stu-id="e3c79-196">You call an iterator from client code by using a [foreach](../../language-reference/keywords/foreach-in.md) statement.</span></span>

<span data-ttu-id="e3c79-197">Тип возврата итератора может быть <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator> или <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="e3c79-197">The return type of an iterator can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="e3c79-198">Дополнительные сведения см. в разделе [Итераторы](../concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="e3c79-198">For more information, see [Iterators](../concepts/iterators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e3c79-199">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="e3c79-199">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="e3c79-200">См. также</span><span class="sxs-lookup"><span data-stu-id="e3c79-200">See also</span></span>

- [<span data-ttu-id="e3c79-201">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="e3c79-201">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e3c79-202">Классы и структуры</span><span class="sxs-lookup"><span data-stu-id="e3c79-202">Classes and Structs</span></span>](index.md)
- [<span data-ttu-id="e3c79-203">Модификаторы доступа</span><span class="sxs-lookup"><span data-stu-id="e3c79-203">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="e3c79-204">Статические классы и члены статических классов</span><span class="sxs-lookup"><span data-stu-id="e3c79-204">Static Classes and Static Class Members</span></span>](static-classes-and-static-class-members.md)
- [<span data-ttu-id="e3c79-205">Наследование</span><span class="sxs-lookup"><span data-stu-id="e3c79-205">Inheritance</span></span>](inheritance.md)
- [<span data-ttu-id="e3c79-206">Абстрактные и запечатанные классы и члены классов</span><span class="sxs-lookup"><span data-stu-id="e3c79-206">Abstract and Sealed Classes and Class Members</span></span>](abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="e3c79-207">params</span><span class="sxs-lookup"><span data-stu-id="e3c79-207">params</span></span>](../../language-reference/keywords/params.md)
- [<span data-ttu-id="e3c79-208">return</span><span class="sxs-lookup"><span data-stu-id="e3c79-208">return</span></span>](../../language-reference/keywords/return.md)
- [<span data-ttu-id="e3c79-209">out</span><span class="sxs-lookup"><span data-stu-id="e3c79-209">out</span></span>](../../language-reference/keywords/out.md)
- [<span data-ttu-id="e3c79-210">ref</span><span class="sxs-lookup"><span data-stu-id="e3c79-210">ref</span></span>](../../language-reference/keywords/ref.md)
- [<span data-ttu-id="e3c79-211">Передача параметров</span><span class="sxs-lookup"><span data-stu-id="e3c79-211">Passing Parameters</span></span>](passing-parameters.md)
