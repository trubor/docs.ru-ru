---
description: 'Дополнительные сведения о: SqlClient для Entity Framework'
title: SqlClient для Entity Framework
ms.date: 03/30/2017
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
ms.openlocfilehash: eba5602c13f66d1ee4404bbc27035304e34c1cd0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673132"
---
# <a name="sqlclient-for-the-entity-framework"></a><span data-ttu-id="4bb6e-103">SqlClient для Entity Framework</span><span class="sxs-lookup"><span data-stu-id="4bb6e-103">SqlClient for the Entity Framework</span></span>

<span data-ttu-id="4bb6e-104">В этом разделе описан поставщик данных .NET Framework для SQL Server (SqlClient), который позволяет платформе Entity Framework работать с сервером Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4bb6e-104">This section describes the .NET Framework Data Provider for SQL Server (SqlClient), which enables the Entity Framework to work over Microsoft SQL Server.</span></span>  
  
## <a name="provider-schema-attribute"></a><span data-ttu-id="4bb6e-105">Атрибут Provider элемента Schema</span><span class="sxs-lookup"><span data-stu-id="4bb6e-105">Provider Schema Attribute</span></span>  

 <span data-ttu-id="4bb6e-106">`Provider` является атрибутом элемента `Schema` в языке SSDL.</span><span class="sxs-lookup"><span data-stu-id="4bb6e-106">`Provider` is an attribute of the `Schema` element in store schema definition language (SSDL).</span></span>  
  
 <span data-ttu-id="4bb6e-107">Для использования SqlClient нужно присвоить атрибуту `Provider` элемента `Schema` значение в виде строки «System.Data.SqlClient».</span><span class="sxs-lookup"><span data-stu-id="4bb6e-107">To use SqlClient, assign the string "System.Data.SqlClient" to the `Provider` attribute of the `Schema` element.</span></span>  
  
