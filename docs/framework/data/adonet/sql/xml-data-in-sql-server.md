---
description: 'Дополнительные сведения: XML-данные в SQL Server'
title: Данные XML в SQL Server
ms.date: 03/30/2017
ms.assetid: 9849d319-f518-4e3d-a7cd-f8fdcaaa1d4d
ms.openlocfilehash: fb087aeb0893ce9de9c5beb7728ff1af3259d3e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766937"
---
# <a name="xml-data-in-sql-server"></a><span data-ttu-id="fd0ad-103">Данные XML в SQL Server</span><span class="sxs-lookup"><span data-stu-id="fd0ad-103">XML Data in SQL Server</span></span>

<span data-ttu-id="fd0ad-104">SQL Server предоставляет возможности SQLXML внутри платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fd0ad-104">SQL Server exposes the functionality of SQLXML inside the .NET Framework.</span></span> <span data-ttu-id="fd0ad-105">Разработчики могут писать приложения, которые обращаются к XML-данным в экземпляре SQL Server, переводят данные в среду .NET Framework, обрабатывают данные и отправляют обновления назад в SQL Server.</span><span class="sxs-lookup"><span data-stu-id="fd0ad-105">Developers can write applications that access XML data from an instance of SQL Server, bring the data into the .NET Framework environment, process the data, and send the updates back to SQL Server.</span></span> <span data-ttu-id="fd0ad-106">Есть несколько вариантов использования XML-данных в SQL Server, включая хранение данных, а также использование в качестве значений параметров для извлечения данных.</span><span class="sxs-lookup"><span data-stu-id="fd0ad-106">XML data can be used in several ways in SQL Server, including data storage, and as parameter values for retrieving data.</span></span> <span data-ttu-id="fd0ad-107">Класс **SQLXML** в платформа .NET Framework предоставляет поддержку на стороне клиента для работы с данными, ХРАНЯЩИМИСЯ в XML-столбце в SQL Server.</span><span class="sxs-lookup"><span data-stu-id="fd0ad-107">The **SqlXml** class in the .NET Framework provides the client-side support for working with data stored in an XML column within SQL Server.</span></span> <span data-ttu-id="fd0ad-108">Дополнительные сведения см. в разделе "Управляемые классы SQLXML" электронной документации на SQL Server.</span><span class="sxs-lookup"><span data-stu-id="fd0ad-108">For more information, see "SQLXML Managed Classes" in SQL Server Books Online.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fd0ad-109">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="fd0ad-109">In This Section</span></span>  

 [<span data-ttu-id="fd0ad-110">Значения столбца SQL XML</span><span class="sxs-lookup"><span data-stu-id="fd0ad-110">SQL XML Column Values</span></span>](sql-xml-column-values.md)  
 <span data-ttu-id="fd0ad-111">Демонстрация получения и работы с XML-данными, полученными из SQL Server.</span><span class="sxs-lookup"><span data-stu-id="fd0ad-111">Demonstrates how to retrieve and work with XML data retrieved from SQL Server.</span></span>  
  
 [<span data-ttu-id="fd0ad-112">Указание значений XML в качестве параметров</span><span class="sxs-lookup"><span data-stu-id="fd0ad-112">Specifying XML Values as Parameters</span></span>](specifying-xml-values-as-parameters.md)  
 <span data-ttu-id="fd0ad-113">Демонстрирует передачу XML-данных в качестве параметра в команду.</span><span class="sxs-lookup"><span data-stu-id="fd0ad-113">Demonstrates how to pass XML data as a parameter to a command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd0ad-114">См. также</span><span class="sxs-lookup"><span data-stu-id="fd0ad-114">See also</span></span>

- [<span data-ttu-id="fd0ad-115">SQL Server и ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fd0ad-115">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="fd0ad-116">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fd0ad-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
