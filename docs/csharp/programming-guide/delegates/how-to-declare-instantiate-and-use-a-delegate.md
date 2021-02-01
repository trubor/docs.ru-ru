---
title: Руководство по программированию на C#. Объявление, создание экземпляра и использование делегата
description: Сведения об объявлении, создании и использовании делегата. Изучите примеры, которые можно применить в C# 1.0, 2.0, 3.0 и более поздних версиях.
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: 08d8e10b4aba3fd75e200b2c8c14bb3d1825b318
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/27/2021
ms.locfileid: "98898883"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a><span data-ttu-id="a7d0b-104">Руководство по программированию на C#. Объявление, создание экземпляра и использование делегата</span><span class="sxs-lookup"><span data-stu-id="a7d0b-104">How to declare, instantiate, and use a Delegate (C# Programming Guide)</span></span>

<span data-ttu-id="a7d0b-105">В C# 1.0 и более поздних версий делегаты можно объявлять так, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="a7d0b-105">In C# 1.0 and later, delegates can be declared as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#13)]  
  
 [!code-csharp[csProgGuideDelegates#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#14)]  
  
 <span data-ttu-id="a7d0b-106">В C# 2.0 предоставлен более простой способ для записи предыдущего объявления, который показан в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="a7d0b-106">C# 2.0 provides a simpler way to write the previous declaration, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#32)]  
  
 <span data-ttu-id="a7d0b-107">В C# 2.0 и более поздних версиях можно использовать анонимный метод для объявления и инициализации [делегата](../../language-reference/builtin-types/reference-types.md), как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="a7d0b-107">In C# 2.0 and later, it is also possible to use an anonymous method to declare and initialize a [delegate](../../language-reference/builtin-types/reference-types.md), as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#15)]  
  
 <span data-ttu-id="a7d0b-108">В C# 3.0 и более поздних версиях можно объявлять делегаты и создавать для них экземпляры с помощью лямбда-выражения, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="a7d0b-108">In C# 3.0 and later, delegates can also be declared and instantiated by using a lambda expression, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#31)]  
  
 <span data-ttu-id="a7d0b-109">Дополнительные сведения см. в разделе [Лямбда-выражения](../../language-reference/operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="a7d0b-109">For more information, see [Lambda Expressions](../../language-reference/operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="a7d0b-110">Следующий пример демонстрирует объявление, создание экземпляра и использование делегата.</span><span class="sxs-lookup"><span data-stu-id="a7d0b-110">The following example illustrates declaring, instantiating, and using a delegate.</span></span> <span data-ttu-id="a7d0b-111">Класс `BookDB` инкапсулирует базу данных книжного магазина, в которой хранится информация о книгах.</span><span class="sxs-lookup"><span data-stu-id="a7d0b-111">The `BookDB` class encapsulates a bookstore database that maintains a database of books.</span></span> <span data-ttu-id="a7d0b-112">Он предоставляет метод `ProcessPaperbackBooks`, который находит в базе данных все книги в мягкой обложке и вызывает делегат для каждой из них.</span><span class="sxs-lookup"><span data-stu-id="a7d0b-112">It exposes a method, `ProcessPaperbackBooks`, which finds all paperback books in the database and calls a delegate for each one.</span></span> <span data-ttu-id="a7d0b-113">Используется тип `delegate` с именем `ProcessBookCallback`.</span><span class="sxs-lookup"><span data-stu-id="a7d0b-113">The `delegate` type that is used is named `ProcessBookCallback`.</span></span> <span data-ttu-id="a7d0b-114">Класс `Test` использует этот класс для печати заголовков и средней цены книг в мягкой обложке.</span><span class="sxs-lookup"><span data-stu-id="a7d0b-114">The `Test` class uses this class to print the titles and average price of the paperback books.</span></span>  
  
 <span data-ttu-id="a7d0b-115">Использование делегата помогает правильно разделить функции между базой данных книжного магазина и кодом клиента.</span><span class="sxs-lookup"><span data-stu-id="a7d0b-115">The use of delegates promotes good separation of functionality between the bookstore database and the client code.</span></span> <span data-ttu-id="a7d0b-116">Код клиента не имеет сведений о том, как хранятся книги и как код книжного магазина находит книги в мягкой обложке.</span><span class="sxs-lookup"><span data-stu-id="a7d0b-116">The client code has no knowledge of how the books are stored or how the bookstore code finds paperback books.</span></span> <span data-ttu-id="a7d0b-117">Код книжного магазина не имеет сведений о том, какая обработка выполняется для найденных книг в мягкой обложке.</span><span class="sxs-lookup"><span data-stu-id="a7d0b-117">The bookstore code has no knowledge of what processing is performed on the paperback books after it finds them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7d0b-118">Пример</span><span class="sxs-lookup"><span data-stu-id="a7d0b-118">Example</span></span>  

 [!code-csharp[csProgGuideDelegates#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#12)]  
  
## <a name="robust-programming"></a><span data-ttu-id="a7d0b-119">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="a7d0b-119">Robust Programming</span></span>  
  
- <span data-ttu-id="a7d0b-120">Объявление делегата.</span><span class="sxs-lookup"><span data-stu-id="a7d0b-120">Declaring a delegate.</span></span>  
  
     <span data-ttu-id="a7d0b-121">Следующая инструкция объявляет новый тип делегата.</span><span class="sxs-lookup"><span data-stu-id="a7d0b-121">The following statement declares a new delegate type.</span></span>  
  
     [!code-csharp[csProgGuideDelegates#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#16)]  
  
     <span data-ttu-id="a7d0b-122">Каждый тип делегата описывает количество аргументов и их типы, а также тип возвращаемого значения для всех методов, которые он может инкапсулировать.</span><span class="sxs-lookup"><span data-stu-id="a7d0b-122">Each delegate type describes the number and types of the arguments, and the type of the return value of methods that it can encapsulate.</span></span> <span data-ttu-id="a7d0b-123">Каждый раз, когда требуется новый набор типов аргументов или новый тип возвращаемого значения, нужно объявить новый тип делегата.</span><span class="sxs-lookup"><span data-stu-id="a7d0b-123">Whenever a new set of argument types or return value type is needed, a new delegate type must be declared.</span></span>  
  
- <span data-ttu-id="a7d0b-124">Создания экземпляра делегата.</span><span class="sxs-lookup"><span data-stu-id="a7d0b-124">Instantiating a delegate.</span></span>  
  
     <span data-ttu-id="a7d0b-125">После объявления типа делегата нужно создать объект этого делегата и связать его с определенным методом.</span><span class="sxs-lookup"><span data-stu-id="a7d0b-125">After a delegate type has been declared, a delegate object must be created and associated with a particular method.</span></span> <span data-ttu-id="a7d0b-126">Продолжая предыдущий пример, вы можете передать метод `PrintTitle` в метод `ProcessPaperbackBooks`, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="a7d0b-126">In the previous example, you do this by passing the `PrintTitle` method to the `ProcessPaperbackBooks` method as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#17)]  
  
     <span data-ttu-id="a7d0b-127">Будет создан новый объект делегата, связанный со [статическим](../../language-reference/keywords/static.md) методом `Test.PrintTitle`.</span><span class="sxs-lookup"><span data-stu-id="a7d0b-127">This creates a new delegate object associated with the [static](../../language-reference/keywords/static.md) method `Test.PrintTitle`.</span></span> <span data-ttu-id="a7d0b-128">Аналогичным образом, в следующем примере передается нестатический метод `AddBookToTotal` для объекта `totaller`:</span><span class="sxs-lookup"><span data-stu-id="a7d0b-128">Similarly, the non-static method `AddBookToTotal` on the object `totaller` is passed as in the following example:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#18)]  
  
     <span data-ttu-id="a7d0b-129">В обоих случаях новый объект делегата передается в метод `ProcessPaperbackBooks`.</span><span class="sxs-lookup"><span data-stu-id="a7d0b-129">In both cases a new delegate object is passed to the `ProcessPaperbackBooks` method.</span></span>  
  
     <span data-ttu-id="a7d0b-130">После создания делегата невозможно изменить метод, с которым он связан. Объекты делегатов являются неизменяемыми.</span><span class="sxs-lookup"><span data-stu-id="a7d0b-130">After a delegate is created, the method it is associated with never changes; delegate objects are immutable.</span></span>  
  
- <span data-ttu-id="a7d0b-131">Использование делегатов</span><span class="sxs-lookup"><span data-stu-id="a7d0b-131">Calling a delegate.</span></span>  
  
     <span data-ttu-id="a7d0b-132">Обычно после создания объекта делегата он передается в другой код, который будет использовать этот делегат.</span><span class="sxs-lookup"><span data-stu-id="a7d0b-132">After a delegate object is created, the delegate object is typically passed to other code that will call the delegate.</span></span> <span data-ttu-id="a7d0b-133">Для вызова объекта делегата используется имя этого объекта, за которым следуют параметризованные аргументы, которые нужно передать делегату.</span><span class="sxs-lookup"><span data-stu-id="a7d0b-133">A delegate object is called by using the name of the delegate object, followed by the parenthesized arguments to be passed to the delegate.</span></span> <span data-ttu-id="a7d0b-134">Ниже показан пример использования делегата.</span><span class="sxs-lookup"><span data-stu-id="a7d0b-134">Following is an example of a delegate call:</span></span>  
  
     [!code-csharp[csProgGuideDelegates#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#19)]  
  
     <span data-ttu-id="a7d0b-135">Делегат можно вызвать синхронно, как показано в этом примере, или асинхронно при помощи методов `BeginInvoke` и `EndInvoke`.</span><span class="sxs-lookup"><span data-stu-id="a7d0b-135">A delegate can be either called synchronously, as in this example, or asynchronously by using `BeginInvoke` and `EndInvoke` methods.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7d0b-136">См. также</span><span class="sxs-lookup"><span data-stu-id="a7d0b-136">See also</span></span>

- [<span data-ttu-id="a7d0b-137">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="a7d0b-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a7d0b-138">События</span><span class="sxs-lookup"><span data-stu-id="a7d0b-138">Events</span></span>](../events/index.md)
- [<span data-ttu-id="a7d0b-139">Делегаты</span><span class="sxs-lookup"><span data-stu-id="a7d0b-139">Delegates</span></span>](./index.md)
