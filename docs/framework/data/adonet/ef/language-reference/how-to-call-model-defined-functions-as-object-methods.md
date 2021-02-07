---
description: Дополнительные сведения см. в статье как вызывать функции Model-Defined как методы объектов.
title: Практическое руководство. Вызов определенных моделью функций как методов объектов
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33bae8a8-4ed8-4a1f-85d1-c62ff288cc61
ms.openlocfilehash: 46f171d5785bf715382e87c3fb7dae932db0bb65
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748678"
---
# <a name="how-to-call-model-defined-functions-as-object-methods"></a><span data-ttu-id="32c18-103">Практическое руководство. Вызов определенных моделью функций как методов объектов</span><span class="sxs-lookup"><span data-stu-id="32c18-103">How to: Call Model-Defined Functions as Object Methods</span></span>

<span data-ttu-id="32c18-104">В данном разделе описывается, как вызвать определяемую в модели функцию в качестве метода для объекта <xref:System.Data.Objects.ObjectContext> или в качестве статического метода для пользовательского класса.</span><span class="sxs-lookup"><span data-stu-id="32c18-104">This topic describes how to call a model-defined function as a method on an <xref:System.Data.Objects.ObjectContext> object or as a static method on a custom class.</span></span> <span data-ttu-id="32c18-105">*Определяемая моделью функция* — это функция, определенная в концептуальной модели.</span><span class="sxs-lookup"><span data-stu-id="32c18-105">A *model-defined function* is a function that is defined in the conceptual model.</span></span> <span data-ttu-id="32c18-106">В данном разделе показываются процедуры вызова этих функций напрямую, а не с помощью запросов LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="32c18-106">The procedures in the topic describe how to call these functions directly instead of calling them from LINQ to Entities queries.</span></span> <span data-ttu-id="32c18-107">Дополнительные сведения о вызове функций, определяемых моделью, в запросах LINQ to Entities см. в разделе [как вызывать функции Model-Defined в запросах](how-to-call-model-defined-functions-in-queries.md).</span><span class="sxs-lookup"><span data-stu-id="32c18-107">For information about calling model-defined functions in LINQ to Entities queries, see [How to: Call Model-Defined Functions in Queries](how-to-call-model-defined-functions-in-queries.md).</span></span>  
  
 <span data-ttu-id="32c18-108">Если определяемая в модели функция вызвается как метод <xref:System.Data.Objects.ObjectContext> или как статический метод для пользовательского класса, в первую очередь необходимо сопоставить метод с определямой в модели функцией с <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="32c18-108">Whether you call a model-defined function as an <xref:System.Data.Objects.ObjectContext> method or as a static method on a custom class, you must first map the method to the model-defined function with an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span> <span data-ttu-id="32c18-109">Если метод определяется для класса <xref:System.Data.Objects.ObjectContext>, то следует использовать свойство <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> для предоставления поставщика LINQ, однако, если статический метод определяется для пользовательского класса, то следует использовать свойство <xref:System.Linq.IQueryable.Provider%2A> для предоставления поставщика LINQ.</span><span class="sxs-lookup"><span data-stu-id="32c18-109">However, when you define a method on the <xref:System.Data.Objects.ObjectContext> class, you must use the <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> property to expose the LINQ provider, whereas when you define a static method on a custom class, you must use the <xref:System.Linq.IQueryable.Provider%2A> property to expose the LINQ provider.</span></span> <span data-ttu-id="32c18-110">Дополнительные сведения см. в примерах, приведенных после указанных ниже процедур.</span><span class="sxs-lookup"><span data-stu-id="32c18-110">For more information, see the examples that follow the procedures below.</span></span>  
  
 <span data-ttu-id="32c18-111">В следующих процедурах описываются высокоуровневые структуры для вызова определяемой в модели функции в качестве метода для объекта <xref:System.Data.Objects.ObjectContext> или в качестве статического метода для пользовательского класса.</span><span class="sxs-lookup"><span data-stu-id="32c18-111">The procedures below provide high-level outlines for calling a model-defined function as a method on an <xref:System.Data.Objects.ObjectContext> object and as a static method on a custom class.</span></span> <span data-ttu-id="32c18-112">В следующих примерах подробно описаны шаги данной процедуры.</span><span class="sxs-lookup"><span data-stu-id="32c18-112">The examples that follow provide more detail about the steps in the procedures.</span></span> <span data-ttu-id="32c18-113">Эта процедура предполагает, что функция была определена в концептуальной модели.</span><span class="sxs-lookup"><span data-stu-id="32c18-113">The procedures assume that you have defined a function in the conceptual model.</span></span> <span data-ttu-id="32c18-114">Дополнительные сведения см. в разделе [инструкции. Определение пользовательских функций в концептуальной модели](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="32c18-114">For more information, see [How to: Define Custom Functions in the Conceptual Model](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).</span></span>  
  
### <a name="to-call-a-model-defined-function-as-a-method-on-an-objectcontext-object"></a><span data-ttu-id="32c18-115">Вызов определяемой в модели функции в качестве метода объекта ObjectContext</span><span class="sxs-lookup"><span data-stu-id="32c18-115">To call a model-defined function as a method on an ObjectContext object</span></span>  
  
1. <span data-ttu-id="32c18-116">Добавьте исходный файл, чтобы расширить разделяемый класс, производный от класса <xref:System.Data.Objects.ObjectContext>, автоматически созданный средствами платформы Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="32c18-116">Add a source file to extend the partial class derived from the <xref:System.Data.Objects.ObjectContext> class, auto-generated by the Entity Framework tools.</span></span> <span data-ttu-id="32c18-117">Если заглушка CLR определена в отдельном исходном файле, это поможет предотвратить потерю изменений при повторном создании файла.</span><span class="sxs-lookup"><span data-stu-id="32c18-117">Defining the CLR stub in a separate source file will prevent the changes from being lost when the file is regenerated.</span></span>  
  
2. <span data-ttu-id="32c18-118">Добавьте к классу <xref:System.Data.Objects.ObjectContext> метод среды CLR, выполняющий следующие действия:</span><span class="sxs-lookup"><span data-stu-id="32c18-118">Add a common language runtime (CLR) method to your <xref:System.Data.Objects.ObjectContext> class that does the following:</span></span>  
  
    - <span data-ttu-id="32c18-119">Устанавливает сопоставление с функцией, определяемой в концептуальной модели.</span><span class="sxs-lookup"><span data-stu-id="32c18-119">Maps to the function defined in the conceptual model.</span></span> <span data-ttu-id="32c18-120">Для сопоставления метода к нему необходимо применить атрибут <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="32c18-120">To map the method, you must apply an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method.</span></span> <span data-ttu-id="32c18-121">Обратите внимание, что параметры атрибута <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> и <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> представляют собой имя пространства имен концептуальной модели и имя функции концептуальной модели соответственно.</span><span class="sxs-lookup"><span data-stu-id="32c18-121">Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model, respectively.</span></span> <span data-ttu-id="32c18-122">При разрешении имени функции для LINQ учитывается регистр.</span><span class="sxs-lookup"><span data-stu-id="32c18-122">Function name resolution for LINQ is case sensitive.</span></span>  
  
    - <span data-ttu-id="32c18-123">Возвращает результаты метода <xref:System.Linq.IQueryProvider.Execute%2A>, возвращаемого свойством <xref:System.Data.Objects.ObjectContext.QueryProvider%2A>.</span><span class="sxs-lookup"><span data-stu-id="32c18-123">Returns the results of the <xref:System.Linq.IQueryProvider.Execute%2A> method that is returned by the <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> property.</span></span>  
  
3. <span data-ttu-id="32c18-124">Вызовите метод в качестве элемента экземпляра класса <xref:System.Data.Objects.ObjectContext>.</span><span class="sxs-lookup"><span data-stu-id="32c18-124">Call the method as a member on an instance of the <xref:System.Data.Objects.ObjectContext> class.</span></span>  
  
### <a name="to-call-a-model-defined-function-as-static-method-on-a-custom-class"></a><span data-ttu-id="32c18-125">Вызов определяемой в модели функции в качестве статического метода из пользовательского класса</span><span class="sxs-lookup"><span data-stu-id="32c18-125">To call a model-defined function as static method on a custom class</span></span>  
  
1. <span data-ttu-id="32c18-126">Добавьте к приложению класс со статическим методом, выполняющий следующие действия:</span><span class="sxs-lookup"><span data-stu-id="32c18-126">Add a class to your application with a static method that does the following:</span></span>  
  
    - <span data-ttu-id="32c18-127">Устанавливает сопоставление с функцией, определяемой в концептуальной модели.</span><span class="sxs-lookup"><span data-stu-id="32c18-127">Maps to the function defined in the conceptual model.</span></span> <span data-ttu-id="32c18-128">Для сопоставления метода к нему необходимо применить атрибут <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="32c18-128">To map the method, you must apply an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method.</span></span> <span data-ttu-id="32c18-129">Обратите внимание, что параметры атрибута <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> и <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> представляют собой имя пространства имен концептуальной модели и имя функции концептуальной модели соответственно.</span><span class="sxs-lookup"><span data-stu-id="32c18-129">Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model, respectively.</span></span>  
  
    - <span data-ttu-id="32c18-130">Принимает аргумент <xref:System.Linq.IQueryable>.</span><span class="sxs-lookup"><span data-stu-id="32c18-130">Accepts an <xref:System.Linq.IQueryable> argument.</span></span>  
  
    - <span data-ttu-id="32c18-131">Возвращает результаты метода <xref:System.Linq.IQueryProvider.Execute%2A>, возвращаемого свойством <xref:System.Linq.IQueryable.Provider%2A>.</span><span class="sxs-lookup"><span data-stu-id="32c18-131">Returns the results of the <xref:System.Linq.IQueryProvider.Execute%2A> method that is returned by the <xref:System.Linq.IQueryable.Provider%2A> property.</span></span>  
  
2. <span data-ttu-id="32c18-132">Вызовите метод в качестве члена статического метода из пользовательского класса</span><span class="sxs-lookup"><span data-stu-id="32c18-132">Call the method as a member a static method on the custom class</span></span>  
  
## <a name="example"></a><span data-ttu-id="32c18-133">Пример</span><span class="sxs-lookup"><span data-stu-id="32c18-133">Example</span></span>  

 <span data-ttu-id="32c18-134">**Вызов определяемой в модели функции в качестве метода объекта ObjectContext**</span><span class="sxs-lookup"><span data-stu-id="32c18-134">**Calling a Model-Defined Function as a Method on an ObjectContext Object**</span></span>  
  
 <span data-ttu-id="32c18-135">В приведенном ниже примере показано, как вызвать определяемую в модели функцию в качестве метода для объекта <xref:System.Data.Objects.ObjectContext>.</span><span class="sxs-lookup"><span data-stu-id="32c18-135">The following example demonstrates how to call a model-defined function as a method on an <xref:System.Data.Objects.ObjectContext> object.</span></span> <span data-ttu-id="32c18-136">В примере используется [модель AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span><span class="sxs-lookup"><span data-stu-id="32c18-136">The example uses the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span>  
  
 <span data-ttu-id="32c18-137">Рассмотрите описанную ниже функцию концептуальной модели, возвращающую доход от указанного продукта.</span><span class="sxs-lookup"><span data-stu-id="32c18-137">Consider the conceptual model function below that returns product revenue for a specified product.</span></span> <span data-ttu-id="32c18-138">(Дополнительные сведения о добавлении функции в концептуальную модель см. в разделе [инструкции. Определение пользовательских функций в концептуальной модели](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).)</span><span class="sxs-lookup"><span data-stu-id="32c18-138">(For information about adding the function to your conceptual model, see [How to: Define Custom Functions in the Conceptual Model](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).)</span></span>  
  
 [!code-xml[DP L2E Methods on ObjectContext#4](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#4)]  

## <a name="example"></a><span data-ttu-id="32c18-139">Пример</span><span class="sxs-lookup"><span data-stu-id="32c18-139">Example</span></span>  

 <span data-ttu-id="32c18-140">Следующий код добавляет метод к классу `AdventureWorksEntities`, который сопоставляется с функцией концептуальной модели, описанной выше.</span><span class="sxs-lookup"><span data-stu-id="32c18-140">The following code adds a method to the `AdventureWorksEntities` class that maps to the conceptual model function above.</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#2)]
 [!code-vb[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="32c18-141">Пример</span><span class="sxs-lookup"><span data-stu-id="32c18-141">Example</span></span>  

 <span data-ttu-id="32c18-142">В следующем коде вызывается описанный выше метод для отображения дохода для указанного продукта:</span><span class="sxs-lookup"><span data-stu-id="32c18-142">The following code calls the method above to display the product revenue for a specified product:</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#3)]
 [!code-vb[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="32c18-143">Пример</span><span class="sxs-lookup"><span data-stu-id="32c18-143">Example</span></span>  

 <span data-ttu-id="32c18-144">В приведенном ниже примере показано, как вызвать определяемую в модели функцию, возвращающую коллекцию (как объект <xref:System.Linq.IQueryable%601>).</span><span class="sxs-lookup"><span data-stu-id="32c18-144">The following example demonstrates how to call a model-defined function that returns a collection (as an <xref:System.Linq.IQueryable%601> object).</span></span> <span data-ttu-id="32c18-145">Рассмотрите описанную ниже функцию концептуальной модели, возвращающую подробные сведения `SalesOrderDetails` для указанного идентификатора продукта.</span><span class="sxs-lookup"><span data-stu-id="32c18-145">Consider the conceptual model function below that returns all the `SalesOrderDetails` for a given product ID.</span></span>  
  
 [!code-xml[DP L2E Methods on ObjectContext#7](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#7)]  
  
## <a name="example"></a><span data-ttu-id="32c18-146">Пример</span><span class="sxs-lookup"><span data-stu-id="32c18-146">Example</span></span>  

 <span data-ttu-id="32c18-147">Следующий код добавляет метод к классу `AdventureWorksEntities`, который сопоставляется с функцией концептуальной модели, описанной выше.</span><span class="sxs-lookup"><span data-stu-id="32c18-147">The following code adds a method to the `AdventureWorksEntities` class that maps to the conceptual model function above.</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#8)]
 [!code-vb[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="32c18-148">Пример</span><span class="sxs-lookup"><span data-stu-id="32c18-148">Example</span></span>  

 <span data-ttu-id="32c18-149">Следующий код вызывает метод.</span><span class="sxs-lookup"><span data-stu-id="32c18-149">The following code calls the method.</span></span> <span data-ttu-id="32c18-150">Обратите внимание, что возвращаемый запрос <xref:System.Linq.IQueryable%601> дорабатывается для возвращения линейных итогов для каждого `SalesOrderDetail`.</span><span class="sxs-lookup"><span data-stu-id="32c18-150">Note that the returned <xref:System.Linq.IQueryable%601> query is further refined to return line totals for each `SalesOrderDetail`.</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#9)]
 [!code-vb[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="32c18-151">Пример</span><span class="sxs-lookup"><span data-stu-id="32c18-151">Example</span></span>  

 <span data-ttu-id="32c18-152">**Вызов определяемой в модели функции в качестве статического метода из пользовательского класса**</span><span class="sxs-lookup"><span data-stu-id="32c18-152">**Calling a Model-Defined Function as a Static Method on a Custom Class**</span></span>  
  
 <span data-ttu-id="32c18-153">В следующем примере показано, как вызвать определяемую в модели функцию в качестве статического метода из пользовательского класса.</span><span class="sxs-lookup"><span data-stu-id="32c18-153">The next example demonstrates how to call a model-defined function as a static method on a custom class.</span></span> <span data-ttu-id="32c18-154">В примере используется [модель AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span><span class="sxs-lookup"><span data-stu-id="32c18-154">The example uses the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="32c18-155">Если определяемая в модели функция вызывается как статический метод для пользовательского класса, эта функция должна принять коллекцию и вернуть результат статистической обработки значений из коллекции.</span><span class="sxs-lookup"><span data-stu-id="32c18-155">When you call a model-defined function as a static method on a custom class, the model-defined function must accept a collection and return an aggregation of values in the collection.</span></span>  
  
 <span data-ttu-id="32c18-156">Рассмотрите описанную ниже функцию концептуальной модели, возвращающую доход от коллекции SalesOrderDetail.</span><span class="sxs-lookup"><span data-stu-id="32c18-156">Consider the conceptual model function below that returns product revenue for a SalesOrderDetail collection.</span></span> <span data-ttu-id="32c18-157">(Дополнительные сведения о добавлении функции в концептуальную модель см. в разделе [инструкции. Определение пользовательских функций в концептуальной модели](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).)</span><span class="sxs-lookup"><span data-stu-id="32c18-157">(For information about adding the function to your conceptual model, see [How to: Define Custom Functions in the Conceptual Model](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).).</span></span>  
  
 [!code-xml[DP L2E Methods on ObjectContext#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#1)]
  
## <a name="example"></a><span data-ttu-id="32c18-158">Пример</span><span class="sxs-lookup"><span data-stu-id="32c18-158">Example</span></span>  

 <span data-ttu-id="32c18-159">Следующий код добавляет к приложению класс, содержащий статический метод, который сопоставляется с функцией концептуальной модели, описанной выше.</span><span class="sxs-lookup"><span data-stu-id="32c18-159">The following code adds a class to your application that contains a static method that maps to the conceptual model function above.</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#5)]
 [!code-vb[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="32c18-160">Пример</span><span class="sxs-lookup"><span data-stu-id="32c18-160">Example</span></span>  

 <span data-ttu-id="32c18-161">В следующем коде вызывается описанный выше метод для отображения дохода для коллекции SalesOrderDetail:</span><span class="sxs-lookup"><span data-stu-id="32c18-161">The following code calls the method above to display the product revenue for a SalesOrderDetail collection:</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#6)]
 [!code-vb[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="32c18-162">См. также</span><span class="sxs-lookup"><span data-stu-id="32c18-162">See also</span></span>

- <span data-ttu-id="32c18-163">[Общие сведения о EDMX-файлах](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="32c18-163">[.edmx File Overview](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- [<span data-ttu-id="32c18-164">Запросы в LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="32c18-164">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
- [<span data-ttu-id="32c18-165">Вызов функций в запросах LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="32c18-165">Calling Functions in LINQ to Entities Queries</span></span>](calling-functions-in-linq-to-entities-queries.md)
