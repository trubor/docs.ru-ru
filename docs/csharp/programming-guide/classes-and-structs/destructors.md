---
title: Руководство по программированию на C#. Методы завершения
description: Методы завершения в C# (также называемые деструкторами) выполняют любую необходимую окончательную очистку, когда сборщик мусора окончательно удаляет экземпляр класса.
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: a2f4f5f9342d5df1f9fa741c86cfe6f8b1d88bd1
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899065"
---
# <a name="finalizers-c-programming-guide"></a><span data-ttu-id="d69f1-103">Методы завершения (руководство по программированию в C#)</span><span class="sxs-lookup"><span data-stu-id="d69f1-103">Finalizers (C# Programming Guide)</span></span>

<span data-ttu-id="d69f1-104">Методы завершения (также называемые **деструкторами**) используются для любой необходимой окончательной очистки, когда сборщик мусора окончательно удаляет экземпляра класса.</span><span class="sxs-lookup"><span data-stu-id="d69f1-104">Finalizers (which are also called **destructors**) are used to perform any necessary final clean-up when a class instance is being collected by the garbage collector.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d69f1-105">Примечания</span><span class="sxs-lookup"><span data-stu-id="d69f1-105">Remarks</span></span>  
  
- <span data-ttu-id="d69f1-106">В структурах определение методов завершения невозможно.</span><span class="sxs-lookup"><span data-stu-id="d69f1-106">Finalizers cannot be defined in structs.</span></span> <span data-ttu-id="d69f1-107">Они применяются только в классах.</span><span class="sxs-lookup"><span data-stu-id="d69f1-107">They are only used with classes.</span></span>  
  
- <span data-ttu-id="d69f1-108">Каждый класс может иметь только один метод завершения.</span><span class="sxs-lookup"><span data-stu-id="d69f1-108">A class can only have one finalizer.</span></span>  
  
- <span data-ttu-id="d69f1-109">Методы завершения не могут быть унаследованы или перегружены.</span><span class="sxs-lookup"><span data-stu-id="d69f1-109">Finalizers cannot be inherited or overloaded.</span></span>  
  
- <span data-ttu-id="d69f1-110">Методы завершения невозможно вызвать.</span><span class="sxs-lookup"><span data-stu-id="d69f1-110">Finalizers cannot be called.</span></span> <span data-ttu-id="d69f1-111">Они запускаются автоматически.</span><span class="sxs-lookup"><span data-stu-id="d69f1-111">They are invoked automatically.</span></span>  
  
