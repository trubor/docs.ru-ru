---
title: Руководство по программированию на C#. Исключения, создаваемые компилятором
description: Сведения об исключениях, создаваемых компилятором. Просмотрите список автоматически создаваемых исключений и условия возникновения ошибок.
ms.date: 12/09/2020
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: 43bacbb1025bc0af3a5f21979315b3d1b0d61066
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110355"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a><span data-ttu-id="5e50e-104">Исключения, создаваемые компилятором (Руководство по программированию в C#)</span><span class="sxs-lookup"><span data-stu-id="5e50e-104">Compiler-Generated Exceptions (C# Programming Guide)</span></span>

<span data-ttu-id="5e50e-105">Некоторые исключения создаются средой выполнения .NET автоматически в случае сбоя основных операций.</span><span class="sxs-lookup"><span data-stu-id="5e50e-105">Some exceptions are thrown automatically by the .NET runtime when basic operations fail.</span></span> <span data-ttu-id="5e50e-106">В следующей таблице перечислены эти исключения и условия возникновения ошибок.</span><span class="sxs-lookup"><span data-stu-id="5e50e-106">These exceptions and their error conditions are listed in the following table.</span></span>

|<span data-ttu-id="5e50e-107">Исключение</span><span class="sxs-lookup"><span data-stu-id="5e50e-107">Exception</span></span>|<span data-ttu-id="5e50e-108">Описание</span><span class="sxs-lookup"><span data-stu-id="5e50e-108">Description</span></span>|
|---------------|-----------------|
|<xref:System.ArithmeticException>|<span data-ttu-id="5e50e-109">Базовый класс для исключений, которые возникают при выполнении арифметических операций, таких как <xref:System.DivideByZeroException> и <xref:System.OverflowException>.</span><span class="sxs-lookup"><span data-stu-id="5e50e-109">A base class for exceptions that occur during arithmetic operations, such as <xref:System.DivideByZeroException> and <xref:System.OverflowException>.</span></span>|
|<xref:System.ArrayTypeMismatchException>|<span data-ttu-id="5e50e-110">Возникает, когда массив не может сохранить данный элемент, поскольку фактический тип элемента несовместим с фактическим типом массива.</span><span class="sxs-lookup"><span data-stu-id="5e50e-110">Thrown when an array can't store a given element because the actual type of the element is incompatible with the actual type of the array.</span></span>|
|<xref:System.DivideByZeroException>|<span data-ttu-id="5e50e-111">Возникает при попытке деления целого значения на ноль.</span><span class="sxs-lookup"><span data-stu-id="5e50e-111">Thrown when an attempt is made to divide an integral value by zero.</span></span>|
|<xref:System.IndexOutOfRangeException>|<span data-ttu-id="5e50e-112">Возникает при попытке индексирования массива, если индекс меньше нуля или выходит за границы массива.</span><span class="sxs-lookup"><span data-stu-id="5e50e-112">Thrown when an attempt is made to index an array when the index is less than zero or outside the bounds of the array.</span></span>|
|<xref:System.InvalidCastException>|<span data-ttu-id="5e50e-113">Возникает, если явное преобразование из базового типа в интерфейс или в производный тип завершается ошибкой во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="5e50e-113">Thrown when an explicit conversion from a base type to an interface or to a derived type fails at runtime.</span></span>|
|<xref:System.NullReferenceException>|<span data-ttu-id="5e50e-114">Возникает при попытке сослаться на объект, имеющий значение [null](../../language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="5e50e-114">Thrown when an attempt is made to reference an object whose value is [null](../../language-reference/keywords/null.md).</span></span>|
|<xref:System.OutOfMemoryException>|<span data-ttu-id="5e50e-115">Возникает, если попытка распределения памяти с помощью оператора [new](../../language-reference/operators/new-operator.md) завершается ошибкой.</span><span class="sxs-lookup"><span data-stu-id="5e50e-115">Thrown when an attempt to allocate memory using the [new](../../language-reference/operators/new-operator.md) operator fails.</span></span> <span data-ttu-id="5e50e-116">Это исключение указывает, что ресурсы памяти, доступные для среды CLR, исчерпаны.</span><span class="sxs-lookup"><span data-stu-id="5e50e-116">This exception indicates that the memory available to the common language runtime has been exhausted.</span></span>|
|<xref:System.OverflowException>|<span data-ttu-id="5e50e-117">Возникает при переполнении арифметической операции в контексте `checked`.</span><span class="sxs-lookup"><span data-stu-id="5e50e-117">Thrown when an arithmetic operation in a `checked` context overflows.</span></span>|
|<xref:System.StackOverflowException>|<span data-ttu-id="5e50e-118">Возникает, когда чрезмерное количество ожидающих вызовов метода истощает стек выполнения; обычно это указывает на крайне глубокую или бесконечную рекурсию.</span><span class="sxs-lookup"><span data-stu-id="5e50e-118">Thrown when the execution stack is exhausted by having too many pending method calls; usually indicates a very deep or infinite recursion.</span></span>|
|<xref:System.TypeInitializationException>|<span data-ttu-id="5e50e-119">Возникает, когда статический конструктор создает исключение, а совместимого предложения `catch` для его захвата нет.</span><span class="sxs-lookup"><span data-stu-id="5e50e-119">Thrown when a static constructor throws an exception and no compatible `catch` clause exists to catch it.</span></span>|

## <a name="see-also"></a><span data-ttu-id="5e50e-120">См. также</span><span class="sxs-lookup"><span data-stu-id="5e50e-120">See also</span></span>

- [<span data-ttu-id="5e50e-121">try-catch</span><span class="sxs-lookup"><span data-stu-id="5e50e-121">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="5e50e-122">try-finally</span><span class="sxs-lookup"><span data-stu-id="5e50e-122">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="5e50e-123">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="5e50e-123">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
