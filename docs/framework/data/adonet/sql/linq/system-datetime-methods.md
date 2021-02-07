---
description: Дополнительные сведения о методах System. DateTime
title: Методы System.DateTime
ms.date: 03/30/2017
ms.assetid: 4f80700c-e83f-4ab6-af0f-1c9a606e1133
ms.openlocfilehash: b4b732bf41be2a943610a26f5abc33d1bb080d2f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681387"
---
# <a name="systemdatetime-methods"></a><span data-ttu-id="d9f46-103">Методы System.DateTime</span><span class="sxs-lookup"><span data-stu-id="d9f46-103">System.DateTime Methods</span></span>

<span data-ttu-id="d9f46-104">Следующие методы, операторы и свойства с поддержкой LINQ to SQL доступны для использования в запросах LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="d9f46-104">The following LINQ to SQL-supported methods, operators, and properties are available to use in LINQ to SQL queries.</span></span> <span data-ttu-id="d9f46-105">Если метод, оператор или свойство не поддерживаются, LINQ to SQL не может преобразовать этот элемент для выполнения в SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d9f46-105">When a method, operator or property is unsupported, LINQ to SQL cannot translate the member for execution on the SQL Server.</span></span> <span data-ttu-id="d9f46-106">Эти элементы можно использовать в коде, но их значения необходимо вычислить перед преобразованием запроса в Transact-SQL или после получения результатов из базы данных.</span><span class="sxs-lookup"><span data-stu-id="d9f46-106">You may use these members in your code, however, they must be evaluated before the query is translated to Transact-SQL or after the results have been retrieved from the database.</span></span>  
  
## <a name="supported-systemdatetime-members"></a><span data-ttu-id="d9f46-107">Поддерживаемые элементы System.DateTime</span><span class="sxs-lookup"><span data-stu-id="d9f46-107">Supported System.DateTime Members</span></span>  

 <span data-ttu-id="d9f46-108">После сопоставления в модели объектов или во внешнем файле сопоставления LINQ to SQL позволяет использовать следующие элементы <xref:System.DateTime?displayProperty=nameWithType> в запросах LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="d9f46-108">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call the following <xref:System.DateTime?displayProperty=nameWithType> members inside LINQ to SQL queries.</span></span>  
  
|<span data-ttu-id="d9f46-109">Поддерживаемые методы <xref:System.DateTime></span><span class="sxs-lookup"><span data-stu-id="d9f46-109">Supported <xref:System.DateTime> Methods</span></span>|<span data-ttu-id="d9f46-110">Поддерживаемые операторы <xref:System.DateTime></span><span class="sxs-lookup"><span data-stu-id="d9f46-110">Supported <xref:System.DateTime> Operators</span></span>|<span data-ttu-id="d9f46-111">Поддерживаемые свойства <xref:System.DateTime></span><span class="sxs-lookup"><span data-stu-id="d9f46-111">Supported <xref:System.DateTime> Properties</span></span>|  
|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Add%2A>|<xref:System.DateTime.op_Addition%2A>|<xref:System.DateTime.Date%2A>|  
|<xref:System.DateTime.AddDays%2A>|<xref:System.DateTime.op_Equality%2A>|<xref:System.DateTime.Day%2A>|  
|<xref:System.DateTime.AddHours%2A>|<xref:System.DateTime.op_GreaterThan%2A>|<xref:System.DateTime.DayOfWeek%2A>|  
|<xref:System.DateTime.AddMilliseconds%2A>|<xref:System.DateTime.op_GreaterThanOrEqual%2A>|<xref:System.DateTime.DayOfYear%2A>|  
|<xref:System.DateTime.AddMinutes%2A>|<xref:System.DateTime.op_Inequality%2A>|<xref:System.DateTime.Hour%2A>|  
|<xref:System.DateTime.AddMonths%2A>|<xref:System.DateTime.op_LessThan%2A>|<xref:System.DateTime.Millisecond%2A>|  
|<xref:System.DateTime.AddSeconds%2A>|<xref:System.DateTime.op_LessThanOrEqual%2A>|<xref:System.DateTime.Minute%2A>|  
|<xref:System.DateTime.AddTicks%2A>|<xref:System.DateTime.op_Subtraction%2A>|<xref:System.DateTime.Month%2A>|  
|<xref:System.DateTime.AddYears%2A>||<xref:System.DateTime.Now%2A>|  
|<xref:System.DateTime.Compare%2A>||<xref:System.DateTime.Second%2A>|  
|<xref:System.DateTime.CompareTo%28System.DateTime%29>||<xref:System.DateTime.TimeOfDay%2A>|  
|<xref:System.DateTime.Equals%28System.DateTime%29>||<xref:System.DateTime.Today%2A>|  
|||<xref:System.DateTime.Year%2A>|  
  