## <a name="providermanifesttoken-schema-attribute"></a><span data-ttu-id="4bb6e-108">Атрибут ProviderManifestToken элемента Schema</span><span class="sxs-lookup"><span data-stu-id="4bb6e-108">ProviderManifestToken Schema Attribute</span></span>  

 <span data-ttu-id="4bb6e-109">`ProviderManifestToken` - обязательный атрибут элемента `Schema` в SSDL.</span><span class="sxs-lookup"><span data-stu-id="4bb6e-109">`ProviderManifestToken` is a required attribute of the `Schema` element in SSDL.</span></span> <span data-ttu-id="4bb6e-110">Этот маркер используется для загрузки манифеста поставщика при автономном использовании.</span><span class="sxs-lookup"><span data-stu-id="4bb6e-110">This token is used to load the provider manifest for offline scenarios.</span></span> <span data-ttu-id="4bb6e-111">Дополнительные сведения об `ProviderManifestToken` атрибуте см. в разделе [элемент Schema (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).</span><span class="sxs-lookup"><span data-stu-id="4bb6e-111">For more information about `ProviderManifestToken` attribute, see [Schema Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#schema-element-ssdl).</span></span>  
  
 <span data-ttu-id="4bb6e-112">SqlClient можно использовать в качестве поставщика данных для разных версий SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4bb6e-112">SqlClient can be used as a data provider for different versions of SQL Server.</span></span> <span data-ttu-id="4bb6e-113">Эти версии имеют разные возможности.</span><span class="sxs-lookup"><span data-stu-id="4bb6e-113">These versions have different capabilities.</span></span> <span data-ttu-id="4bb6e-114">Например, SQL Server 2000 не поддерживает `varchar(max)` `nvarchar(max)` типы и, которые появились в SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="4bb6e-114">For example, SQL Server 2000 does not support `varchar(max)` and `nvarchar(max)` types that were introduced with SQL Server 2005.</span></span>  
  
 <span data-ttu-id="4bb6e-115">SqlClient формирует и принимает следующие маркеры манифеста поставщика для различных версий SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4bb6e-115">SqlClient produces and accepts the following provider manifest tokens for different versions of SQL Server.</span></span>  
  
|<span data-ttu-id="4bb6e-116">SQL Server 2000</span><span class="sxs-lookup"><span data-stu-id="4bb6e-116">SQL Server 2000</span></span>|<span data-ttu-id="4bb6e-117">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="4bb6e-117">SQL Server 2005</span></span>|<span data-ttu-id="4bb6e-118">SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="4bb6e-118">SQL Server 2008</span></span>|  
|-|-|-|  
|<span data-ttu-id="4bb6e-119">2000</span><span class="sxs-lookup"><span data-stu-id="4bb6e-119">2000</span></span>|<span data-ttu-id="4bb6e-120">2005</span><span class="sxs-lookup"><span data-stu-id="4bb6e-120">2005</span></span>|<span data-ttu-id="4bb6e-121">2008</span><span class="sxs-lookup"><span data-stu-id="4bb6e-121">2008</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="4bb6e-122">Начиная с Visual Studio 2010 [средства ADO.NET EDM](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) не поддерживают SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="4bb6e-122">Starting with Visual Studio 2010, the [ADO.NET Entity Data Model Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)) do not support SQL Server 2000.</span></span>  
  
## <a name="provider-namespace-name"></a><span data-ttu-id="4bb6e-123">Имя пространства имен поставщика</span><span class="sxs-lookup"><span data-stu-id="4bb6e-123">Provider Namespace Name</span></span>  

 <span data-ttu-id="4bb6e-124">Все поставщики должны указывать пространство имен.</span><span class="sxs-lookup"><span data-stu-id="4bb6e-124">All providers must specify a namespace.</span></span> <span data-ttu-id="4bb6e-125">Это свойство сообщает платформе Entity Framework о том, какой префикс используется поставщиком для конкретных конструкций, таких как типы или функции.</span><span class="sxs-lookup"><span data-stu-id="4bb6e-125">This property tells the Entity Framework which prefix is used by the provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="4bb6e-126">Пространством имен для манифестов поставщика SqlClient является `SqlServer`.</span><span class="sxs-lookup"><span data-stu-id="4bb6e-126">The namespace for SqlClient provider manifests is `SqlServer`.</span></span> <span data-ttu-id="4bb6e-127">Дополнительные сведения о пространствах имен см. в разделе [пространства имен](./language-reference/namespaces-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="4bb6e-127">For more information about namespaces, see [Namespaces](./language-reference/namespaces-entity-sql.md).</span></span>  
  
## <a name="types"></a><span data-ttu-id="4bb6e-128">Типы</span><span class="sxs-lookup"><span data-stu-id="4bb6e-128">Types</span></span>  

 <span data-ttu-id="4bb6e-129">Поставщик SqlClient для платформы Entity Framework предоставляет сведения о сопоставлении между типами концептуальной модели и типами SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4bb6e-129">The SqlClient provider for the Entity Framework provides mapping information between conceptual model types and SQL Server types.</span></span> <span data-ttu-id="4bb6e-130">Дополнительные сведения см. в разделе [SqlClient для Entity Framework](sqlclient-for-ef-types.md).</span><span class="sxs-lookup"><span data-stu-id="4bb6e-130">For more information, see [SqlClient for Entity FrameworkTypes](sqlclient-for-ef-types.md).</span></span>  
  
## <a name="functions"></a><span data-ttu-id="4bb6e-131">Функции</span><span class="sxs-lookup"><span data-stu-id="4bb6e-131">Functions</span></span>  

 <span data-ttu-id="4bb6e-132">Поставщик SqlClient для платформы Entity Framework определяет список функций, поддерживаемых поставщиком.</span><span class="sxs-lookup"><span data-stu-id="4bb6e-132">The SqlClient provider for the Entity Framework defines the list of functions supported by the provider.</span></span> <span data-ttu-id="4bb6e-133">Список поддерживаемых функций см. в разделе [SqlClient for Entity Framework functions](sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="4bb6e-133">For a list of the supported functions, see [SqlClient for Entity Framework Functions](sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4bb6e-134">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="4bb6e-134">In This Section</span></span>  

 [<span data-ttu-id="4bb6e-135">Функции SqlClient для Entity Framework</span><span class="sxs-lookup"><span data-stu-id="4bb6e-135">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)  
  
 [<span data-ttu-id="4bb6e-136">Типы SqlClient для Entity Framework</span><span class="sxs-lookup"><span data-stu-id="4bb6e-136">SqlClient for Entity FrameworkTypes</span></span>](sqlclient-for-ef-types.md)  
  
 [<span data-ttu-id="4bb6e-137">Известные проблемы SqlClient для Entity Framework</span><span class="sxs-lookup"><span data-stu-id="4bb6e-137">Known Issues in SqlClient for Entity Framework</span></span>](known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="4bb6e-138">См. также</span><span class="sxs-lookup"><span data-stu-id="4bb6e-138">See also</span></span>

- [<span data-ttu-id="4bb6e-139">Язык Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4bb6e-139">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
- [<span data-ttu-id="4bb6e-140">Справочник по языку</span><span class="sxs-lookup"><span data-stu-id="4bb6e-140">Language Reference</span></span>](./language-reference/index.md)
- [<span data-ttu-id="4bb6e-141">Известные проблемы в поставщике SqlClient для Entity Framework</span><span class="sxs-lookup"><span data-stu-id="4bb6e-141">Known Issues in SqlClient Provider for Entity Framework</span></span>](sqlclient-for-the-entity-framework.md)
