---
description: Дополнительные сведения о пространствах имен (Entity SQL)
title: Пространства имен (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
ms.openlocfilehash: 70ef0021c3015fd661b42becb5371dcfd958f20f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696559"
---
# <a name="namespaces-entity-sql"></a><span data-ttu-id="af49d-103">Пространства имен (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="af49d-103">Namespaces (Entity SQL)</span></span>

<span data-ttu-id="af49d-104">В [!INCLUDE[esql](../../../../../../includes/esql-md.md)] были введены пространства имен, чтобы избежать возникновения конфликтов с именами глобальных идентификаторов, например именами типов, наборов сущностей, функций и т. д.</span><span class="sxs-lookup"><span data-stu-id="af49d-104">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] introduces namespaces to avoid name conflicts for global identifiers such as type names, entity sets, functions, and so on.</span></span> <span data-ttu-id="af49d-105">Поддержка пространства имен в [!INCLUDE[esql](../../../../../../includes/esql-md.md)] аналогична поддержке пространства имен в платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="af49d-105">The namespace support in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is similar to the namespace support in the .NET Framework.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="af49d-106">предоставляет две формы предложения USING: полные пространства имен (для пространства имен предоставляется короткий псевдоним) и неполные пространства имен, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="af49d-106">provides two forms of the USING clause: qualified namespaces (where a shorter alias is provided for the namespace), and unqualified namespaces, as illustrated in the following example:</span></span>  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a><span data-ttu-id="af49d-107">Правила разрешения имен</span><span class="sxs-lookup"><span data-stu-id="af49d-107">Name Resolution Rules</span></span>  

 <span data-ttu-id="af49d-108">Если идентификатор не может быть разрешен в локальных областях, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] пытается определить имя в глобальных областях (пространства имен).</span><span class="sxs-lookup"><span data-stu-id="af49d-108">If an identifier cannot be resolved in the local scopes, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to locate the name in the global scopes (the namespaces).</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="af49d-109">вначале пытается сопоставить идентификатор (префикс) с одним из полных пространств имен.</span><span class="sxs-lookup"><span data-stu-id="af49d-109">first tries to match the identifier (prefix) with one of the qualified namespaces.</span></span> <span data-ttu-id="af49d-110">При наличии совпадения [!INCLUDE[esql](../../../../../../includes/esql-md.md)] пытается разрешить оставшуюся часть идентификатора в указанном пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="af49d-110">If there is a match, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to resolve the rest of the identifier in the specified namespace.</span></span> <span data-ttu-id="af49d-111">Если совпадение не найдено, вызывается исключение.</span><span class="sxs-lookup"><span data-stu-id="af49d-111">If no match is found, an exception is thrown.</span></span>  
  
 <span data-ttu-id="af49d-112">Затем [!INCLUDE[esql](../../../../../../includes/esql-md.md)] пытается выполнить поиск идентификатора в всех неполных пространствах имен (указанных в прологе).</span><span class="sxs-lookup"><span data-stu-id="af49d-112">Next, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to search all unqualified namespaces (specified in the prolog) for the identifier.</span></span> <span data-ttu-id="af49d-113">Если идентификатор удается найти только в одном пространстве имен, возвращается расположение.</span><span class="sxs-lookup"><span data-stu-id="af49d-113">If the identifier can be located in exactly one namespace, that location is returned.</span></span> <span data-ttu-id="af49d-114">Если для идентификатора обнаружены совпадения в нескольких пространствах имен, вызывается исключение.</span><span class="sxs-lookup"><span data-stu-id="af49d-114">If more than one namespace has a match for that identifier, an exception is thrown.</span></span> <span data-ttu-id="af49d-115">Если для идентификатора не может быть определено пространство имен, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] передает имя в следующую внешную область ( <xref:System.Data.Common.DbCommand> объект или <xref:System.Data.Common.DbConnection> ), как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="af49d-115">If no namespace can be identified for the identifier, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] passes the name onto the next outward scope (the <xref:System.Data.Common.DbCommand> or <xref:System.Data.Common.DbConnection> object), as illustrated in the following example:</span></span>  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a><span data-ttu-id="af49d-116">Отличия от платформы .NET Framework</span><span class="sxs-lookup"><span data-stu-id="af49d-116">Differences from the .NET Framework</span></span>  

 <span data-ttu-id="af49d-117">В платформа .NET Framework можно использовать частично определенные пространства имен.</span><span class="sxs-lookup"><span data-stu-id="af49d-117">In the .NET Framework, you can use partially qualified namespaces.</span></span> <span data-ttu-id="af49d-118">В [!INCLUDE[esql](../../../../../../includes/esql-md.md)] это недопустимо.</span><span class="sxs-lookup"><span data-stu-id="af49d-118">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not allow this.</span></span>  
  
## <a name="adonet-usage"></a><span data-ttu-id="af49d-119">Использование ADO.NET</span><span class="sxs-lookup"><span data-stu-id="af49d-119">ADO.NET Usage</span></span>  

 <span data-ttu-id="af49d-120">Запросы выражаются посредством объектов <xref:System.Data.Common.DbCommand> ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="af49d-120">Queries are expressed through ADO.NET <xref:System.Data.Common.DbCommand> objects.</span></span> <span data-ttu-id="af49d-121">Объекты <xref:System.Data.Common.DbCommand> могут быть построены на основе объектов <xref:System.Data.Common.DbConnection>.</span><span class="sxs-lookup"><span data-stu-id="af49d-121"><xref:System.Data.Common.DbCommand> objects can be built over <xref:System.Data.Common.DbConnection> objects.</span></span> <span data-ttu-id="af49d-122">Пространства имен также могут быть указаны как часть объектов <xref:System.Data.Common.DbCommand> и <xref:System.Data.Common.DbConnection>.</span><span class="sxs-lookup"><span data-stu-id="af49d-122">Namespaces can also be specified as part of the <xref:System.Data.Common.DbCommand> and <xref:System.Data.Common.DbConnection> objects.</span></span> <span data-ttu-id="af49d-123">Если [!INCLUDE[esql](../../../../../../includes/esql-md.md)] не может разрешить идентификатор внутри самого запроса, внешние пространства имен проходят проверку (на основе аналогичных правил).</span><span class="sxs-lookup"><span data-stu-id="af49d-123">If [!INCLUDE[esql](../../../../../../includes/esql-md.md)] cannot resolve an identifier within the query itself, the external namespaces are probed (based on similar rules).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af49d-124">См. также</span><span class="sxs-lookup"><span data-stu-id="af49d-124">See also</span></span>

- [<span data-ttu-id="af49d-125">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="af49d-125">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="af49d-126">Общие сведения об Entity SQL</span><span class="sxs-lookup"><span data-stu-id="af49d-126">Entity SQL Overview</span></span>](entity-sql-overview.md)
