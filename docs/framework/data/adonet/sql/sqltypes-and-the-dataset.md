---
description: 'Подробнее о: SqlTypes и наборе данных'
title: Типы SqlType и набор данных
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
ms.openlocfilehash: 088c1cdc65b3c79a77e0bf724b5550c001a40554
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767002"
---
# <a name="sqltypes-and-the-dataset"></a><span data-ttu-id="3dedc-103">Типы SqlType и набор данных</span><span class="sxs-lookup"><span data-stu-id="3dedc-103">SqlTypes and the DataSet</span></span>

<span data-ttu-id="3dedc-104">В ADO.NET 2.0 добавлена поддержка расширенных типов `DataSet` через пространство имен <xref:System.Data.SqlTypes>.</span><span class="sxs-lookup"><span data-stu-id="3dedc-104">ADO.NET 2.0 introduced enhanced type support for the `DataSet` through the  <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="3dedc-105">Типы в пространстве имен <xref:System.Data.SqlTypes> предназначены для предоставления типов данных с той же семантикой и точностью, которыми обладают типы данных в базе данных SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3dedc-105">The types in <xref:System.Data.SqlTypes> are designed to provide data types with the same semantics and precision as the data types in a SQL Server database.</span></span> <span data-ttu-id="3dedc-106">Каждый тип данных в пространстве имен <xref:System.Data.SqlTypes> имеет эквивалентный тип данных в SQL Server с аналогичным базовым представлением данных.</span><span class="sxs-lookup"><span data-stu-id="3dedc-106">Each data type in <xref:System.Data.SqlTypes> has an equivalent data type in SQL Server, with the same underlying data representation.</span></span>  
  
 <span data-ttu-id="3dedc-107">Использование <xref:System.Data.SqlTypes> непосредственно в <xref:System.Data.DataSet> дает несколько преимуществ при работе с типами данных SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3dedc-107">Using <xref:System.Data.SqlTypes> directly in a <xref:System.Data.DataSet> confers several benefits when working with SQL Server data types.</span></span> <span data-ttu-id="3dedc-108"><xref:System.Data.SqlTypes> поддерживает такую же семантику, как и собственные типы данных SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3dedc-108"><xref:System.Data.SqlTypes> supports the same semantics as SQL Server native data types.</span></span> <span data-ttu-id="3dedc-109">Указав любой из типов <xref:System.Data.SqlTypes> в определении <xref:System.Data.DataColumn>, вы исключите потерю точности от преобразования типов данных decimal или numeric в типы данных среды CLR.</span><span class="sxs-lookup"><span data-stu-id="3dedc-109">Specifying one of the <xref:System.Data.SqlTypes> in the definition of a <xref:System.Data.DataColumn> eliminates the loss of precision that can occur when converting decimal or numeric data types to one of the common language runtime (CLR) data types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3dedc-110">Пример</span><span class="sxs-lookup"><span data-stu-id="3dedc-110">Example</span></span>  

 <span data-ttu-id="3dedc-111">В следующем примере создается объект <xref:System.Data.DataTable> с явным определением типов данных <xref:System.Data.DataColumn> при помощи <xref:System.Data.SqlTypes>, а не типов CLR.</span><span class="sxs-lookup"><span data-stu-id="3dedc-111">The following example creates a <xref:System.Data.DataTable> object, explicitly defining the <xref:System.Data.DataColumn> data types by using <xref:System.Data.SqlTypes> instead of CLR types.</span></span> <span data-ttu-id="3dedc-112">Этот код заполняет таблицу <xref:System.Data.DataTable> данными из таблицы Sales.SalesOrderDetail базы данных AdventureWorks в SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3dedc-112">The code fills the <xref:System.Data.DataTable> with data from the Sales.SalesOrderDetail table in the AdventureWorks database in SQL Server.</span></span> <span data-ttu-id="3dedc-113">Выходные данные, отображаемые в окне консоли, содержат тип данных для каждого столбца и значения, полученные из SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3dedc-113">The output displayed in the console window shows the data type of each column, and the values retrieved from SQL Server.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3dedc-114">См. также</span><span class="sxs-lookup"><span data-stu-id="3dedc-114">See also</span></span>

- [<span data-ttu-id="3dedc-115">Сопоставления типов данных SQL Server</span><span class="sxs-lookup"><span data-stu-id="3dedc-115">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="3dedc-116">Настройка параметров и типы данных параметров</span><span class="sxs-lookup"><span data-stu-id="3dedc-116">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="3dedc-117">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3dedc-117">ADO.NET Overview</span></span>](../ado-net-overview.md)
