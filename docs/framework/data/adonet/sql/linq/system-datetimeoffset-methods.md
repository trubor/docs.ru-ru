---
description: Дополнительные сведения о методах System. DateTimeOffset
title: Методы System.DateTimeOffset
ms.date: 03/30/2017
ms.assetid: 25b3e5c0-7603-4a70-b3e5-2149e3da69a2
ms.openlocfilehash: 050c710d4a3f3db8112d0d108338c010345afdda
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681334"
---
# <a name="systemdatetimeoffset-methods"></a><span data-ttu-id="7fbaa-103">Методы System.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="7fbaa-103">System.DateTimeOffset Methods</span></span>

<span data-ttu-id="7fbaa-104">После их сопоставления в модели объектов или внешнем файле сопоставления LINQ to SQL позволяет использовать большинство методов, операторов и свойств <xref:System.DateTimeOffset?displayProperty=nameWithType> внутри запросов LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="7fbaa-104">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call most of the <xref:System.DateTimeOffset?displayProperty=nameWithType> methods, operators, and properties from within your LINQ to SQL queries.</span></span>  
  
 <span data-ttu-id="7fbaa-105">Не поддерживаются только те методы, которые унаследованы от <xref:System.Object?displayProperty=nameWithType> и не имеют смысла в контексте запросов LINQ to SQL, например `Finalize`, `GetHashCode`, `GetType` и `MemberwiseClone`.</span><span class="sxs-lookup"><span data-stu-id="7fbaa-105">The only methods not supported are those inherited from <xref:System.Object?displayProperty=nameWithType> that do not make sense in the context of LINQ to SQL queries, such as: `Finalize`, `GetHashCode`, `GetType`, and `MemberwiseClone`.</span></span> <span data-ttu-id="7fbaa-106">Эти методы не поддерживаются, поскольку LINQ to SQL не может перевести их для выполнения в SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7fbaa-106">These methods are not supported because LINQ to SQL cannot translate them for execution on the SQL Server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7fbaa-107">Для структуры среды CLR <xref:System.DateTimeOffset?displayProperty=nameWithType> и для обеспечения возможности ее сопоставления столбцу SQL `DATETIMEOFFSET` с помощью LINQ to SQL необходима платформа .NET Framework 3.5 с пакетом обновления 1 (SP1) или выше.</span><span class="sxs-lookup"><span data-stu-id="7fbaa-107">The common language runtime (CLR) <xref:System.DateTimeOffset?displayProperty=nameWithType> structure, and the ability to map it to a SQL `DATETIMEOFFSET` column with LINQ to SQL, requires the .NET Framework 3.5 SP1 or beyond.</span></span> <span data-ttu-id="7fbaa-108">Столбец SQL типа `DATETIMEOFFSET` доступен только в версиях Microsoft SQL Server 2008 и выше.</span><span class="sxs-lookup"><span data-stu-id="7fbaa-108">The SQL `DATETIMEOFFSET` column is only available in Microsoft SQL Server 2008 and beyond.</span></span>  
  
## <a name="sqlmethods-date-and-time-methods"></a><span data-ttu-id="7fbaa-109">Методы даты и времени класса SQLMethods</span><span class="sxs-lookup"><span data-stu-id="7fbaa-109">SQLMethods Date and Time Methods</span></span>  

 <span data-ttu-id="7fbaa-110">Помимо методов, содержащихся в структуре <xref:System.DateTimeOffset>, LINQ to SQL поддерживает методы для работы с датой и временем из класса <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType>, перечисленные в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="7fbaa-110">In addition to the methods offered by the <xref:System.DateTimeOffset> structure, LINQ to SQL offers the methods listed in the following table from the <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> class for working with date and time.</span></span>  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="7fbaa-111">См. также</span><span class="sxs-lookup"><span data-stu-id="7fbaa-111">See also</span></span>

- [<span data-ttu-id="7fbaa-112">Основные принципы запросов</span><span class="sxs-lookup"><span data-stu-id="7fbaa-112">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="7fbaa-113">Создание модели объектов</span><span class="sxs-lookup"><span data-stu-id="7fbaa-113">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="7fbaa-114">Сопоставление типов SQL-CLR</span><span class="sxs-lookup"><span data-stu-id="7fbaa-114">SQL-CLR Type Mapping</span></span>](sql-clr-type-mapping.md)
