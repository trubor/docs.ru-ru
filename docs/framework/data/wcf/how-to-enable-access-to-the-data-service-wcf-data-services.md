---
description: Дополнительные сведения см. в статье Включение доступа к службе данных (службы данных WCF).
title: Как включить доступ к службе данных (службы WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
ms.openlocfilehash: 42be9c4c31da7bbbfef07958deef685d52df597b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765429"
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a><span data-ttu-id="cd2e3-103">Как включить доступ к службе данных (службы WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="cd2e3-103">How to: Enable Access to the Data Service (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="cd2e3-104">В службы данных WCF необходимо явно предоставить доступ к ресурсам, предоставляемым службой данных.</span><span class="sxs-lookup"><span data-stu-id="cd2e3-104">In WCF Data Services, you must explicitly grant access to the resources that are exposed by a data service.</span></span> <span data-ttu-id="cd2e3-105">Это значит, что после создания новой службы данных все равно требуется явно предоставлять доступ к отдельным ресурсам в виде набора сущностей.</span><span class="sxs-lookup"><span data-stu-id="cd2e3-105">This means that after you create a new data service, you must still explicitly provide access to individual resources as entity sets.</span></span> <span data-ttu-id="cd2e3-106">В этом разделе показано, как включить доступ на чтение и запись к пяти наборам сущностей в службе данных Northwind, которая создается при завершении [краткого руководства](quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="cd2e3-106">This topic shows how to enable read and write access to five of the entity sets in the Northwind data service that is created when you complete the [quickstart](quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="cd2e3-107">Поскольку перечисление <xref:System.Data.Services.EntitySetRights> определяется с помощью <xref:System.FlagsAttribute>, для указания нескольких разрешений для одного набора сущностей или операции можно использовать логический оператор OR.</span><span class="sxs-lookup"><span data-stu-id="cd2e3-107">Because the <xref:System.Data.Services.EntitySetRights> enumeration is defined by using the <xref:System.FlagsAttribute>, you can use a logical OR operator to specify multiple permissions for a single entity set.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cd2e3-108">Любой клиент, имеющий доступ к приложению ASP.NET, имеет также доступ к ресурсам, предоставляемым службой данных.</span><span class="sxs-lookup"><span data-stu-id="cd2e3-108">Any client that can access the ASP.NET application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="cd2e3-109">Для предотвращения несанкционированного доступа к ресурсам производственной службы данных необходимо также установить защиту самого приложения.</span><span class="sxs-lookup"><span data-stu-id="cd2e3-109">In a production data service, to prevent unauthorized access to resources, you should also secure the application itself.</span></span> <span data-ttu-id="cd2e3-110">Дополнительные сведения см. в статье [Защита веб-сайтов ASP.NET](/previous-versions/aspnet/91f66yxt(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="cd2e3-110">For more information, see [Securing ASP.NET Web Sites](/previous-versions/aspnet/91f66yxt(v=vs.100)).</span></span>  
  
### <a name="to-enable-access-to-the-data-service"></a><span data-ttu-id="cd2e3-111">Включение доступа к службе данных</span><span class="sxs-lookup"><span data-stu-id="cd2e3-111">To enable access to the data service</span></span>  
  
- <span data-ttu-id="cd2e3-112">В коде службы данных замените код местозаполнителя в функции `InitializeService` следующим текстом:</span><span class="sxs-lookup"><span data-stu-id="cd2e3-112">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]  
  
     <span data-ttu-id="cd2e3-113">Это обеспечивает клиентам доступ для чтения и записи к наборам сущностей `Orders` и `Order_Details` и доступ только для чтения к наборам сущностей `Customers`.</span><span class="sxs-lookup"><span data-stu-id="cd2e3-113">This enables clients to have read and write access to the `Orders` and `Order_Details` entity sets and read-only access to the `Customers` entity sets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd2e3-114">См. также</span><span class="sxs-lookup"><span data-stu-id="cd2e3-114">See also</span></span>

- [<span data-ttu-id="cd2e3-115">Практическое руководство. Разработка службы данных WCF Data Service, работающей на IIS</span><span class="sxs-lookup"><span data-stu-id="cd2e3-115">How to: Develop a WCF Data Service Running on IIS</span></span>](how-to-develop-a-wcf-data-service-running-on-iis.md)
- [<span data-ttu-id="cd2e3-116">Настройка службы данных</span><span class="sxs-lookup"><span data-stu-id="cd2e3-116">Configuring the Data Service</span></span>](configuring-the-data-service-wcf-data-services.md)
