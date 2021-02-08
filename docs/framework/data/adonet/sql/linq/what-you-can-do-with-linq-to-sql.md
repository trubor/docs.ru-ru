---
description: Дополнительные сведения о том, что можно делать с LINQ to SQL
title: Возможности LINQ to SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 061d98b2-baa7-4336-8ad2-c14de8134d91
ms.openlocfilehash: adf1d8dfab69db27d15634a12dbdfbfa287dbb4c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791755"
---
# <a name="what-you-can-do-with-linq-to-sql"></a><span data-ttu-id="cf52e-103">Возможности LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="cf52e-103">What You Can Do With LINQ to SQL</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="cf52e-104">поддерживает все основные возможности, необходимые для разработчиков на SQL.</span><span class="sxs-lookup"><span data-stu-id="cf52e-104">supports all the key capabilities you would expect as a SQL developer.</span></span> <span data-ttu-id="cf52e-105">Можно запрашивать данные, вставлять, обновлять и удалять сведения из таблиц.</span><span class="sxs-lookup"><span data-stu-id="cf52e-105">You can query for information, and insert, update, and delete information from tables.</span></span>  
  
## <a name="selecting"></a><span data-ttu-id="cf52e-106">Выбрать</span><span class="sxs-lookup"><span data-stu-id="cf52e-106">Selecting</span></span>  

 <span data-ttu-id="cf52e-107">Выбор (*проекция*) достигается путем простого НАПИСАНИЯ запроса LINQ на собственном языке программирования и последующего выполнения этого запроса для получения результатов.</span><span class="sxs-lookup"><span data-stu-id="cf52e-107">Selecting (*projection*) is achieved by just writing a LINQ query in your own programming language, and then executing that query to retrieve the results.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="cf52e-108">автоматически преобразует все необходимые операции в привычные операции SQL.</span><span class="sxs-lookup"><span data-stu-id="cf52e-108">itself translates all the necessary operations into the necessary SQL operations that you are familiar with.</span></span> <span data-ttu-id="cf52e-109">Дополнительные сведения см. в разделе [LINQ to SQL](index.md).</span><span class="sxs-lookup"><span data-stu-id="cf52e-109">For more information, see [LINQ to SQL](index.md).</span></span>  
  
 <span data-ttu-id="cf52e-110">В следующем примере извлекаются названий компаний клиентов из Лондона, которые затем отображаются в окне консоли.</span><span class="sxs-lookup"><span data-stu-id="cf52e-110">In the following example, the company names of customers from London are retrieved and displayed in the console window.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="inserting"></a><span data-ttu-id="cf52e-111">Вставка</span><span class="sxs-lookup"><span data-stu-id="cf52e-111">Inserting</span></span>  

 <span data-ttu-id="cf52e-112">Для выполнения SQL `Insert`просто нужно добавить объекты в созданную объектную модель и вызвать метод <xref:System.Data.Linq.DataContext.SubmitChanges%2A> в <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="cf52e-112">To execute a SQL `Insert`, just add objects to the object model you have created, and call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="cf52e-113">В следующем примере новый клиент и сведения о нем добавляются в таблицу `Customers` с помощью метода <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>.</span><span class="sxs-lookup"><span data-stu-id="cf52e-113">In the following example, a new customer and information about the customer is added to the `Customers` table by using <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#2)]
 [!code-vb[DLinqGettingStarted#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#2)]  
  
## <a name="updating"></a><span data-ttu-id="cf52e-114">Обновление</span><span class="sxs-lookup"><span data-stu-id="cf52e-114">Updating</span></span>  

 <span data-ttu-id="cf52e-115">Чтобы `Update` запись в базе данных, сначала следует извлечь элемент и изменить его непосредственно в объектной модели.</span><span class="sxs-lookup"><span data-stu-id="cf52e-115">To `Update` a database entry, first retrieve the item and edit it directly in the object model.</span></span> <span data-ttu-id="cf52e-116">После изменения объекта вызовите метод <xref:System.Data.Linq.DataContext.SubmitChanges%2A> в <xref:System.Data.Linq.DataContext> , чтобы обновить базу данных.</span><span class="sxs-lookup"><span data-stu-id="cf52e-116">After you have modified the object, call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext> to update the database.</span></span>  
  
 <span data-ttu-id="cf52e-117">В следующем примере извлекаются все клиенты из Лондона.</span><span class="sxs-lookup"><span data-stu-id="cf52e-117">In the following example, all customers who are from London are retrieved.</span></span> <span data-ttu-id="cf52e-118">Затем название города меняется с "Лондон" на "Лондон - Метро".</span><span class="sxs-lookup"><span data-stu-id="cf52e-118">Then the name of the city is changed from "London" to "London - Metro".</span></span> <span data-ttu-id="cf52e-119">Наконец, вызывается метод <xref:System.Data.Linq.DataContext.SubmitChanges%2A> для отправления изменений в базу данных.</span><span class="sxs-lookup"><span data-stu-id="cf52e-119">Finally, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called to send the changes to the database.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#3)]
 [!code-vb[DLinqGettingStarted#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#3)]  
  
## <a name="deleting"></a><span data-ttu-id="cf52e-120">Удаление</span><span class="sxs-lookup"><span data-stu-id="cf52e-120">Deleting</span></span>  

 <span data-ttu-id="cf52e-121">Чтобы `Delete` элемент, удалите его из коллекции, в которую он входит, а затем вызовите метод <xref:System.Data.Linq.DataContext.SubmitChanges%2A> в <xref:System.Data.Linq.DataContext> , чтобы применить изменение.</span><span class="sxs-lookup"><span data-stu-id="cf52e-121">To `Delete` an item, remove the item from the collection to which it belongs, and then call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext> to commit the change.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="cf52e-122">не распознает операции каскадного удаления.</span><span class="sxs-lookup"><span data-stu-id="cf52e-122">does not recognize cascade-delete operations.</span></span> <span data-ttu-id="cf52e-123">Если вы хотите удалить строку в таблице с ограничениями, см. статью [как удалить строки из базы данных](how-to-delete-rows-from-the-database.md).</span><span class="sxs-lookup"><span data-stu-id="cf52e-123">If you want to delete a row in a table that has constraints against it, see [How to: Delete Rows From the Database](how-to-delete-rows-from-the-database.md).</span></span>  
  
 <span data-ttu-id="cf52e-124">В следующем примере из базы данных извлекается клиент, `CustomerID` которого равен `98128` .</span><span class="sxs-lookup"><span data-stu-id="cf52e-124">In the following example, the customer who has `CustomerID` of `98128` is retrieved from the database.</span></span> <span data-ttu-id="cf52e-125">Затем, после подтверждения извлечения строки клиента, вызывается метод <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> , необходимый для удаления объекта из коллекции.</span><span class="sxs-lookup"><span data-stu-id="cf52e-125">Then, after confirming that the customer row was retrieved, <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> is called to remove that object from the collection.</span></span> <span data-ttu-id="cf52e-126">Наконец, вызывается метод <xref:System.Data.Linq.DataContext.SubmitChanges%2A> для передачи удаления в базу данных.</span><span class="sxs-lookup"><span data-stu-id="cf52e-126">Finally, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called to forward the deletion to the database.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#4)]
 [!code-vb[DLinqGettingStarted#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="cf52e-127">См. также</span><span class="sxs-lookup"><span data-stu-id="cf52e-127">See also</span></span>

- [<span data-ttu-id="cf52e-128">Руководство по программированию</span><span class="sxs-lookup"><span data-stu-id="cf52e-128">Programming Guide</span></span>](programming-guide.md)
- [<span data-ttu-id="cf52e-129">Модель объектов LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="cf52e-129">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="cf52e-130">Начало работы</span><span class="sxs-lookup"><span data-stu-id="cf52e-130">Getting Started</span></span>](getting-started.md)
