---
description: Справочник по C#. Ключевое слово ref
title: Справочник по C#. Ключевое слово ref
ms.date: 03/29/2021
f1_keywords:
- ref_CSharpKeyword
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.openlocfilehash: 3392e560eaf0bac39cf4e9707574fd2bb3d96057
ms.sourcegitcommit: 109507b6c16704ed041efe9598c70cd3438a9fbc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106079444"
---
# <a name="ref-c-reference"></a><span data-ttu-id="48377-103">ref (Справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="48377-103">ref (C# Reference)</span></span>

<span data-ttu-id="48377-104">Ключевое слово `ref` указывает, что значение передается по ссылке.</span><span class="sxs-lookup"><span data-stu-id="48377-104">The `ref` keyword indicates that a value is passed by reference.</span></span> <span data-ttu-id="48377-105">Оно используется в четырех разных контекстах:</span><span class="sxs-lookup"><span data-stu-id="48377-105">It is used in four different contexts:</span></span>

- <span data-ttu-id="48377-106">В сигнатуре и вызове метода для передачи аргумента в метод по ссылке.</span><span class="sxs-lookup"><span data-stu-id="48377-106">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="48377-107">Дополнительные сведения см. в статье о [передаче аргументов по ссылке](#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="48377-107">For more information, see [Passing an argument by reference](#passing-an-argument-by-reference).</span></span>
- <span data-ttu-id="48377-108">В сигнатуре метода для возврата значения вызывающему объекту по ссылке.</span><span class="sxs-lookup"><span data-stu-id="48377-108">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="48377-109">Дополнительные сведения см. в разделе [Значения, возвращаемые по ссылке](#reference-return-values).</span><span class="sxs-lookup"><span data-stu-id="48377-109">For more information, see [Reference return values](#reference-return-values).</span></span>
- <span data-ttu-id="48377-110">В теле элемента для указания на то, что возвращаемые ссылочные значения хранятся локально в виде ссылки, которая может быть изменена вызывающим объектом.</span><span class="sxs-lookup"><span data-stu-id="48377-110">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify.</span></span> <span data-ttu-id="48377-111">Или чтобы указать, что локальная переменная обращается к другому значению по ссылке.</span><span class="sxs-lookup"><span data-stu-id="48377-111">Or to indicate that a local variable accesses another value by reference.</span></span> <span data-ttu-id="48377-112">Дополнительные сведения см. в статье о [ссылочных локальных переменных](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="48377-112">For more information, see [Ref locals](#ref-locals).</span></span>
- <span data-ttu-id="48377-113">В объявлении `struct`, чтобы объявить `ref struct` или `readonly ref struct`.</span><span class="sxs-lookup"><span data-stu-id="48377-113">In a `struct` declaration, to declare a `ref struct` or a `readonly ref struct`.</span></span> <span data-ttu-id="48377-114">Дополнительные сведения см. в описании [структуры `ref`](../builtin-types/struct.md#ref-struct) в статье [Типы структур](../builtin-types/struct.md).</span><span class="sxs-lookup"><span data-stu-id="48377-114">For more information, see the [`ref` struct](../builtin-types/struct.md#ref-struct) section of the [Structure types](../builtin-types/struct.md) article.</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="48377-115">Передача аргументов по ссылке</span><span class="sxs-lookup"><span data-stu-id="48377-115">Passing an argument by reference</span></span>

<span data-ttu-id="48377-116">При использовании в списке параметров метода ключевое слово `ref` указывает на то, что аргумент передается по ссылке, а не по значению.</span><span class="sxs-lookup"><span data-stu-id="48377-116">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="48377-117">Ключевое слово `ref` позволяет превратить этот формальный параметр в псевдоним для аргумента, который должен представлять собой переменную.</span><span class="sxs-lookup"><span data-stu-id="48377-117">The `ref` keyword makes the formal parameter an alias for the argument, which must be a variable.</span></span> <span data-ttu-id="48377-118">Другими словами, любая операция в параметре осуществляется с аргументом.</span><span class="sxs-lookup"><span data-stu-id="48377-118">In other words, any operation on the parameter is made on the argument.</span></span>

<span data-ttu-id="48377-119">Для примера предположим, что вызывающая сторона передает выражение локальной переменной или выражение доступа к элементу массива.</span><span class="sxs-lookup"><span data-stu-id="48377-119">For example, suppose the caller passes a local variable expression or an array element access expression.</span></span> <span data-ttu-id="48377-120">Тогда вызываемый метод может заменить объект, на который ссылается параметр ref.</span><span class="sxs-lookup"><span data-stu-id="48377-120">The called method can then replace the object to which the ref parameter refers.</span></span> <span data-ttu-id="48377-121">В этом случае или элемент массива или локальная переменная вызывающей стороны будет ссылаться на новый объект, когда метод возвращает значение.</span><span class="sxs-lookup"><span data-stu-id="48377-121">In that case, the caller's local variable or the array element refers to the new object when the method returns.</span></span>

> [!NOTE]
> <span data-ttu-id="48377-122">Не путайте понятие передачи по ссылке с понятием ссылочных типов.</span><span class="sxs-lookup"><span data-stu-id="48377-122">Don't confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="48377-123">Эти два понятия не совпадают.</span><span class="sxs-lookup"><span data-stu-id="48377-123">The two concepts are not the same.</span></span> <span data-ttu-id="48377-124">Параметр метода может быть изменен с помощью `ref` независимо от того, принадлежит ли он к типу значения или ссылочному типу.</span><span class="sxs-lookup"><span data-stu-id="48377-124">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="48377-125">При передаче по ссылке упаковка-преобразование типа значения не производится.</span><span class="sxs-lookup"><span data-stu-id="48377-125">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="48377-126">Для использования параметра `ref` и при определении метода, и при вызове метода следует явно использовать ключевое слово `ref`, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="48377-126">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span> <span data-ttu-id="48377-127">(За исключением того, что вызывающий метод может опускать `ref` при вызове COM.)</span><span class="sxs-lookup"><span data-stu-id="48377-127">(Except that the calling method can omit `ref` when making a COM call.)</span></span>

[!code-csharp-interactive[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#1)]

<span data-ttu-id="48377-128">Аргумент, передаваемый в параметр `ref` или `in`, нужно инициализировать перед передачей.</span><span class="sxs-lookup"><span data-stu-id="48377-128">An argument that is passed to a `ref` or `in` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="48377-129">В этом и заключается отличие от параметров [out](out-parameter-modifier.md), аргументы которых не нужно явно инициализировать перед передачей.</span><span class="sxs-lookup"><span data-stu-id="48377-129">This requirement differs from [out](out-parameter-modifier.md) parameters, whose arguments don't have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="48377-130">Члены класса не могут иметь сигнатуры, отличающихся только `ref`, `in` или `out`.</span><span class="sxs-lookup"><span data-stu-id="48377-130">Members of a class can't have signatures that differ only by `ref`, `in`, or `out`.</span></span> <span data-ttu-id="48377-131">Если единственное различие между двумя членами типа состоит в том, что один из них имеет параметр `ref`, а второй — параметр `out` или `in`, возникает ошибка компилятора.</span><span class="sxs-lookup"><span data-stu-id="48377-131">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out`, or `in` parameter.</span></span> <span data-ttu-id="48377-132">Например, следующий код не будет компилироваться.</span><span class="sxs-lookup"><span data-stu-id="48377-132">The following code, for example, doesn't compile.</span></span>  

```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```

<span data-ttu-id="48377-133">Но методы можно перегружать, если один метод имеет параметр `ref`, `in` или `out`, а другой — передаваемый по значению параметр, как показано в приведенном ниже примере.</span><span class="sxs-lookup"><span data-stu-id="48377-133">However, methods can be overloaded when one method has a `ref`, `in`, or `out` parameter and the other has a parameter that is passed by value, as shown in the following example.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#2)]
  
 <span data-ttu-id="48377-134">В других ситуациях, требующих соответствия сигнатур, таких как скрытие или переопределение, `in`, `ref` и `out` являются частью сигнатуры и не соответствуют друг другу.</span><span class="sxs-lookup"><span data-stu-id="48377-134">In other situations that require signature matching, such as hiding or overriding, `in`, `ref`, and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="48377-135">Свойства не являются переменными.</span><span class="sxs-lookup"><span data-stu-id="48377-135">Properties are not variables.</span></span> <span data-ttu-id="48377-136">Они являются методами и не могут передаваться в параметры `ref`.</span><span class="sxs-lookup"><span data-stu-id="48377-136">They're methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="48377-137">Ключевые слова `ref`, `in` и `out` запрещено использовать для следующих типов методов.</span><span class="sxs-lookup"><span data-stu-id="48377-137">You can't use the `ref`, `in`, and `out` keywords for the following kinds of methods:</span></span>  
  
- <span data-ttu-id="48377-138">Асинхронные методы, которые определяются с помощью модификатора [async](async.md).</span><span class="sxs-lookup"><span data-stu-id="48377-138">Async methods, which you define by using the [async](async.md) modifier.</span></span>  
- <span data-ttu-id="48377-139">Методы итератора, которые включают оператор [yield return](yield.md) или `yield break`.</span><span class="sxs-lookup"><span data-stu-id="48377-139">Iterator methods, which include a [yield return](yield.md) or `yield break` statement.</span></span>

<span data-ttu-id="48377-140">[Методы расширения](../../programming-guide/classes-and-structs/extension-methods.md) также имеют ряд ограничений при использовании этих ключевых слов:</span><span class="sxs-lookup"><span data-stu-id="48377-140">[extension methods](../../programming-guide/classes-and-structs/extension-methods.md) also have restrictions on the use of these keywords:</span></span>

- <span data-ttu-id="48377-141">Ключевое слово `out` нельзя использовать в первом аргументе метода расширения.</span><span class="sxs-lookup"><span data-stu-id="48377-141">The `out` keyword cannot be used on the first argument of an extension method.</span></span>
- <span data-ttu-id="48377-142">Ключевое слово `ref` нельзя использовать в первом аргументе метода расширения, если аргумент не является структурой, или если универсальный тип не ограничен структурой.</span><span class="sxs-lookup"><span data-stu-id="48377-142">The `ref` keyword cannot be used on the first argument of an extension method when the argument is not a struct, or a generic type not constrained to be a struct.</span></span>
- <span data-ttu-id="48377-143">Ключевое слово `in` нельзя использовать, если только первый аргумент не является структурой.</span><span class="sxs-lookup"><span data-stu-id="48377-143">The `in` keyword cannot be used unless the first argument is a struct.</span></span> <span data-ttu-id="48377-144">Ключевое слово `in` нельзя использовать ни для одного универсального типа, даже если оно ограничено структурой.</span><span class="sxs-lookup"><span data-stu-id="48377-144">The `in` keyword cannot be used on any generic type, even when constrained to be a struct.</span></span>

## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="48377-145">Передача аргументов по ссылке. Пример</span><span class="sxs-lookup"><span data-stu-id="48377-145">Passing an argument by reference: An example</span></span>

<span data-ttu-id="48377-146">В предыдущих примерах типы значений передаются по ссылке.</span><span class="sxs-lookup"><span data-stu-id="48377-146">The previous examples pass value types by reference.</span></span> <span data-ttu-id="48377-147">Также можно использовать ключевое слово `ref` для передачи ссылочных типов по ссылке.</span><span class="sxs-lookup"><span data-stu-id="48377-147">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="48377-148">Передача ссылочного типа по ссылке позволяет вызываемому методу заменять объект, на который указывает ссылочный параметр в вызывающем объекте.</span><span class="sxs-lookup"><span data-stu-id="48377-148">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="48377-149">Место хранения объекта передается методу в качестве значения ссылочного параметра.</span><span class="sxs-lookup"><span data-stu-id="48377-149">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="48377-150">Если изменить место хранения параметра (с указанием на новый объект), необходимо изменить место хранения, на который ссылается вызывающий объект.</span><span class="sxs-lookup"><span data-stu-id="48377-150">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="48377-151">В следующем примере экземпляр ссылочного типа передается как параметр `ref`.</span><span class="sxs-lookup"><span data-stu-id="48377-151">The following example passes an instance of a reference type as a `ref` parameter.</span></span>
  
[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#3)]

<span data-ttu-id="48377-152">Дополнительные сведения о передаче ссылочных типов по значению и по ссылке см. в разделе [Передача параметров ссылочного типа](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="48377-152">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="48377-153">Возвращаемые ссылочные значения</span><span class="sxs-lookup"><span data-stu-id="48377-153">Reference return values</span></span>

<span data-ttu-id="48377-154">Возвращаемые ссылочные значения — это значения, которые метод возвращает вызывающему объекту по ссылке.</span><span class="sxs-lookup"><span data-stu-id="48377-154">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="48377-155">Это значит, что вызывающий объект может изменять значение, возвращаемое методом, и это изменение будет отражаться в состоянии объекта в вызывающем методе.</span><span class="sxs-lookup"><span data-stu-id="48377-155">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object in the calling method.</span></span>

<span data-ttu-id="48377-156">Возвращаемое ссылочное значение определяется с помощью ключевого слова `ref`:</span><span class="sxs-lookup"><span data-stu-id="48377-156">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="48377-157">В сигнатуре метода.</span><span class="sxs-lookup"><span data-stu-id="48377-157">In the method signature.</span></span> <span data-ttu-id="48377-158">Например, следующая сигнатура указывает, что метод `GetCurrentPrice` возвращает значение <xref:System.Decimal> по ссылке.</span><span class="sxs-lookup"><span data-stu-id="48377-158">For example, the following method signature indicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

```csharp
public ref decimal GetCurrentPrice()
```

- <span data-ttu-id="48377-159">Между токеном `return` и переменной, возвращенной в инструкции `return` в методе.</span><span class="sxs-lookup"><span data-stu-id="48377-159">Between the `return` token and the variable returned in a `return` statement in the method.</span></span> <span data-ttu-id="48377-160">Пример:</span><span class="sxs-lookup"><span data-stu-id="48377-160">For example:</span></span>

```csharp
return ref DecimalArray[0];
```

<span data-ttu-id="48377-161">Чтобы вызывающий объект имел возможность изменять состояние объекта, возвращаемое ссылочное значение должно храниться в переменной, которая явно определена как [ссылочная локальная переменная](#ref-locals).</span><span class="sxs-lookup"><span data-stu-id="48377-161">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span>

<span data-ttu-id="48377-162">Ниже приведен более полный пример возвращаемого ссылочного значения, в котором показаны сигнатура и тело метода.</span><span class="sxs-lookup"><span data-stu-id="48377-162">Here's a more complete ref return example, showing both the method signature and method body.</span></span>

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

<span data-ttu-id="48377-163">Вызываемый метод может также объявить возвращаемое значение `ref readonly`, чтобы вернуть значение по ссылке, и запретить вызывающему коду изменять возвращаемое значение.</span><span class="sxs-lookup"><span data-stu-id="48377-163">The called method may also declare the return value as `ref readonly` to return the value by reference, and enforce that the calling code can't modify the returned value.</span></span> <span data-ttu-id="48377-164">Вызывающий метод может обойтись без копирования возвращаемого значения, сохраняя его в локальной переменной [ref readonly](#ref-readonly-locals).</span><span class="sxs-lookup"><span data-stu-id="48377-164">The calling method can avoid copying the returned value by storing the value in a local [ref readonly](#ref-readonly-locals) variable.</span></span>

<span data-ttu-id="48377-165">Пример см. в разделе [Пример использования возвращаемых ссылочных значений и ссылочных локальных переменных](#a-ref-returns-and-ref-locals-example).</span><span class="sxs-lookup"><span data-stu-id="48377-165">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example).</span></span>

## <a name="ref-locals"></a><span data-ttu-id="48377-166">Ссылочные локальные переменные</span><span class="sxs-lookup"><span data-stu-id="48377-166">Ref locals</span></span>

<span data-ttu-id="48377-167">Ссылочная локальная переменная задает ссылку на значения, возвращаемые с помощью `return ref`.</span><span class="sxs-lookup"><span data-stu-id="48377-167">A ref local variable is used to refer to values returned using `return ref`.</span></span> <span data-ttu-id="48377-168">Ссылочная локальная переменная не может инициализироваться как не ссылочное возвращаемое значение.</span><span class="sxs-lookup"><span data-stu-id="48377-168">A ref local variable cannot be initialized to a non-ref return value.</span></span> <span data-ttu-id="48377-169">Другими словами, правая часть инициализации должна быть ссылкой.</span><span class="sxs-lookup"><span data-stu-id="48377-169">In other words, the right-hand side of the initialization must be a reference.</span></span> <span data-ttu-id="48377-170">Любые изменения в значении ссылочной локальной переменной отражаются в состоянии объекта, метод которого возвращает значение по ссылке.</span><span class="sxs-lookup"><span data-stu-id="48377-170">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="48377-171">Чтобы определить локальное ссылочное значение, ключевое слово `ref` следует указать в двух местах:</span><span class="sxs-lookup"><span data-stu-id="48377-171">You define a ref local by using the `ref` keyword in two places:</span></span>

- <span data-ttu-id="48377-172">перед объявлением переменной;</span><span class="sxs-lookup"><span data-stu-id="48377-172">Before the variable declaration.</span></span>
- <span data-ttu-id="48377-173">сразу после вызова метода, который возвращает значение по ссылке.</span><span class="sxs-lookup"><span data-stu-id="48377-173">Immediately before the call to the method that returns the value by reference.</span></span>

<span data-ttu-id="48377-174">Например, следующая инструкция определяет значение ссылочной локальной переменной, которое возвращается методом `GetEstimatedValue`:</span><span class="sxs-lookup"><span data-stu-id="48377-174">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="48377-175">Вы можете таким же образом обратиться к значению по ссылке.</span><span class="sxs-lookup"><span data-stu-id="48377-175">You can access a value by reference in the same way.</span></span> <span data-ttu-id="48377-176">В некоторых случаях обращение к значению по ссылке повышает производительность, поскольку позволяет избежать потенциально затратной операции копирования.</span><span class="sxs-lookup"><span data-stu-id="48377-176">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="48377-177">Например, следующая инструкция позволяет определить локальную ссылочную переменную, которая используется для создания ссылки на значение.</span><span class="sxs-lookup"><span data-stu-id="48377-177">For example, the following statement shows how to define a ref local variable that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="48377-178">В обоих примерах ключевое слово `ref` необходимо использовать в обоих местах. В противном случае возникает ошибка компилятора CS8172, "Невозможно инициализировать значением переменную по ссылке".</span><span class="sxs-lookup"><span data-stu-id="48377-178">In both examples the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span>

<span data-ttu-id="48377-179">Начиная с версии C# 7.3, переменная итерации в операторе `foreach` может являться локальной ссылочной переменной или локальной ссылочной переменной только для чтения.</span><span class="sxs-lookup"><span data-stu-id="48377-179">Beginning with C# 7.3, the iteration variable of the `foreach` statement can be a ref local or ref readonly local variable.</span></span> <span data-ttu-id="48377-180">Дополнительные сведения см. в статье, посвященной [инструкции foreach](foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="48377-180">For more information, see the [foreach statement](foreach-in.md) article.</span></span>

<span data-ttu-id="48377-181">Также, начиная с версии C# 7.3, вы можете переназначать ссылочную локальную переменную или ссылочную локальную переменную только для чтения с помощью [ссылочного оператора присваивания](../operators/assignment-operator.md#ref-assignment-operator).</span><span class="sxs-lookup"><span data-stu-id="48377-181">Also beginning with C# 7.3, you can reassign a ref local or ref readonly local variable with the [ref assignment operator](../operators/assignment-operator.md#ref-assignment-operator).</span></span>

## <a name="ref-readonly-locals"></a><span data-ttu-id="48377-182">Ссылочные локальные переменные только для чтения</span><span class="sxs-lookup"><span data-stu-id="48377-182">Ref readonly locals</span></span>

<span data-ttu-id="48377-183">Ссылочная локальная переменная только для чтения позволяет создать ссылку на значения, возвращаемые методом или свойством, которые имеют в сигнатуре модификатор `ref readonly` и используют `return ref`.</span><span class="sxs-lookup"><span data-stu-id="48377-183">A ref readonly local is used to refer to values returned by a method or property that has `ref readonly` in its signature and uses `return ref`.</span></span> <span data-ttu-id="48377-184">Переменная `ref readonly` сочетает свойства локальной переменной `ref` и переменной `readonly`. Это псевдоним для хранилища, которому она присвоена, который не может изменять свое значение.</span><span class="sxs-lookup"><span data-stu-id="48377-184">A `ref readonly` variable combines the properties of a `ref` local variable with a `readonly` variable: it's an alias to the storage it's assigned to, and it cannot be modified.</span></span>

## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="48377-185">Пример использования возвращаемых ссылочных значений и ссылочных локальных переменных</span><span class="sxs-lookup"><span data-stu-id="48377-185">A ref returns and ref locals example</span></span>

<span data-ttu-id="48377-186">В следующем примере определяется класс `Book`, содержащий два поля <xref:System.String>: `Title` и `Author`.</span><span class="sxs-lookup"><span data-stu-id="48377-186">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="48377-187">Также определяется класс `BookCollection`, который включает частный массив объектов `Book`.</span><span class="sxs-lookup"><span data-stu-id="48377-187">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="48377-188">Отдельные объекты книг возвращаются по ссылке путем вызова метода `GetBookByTitle`.</span><span class="sxs-lookup"><span data-stu-id="48377-188">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#4)]

<span data-ttu-id="48377-189">Если вызывающий объект сохраняет значение, возвращаемое методом `GetBookByTitle`, в качестве ссылочной локальной переменной, изменения, которые этот объект вносит в возвращаемое значение, отражаются в объекте `BookCollection`, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="48377-189">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsMethodParams#6](~/samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/RefParameterModifier.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="48377-190">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="48377-190">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="48377-191">См. также</span><span class="sxs-lookup"><span data-stu-id="48377-191">See also</span></span>

- [<span data-ttu-id="48377-192">Написание безопасного и эффективного кода</span><span class="sxs-lookup"><span data-stu-id="48377-192">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
- [<span data-ttu-id="48377-193">Возвращаемые значения ref и локальные переменные ref</span><span class="sxs-lookup"><span data-stu-id="48377-193">Ref returns and ref locals</span></span>](../../programming-guide/classes-and-structs/ref-returns.md)
- [<span data-ttu-id="48377-194">Условное выражение REF</span><span class="sxs-lookup"><span data-stu-id="48377-194">Conditional ref expression</span></span>](../operators/conditional-operator.md#conditional-ref-expression)
- [<span data-ttu-id="48377-195">Передача параметров</span><span class="sxs-lookup"><span data-stu-id="48377-195">Passing Parameters</span></span>](../../programming-guide/classes-and-structs/passing-parameters.md)
- [<span data-ttu-id="48377-196">Параметры методов</span><span class="sxs-lookup"><span data-stu-id="48377-196">Method Parameters</span></span>](method-parameters.md)
- [<span data-ttu-id="48377-197">Справочник по C#</span><span class="sxs-lookup"><span data-stu-id="48377-197">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="48377-198">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="48377-198">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="48377-199">Ключевые слова в C#</span><span class="sxs-lookup"><span data-stu-id="48377-199">C# Keywords</span></span>](index.md)