- <span data-ttu-id="d69f1-112">Метод завершения не принимает модификаторов и не имеет параметров.</span><span class="sxs-lookup"><span data-stu-id="d69f1-112">A finalizer does not take modifiers or have parameters.</span></span>  
  
 <span data-ttu-id="d69f1-113">Например, ниже показано объявление метода завершения для класса `Car`.</span><span class="sxs-lookup"><span data-stu-id="d69f1-113">For example, the following is a declaration of a finalizer for the `Car` class.</span></span>
  
 [!code-csharp[csProgGuideObjects#86](snippets/destructors/Program.cs#2)]

<span data-ttu-id="d69f1-114">Метод завершения можно также реализовать как определение тела выражения, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="d69f1-114">A finalizer can also be implemented as an expression body definition, as the following example shows.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 <span data-ttu-id="d69f1-115">Метод завершения неявно вызывает метод <xref:System.Object.Finalize%2A> для базового класса объекта.</span><span class="sxs-lookup"><span data-stu-id="d69f1-115">The finalizer implicitly calls <xref:System.Object.Finalize%2A> on the base class of the object.</span></span> <span data-ttu-id="d69f1-116">В связи с этим вызов метода завершения неявно преобразуется в следующий код:</span><span class="sxs-lookup"><span data-stu-id="d69f1-116">Therefore, a call to a finalizer is implicitly translated to the following code:</span></span>  
  
```csharp  
protected override void Finalize()  
{  
    try  
    {  
        // Cleanup statements...  
    }  
    finally  
    {  
        base.Finalize();  
    }  
}  
```  
  
 <span data-ttu-id="d69f1-117">Это означает, что метод `Finalize` вызывается рекурсивно для всех экземпляров цепочки наследования начиная с самого дальнего и заканчивая самым первым.</span><span class="sxs-lookup"><span data-stu-id="d69f1-117">This design means that the `Finalize` method is called recursively for all instances in the inheritance chain, from the most-derived to the least-derived.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d69f1-118">Не следует использовать пустые методы завершения.</span><span class="sxs-lookup"><span data-stu-id="d69f1-118">Empty finalizers should not be used.</span></span> <span data-ttu-id="d69f1-119">Если класс содержит метод завершения, то в очереди метода `Finalize` создается запись.</span><span class="sxs-lookup"><span data-stu-id="d69f1-119">When a class contains a finalizer, an entry is created in the `Finalize` queue.</span></span> <span data-ttu-id="d69f1-120">При вызове метода завершения вызывается сборщик мусора, выполняющий обработку очереди.</span><span class="sxs-lookup"><span data-stu-id="d69f1-120">When the finalizer is called, the garbage collector is invoked to process the queue.</span></span> <span data-ttu-id="d69f1-121">Если метод завершения пустой, это приводит только к ненужному снижению производительности.</span><span class="sxs-lookup"><span data-stu-id="d69f1-121">An empty finalizer just causes a needless loss of performance.</span></span>  
  
 <span data-ttu-id="d69f1-122">Программист не может управлять моментом вызова метода завершения, поскольку это определяется сборщиком мусора.</span><span class="sxs-lookup"><span data-stu-id="d69f1-122">The programmer has no control over when the finalizer is called; the garbage collector decides when to call it.</span></span> <span data-ttu-id="d69f1-123">Сборщик мусора проверяет наличие объектов, которые больше не используются приложением.</span><span class="sxs-lookup"><span data-stu-id="d69f1-123">The garbage collector checks for objects that are no longer being used by the application.</span></span> <span data-ttu-id="d69f1-124">Если он считает, что какой-либо объект требует уничтожения, то вызывает метод завершения (при наличии) и освобождает память, используемую для хранения этого объекта.</span><span class="sxs-lookup"><span data-stu-id="d69f1-124">If it considers an object eligible for finalization, it calls the finalizer (if any) and reclaims the memory used to store the object.</span></span>

 <span data-ttu-id="d69f1-125">В приложениях .NET Framework (но не в приложениях .NET Core) методы завершения также вызываются при выходе из программы.</span><span class="sxs-lookup"><span data-stu-id="d69f1-125">In .NET Framework applications (but not in .NET Core applications), finalizers are also called when the program exits.</span></span>
  
 <span data-ttu-id="d69f1-126">Сборку мусора можно выполнить принудительно, вызвав метод <xref:System.GC.Collect%2A>, но в большинстве случаев этого следует избегать из-за возможных проблем с производительностью.</span><span class="sxs-lookup"><span data-stu-id="d69f1-126">It's possible to force garbage collection by calling <xref:System.GC.Collect%2A>, but most of the time, this call should be avoided because it may create performance issues.</span></span>  
  
## <a name="using-finalizers-to-release-resources"></a><span data-ttu-id="d69f1-127">Использование методов завершения для освобождения ресурсов</span><span class="sxs-lookup"><span data-stu-id="d69f1-127">Using finalizers to release resources</span></span>  

 <span data-ttu-id="d69f1-128">В целом язык C# не требует управления памятью в той степени, в какой это требуется в случае разработки кода на языке, не рассчитанном на среду выполнения со сборкой мусора.</span><span class="sxs-lookup"><span data-stu-id="d69f1-128">In general, C# does not require as much memory management on the part of the developer as languages that don't target a runtime with garbage collection.</span></span> <span data-ttu-id="d69f1-129">Это связано с тем, что сборщик мусора платформы .NET неявным образом управляет выделением и высвобождением памяти для объектов.</span><span class="sxs-lookup"><span data-stu-id="d69f1-129">This is because the .NET garbage collector implicitly manages the allocation and release of memory for your objects.</span></span> <span data-ttu-id="d69f1-130">Однако при инкапсуляции приложением неуправляемых ресурсов, например окон, файлов и сетевых подключений, для высвобождения этих ресурсов следует использовать методы завершения.</span><span class="sxs-lookup"><span data-stu-id="d69f1-130">However, when your application encapsulates unmanaged resources, such as windows, files, and network connections, you should use finalizers to free those resources.</span></span> <span data-ttu-id="d69f1-131">Если объект допускает завершение, то сборщик мусора выполняет метод `Finalize` этого объекта.</span><span class="sxs-lookup"><span data-stu-id="d69f1-131">When the object is eligible for finalization, the garbage collector runs the `Finalize` method of the object.</span></span>
  
## <a name="explicit-release-of-resources"></a><span data-ttu-id="d69f1-132">Освобождение ресурсов явным образом</span><span class="sxs-lookup"><span data-stu-id="d69f1-132">Explicit release of resources</span></span>  

 <span data-ttu-id="d69f1-133">В случае, когда приложением используется ценный внешний ресурс, также рекомендуется обеспечить способ высвобождения этого ресурса явным образом, прежде чем сборщик мусора освободит объект.</span><span class="sxs-lookup"><span data-stu-id="d69f1-133">If your application is using an expensive external resource, we also recommend that you provide a way to explicitly release the resource before the garbage collector frees the object.</span></span> <span data-ttu-id="d69f1-134">Для высвобождения ресурса реализуется метод `Dispose` интерфейса <xref:System.IDisposable>, который выполняет необходимую для объекта очистку.</span><span class="sxs-lookup"><span data-stu-id="d69f1-134">To release the resource, implement a `Dispose` method from the <xref:System.IDisposable> interface that performs the necessary cleanup for the object.</span></span> <span data-ttu-id="d69f1-135">Это может значительно повысить производительность приложения.</span><span class="sxs-lookup"><span data-stu-id="d69f1-135">This can considerably improve the performance of the application.</span></span> <span data-ttu-id="d69f1-136">Даже в случае использования такого явного управления ресурсами метод завершения становится резервным средством очистки ресурсов, если вызов метода `Dispose` выполнить не удастся.</span><span class="sxs-lookup"><span data-stu-id="d69f1-136">Even with this explicit control over resources, the finalizer becomes a safeguard to clean up resources if the call to the `Dispose` method fails.</span></span>  
  
 <span data-ttu-id="d69f1-137">Дополнительные сведения об очистке ресурсов см. в следующих статьях:</span><span class="sxs-lookup"><span data-stu-id="d69f1-137">For more information about cleaning up resources, see the following articles:</span></span>  
  
- [<span data-ttu-id="d69f1-138">Очистка неуправляемых ресурсов</span><span class="sxs-lookup"><span data-stu-id="d69f1-138">Cleaning Up Unmanaged Resources</span></span>](../../../standard/garbage-collection/unmanaged.md)  
  
- [<span data-ttu-id="d69f1-139">Реализация метода dispose</span><span class="sxs-lookup"><span data-stu-id="d69f1-139">Implementing a Dispose Method</span></span>](../../../standard/garbage-collection/implementing-dispose.md)  
  
- [<span data-ttu-id="d69f1-140">Оператор using</span><span class="sxs-lookup"><span data-stu-id="d69f1-140">using Statement</span></span>](../../language-reference/keywords/using-statement.md)  
  
## <a name="example"></a><span data-ttu-id="d69f1-141">Пример</span><span class="sxs-lookup"><span data-stu-id="d69f1-141">Example</span></span>  

 <span data-ttu-id="d69f1-142">В приведенном ниже примере создаются три класса, образующих цепочку наследования.</span><span class="sxs-lookup"><span data-stu-id="d69f1-142">The following example creates three classes that make a chain of inheritance.</span></span> <span data-ttu-id="d69f1-143">Класс `First` является базовым, класс `Second` является производным от класса `First`, а класс `Third` является производным от класса `Second`.</span><span class="sxs-lookup"><span data-stu-id="d69f1-143">The class `First` is the base class, `Second` is derived from `First`, and `Third` is derived from `Second`.</span></span> <span data-ttu-id="d69f1-144">Все три класса имеют методы завершения.</span><span class="sxs-lookup"><span data-stu-id="d69f1-144">All three have finalizers.</span></span> <span data-ttu-id="d69f1-145">В методе `Main` создается экземпляр самого дальнего в цепочке наследования класса.</span><span class="sxs-lookup"><span data-stu-id="d69f1-145">In `Main`, an instance of the most-derived class is created.</span></span> <span data-ttu-id="d69f1-146">При выполнении программы обратите внимание на то, что методы завершения для всех трех классов вызываются автоматически в порядке от самого дальнего до первого в цепочке наследования.</span><span class="sxs-lookup"><span data-stu-id="d69f1-146">When the program runs, notice that the finalizers for the three classes are called automatically, and in order, from the most-derived to the least-derived.</span></span>  
  
 [!code-csharp[Destructors#1](snippets/destructors/Program.cs#1)]
  
## <a name="c-language-specification"></a><span data-ttu-id="d69f1-147">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="d69f1-147">C# language specification</span></span>  

<span data-ttu-id="d69f1-148">Дополнительные сведения см. в разделе [Деструкторы](~/_csharplang/spec/classes.md#destructors)[спецификация языка C# 6.0](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="d69f1-148">For more information, see the [Destructors](~/_csharplang/spec/classes.md#destructors) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d69f1-149">См. также</span><span class="sxs-lookup"><span data-stu-id="d69f1-149">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="d69f1-150">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="d69f1-150">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d69f1-151">Конструкторы</span><span class="sxs-lookup"><span data-stu-id="d69f1-151">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="d69f1-152">Сборка мусора</span><span class="sxs-lookup"><span data-stu-id="d69f1-152">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
