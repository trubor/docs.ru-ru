---
description: 'Дополнительные сведения: получение данных и операции CUD в N-уровневых приложениях (LINQ to SQL)'
title: Извлечение данных и операции создания, обновления и удаления в N-уровневых приложениях (LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3133d53-83ed-4a4d-af8b-82edcf3831db
ms.openlocfilehash: dbad65e1bd29227f434166dca364946a68256177
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672170"
---
# <a name="data-retrieval-and-cud-operations-in-n-tier-applications-linq-to-sql"></a><span data-ttu-id="668ef-103">Извлечение данных и операции создания, обновления и удаления в N-уровневых приложениях (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="668ef-103">Data Retrieval and CUD Operations in N-Tier Applications (LINQ to SQL)</span></span>

<span data-ttu-id="668ef-104">При сериализации объектов сущностей, например объектов "Customers" или "Orders", на клиент по сети эти сущности отсоединяются от своего контекста данных.</span><span class="sxs-lookup"><span data-stu-id="668ef-104">When you serialize entity objects such as Customers or Orders to a client over a network, those entities are detached from their data context.</span></span> <span data-ttu-id="668ef-105">Контекст данных более не отслеживает их изменения или их связи с другими объектами.</span><span class="sxs-lookup"><span data-stu-id="668ef-105">The data context no longer tracks their changes or their associations with other objects.</span></span> <span data-ttu-id="668ef-106">Это не вызывает проблемы, если клиент осуществляет только чтение данных.</span><span class="sxs-lookup"><span data-stu-id="668ef-106">This is not an issue as long as the clients are only reading the data.</span></span> <span data-ttu-id="668ef-107">Также довольно просто реализовать добавление клиентами строк в базу данных.</span><span class="sxs-lookup"><span data-stu-id="668ef-107">It is also relatively simple to enable clients to add new rows to a database.</span></span> <span data-ttu-id="668ef-108">Однако если приложению требуется, чтобы клиенты имели возможность обновлять или удалять данные, то перед вызовом метода <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType> необходимо присоединить сущности к новому контексту данных.</span><span class="sxs-lookup"><span data-stu-id="668ef-108">However, if your application requires that clients be able to update or delete data, then you must attach the entities to a new data context before you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="668ef-109">Кроме того, если используется проверка оптимистического параллелизма на основе исходных значений, также требуется реализовать способ предоставления базе данных исходной сущности и сущности после изменения.</span><span class="sxs-lookup"><span data-stu-id="668ef-109">In addition, if you are using an optimistic concurrency check with original values, then you will also need a way to provide the database both the original entity and the entity as modified.</span></span> <span data-ttu-id="668ef-110">С помощью методов `Attach` можно поместить сущности в новый контекст данных после их отсоединения.</span><span class="sxs-lookup"><span data-stu-id="668ef-110">The `Attach` methods are provided to enable you to put entities into a new data context after they have been detached.</span></span>  
  
 <span data-ttu-id="668ef-111">Даже при сериализации прокси-объектов вместо [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] сущностей все равно необходимо создать сущность на уровне DAL и присоединить ее к новому <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> , чтобы отправить данные в базу данных.</span><span class="sxs-lookup"><span data-stu-id="668ef-111">Even if you are serializing proxy objects in place of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] entities, you still have to construct an entity on the data access layer (DAL), and attach it to a new <xref:System.Data.Linq.DataContext?displayProperty=nameWithType>, in order to submit the data to the database.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="668ef-112">совершенно не отличается от сериализации сущностей.</span><span class="sxs-lookup"><span data-stu-id="668ef-112">is completely indifferent about how entities are serialized.</span></span> <span data-ttu-id="668ef-113">Дополнительные сведения об использовании средств реляционный конструктор объектов и SQLMetal для создания классов, сериализуемых с помощью Windows Communication Foundation (WCF), см. [в разделе как сделать сущности сериализуемыми](how-to-make-entities-serializable.md).</span><span class="sxs-lookup"><span data-stu-id="668ef-113">For more information about how to use the Object Relational Designer and SQLMetal tools to generate classes that are serializable by using Windows Communication Foundation (WCF), see [How to: Make Entities Serializable](how-to-make-entities-serializable.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="668ef-114">Для новых или десериализованных сущностей следует вызывать только методы `Attach`.</span><span class="sxs-lookup"><span data-stu-id="668ef-114">Only call the `Attach` methods on new or deserialized entities.</span></span> <span data-ttu-id="668ef-115">При сериализации сущности ее обязательно следует отсоединить от исходного контекста данных.</span><span class="sxs-lookup"><span data-stu-id="668ef-115">The only way for an entity to be detached from its original data context is for it to be serialized.</span></span> <span data-ttu-id="668ef-116">Если выполняется попытка присоединить неотсоединенную сущность к новому контексту данных и у этой сущности по-прежнему имеются отложенные загрузчики из предыдущего контекста данных, технология [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] вызовет исключение.</span><span class="sxs-lookup"><span data-stu-id="668ef-116">If you try to attach an undetached entity to a new data context, and that entity still has deferred loaders from its previous data context, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] will thrown an exception.</span></span> <span data-ttu-id="668ef-117">Наличие сущности с отложенными загрузчиками из двух разных контекстов данных может привести к нежелательным результатам при выполнении операций вставки, обновления и удаления для этой сущности.</span><span class="sxs-lookup"><span data-stu-id="668ef-117">An entity with deferred loaders from two different data contexts could cause unwanted results when you perform insert, update, and delete operations on that entity.</span></span> <span data-ttu-id="668ef-118">Дополнительные сведения о отложенных загрузчиках см. в разделе [Отложенная и немедленная загрузка](deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="668ef-118">For more information about deferred loaders, see [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
## <a name="retrieving-data"></a><span data-ttu-id="668ef-119">Извлечение данных</span><span class="sxs-lookup"><span data-stu-id="668ef-119">Retrieving Data</span></span>  
  
### <a name="client-method-call"></a><span data-ttu-id="668ef-120">Вызов клиентского метода</span><span class="sxs-lookup"><span data-stu-id="668ef-120">Client Method Call</span></span>  

 <span data-ttu-id="668ef-121">В следующих примерах показан метод вызова компонента DAL из клиента Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="668ef-121">The following examples show a sample method call to the DAL from a Windows Forms client.</span></span> <span data-ttu-id="668ef-122">В данном примере компонент DAL реализован в качестве библиотеки служб Windows.</span><span class="sxs-lookup"><span data-stu-id="668ef-122">In this example, the DAL is implemented as a Windows Service Library:</span></span>  
  
```vb  
Private Function GetProdsByCat_Click(ByVal sender As Object, ByVal e _  
    As EventArgs)  
  
    ' Create the WCF client proxy.  
    Dim proxy As New NorthwindServiceReference.Service1Client  
  
    ' Call the method on the service.  
    Dim products As NorthwindServiceReference.Product() = _  
        proxy.GetProductsByCategory(1)  
  
    ' If the database uses original values for concurrency checks,  
    ' the client needs to store them and pass them back to the  
    ' middle tier along with the new values when updating data.  
  
    For Each v As NorthwindClient1.NorthwindServiceReference.Product _  
        In products  
        ' Persist to a List(Of Product) declared at class scope.  
        ' Additional change-tracking logic is the responsibility  
        ' of the presentation tier and/or middle tier.  
        originalProducts.Add(v)  
    Next  
  
    ' (Not shown) Bind the products list to a control  
    ' and/or perform whatever processing is necessary.  
End Function  
```  
  
```csharp  
private void GetProdsByCat_Click(object sender, EventArgs e)  
{  
    // Create the WCF client proxy.  
    NorthwindServiceReference.Service1Client proxy =
    new NorthwindClient.NorthwindServiceReference.Service1Client();  
  
    // Call the method on the service.  
    NorthwindServiceReference.Product[] products =
    proxy.GetProductsByCategory(1);  
  
    // If the database uses original values for concurrency checks,
    // the client needs to store them and pass them back to the
    // middle tier along with the new values when updating data.  
    foreach (var v in products)  
    {  
        // Persist to a list<Product> declared at class scope.  
        // Additional change-tracking logic is the responsibility  
        // of the presentation tier and/or middle tier.  
        originalProducts.Add(v);  
    }  
  
    // (Not shown) Bind the products list to a control  
    // and/or perform whatever processing is necessary.  
    }  
```  
  
### <a name="middle-tier-implementation"></a><span data-ttu-id="668ef-123">Реализация среднего уровня</span><span class="sxs-lookup"><span data-stu-id="668ef-123">Middle Tier Implementation</span></span>  

 <span data-ttu-id="668ef-124">В следующем примере приведена реализация данного метода интерфейса для среднего уровня.</span><span class="sxs-lookup"><span data-stu-id="668ef-124">The following example shows an implementation of the interface method on the middle tier.</span></span> <span data-ttu-id="668ef-125">Необходимо отметить два основных момента.</span><span class="sxs-lookup"><span data-stu-id="668ef-125">The following are the two main points to note:</span></span>  
  
- <span data-ttu-id="668ef-126">Класс <xref:System.Data.Linq.DataContext> объявляется в области действия метода.</span><span class="sxs-lookup"><span data-stu-id="668ef-126">The <xref:System.Data.Linq.DataContext> is declared at method scope.</span></span>  
  
- <span data-ttu-id="668ef-127">Метод возвращает коллекцию <xref:System.Collections.IEnumerable>, содержащую фактические результаты.</span><span class="sxs-lookup"><span data-stu-id="668ef-127">The method returns an <xref:System.Collections.IEnumerable> collection of the actual results.</span></span> <span data-ttu-id="668ef-128">Для отправки результатов обратно на клиентский уровень или уровень представления данных сериализатор выполняет запрос.</span><span class="sxs-lookup"><span data-stu-id="668ef-128">The serializer will execute the query to send the results back to the client/presentation tier.</span></span> <span data-ttu-id="668ef-129">Для получения доступа к результатам запроса локально на среднем уровне можно принудительно выполнить запрос, вызвав метод `ToList` или `ToArray` для переменной запроса.</span><span class="sxs-lookup"><span data-stu-id="668ef-129">To access the query results locally on the middle tier, you can force execution by calling `ToList` or `ToArray` on the query variable.</span></span> <span data-ttu-id="668ef-130">После этого можно возвратить этот список или массив в качестве коллекции `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="668ef-130">You can then return that list or array as an `IEnumerable`.</span></span>  
  
```vb  
Public Function GetProductsByCategory(ByVal categoryID As Integer) _  
    As IEnumerable(Of Product)  
  
    Dim db As New NorthwindClasses1DataContext(connectionString)  
    Dim productQuery = _  
    From prod In db.Products _  
    Where prod.CategoryID = categoryID _  
    Select prod  
  
    Return productQuery.AsEnumerable()  
  
End Function  
```  
  
```csharp  
public IEnumerable<Product> GetProductsByCategory(int categoryID)  
{  
    NorthwindClasses1DataContext db =
    new NorthwindClasses1DataContext(connectionString);  
  
    IEnumerable<Product> productQuery =  
    from prod in db.Products  
    where prod.CategoryID == categoryID  
    select prod;  
  
    return productQuery.AsEnumerable();
}  
```  
  
 <span data-ttu-id="668ef-131">Время существования экземпляра контекста данных должно составлять одну "единицу работы".</span><span class="sxs-lookup"><span data-stu-id="668ef-131">An instance of a data context should have a lifetime of one "unit of work."</span></span> <span data-ttu-id="668ef-132">В слабо связанных средах единица работы обычно мала и, как правило, составляет одну оптимистическую транзакцию, включающую вызов метода `SubmitChanges`.</span><span class="sxs-lookup"><span data-stu-id="668ef-132">In a loosely-coupled environment, a unit of work is typically small, perhaps one optimistic transaction, including a single call to `SubmitChanges`.</span></span> <span data-ttu-id="668ef-133">Поэтому контекст данных создается и уничтожается в области действия метода.</span><span class="sxs-lookup"><span data-stu-id="668ef-133">Therefore, the data context is created and disposed at method scope.</span></span> <span data-ttu-id="668ef-134">Если единица работы включает вызовы логики бизнес-правил, то, как правило, требуется сохранять экземпляр `DataContext` в течение всей операции.</span><span class="sxs-lookup"><span data-stu-id="668ef-134">If the unit of work includes calls to business rules logic, then generally you will want to keep the `DataContext` instance for that whole operation.</span></span> <span data-ttu-id="668ef-135">В любом случае экземпляры `DataContext` не предназначены для существования в течение продолжительного периода времени в составе произвольного числа транзакций.</span><span class="sxs-lookup"><span data-stu-id="668ef-135">In any case, `DataContext` instances are not intended to be kept alive for long periods of time across arbitrary numbers of transactions.</span></span>  
  
 <span data-ttu-id="668ef-136">Данный метод возвращает объекты "Product", а не коллекцию объектов "Order_Detail", связанных с каждым объектом "Product".</span><span class="sxs-lookup"><span data-stu-id="668ef-136">This method will return Product objects but not the collection of Order_Detail objects that are associated with each Product.</span></span> <span data-ttu-id="668ef-137">Для изменения данного поведения, установленного по умолчанию, используйте объект <xref:System.Data.Linq.DataLoadOptions>.</span><span class="sxs-lookup"><span data-stu-id="668ef-137">Use the <xref:System.Data.Linq.DataLoadOptions> object to change this default behavior.</span></span> <span data-ttu-id="668ef-138">Дополнительные сведения см. [в разделе руководство. Управление объемом извлекаемых связанных данных](how-to-control-how-much-related-data-is-retrieved.md).</span><span class="sxs-lookup"><span data-stu-id="668ef-138">For more information, see [How to: Control How Much Related Data Is Retrieved](how-to-control-how-much-related-data-is-retrieved.md).</span></span>  
  
## <a name="inserting-data"></a><span data-ttu-id="668ef-139">Вставка данных</span><span class="sxs-lookup"><span data-stu-id="668ef-139">Inserting Data</span></span>  

 <span data-ttu-id="668ef-140">Для вставки нового объекта уровень представления данных просто вызывает соответствующий метод в интерфейсе среднего уровня и передает новый объект для вставки.</span><span class="sxs-lookup"><span data-stu-id="668ef-140">To insert a new object, the presentation tier just calls the relevant method on the middle tier interface, and passes in the new object to insert.</span></span> <span data-ttu-id="668ef-141">В некоторых случаях более эффективным становится способ, когда клиент передает только некоторые значения и указывает среднему уровню создать полный объект.</span><span class="sxs-lookup"><span data-stu-id="668ef-141">In some cases, it may be more efficient for the client to pass in only some values and have the middle tier construct the full object.</span></span>  
  
### <a name="middle-tier-implementation"></a><span data-ttu-id="668ef-142">Реализация среднего уровня</span><span class="sxs-lookup"><span data-stu-id="668ef-142">Middle Tier Implementation</span></span>  

 <span data-ttu-id="668ef-143">На среднем уровне создается новый класс <xref:System.Data.Linq.DataContext>, объект присоединяется к классу <xref:System.Data.Linq.DataContext> с помощью метода <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> и объект вставляется при вызове метода <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span><span class="sxs-lookup"><span data-stu-id="668ef-143">On the middle tier, a new <xref:System.Data.Linq.DataContext> is created, the object is attached to the <xref:System.Data.Linq.DataContext> by using the <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> method, and the object is inserted when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="668ef-144">Исключения, обратные вызовы и состояния ошибки можно обрабатывать точно так же, как в других сценариях веб-служб.</span><span class="sxs-lookup"><span data-stu-id="668ef-144">Exceptions, callbacks, and error conditions can be handled just as in any other Web service scenario.</span></span>  
  
```vb  
' No call to Attach is necessary for inserts.  
Public Sub InsertOrder(ByVal o As Order)  
  
    Dim db As New NorthwindClasses1DataContext(connectionString)  
    db.Orders.InsertOnSubmit(o)  
  
    ' Exception handling not shown.  
    db.SubmitChanges()  
  
End Sub  
```  
  
```csharp  
// No call to Attach is necessary for inserts.  
    public void InsertOrder(Order o)  
    {  
        NorthwindClasses1DataContext db = new NorthwindClasses1DataContext(connectionString);  
        db.Orders.InsertOnSubmit(o);  
  
        // Exception handling not shown.  
        db.SubmitChanges();  
    }  
```  
  
## <a name="deleting-data"></a><span data-ttu-id="668ef-145">Удаление данных</span><span class="sxs-lookup"><span data-stu-id="668ef-145">Deleting Data</span></span>  

 <span data-ttu-id="668ef-146">Для удаления существующего объекта из базы данных уровень представления данных вызывает соответствующий метод в интерфейсе среднего уровня и передает копию, которая содержит исходные значения удаляемого объекта.</span><span class="sxs-lookup"><span data-stu-id="668ef-146">To delete an existing object from the database, the presentation tier calls the relevant method on the middle tier interface, and passes in its copy that includes original values of the object to be deleted.</span></span>  
  
 <span data-ttu-id="668ef-147">В состав операций удаления входят проверки оптимистического параллелизма, а удаляемый объект должен сначала быть присоединен к новому контексту данных.</span><span class="sxs-lookup"><span data-stu-id="668ef-147">Delete operations involve optimistic concurrency checks, and the object to be deleted must first be attached to the new data context.</span></span> <span data-ttu-id="668ef-148">В данном примере для параметра `Boolean` устанавливается значение `false`, которое указывает, что объект не имеет отметки времени (столбца "RowVersion").</span><span class="sxs-lookup"><span data-stu-id="668ef-148">In this example, the `Boolean` parameter is set to `false` to indicate that the object does not have a timestamp (RowVersion).</span></span> <span data-ttu-id="668ef-149">Если таблица базы данных создает отметки времени для каждой записи, проверки параллелизма выполняются гораздо проще, особенно для клиента.</span><span class="sxs-lookup"><span data-stu-id="668ef-149">If your database table does generate timestamps for each record, then concurrency checks are much simpler, especially for the client.</span></span> <span data-ttu-id="668ef-150">Для этого достаточно передать исходный или измененный объект и установить для параметра `Boolean` значение `true`.</span><span class="sxs-lookup"><span data-stu-id="668ef-150">Just pass in either the original or modified object and set the `Boolean` parameter to `true`.</span></span> <span data-ttu-id="668ef-151">В любом случае на среднем уровне, как правило, требуется перехватывать исключение <xref:System.Data.Linq.ChangeConflictException>.</span><span class="sxs-lookup"><span data-stu-id="668ef-151">In any case, on the middle tier it is typically necessary to catch the <xref:System.Data.Linq.ChangeConflictException>.</span></span> <span data-ttu-id="668ef-152">Дополнительные сведения об обработке конфликтов оптимистического параллелизма см. в разделе [Оптимистическая блокировка: обзор](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="668ef-152">For more information about how to handle optimistic concurrency conflicts, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="668ef-153">При удалении сущностей, которые имеют ограничения внешних ключей для связанных таблиц, необходимо сначала удалить все объекты в коллекции <xref:System.Data.Linq.EntitySet%601> для сущности.</span><span class="sxs-lookup"><span data-stu-id="668ef-153">When deleting entities that have foreign key constraints on associated tables, you must first delete all the objects in its <xref:System.Data.Linq.EntitySet%601> collections.</span></span>  
  
```vb  
' Attach is necessary for deletes.  
Public Sub DeleteOrder(ByVal order As Order)  
    Dim db As New NorthwindClasses1DataContext(connectionString)  
  
    db.Orders.Attach(order, False)  
    ' This will throw an exception if the order has order details.  
    db.Orders.DeleteOnSubmit(order)  
  
    Try  
        ' ConflictMode is an optional parameter.  
        db.SubmitChanges(ConflictMode.ContinueOnConflict)  
  
    Catch ex As ChangeConflictException  
        ' Get conflict information, and take actions  
        ' that are appropriate for your application.  
        ' See MSDN Article "How to: Manage Change  
        ' Conflicts (LINQ to SQL).  
  
    End Try  
End Sub  
```  
  
```csharp  
// Attach is necessary for deletes.  
public void DeleteOrder(Order order)  
{  
    NorthwindClasses1DataContext db = new NorthwindClasses1DataContext(connectionString);  
  
    db.Orders.Attach(order, false);  
    // This will throw an exception if the order has order details.  
    db.Orders.DeleteOnSubmit(order);  
    try  
    {  
        // ConflictMode is an optional parameter.  
        db.SubmitChanges(ConflictMode.ContinueOnConflict);  
    }  
    catch (ChangeConflictException e)  
    {  
       // Get conflict information, and take actions  
       // that are appropriate for your application.  
       // See MSDN Article How to: Manage Change Conflicts (LINQ to SQL).  
    }  
}  
```  
  
## <a name="updating-data"></a><span data-ttu-id="668ef-154">Обновление данных</span><span class="sxs-lookup"><span data-stu-id="668ef-154">Updating Data</span></span>  

 <span data-ttu-id="668ef-155">Технология [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] поддерживает обновления в перечисленных ниже сценариях, в которых используется оптимистический параллелизм.</span><span class="sxs-lookup"><span data-stu-id="668ef-155">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] supports updates in these scenarios involving optimistic concurrency:</span></span>  
  
- <span data-ttu-id="668ef-156">Оптимистический параллелизм, основанный на метках времени (или значениях столбца "RowVersion").</span><span class="sxs-lookup"><span data-stu-id="668ef-156">Optimistic concurrency based on timestamps or RowVersion numbers.</span></span>  
  
- <span data-ttu-id="668ef-157">Оптимистический параллелизм, основанный на исходных значениях вложенного набора свойств сущности.</span><span class="sxs-lookup"><span data-stu-id="668ef-157">Optimistic concurrency based on original values of a subset of entity properties.</span></span>  
  
- <span data-ttu-id="668ef-158">Оптимистический параллелизм, основанный на полных исходных и измененных сущностях.</span><span class="sxs-lookup"><span data-stu-id="668ef-158">Optimistic concurrency based on the complete original and modified entities.</span></span>  
  
 <span data-ttu-id="668ef-159">Можно также выполнять операции обновления или удаления сущности вместе с ее связями, например обновить или удалить объект "Customer" и коллекцию связанных с ним объектов "Order".</span><span class="sxs-lookup"><span data-stu-id="668ef-159">You can also perform updates or deletes on an entity together with its relations, for example a Customer and a collection of its associated Order objects.</span></span> <span data-ttu-id="668ef-160">Если при внесении изменений в граф объектов сущностей и их дочерних коллекций (`EntitySet`) на клиенте для проверок оптимистического параллелизма требуются исходные значения, то клиенту необходимо предоставить эти исходные значения для каждой сущности и объекта <xref:System.Data.Linq.EntitySet%601>.</span><span class="sxs-lookup"><span data-stu-id="668ef-160">When you make modifications on the client to a graph of entity objects and their child (`EntitySet`) collections, and the optimistic concurrency checks require original values, the client must provide those original values for each entity and <xref:System.Data.Linq.EntitySet%601> object.</span></span> <span data-ttu-id="668ef-161">Если необходимо предоставить клиенту возможность выполнить набор связанных операций удаления, обновления и вставки в одном методе, следует предоставить клиенту способ указания типа операции, которую необходимо выполнить для каждой сущности.</span><span class="sxs-lookup"><span data-stu-id="668ef-161">If you want to enable clients to make a set of related updates, deletes, and insertions in a single method call, you must provide the client a way to indicate what type of operation to perform on each entity.</span></span> <span data-ttu-id="668ef-162">На среднем уровне требуется вызвать соответствующий метод <xref:System.Data.Linq.ITable.Attach%2A>, а затем перед вызовом метода <xref:System.Data.Linq.ITable.InsertOnSubmit%2A> необходимо вызвать метод <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>, <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> или `Attach` (для операций вставки вызывать метод <xref:System.Data.Linq.DataContext.SubmitChanges%2A> вызывать не следует) для каждой сущности.</span><span class="sxs-lookup"><span data-stu-id="668ef-162">On the middle tier, you then must call the appropriate <xref:System.Data.Linq.ITable.Attach%2A> method and then <xref:System.Data.Linq.ITable.InsertOnSubmit%2A>, <xref:System.Data.Linq.ITable.DeleteAllOnSubmit%2A>, or <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> (without `Attach`, for insertions) for each entity before you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span> <span data-ttu-id="668ef-163">Не используйте извлечение данных из базы данных в качестве способа получения исходных значений перед обновлением.</span><span class="sxs-lookup"><span data-stu-id="668ef-163">Do not retrieve data from the database as a way to obtain original values before you try updates.</span></span>  
  
 <span data-ttu-id="668ef-164">Дополнительные сведения о оптимистичном параллелизме см. в разделе [Оптимистическая блокировка: обзор](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="668ef-164">For more information about optimistic concurrency, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span> <span data-ttu-id="668ef-165">Подробные сведения об устранении конфликтов изменений оптимистичного параллелизма см. [в разделе Управление конфликтами изменений](how-to-manage-change-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="668ef-165">For detailed information about resolving optimistic concurrency change conflicts, see [How to: Manage Change Conflicts](how-to-manage-change-conflicts.md).</span></span>  
  
 <span data-ttu-id="668ef-166">В следующих примерах демонстрируется каждый из описанных выше сценариев.</span><span class="sxs-lookup"><span data-stu-id="668ef-166">The following examples demonstrate each scenario:</span></span>  
  
### <a name="optimistic-concurrency-with-timestamps"></a><span data-ttu-id="668ef-167">Оптимистический параллелизм на основе меток времени</span><span class="sxs-lookup"><span data-stu-id="668ef-167">Optimistic concurrency with timestamps</span></span>  
  
```vb  
' Assume that "customer" has been sent by client.  
' Attach with "true" to say this is a modified entity  
' and it can be checked for optimistic concurrency  
' because it has a column that is marked with the  
' "RowVersion" attribute.  
  
db.Customers.Attach(customer, True)  
  
Try  
    ' Optional: Specify a ConflictMode value  
    ' in call to SubmitChanges.  
    db.SubmitChanges()  
Catch ex As ChangeConflictException  
    ' Handle conflict based on options provided.  
    ' See MSDN article "How to: Manage Change  
    ' Conflicts (LINQ to SQL)".  
End Try  
```  
  
```csharp  
// Assume that "customer" has been sent by client.  
// Attach with "true" to say this is a modified entity  
// and it can be checked for optimistic concurrency because  
//  it has a column that is marked with "RowVersion" attribute  
db.Customers.Attach(customer, true)  
try  
{  
    // Optional: Specify a ConflictMode value  
    // in call to SubmitChanges.  
    db.SubmitChanges();  
}  
catch(ChangeConflictException e)  
{  
    // Handle conflict based on options provided  
    // See MSDN article How to: Manage Change Conflicts (LINQ to SQL).  
}  
```  
  
### <a name="with-subset-of-original-values"></a><span data-ttu-id="668ef-168">На основе вложенного набора исходных значений</span><span class="sxs-lookup"><span data-stu-id="668ef-168">With Subset of Original Values</span></span>  

 <span data-ttu-id="668ef-169">В данном методе клиент возвращает полный сериализованный объект вместе со значениями, которые требуется изменить.</span><span class="sxs-lookup"><span data-stu-id="668ef-169">In this approach, the client returns the complete serialized object, together with the values to be modified.</span></span>  
  
```vb  
Public Sub UpdateProductInventory(ByVal p As Product, ByVal _  
    unitsInStock As Short?, ByVal unitsOnOrder As Short?)  
  
    Using db As New NorthwindClasses1DataContext(connectionString)  
        ' p is the original unmodified product  
        ' that was obtained from the database.  
        ' The client kept a copy and returns it now.  
        db.Products.Attach(p, False)  
  
        ' Now that the original values are in the data context,  
        ' apply the changes.  
        p.UnitsInStock = unitsInStock  
        p.UnitsOnOrder = unitsOnOrder  
  
        Try  
            ' Optional: Specify a ConflictMode value  
            ' in call to SubmitChanges.  
            db.SubmitChanges()  
  
        Catch ex As Exception  
            ' Handle conflict based on options provided.  
            ' See MSDN article "How to: Manage Change Conflicts  
            ' (LINQ to SQL)".  
        End Try  
    End Using  
End Sub  
```  
  
```csharp  
public void UpdateProductInventory(Product p, short? unitsInStock, short? unitsOnOrder)  
{  
    using (NorthwindClasses1DataContext db = new NorthwindClasses1DataContext(connectionString))  
    {  
        // p is the original unmodified product  
        // that was obtained from the database.  
        // The client kept a copy and returns it now.  
        db.Products.Attach(p, false);  
  
        // Now that the original values are in the data context, apply the changes.  
        p.UnitsInStock = unitsInStock;  
        p.UnitsOnOrder = unitsOnOrder;  
        try  
        {  
             // Optional: Specify a ConflictMode value  
             // in call to SubmitChanges.  
             db.SubmitChanges();  
        }  
        catch (ChangeConflictException e)  
        {  
            // Handle conflict based on provided options.  
            // See MSDN article How to: Manage Change Conflicts  
            // (LINQ to SQL).  
        }  
    }  
}  
```  
  
### <a name="with-complete-entities"></a><span data-ttu-id="668ef-170">На основе полных сущностей</span><span class="sxs-lookup"><span data-stu-id="668ef-170">With Complete Entities</span></span>  
  
```vb  
Public Sub UpdateProductInfo(ByVal newProd As Product, ByVal _  
    originalProd As Product)  
  
    Using db As New NorthwindClasses1DataContext(connectionString)  
        db.Products.Attach(newProd, originalProd)  
  
        Try  
            ' Optional: Specify a ConflictMode value  
            ' in call to SubmitChanges.  
            db.SubmitChanges()  
  
        Catch ex As Exception  
            ' Handle potential change conflicgt in whatever way  
            ' is appropriate for your application.  
            ' For more information, see the MSDN article  
            ' "How to: Manage Change Conflicts (LINQ to  
            ' SQL)".  
        End Try  
  
    End Using  
End Sub  
```  
  
```csharp  
public void UpdateProductInfo(Product newProd, Product originalProd)  
{  
     using (NorthwindClasses1DataContext db = new  
        NorthwindClasses1DataContext(connectionString))  
     {  
         db.Products.Attach(newProd, originalProd);  
         try  
         {  
               // Optional: Specify a ConflictMode value  
               // in call to SubmitChanges.  
               db.SubmitChanges();  
         }  
        catch (ChangeConflictException e)  
        {  
            // Handle potential change conflict in whatever way  
            // is appropriate for your application.  
            // For more information, see the MSDN article  
            // How to: Manage Change Conflicts (LINQ to SQL)/  
        }
    }  
}  
```  
  
 <span data-ttu-id="668ef-171">Для обновления коллекции вместо метода <xref:System.Data.Linq.ITable.AttachAll%2A> вызовите метод `Attach`.</span><span class="sxs-lookup"><span data-stu-id="668ef-171">To update a collection, call <xref:System.Data.Linq.ITable.AttachAll%2A> instead of `Attach`.</span></span>  
  
### <a name="expected-entity-members"></a><span data-ttu-id="668ef-172">Ожидаемые члены сущности</span><span class="sxs-lookup"><span data-stu-id="668ef-172">Expected Entity Members</span></span>  

 <span data-ttu-id="668ef-173">Как уже указывалось выше, перед вызовом методов `Attach` требуется установить только некоторые члены объекта сущности.</span><span class="sxs-lookup"><span data-stu-id="668ef-173">As stated previously, only certain members of the entity object are required to be set before you call the `Attach` methods.</span></span> <span data-ttu-id="668ef-174">Ниже перечислены критерии, которым должны удовлетворять члены сущности, которые требуется установить.</span><span class="sxs-lookup"><span data-stu-id="668ef-174">Entity members that are required to be set must fulfill the following criteria:</span></span>  
  
- <span data-ttu-id="668ef-175">Члены должны входить в состав идентификации сущности.</span><span class="sxs-lookup"><span data-stu-id="668ef-175">Be part of the entity’s identity.</span></span>  
  
- <span data-ttu-id="668ef-176">Их изменение должно быть ожидаемо.</span><span class="sxs-lookup"><span data-stu-id="668ef-176">Be expected to be modified.</span></span>  
  
- <span data-ttu-id="668ef-177">Они должны представлять собой метку времени или для их атрибута <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> должно быть установлено значение, отличное от `Never`.</span><span class="sxs-lookup"><span data-stu-id="668ef-177">Be a timestamp or have its <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> attribute set to something besides `Never`.</span></span>  
  
 <span data-ttu-id="668ef-178">Если для проверки оптимистического параллелизма в таблице используется метка времени или номер версии, то перед вызовом метода <xref:System.Data.Linq.ITable.Attach%2A> необходимо установить значения этих членов.</span><span class="sxs-lookup"><span data-stu-id="668ef-178">If a table uses a timestamp or version number for an optimistic concurrency check, you must set those members before you call <xref:System.Data.Linq.ITable.Attach%2A>.</span></span> <span data-ttu-id="668ef-179">Член предназначен для проверки оптимистического параллелизма в том случае, если свойства <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> данного атрибута столбца установлено значение "true".</span><span class="sxs-lookup"><span data-stu-id="668ef-179">A member is dedicated for optimistic concurrency checking when the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property is set to true on that Column attribute.</span></span> <span data-ttu-id="668ef-180">Любые запрошенные обновления будут отправлены только в том случае, если значения номера версии или метки времени совпадают в базе данных.</span><span class="sxs-lookup"><span data-stu-id="668ef-180">Any requested updates will be submitted only if the version number or timestamp values are the same on the database.</span></span>  
  
 <span data-ttu-id="668ef-181">Кроме того, член используется для проверки оптимистического параллелизма в том случае, если для свойства <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> данного члена не установлено значение `Never`.</span><span class="sxs-lookup"><span data-stu-id="668ef-181">A member is also used in the optimistic concurrency check as long as the member does not have <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> set to `Never`.</span></span> <span data-ttu-id="668ef-182">Если значение этого атрибута не установлено, по умолчанию используется значение `Always`.</span><span class="sxs-lookup"><span data-stu-id="668ef-182">The default value is `Always` if no other value is specified.</span></span>  
  
 <span data-ttu-id="668ef-183">Если один из этих обязательных членов отсутствует, то при выполнении метода <xref:System.Data.Linq.ChangeConflictException> вызывается исключение <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("Строка не найдена или изменена").</span><span class="sxs-lookup"><span data-stu-id="668ef-183">If any one of these required members is missing, a <xref:System.Data.Linq.ChangeConflictException> is thrown during <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ("Row not found or changed").</span></span>  
  
### <a name="state"></a><span data-ttu-id="668ef-184">Область</span><span class="sxs-lookup"><span data-stu-id="668ef-184">State</span></span>  

 <span data-ttu-id="668ef-185">После того как объект сущности присоединен к экземпляру <xref:System.Data.Linq.DataContext>, состоянием объекта считается значение `PossiblyModified`.</span><span class="sxs-lookup"><span data-stu-id="668ef-185">After an entity object is attached to the <xref:System.Data.Linq.DataContext> instance, the object is considered to be in the `PossiblyModified` state.</span></span> <span data-ttu-id="668ef-186">Для принудительного присвоения объекту состояния `Modified` можно использовать три способа.</span><span class="sxs-lookup"><span data-stu-id="668ef-186">There are three ways to force an attached object to be considered `Modified`.</span></span>  
  
1. <span data-ttu-id="668ef-187">Присоединить объект как неизмененный и затем изменить непосредственно поля.</span><span class="sxs-lookup"><span data-stu-id="668ef-187">Attach it as unmodified, and then directly modify the fields.</span></span>  
  
2. <span data-ttu-id="668ef-188">Присоединить объект с помощью перегрузки метода <xref:System.Data.Linq.Table%601.Attach%2A>, которая принимает текущий и исходный экземпляры объекта.</span><span class="sxs-lookup"><span data-stu-id="668ef-188">Attach it with the <xref:System.Data.Linq.Table%601.Attach%2A> overload that takes current and original object instances.</span></span> <span data-ttu-id="668ef-189">При этом средству отслеживания изменений предоставляются старое и новое значения, и он можно автоматически определить, какие поля изменились.</span><span class="sxs-lookup"><span data-stu-id="668ef-189">This supplies the change tracker with old and new values so that it will automatically know which fields have changed.</span></span>  
  
3. <span data-ttu-id="668ef-190">Присоединить объект с помощью перегрузки метода <xref:System.Data.Linq.Table%601.Attach%2A>, которая принимает "Boolean" в качестве второго параметра (с установленным значением "true").</span><span class="sxs-lookup"><span data-stu-id="668ef-190">Attach it with the <xref:System.Data.Linq.Table%601.Attach%2A> overload that takes a second Boolean parameter (set to true).</span></span> <span data-ttu-id="668ef-191">При этом средство отслеживания изменений получает указание рассматривать объект как измененный, и предоставлять исходные значения не требуется.</span><span class="sxs-lookup"><span data-stu-id="668ef-191">This will tell the change tracker to consider the object modified without having to supply any original values.</span></span> <span data-ttu-id="668ef-192">При использовании этого метода объект должен иметь поле версии или метки времени.</span><span class="sxs-lookup"><span data-stu-id="668ef-192">In this approach, the object must have a version/timestamp field.</span></span>  
  
 <span data-ttu-id="668ef-193">Дополнительные сведения см. в разделе [состояния объектов и отслеживание изменений](object-states-and-change-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="668ef-193">For more information, see [Object States and Change-Tracking](object-states-and-change-tracking.md).</span></span>  
  
 <span data-ttu-id="668ef-194">Если в кэше уже имеется объект сущности с идентификацией присоединяемого объекта, вызывается исключение <xref:System.Data.Linq.DuplicateKeyException>.</span><span class="sxs-lookup"><span data-stu-id="668ef-194">If an entity object already occurs in the ID Cache with the same identity as the object being attached, a <xref:System.Data.Linq.DuplicateKeyException> is thrown.</span></span>  
  
 <span data-ttu-id="668ef-195">Если при присоединении набора объектов `IEnumerable` в кэше оказывается совпадающий ключ, вызывается исключение <xref:System.Data.Linq.DuplicateKeyException>.</span><span class="sxs-lookup"><span data-stu-id="668ef-195">When you attach with an `IEnumerable` set of objects, a <xref:System.Data.Linq.DuplicateKeyException> is thrown when an already existing key is present.</span></span> <span data-ttu-id="668ef-196">Остальные объекты не присоединяются.</span><span class="sxs-lookup"><span data-stu-id="668ef-196">Remaining objects are not attached.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="668ef-197">См. также</span><span class="sxs-lookup"><span data-stu-id="668ef-197">See also</span></span>

- [<span data-ttu-id="668ef-198">N-уровневые и удаленные приложения с LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="668ef-198">N-Tier and Remote Applications with LINQ to SQL</span></span>](n-tier-and-remote-applications-with-linq-to-sql.md)
- [<span data-ttu-id="668ef-199">Основные сведения</span><span class="sxs-lookup"><span data-stu-id="668ef-199">Background Information</span></span>](background-information.md)
