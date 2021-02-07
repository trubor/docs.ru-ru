---
description: Дополнительные сведения см. в статье Пошаговое руководство. выполнение запросов между связями (C#)
title: Пошаговое руководство. Запросы по связям (C#)
ms.date: 03/30/2017
ms.assetid: 552abeb1-18f2-4e93-a9c6-ef7b2db30c32
ms.openlocfilehash: 35811043ddd7ecc9aca5e1bd87a370abebf90853
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729449"
---
# <a name="walkthrough-querying-across-relationships-c"></a><span data-ttu-id="99742-103">Пошаговое руководство. Запросы по связям (C#)</span><span class="sxs-lookup"><span data-stu-id="99742-103">Walkthrough: Querying Across Relationships (C#)</span></span>

<span data-ttu-id="99742-104">В этом пошаговом руководстве демонстрируется использование [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *ассоциаций* для представления связей внешнего ключа в базе данных.</span><span class="sxs-lookup"><span data-stu-id="99742-104">This walkthrough demonstrates the use of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *associations* to represent foreign-key relationships in the database.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="99742-105">Это пошаговое руководство было написано с использованием параметров разработки Visual C#.</span><span class="sxs-lookup"><span data-stu-id="99742-105">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="99742-106">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="99742-106">Prerequisites</span></span>  

 <span data-ttu-id="99742-107">Необходимо выполнить [Пошаговое руководство: простая модель объектов и запрос (C#)](walkthrough-simple-object-model-and-query-csharp.md).</span><span class="sxs-lookup"><span data-stu-id="99742-107">You must have completed [Walkthrough: Simple Object Model and Query (C#)](walkthrough-simple-object-model-and-query-csharp.md).</span></span> <span data-ttu-id="99742-108">В основе данного пошагового руководства лежит руководство, описываемое в данном разделе; кроме того, в компьютере должен быть файл northwnd.mdf в папке c:\linqtest5.</span><span class="sxs-lookup"><span data-stu-id="99742-108">This walkthrough builds on that one, including the presence of the northwnd.mdf file in c:\linqtest5.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="99742-109">Обзор</span><span class="sxs-lookup"><span data-stu-id="99742-109">Overview</span></span>  

 <span data-ttu-id="99742-110">Данное пошаговое руководство состоит из трех основных задач.</span><span class="sxs-lookup"><span data-stu-id="99742-110">This walkthrough consists of three main tasks:</span></span>  
  
- <span data-ttu-id="99742-111">Добавление класса сущности, который представляет таблицу "Orders" в базе данных "Northwind".</span><span class="sxs-lookup"><span data-stu-id="99742-111">Adding an entity class to represent the Orders table in the sample Northwind database.</span></span>  
  
- <span data-ttu-id="99742-112">Добавление примечаний к классу `Customer`, чтобы расширить связи между классами `Customer` и `Order`.</span><span class="sxs-lookup"><span data-stu-id="99742-112">Supplementing annotations to the `Customer` class to enhance the relationship between the `Customer` and `Order` classes.</span></span>  
  
- <span data-ttu-id="99742-113">Создание и выполнение запроса для тестирования процесса получения сведений о классе `Order` с помощью класса `Customer`.</span><span class="sxs-lookup"><span data-stu-id="99742-113">Creating and running a query to test obtaining `Order` information by using the `Customer` class.</span></span>  
  
## <a name="mapping-relationships-across-tables"></a><span data-ttu-id="99742-114">Сопоставление связей между таблицами</span><span class="sxs-lookup"><span data-stu-id="99742-114">Mapping Relationships Across Tables</span></span>  

 <span data-ttu-id="99742-115">После определения класса `Customer` создайте определение класса сущностей `Order`, включающее следующий код, который указывает, что свойство `Order.Customer` связано как внешний ключ со свойством `Customer.CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="99742-115">After the `Customer` class definition, create the `Order` entity class definition that includes the following code, which indicates that `Order.Customer` relates as a foreign key to `Customer.CustomerID`.</span></span>  
  
### <a name="to-add-the-order-entity-class"></a><span data-ttu-id="99742-116">Добавление класса сущностей "Order"</span><span class="sxs-lookup"><span data-stu-id="99742-116">To add the Order entity class</span></span>  
  
- <span data-ttu-id="99742-117">Введите или вставьте следующий код после определения класса `Customer`.</span><span class="sxs-lookup"><span data-stu-id="99742-117">Type or paste the following code after the `Customer` class:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#1)]  
  
## <a name="annotating-the-customer-class"></a><span data-ttu-id="99742-118">Добавление примечаний к классу "Customer"</span><span class="sxs-lookup"><span data-stu-id="99742-118">Annotating the Customer Class</span></span>  

 <span data-ttu-id="99742-119">На этом этапе добавляются примечания к классу `Customer`, чтобы указать его связь с классом `Order`.</span><span class="sxs-lookup"><span data-stu-id="99742-119">In this step, you annotate the `Customer` class to indicate its relationship to the `Order` class.</span></span> <span data-ttu-id="99742-120">(Это добавление не является обязательным, поскольку для создания связи достаточно создать определение связи в любом направлении.</span><span class="sxs-lookup"><span data-stu-id="99742-120">(This addition is not strictly necessary, because defining the relationship in either direction is sufficient to create the link.</span></span> <span data-ttu-id="99742-121">Однако добавление этого примечания позволит с легкостью переходить по объектам в любом направлении.)</span><span class="sxs-lookup"><span data-stu-id="99742-121">But adding this annotation does enable you to easily navigate objects in either direction.)</span></span>  
  
### <a name="to-annotate-the-customer-class"></a><span data-ttu-id="99742-122">Добавление примечаний к классу "Customer"</span><span class="sxs-lookup"><span data-stu-id="99742-122">To annotate the Customer class</span></span>  
  
- <span data-ttu-id="99742-123">Введите или вставьте следующий код в класс `Customer`.</span><span class="sxs-lookup"><span data-stu-id="99742-123">Type or paste the following code into the `Customer` class:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a><span data-ttu-id="99742-124">Создание и выполнение запроса в рамках связи "Customer-Order"</span><span class="sxs-lookup"><span data-stu-id="99742-124">Creating and Running a Query Across the Customer-Order Relationship</span></span>  

 <span data-ttu-id="99742-125">Теперь можно получить доступ к объектам `Order` непосредственно из объектов `Customer` или в обратном направлении.</span><span class="sxs-lookup"><span data-stu-id="99742-125">You can now access `Order` objects directly from the `Customer` objects, or in the opposite order.</span></span> <span data-ttu-id="99742-126">Явное *соединение* между клиентами и заказами не требуется.</span><span class="sxs-lookup"><span data-stu-id="99742-126">You do not need an explicit *join* between customers and orders.</span></span>  
  
### <a name="to-access-order-objects-by-using-customer-objects"></a><span data-ttu-id="99742-127">Получение доступа к объектам "Order" с помощью объектов "Customer"</span><span class="sxs-lookup"><span data-stu-id="99742-127">To access Order objects by using Customer objects</span></span>  
  
1. <span data-ttu-id="99742-128">Измените метод `Main` посредством ввода или вставки в метод следующего кода:</span><span class="sxs-lookup"><span data-stu-id="99742-128">Modify the `Main` method by typing or pasting the following code into the method:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#3)]  
  
2. <span data-ttu-id="99742-129">Нажмите клавишу F5, чтобы начать отладку приложения.</span><span class="sxs-lookup"><span data-stu-id="99742-129">Press F5 to debug your application.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="99742-130">Чтобы избежать отображения кода SQL в окне "Консоль", преобразуйте `db.Log = Console.Out;` в комментарий.</span><span class="sxs-lookup"><span data-stu-id="99742-130">You can eliminate the SQL code in the Console window by commenting out `db.Log = Console.Out;`.</span></span>  
  
3. <span data-ttu-id="99742-131">Чтобы остановить отладку, в окне консоли нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="99742-131">Press Enter in the Console window to stop debugging.</span></span>  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a><span data-ttu-id="99742-132">Создание строго типизированного представления базы данных</span><span class="sxs-lookup"><span data-stu-id="99742-132">Creating a Strongly Typed View of Your Database</span></span>  

 <span data-ttu-id="99742-133">Общая процедура становится гораздо проще, если в начале использовать строго типизированное представление базы данных.</span><span class="sxs-lookup"><span data-stu-id="99742-133">It is much easier to start with a strongly typed view of your database.</span></span> <span data-ttu-id="99742-134">Задавая строгую типизацию объекта <xref:System.Data.Linq.DataContext>, можно избежать вызовов метода <xref:System.Data.Linq.DataContext.GetTable%2A>.</span><span class="sxs-lookup"><span data-stu-id="99742-134">By strongly typing the <xref:System.Data.Linq.DataContext> object, you do not need calls to <xref:System.Data.Linq.DataContext.GetTable%2A>.</span></span> <span data-ttu-id="99742-135">Строго типизированные таблицы можно использовать в запросах только при использовании строго типизированного объекта <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="99742-135">You can use strongly typed tables in all your queries when you use the strongly typed <xref:System.Data.Linq.DataContext> object.</span></span>  
  
 <span data-ttu-id="99742-136">В представленных ниже шагах создается объект `Customers` в качестве строго типизированной таблицы, которая сопоставляется с таблицей "Customers" в базе данных.</span><span class="sxs-lookup"><span data-stu-id="99742-136">In the following steps, you will create `Customers` as a strongly typed table that maps to the Customers table in the database.</span></span>  
  
### <a name="to-strongly-type-the-datacontext-object"></a><span data-ttu-id="99742-137">Установка строгой типизации объекта "DataContext"</span><span class="sxs-lookup"><span data-stu-id="99742-137">To strongly type the DataContext object</span></span>  
  
1. <span data-ttu-id="99742-138">Добавьте следующий код непосредственно перед объявлением класса `Customer`.</span><span class="sxs-lookup"><span data-stu-id="99742-138">Add the following code above the `Customer` class declaration.</span></span>  
  
     [!code-csharp[DLinqWalk2CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#4)]  
  
2. <span data-ttu-id="99742-139">Измените метод `Main`, чтобы использовать строго типизированный объект <xref:System.Data.Linq.DataContext>, как показано далее.</span><span class="sxs-lookup"><span data-stu-id="99742-139">Modify the `Main` method to use the strongly typed <xref:System.Data.Linq.DataContext> as follows:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#5)]  
  
3. <span data-ttu-id="99742-140">Нажмите клавишу F5, чтобы начать отладку приложения.</span><span class="sxs-lookup"><span data-stu-id="99742-140">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="99742-141">В окне «Консоль"» отобразится следующее.</span><span class="sxs-lookup"><span data-stu-id="99742-141">The Console window output is:</span></span>  
  
     `ID=WHITC`  
  
4. <span data-ttu-id="99742-142">Чтобы остановить отладку, в окне консоли нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="99742-142">Press Enter in the console window to stop debugging.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="99742-143">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="99742-143">Next Steps</span></span>  

 <span data-ttu-id="99742-144">В следующем пошаговом руководстве ([Пошаговое руководство. манипулирование данными (C#)](walkthrough-manipulating-data-csharp.md)) показано, как управлять данными.</span><span class="sxs-lookup"><span data-stu-id="99742-144">The next walkthrough ([Walkthrough: Manipulating Data (C#)](walkthrough-manipulating-data-csharp.md)) demonstrates how to manipulate data.</span></span> <span data-ttu-id="99742-145">Для этого пошагового руководства не требуется сохранять два пошаговых руководства, которые уже выполнены в этой серии.</span><span class="sxs-lookup"><span data-stu-id="99742-145">That walkthrough does not require that you save the two walkthroughs in this series that you have already completed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99742-146">См. также</span><span class="sxs-lookup"><span data-stu-id="99742-146">See also</span></span>

- [<span data-ttu-id="99742-147">Обучение с использованием пошаговых руководств</span><span class="sxs-lookup"><span data-stu-id="99742-147">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
