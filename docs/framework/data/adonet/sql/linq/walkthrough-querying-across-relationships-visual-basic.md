---
description: Дополнительные сведения см. в разделе Пошаговое выполнение запросов по связям (Visual Basic).
title: Пошаговое руководство. Выполнение запросов со связями (Visual Basic)
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: a7da43e3-769f-4e07-bcd6-552b8bde66f4
ms.openlocfilehash: 002ec53c5a56d988dcd71af658a546d199473425
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650587"
---
# <a name="walkthrough-querying-across-relationships-visual-basic"></a><span data-ttu-id="19abd-103">Пошаговое руководство. Выполнение запросов со связями (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19abd-103">Walkthrough: Querying Across Relationships (Visual Basic)</span></span>

<span data-ttu-id="19abd-104">В этом пошаговом руководстве демонстрируется использование [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *ассоциаций* для представления связей внешнего ключа в базе данных.</span><span class="sxs-lookup"><span data-stu-id="19abd-104">This walkthrough demonstrates the use of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *associations* to represent foreign-key relationships in the database.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="19abd-105">Это пошаговое руководство было написано с помощью параметров разработки Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="19abd-105">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="19abd-106">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="19abd-106">Prerequisites</span></span>  

 <span data-ttu-id="19abd-107">Необходимо выполнить [Пошаговое руководство: простая модель объектов и запрос (Visual Basic)](walkthrough-simple-object-model-and-query-visual-basic.md).</span><span class="sxs-lookup"><span data-stu-id="19abd-107">You must have completed [Walkthrough: Simple Object Model and Query (Visual Basic)](walkthrough-simple-object-model-and-query-visual-basic.md).</span></span> <span data-ttu-id="19abd-108">На этом пошаговом руководстве основано руководство, описываемое в данном разделе. В частности на компьютере должен иметься файл northwnd.mdf в папке c:\linqtest.</span><span class="sxs-lookup"><span data-stu-id="19abd-108">This walkthrough builds on that one, including the presence of the northwnd.mdf file in c:\linqtest.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="19abd-109">Обзор</span><span class="sxs-lookup"><span data-stu-id="19abd-109">Overview</span></span>  

 <span data-ttu-id="19abd-110">Данное пошаговое руководство состоит из трех основных задач.</span><span class="sxs-lookup"><span data-stu-id="19abd-110">This walkthrough consists of three main tasks:</span></span>  
  
- <span data-ttu-id="19abd-111">Добавление класса сущности, который представляет таблицу "Orders" в базе данных "Northwind".</span><span class="sxs-lookup"><span data-stu-id="19abd-111">Adding an entity class to represent the Orders table in the sample Northwind database.</span></span>  
  
- <span data-ttu-id="19abd-112">Добавление примечаний к классу `Customer`, чтобы расширить связи между классами `Customer` и `Order`.</span><span class="sxs-lookup"><span data-stu-id="19abd-112">Supplementing annotations to the `Customer` class to enhance the relationship between the `Customer` and `Order` classes.</span></span>  
  
- <span data-ttu-id="19abd-113">Создание и выполнение запроса для тестирования процесса получения сведений класса `Order` с помощью класса `Customer`.</span><span class="sxs-lookup"><span data-stu-id="19abd-113">Creating and running a query to test the process of obtaining `Order` information by using the `Customer` class.</span></span>  
  
## <a name="mapping-relationships-across-tables"></a><span data-ttu-id="19abd-114">Сопоставление связей между таблицами</span><span class="sxs-lookup"><span data-stu-id="19abd-114">Mapping Relationships across Tables</span></span>  

 <span data-ttu-id="19abd-115">После определения класса `Customer` создайте определение класса сущностей `Order`, включающее следующий код, который указывает, что свойство `Orders.Customer` связано как внешний ключ со свойством `Customers.CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="19abd-115">After the `Customer` class definition, create the `Order` entity class definition that includes the following code, which indicates that `Orders.Customer` relates as a foreign key to `Customers.CustomerID`.</span></span>  
  
#### <a name="to-add-the-order-entity-class"></a><span data-ttu-id="19abd-116">Добавление класса сущностей "Order"</span><span class="sxs-lookup"><span data-stu-id="19abd-116">To add the Order entity class</span></span>  
  
- <span data-ttu-id="19abd-117">Введите или вставьте следующий код после определения класса `Customer`.</span><span class="sxs-lookup"><span data-stu-id="19abd-117">Type or paste the following code after the `Customer` class:</span></span>  
  
     [!code-vb[DLinqWalk2VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#1)]  
  
## <a name="annotating-the-customer-class"></a><span data-ttu-id="19abd-118">Добавление примечаний к классу "Customer"</span><span class="sxs-lookup"><span data-stu-id="19abd-118">Annotating the Customer Class</span></span>  

 <span data-ttu-id="19abd-119">На этом этапе добавляются примечания к классу `Customer`, чтобы указать его связь с классом `Order`.</span><span class="sxs-lookup"><span data-stu-id="19abd-119">In this step, you annotate the `Customer` class to indicate its relationship to the `Order` class.</span></span> <span data-ttu-id="19abd-120">(Это добавление не является обязательным, поскольку для создания связи достаточно создать определение связи в любом направлении.</span><span class="sxs-lookup"><span data-stu-id="19abd-120">(This addition is not strictly necessary, because defining the relationship in either direction is sufficient to create the link.</span></span> <span data-ttu-id="19abd-121">Однако добавление этого примечания позволит с легкостью переходить по объектам в любом направлении.)</span><span class="sxs-lookup"><span data-stu-id="19abd-121">But adding this annotation does enable you to easily navigate objects in either direction.)</span></span>  
  
#### <a name="to-annotate-the-customer-class"></a><span data-ttu-id="19abd-122">Добавление примечаний к классу "Customer"</span><span class="sxs-lookup"><span data-stu-id="19abd-122">To annotate the Customer class</span></span>  
  
- <span data-ttu-id="19abd-123">Введите или вставьте следующий код в класс `Customer`.</span><span class="sxs-lookup"><span data-stu-id="19abd-123">Type or paste the following code into the `Customer` class:</span></span>  
  
     [!code-vb[DLinqWalk2VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a><span data-ttu-id="19abd-124">Создание и выполнение запроса в рамках связи "Customer-Order"</span><span class="sxs-lookup"><span data-stu-id="19abd-124">Creating and Running a Query across the Customer-Order Relationship</span></span>  

 <span data-ttu-id="19abd-125">Теперь можно получить доступ к объектам `Order` непосредственно из объектов `Customer` или в обратном направлении.</span><span class="sxs-lookup"><span data-stu-id="19abd-125">You can now access `Order` objects directly from the `Customer` objects, or in the opposite order.</span></span> <span data-ttu-id="19abd-126">Явное *соединение* между клиентами и заказами не требуется.</span><span class="sxs-lookup"><span data-stu-id="19abd-126">You do not need an explicit *join* between customers and orders.</span></span>  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a><span data-ttu-id="19abd-127">Получение доступа к объектам "Order" с помощью объектов "Customer"</span><span class="sxs-lookup"><span data-stu-id="19abd-127">To access Order objects by using Customer objects</span></span>  
  
1. <span data-ttu-id="19abd-128">Измените метод `Sub Main` посредством ввода или вставки в метод следующего кода:</span><span class="sxs-lookup"><span data-stu-id="19abd-128">Modify the `Sub Main` method by typing or pasting the following code into the method:</span></span>  
  
     [!code-vb[DLinqWalk2VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#3)]  
  
2. <span data-ttu-id="19abd-129">Нажмите клавишу F5, чтобы начать отладку приложения.</span><span class="sxs-lookup"><span data-stu-id="19abd-129">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="19abd-130">В окне сообщения отобразятся два имени, и в окне "Консоль" появится созданный код SQL.</span><span class="sxs-lookup"><span data-stu-id="19abd-130">Two names appear in the message box, and the Console window shows the generated SQL code.</span></span>  
  
3. <span data-ttu-id="19abd-131">Закройте окно сообщения, чтобы остановить отладку.</span><span class="sxs-lookup"><span data-stu-id="19abd-131">Close the message box to stop debugging.</span></span>  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a><span data-ttu-id="19abd-132">Создание строго типизированного представления базы данных</span><span class="sxs-lookup"><span data-stu-id="19abd-132">Creating a Strongly Typed View of Your Database</span></span>  

 <span data-ttu-id="19abd-133">Общая процедура становится гораздо проще, если в начале использовать строго типизированное представление базы данных.</span><span class="sxs-lookup"><span data-stu-id="19abd-133">It is much easier to start with a strongly typed view of your database.</span></span> <span data-ttu-id="19abd-134">Задавая строгую типизацию объекта <xref:System.Data.Linq.DataContext>, можно избежать вызовов метода <xref:System.Data.Linq.DataContext.GetTable%2A>.</span><span class="sxs-lookup"><span data-stu-id="19abd-134">By strongly typing the <xref:System.Data.Linq.DataContext> object, you do not need calls to <xref:System.Data.Linq.DataContext.GetTable%2A>.</span></span> <span data-ttu-id="19abd-135">Строго типизированные таблицы можно использовать в запросах только при использовании строго типизированного объекта <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="19abd-135">You can use strongly typed tables in all your queries when you use the strongly typed <xref:System.Data.Linq.DataContext> object.</span></span>  
  
 <span data-ttu-id="19abd-136">В представленных ниже шагах создается объект `Customers` в качестве строго типизированной таблицы, которая сопоставляется с таблицей "Customers" в базе данных.</span><span class="sxs-lookup"><span data-stu-id="19abd-136">In the following steps, you will create `Customers` as a strongly typed table that maps to the Customers table in the database.</span></span>  
  
#### <a name="to-strongly-type-the-datacontext-object"></a><span data-ttu-id="19abd-137">Установка строгой типизации объекта "DataContext"</span><span class="sxs-lookup"><span data-stu-id="19abd-137">To strongly type the DataContext object</span></span>  
  
1. <span data-ttu-id="19abd-138">Добавьте следующий код непосредственно перед объявлением класса `Customer`.</span><span class="sxs-lookup"><span data-stu-id="19abd-138">Add the following code above the `Customer` class declaration.</span></span>  
  
     [!code-vb[DLinqWalk2VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#4)]  
  
2. <span data-ttu-id="19abd-139">Измените метод `Sub Main`, чтобы использовать строго типизированный объект <xref:System.Data.Linq.DataContext>, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="19abd-139">Modify `Sub Main` to use the strongly typed <xref:System.Data.Linq.DataContext> as follows:</span></span>  
  
     [!code-vb[DLinqWalk2VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#5)]  
  
3. <span data-ttu-id="19abd-140">Нажмите клавишу F5, чтобы начать отладку приложения.</span><span class="sxs-lookup"><span data-stu-id="19abd-140">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="19abd-141">В окне «Консоль"» отобразится следующее.</span><span class="sxs-lookup"><span data-stu-id="19abd-141">The Console window output is:</span></span>  
  
     `ID=WHITC`  
  
4. <span data-ttu-id="19abd-142">Чтобы закрыть приложение, в окне "Консоль" нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="19abd-142">Press Enter in the Console window to close the application.</span></span>  
  
5. <span data-ttu-id="19abd-143">Чтобы сохранить это приложение, в меню **файл** выберите команду **сохранить все** .</span><span class="sxs-lookup"><span data-stu-id="19abd-143">On the **File** menu, click **Save All** if you want to save this application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="19abd-144">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="19abd-144">Next Steps</span></span>  

 <span data-ttu-id="19abd-145">В следующем пошаговом руководстве ([Пошаговое руководство. Управление данными (Visual Basic)](walkthrough-manipulating-data-visual-basic.md)) демонстрируется управление данными.</span><span class="sxs-lookup"><span data-stu-id="19abd-145">The next walkthrough ([Walkthrough: Manipulating Data (Visual Basic)](walkthrough-manipulating-data-visual-basic.md)) demonstrates how to manipulate data.</span></span> <span data-ttu-id="19abd-146">Для этого пошагового руководства не требуется сохранять два пошаговых руководства, которые уже выполнены в этой серии.</span><span class="sxs-lookup"><span data-stu-id="19abd-146">That walkthrough does not require that you save the two walkthroughs in this series that you have already completed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19abd-147">См. также</span><span class="sxs-lookup"><span data-stu-id="19abd-147">See also</span></span>

- [<span data-ttu-id="19abd-148">Обучение с использованием пошаговых руководств</span><span class="sxs-lookup"><span data-stu-id="19abd-148">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
