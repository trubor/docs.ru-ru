---
description: 'Дополнительные сведения: кэширование плана запроса (Entity SQL)'
title: Кэширование плана запроса (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: eee8e3afcd6f97b7e6021389d59a8ce03507fb9f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802103"
---
# <a name="query-plan-caching-entity-sql"></a><span data-ttu-id="cb0d0-103">Кэширование плана запроса (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="cb0d0-103">Query Plan Caching (Entity SQL)</span></span>

<span data-ttu-id="cb0d0-104">При каждой попытке выполнения запроса конвейер запросов обращается в кэш планов запросов, чтобы определить, что конкретный запрос уже скомпилирован и доступен.</span><span class="sxs-lookup"><span data-stu-id="cb0d0-104">Whenever an attempt to execute a query is made, the query pipeline looks up its query plan cache to see whether the exact query is already compiled and available.</span></span> <span data-ttu-id="cb0d0-105">Если это так, то кэшированный план используется повторно вместо построения нового плана.</span><span class="sxs-lookup"><span data-stu-id="cb0d0-105">If so, it reuses the cached plan rather than building a new one.</span></span> <span data-ttu-id="cb0d0-106">Если совпадение в кэше планов запросов не обнаружено, запрос компилируется и кэшируется.</span><span class="sxs-lookup"><span data-stu-id="cb0d0-106">If a match is not found in the query plan cache, the query is compiled and cached.</span></span> <span data-ttu-id="cb0d0-107">Запрос идентифицируется его текстом [!INCLUDE[esql](../../../../../../includes/esql-md.md)] и коллекцией параметров (имен и типов).</span><span class="sxs-lookup"><span data-stu-id="cb0d0-107">A query is identified by its [!INCLUDE[esql](../../../../../../includes/esql-md.md)] text and parameter collection (names and types).</span></span> <span data-ttu-id="cb0d0-108">Все текстовые сравнения выполняются с учетом регистра.</span><span class="sxs-lookup"><span data-stu-id="cb0d0-108">All text comparisons are case-sensitive.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="cb0d0-109">Конфигурация</span><span class="sxs-lookup"><span data-stu-id="cb0d0-109">Configuration</span></span>  

 <span data-ttu-id="cb0d0-110">Кэширование планов запросов можно настроить с помощью <xref:System.Data.EntityClient.EntityCommand>.</span><span class="sxs-lookup"><span data-stu-id="cb0d0-110">Query plan caching is configurable through the <xref:System.Data.EntityClient.EntityCommand>.</span></span>  
  
 <span data-ttu-id="cb0d0-111">Чтобы включить или выключить кэширование планов запросов с помощью свойства <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, назначьте этому свойству значение `true` или `false`.</span><span class="sxs-lookup"><span data-stu-id="cb0d0-111">To enable or disable query plan caching through <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, set this property to `true` or `false`.</span></span> <span data-ttu-id="cb0d0-112">Отключение кэширования планов для отдельных динамических запросов, которые вряд ли будут использованы повторно, повышает производительность.</span><span class="sxs-lookup"><span data-stu-id="cb0d0-112">Disabling plan caching for individual dynamic queries that are unlikely to be used more then once improves performance.</span></span>  
  
 <span data-ttu-id="cb0d0-113">Можно включить кэширование планов запросов с помощью <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span><span class="sxs-lookup"><span data-stu-id="cb0d0-113">You can enable query plan caching through <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span></span>  
  
## <a name="recommended-practice"></a><span data-ttu-id="cb0d0-114">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="cb0d0-114">Recommended Practice</span></span>  

 <span data-ttu-id="cb0d0-115">Как правило, следует избегать динамических запросов.</span><span class="sxs-lookup"><span data-stu-id="cb0d0-115">Dynamic queries should be avoided, in general.</span></span> <span data-ttu-id="cb0d0-116">Динамический запрос в следующем примере уязвим для атак путем внедрения кода SQL, так как входные данные пользователя принимаются напрямую без проверки.</span><span class="sxs-lookup"><span data-stu-id="cb0d0-116">The following dynamic query example is vulnerable to SQL injection attacks, because it takes user input directly without any validation.</span></span>  
  
 ```csharp
 var query = "SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;  
 ```

 <span data-ttu-id="cb0d0-117">Если используются динамически формируемые запросы, подумайте об отключении кэширования плана запроса, чтобы избежать ненужного расходования памяти для записей кэша, которые вряд ли будут использоваться повторно.</span><span class="sxs-lookup"><span data-stu-id="cb0d0-117">If you do use dynamically generated queries, consider disabling query plan caching to avoid unnecessary memory consumption for cache entries that are unlikely to be reused.</span></span>  
  
 <span data-ttu-id="cb0d0-118">Кэширование планов запросов для статических запросов и параметризованных запросов может увеличить производительность.</span><span class="sxs-lookup"><span data-stu-id="cb0d0-118">Query plan caching on static queries and parameterized queries can provide performance benefits.</span></span> <span data-ttu-id="cb0d0-119">Ниже приводится пример статического запроса:</span><span class="sxs-lookup"><span data-stu-id="cb0d0-119">The following is an example of a static query:</span></span>  
  
```csharp
var query = "SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 <span data-ttu-id="cb0d0-120">Для правильного сопоставления запросов кэшу планов запросов они должны соответствовать следующим требованиям.</span><span class="sxs-lookup"><span data-stu-id="cb0d0-120">For queries to be matched properly by the query plan cache, they should comply with the following requirements:</span></span>  
  
- <span data-ttu-id="cb0d0-121">Текст запроса должен быть постоянным шаблоном, предпочтительно постоянной строкой или ресурсом.</span><span class="sxs-lookup"><span data-stu-id="cb0d0-121">Query text should be a constant pattern, preferably a constant string or a resource.</span></span>  
  
- <span data-ttu-id="cb0d0-122">Экземпляр <xref:System.Data.EntityClient.EntityParameter> или <xref:System.Data.Objects.ObjectParameter> должен быть использован всегда, когда нужно передать введенное пользователем значение.</span><span class="sxs-lookup"><span data-stu-id="cb0d0-122"><xref:System.Data.EntityClient.EntityParameter> or <xref:System.Data.Objects.ObjectParameter> should be used wherever a user-supplied value must be passed.</span></span>  
  
 <span data-ttu-id="cb0d0-123">Необходимо избегать следующих шаблонов запросов, которые напрасно занимают слоты в кэше планов запросов.</span><span class="sxs-lookup"><span data-stu-id="cb0d0-123">You should avoid the following query patterns, which unnecessarily consume slots in the query plan cache:</span></span>  
  
- <span data-ttu-id="cb0d0-124">Изменение регистра символов в тексте.</span><span class="sxs-lookup"><span data-stu-id="cb0d0-124">Changes to letter case in the text.</span></span>  
  
- <span data-ttu-id="cb0d0-125">Изменение пробельных символов.</span><span class="sxs-lookup"><span data-stu-id="cb0d0-125">Changes to white space.</span></span>  
  
- <span data-ttu-id="cb0d0-126">Изменение литеральных значений.</span><span class="sxs-lookup"><span data-stu-id="cb0d0-126">Changes to literal values.</span></span>  
  
- <span data-ttu-id="cb0d0-127">Изменение текста внутри комментариев.</span><span class="sxs-lookup"><span data-stu-id="cb0d0-127">Changes to text inside comments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb0d0-128">См. также</span><span class="sxs-lookup"><span data-stu-id="cb0d0-128">See also</span></span>

- [<span data-ttu-id="cb0d0-129">Общие сведения об Entity SQL</span><span class="sxs-lookup"><span data-stu-id="cb0d0-129">Entity SQL Overview</span></span>](entity-sql-overview.md)