## <a name="members-not-supported-by-linq-to-sql"></a><span data-ttu-id="d9f46-112">Элементы, не поддерживаемые в LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="d9f46-112">Members Not Supported by LINQ to SQL</span></span>  

 <span data-ttu-id="d9f46-113">Следующие элементы не поддерживаются в запросах LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="d9f46-113">The following members are not supported inside LINQ to SQL queries.</span></span>  
  
|||  
|-|-|  
|<xref:System.DateTime.IsDaylightSavingTime%2A>|<xref:System.DateTime.IsLeapYear%2A>|  
|<xref:System.DateTime.DaysInMonth%2A>|<xref:System.DateTime.ToBinary%2A>|  
|<xref:System.DateTime.ToFileTime%2A>|<xref:System.DateTime.ToFileTimeUtc%2A>|  
|<xref:System.DateTime.ToLongDateString%2A>|<xref:System.DateTime.ToLongTimeString%2A>|  
|<xref:System.DateTime.ToOADate%2A>|<xref:System.DateTime.ToShortDateString%2A>|  
|<xref:System.DateTime.ToShortTimeString%2A>|<xref:System.DateTime.ToUniversalTime%2A>|  
|<xref:System.DateTime.FromBinary%2A>|<xref:System.DateTime.UtcNow%2A>|  
|<xref:System.DateTime.FromFileTime%2A>|<xref:System.DateTime.FromFileTimeUtc%2A>|  
|<xref:System.DateTime.FromOADate%2A>|<xref:System.DateTime.GetDateTimeFormats%2A>|  
  
## <a name="method-translation-example"></a><span data-ttu-id="d9f46-114">Пример преобразования методов</span><span class="sxs-lookup"><span data-stu-id="d9f46-114">Method Translation Example</span></span>  

 <span data-ttu-id="d9f46-115">Все методы, поддерживаемые LINQ to SQL, преобразуются в Transact-SQL перед отправкой в SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d9f46-115">All methods supported by LINQ to SQL are translated to Transact-SQL before they are sent to   SQL Server.</span></span> <span data-ttu-id="d9f46-116">Например, рассмотрим следующий шаблон.</span><span class="sxs-lookup"><span data-stu-id="d9f46-116">For example, consider the following pattern.</span></span>  
  
 `(dateTime1 – dateTime2).{Days, Hours, Milliseconds, Minutes, Months, Seconds, Years}`  
  
 <span data-ttu-id="d9f46-117">Когда шаблон распознается, он преобразуется в прямой вызов функции SQL Server `DATEDIFF` следующим образом:</span><span class="sxs-lookup"><span data-stu-id="d9f46-117">When it is recognized, it is translated into a direct call to the SQL Server `DATEDIFF` function, as follows:</span></span>  
  
 `DATEDIFF({DatePart}, @dateTime1, @dateTime2)`  
  
## <a name="sqlmethods-date-and-time-methods"></a><span data-ttu-id="d9f46-118">Методы даты и времени класса SQLMethods</span><span class="sxs-lookup"><span data-stu-id="d9f46-118">SQLMethods Date and Time Methods</span></span>  

 <span data-ttu-id="d9f46-119">Помимо методов, содержащихся в структуре <xref:System.DateTime>, LINQ to SQL поддерживает методы для работы с датой и временем из класса <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType>, перечисленные в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="d9f46-119">In addition to the methods offered by the <xref:System.DateTime> structure, LINQ to SQL offers the methods listed in the following table from the <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> class for working with date and time.</span></span>  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="d9f46-120">См. также</span><span class="sxs-lookup"><span data-stu-id="d9f46-120">See also</span></span>

- [<span data-ttu-id="d9f46-121">Основные принципы запросов</span><span class="sxs-lookup"><span data-stu-id="d9f46-121">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="d9f46-122">Создание модели объектов</span><span class="sxs-lookup"><span data-stu-id="d9f46-122">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="d9f46-123">Сопоставление типов SQL-CLR</span><span class="sxs-lookup"><span data-stu-id="d9f46-123">SQL-CLR Type Mapping</span></span>](sql-clr-type-mapping.md)
- [<span data-ttu-id="d9f46-124">Типы данных и функции</span><span class="sxs-lookup"><span data-stu-id="d9f46-124">Data Types and Functions</span></span>](data-types-and-functions.md)
