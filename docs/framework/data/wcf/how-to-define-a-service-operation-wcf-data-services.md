---
description: Дополнительные сведения см. в статье как определить операцию службы (службы данных WCF).
title: Практическое руководство. Определение операции службы (службы данных WCF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Service Operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: dfcd3cb1-2f07-4d0b-b16a-6b056c4f45fa
ms.openlocfilehash: 9fcad3a31ea5b439c248ba103cbf4ddd75b8109a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765624"
---
# <a name="how-to-define-a-service-operation-wcf-data-services"></a><span data-ttu-id="29792-103">Практическое руководство. Определение операции службы (службы данных WCF)</span><span class="sxs-lookup"><span data-stu-id="29792-103">How to: Define a Service Operation (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="29792-104">Службы данных WCF предоставить методы, определенные на сервере как операции службы.</span><span class="sxs-lookup"><span data-stu-id="29792-104">WCF Data Services expose methods that are defined on the server as service operations.</span></span> <span data-ttu-id="29792-105">Операции службы позволяют службе данных предоставить доступ через URI к методу, определенному на сервере.</span><span class="sxs-lookup"><span data-stu-id="29792-105">Service operations allow a data service to provide access through a URI to a method that is defined on the server.</span></span> <span data-ttu-id="29792-106">Чтобы определить операцию службы, примените `WebGet]` `[WebInvoke]` к методу атрибут [или.</span><span class="sxs-lookup"><span data-stu-id="29792-106">To define a service operation, apply the [`WebGet]` or `[WebInvoke]` attribute to the method.</span></span> <span data-ttu-id="29792-107">Для поддержки операторов запросов операция службы должна возвращать <xref:System.Linq.IQueryable%601> экземпляр.</span><span class="sxs-lookup"><span data-stu-id="29792-107">To support query operators, the service operation must return an <xref:System.Linq.IQueryable%601> instance.</span></span> <span data-ttu-id="29792-108">Операции службы могут обращаться к базовому источнику данных через свойство <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> объекта <xref:System.Data.Services.DataService%601>.</span><span class="sxs-lookup"><span data-stu-id="29792-108">Service operations may access the underlying data source through the <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> property on the <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="29792-109">Дополнительные сведения см. в разделе [операции службы](service-operations-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="29792-109">For more information, see [Service Operations](service-operations-wcf-data-services.md).</span></span>

<span data-ttu-id="29792-110">Пример в этом разделе определяет операцию службы с именем `GetOrdersByCity`, возвращающую фильтрованный экземпляр <xref:System.Linq.IQueryable%601>`Orders` и связанные объекты `Order_Details`.</span><span class="sxs-lookup"><span data-stu-id="29792-110">The example in this topic defines a service operation named `GetOrdersByCity` that returns a filtered <xref:System.Linq.IQueryable%601> instance of `Orders` and related `Order_Details` objects.</span></span> <span data-ttu-id="29792-111">Пример обращается к экземпляру <xref:System.Data.Objects.ObjectContext>, являющемуся источником данных для образца службы данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="29792-111">The example accesses the <xref:System.Data.Objects.ObjectContext> instance that is the data source for the Northwind sample data service.</span></span> <span data-ttu-id="29792-112">Эта служба создается при завершении [краткого руководства по службы данных WCF](quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="29792-112">This service is created when you complete the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>

### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a><span data-ttu-id="29792-113">Определение операции службы в службе данных Northwind</span><span class="sxs-lookup"><span data-stu-id="29792-113">To define a service operation in the Northwind data service</span></span>

1. <span data-ttu-id="29792-114">Откройте в проекте службы данных Northwind файл Northwind.svc.</span><span class="sxs-lookup"><span data-stu-id="29792-114">In the Northwind data service project, open the Northwind.svc file.</span></span>

2. <span data-ttu-id="29792-115">Определите в классе `Northwind` метод операции службы с именем `GetOrdersByCity`, как показано дальше:</span><span class="sxs-lookup"><span data-stu-id="29792-115">In the `Northwind` class, define a service operation method named `GetOrdersByCity` as follows:</span></span>

     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationdef)]

3. <span data-ttu-id="29792-116">Добавьте в метод `InitializeService` класса `Northwind` следующий код, разрешающий доступ к операции службы:</span><span class="sxs-lookup"><span data-stu-id="29792-116">In the `InitializeService` method of the `Northwind` class, add the following code to enable access to the service operation:</span></span>

     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationconfig)]

### <a name="to-query-the-getordersbycity-service-operation"></a><span data-ttu-id="29792-117">Запрос к операции службы GetOrdersByCity</span><span class="sxs-lookup"><span data-stu-id="29792-117">To query the GetOrdersByCity service operation</span></span>

- <span data-ttu-id="29792-118">Введите в веб-браузере один из следующих URI для вызова операции службы, определенной в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="29792-118">In a Web browser, enter one of the following URIs to invoke the service operation that is defined in the following example:</span></span>

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`

## <a name="example"></a><span data-ttu-id="29792-119">Пример</span><span class="sxs-lookup"><span data-stu-id="29792-119">Example</span></span>

<span data-ttu-id="29792-120">В следующем примере реализована операция службы с именем `GetOrderByCity` в службе данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="29792-120">The following example implements a service operation named `GetOrderByCity` on the Northwind data service.</span></span> <span data-ttu-id="29792-121">Эта операция использует ADO.NET Entity Framework для возвращения набора сущностей `Orders` и связанных объектов `Order_Details` в виде экземпляра <xref:System.Linq.IQueryable%601> на основе переданного названия города.</span><span class="sxs-lookup"><span data-stu-id="29792-121">This operation uses the ADO.NET Entity Framework to return a set of `Orders` and related `Order_Details` objects as an <xref:System.Linq.IQueryable%601> instance based on the provided city name.</span></span>

> [!NOTE]
> <span data-ttu-id="29792-122">Операторы запросов поддерживаются для этой конечной точки операции службы, потому что метод возвращает экземпляр <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="29792-122">Query operators are supported on this service operation endpoint because the method returns an <xref:System.Linq.IQueryable%601> instance.</span></span>

[!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperation)]
[!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperation)]

## <a name="see-also"></a><span data-ttu-id="29792-123">См. также</span><span class="sxs-lookup"><span data-stu-id="29792-123">See also</span></span>

- [<span data-ttu-id="29792-124">Определение служб данных WCF</span><span class="sxs-lookup"><span data-stu-id="29792-124">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
