---
description: 'Дополнительные сведения о: Дбпровидерфакториес'
title: DbProviderFactories
ms.date: 03/30/2017
ms.assetid: 2a8e2640-3a49-42a1-a3a9-b43026907ae1
ms.openlocfilehash: 735c78a846fc8df31a922acf90e587c6d96f4995
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651266"
---
# <a name="dbproviderfactories"></a><span data-ttu-id="063fb-103">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="063fb-103">DbProviderFactories</span></span>

<span data-ttu-id="063fb-104">Пространство имен <xref:System.Data.Common> предоставляет классы для создания экземпляров <xref:System.Data.Common.DbProviderFactory> для работы с конкретными источниками данных.</span><span class="sxs-lookup"><span data-stu-id="063fb-104">The <xref:System.Data.Common> namespace provides classes for creating <xref:System.Data.Common.DbProviderFactory> instances to work with specific data sources.</span></span> <span data-ttu-id="063fb-105">При создании экземпляра <xref:System.Data.Common.DbProviderFactory> и передаче ему сведений о поставщике данных фабрика `DbProviderFactory` может на их основе определить верный, строго типизированный объект соединения, который необходимо возвратить.</span><span class="sxs-lookup"><span data-stu-id="063fb-105">When you create a <xref:System.Data.Common.DbProviderFactory> instance and pass it information about the data provider, the `DbProviderFactory` can determine the correct, strongly typed connection object to return based on the information it has been provided.</span></span>  
  
 <span data-ttu-id="063fb-106">Начиная с версии 4 платформы .NET Framework, такие поставщики данных, как <xref:System.Data.Odbc>, <xref:System.Data.OleDb>, <xref:System.Data.SqlClient> и <xref:System.Data.OracleClient>, больше не перечисляются в файле machine.config, однако настраиваемые поставщики будут по-прежнему перечислены там.</span><span class="sxs-lookup"><span data-stu-id="063fb-106">Beginning in the .NET Framework version 4, data providers such as <xref:System.Data.Odbc>, <xref:System.Data.OleDb>, <xref:System.Data.SqlClient>, and <xref:System.Data.OracleClient> are no longer listed in machine.config file, but custom providers will continue to be listed there.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="063fb-107">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="063fb-107">In This Section</span></span>  

 [<span data-ttu-id="063fb-108">Общие сведения о модели фабрики</span><span class="sxs-lookup"><span data-stu-id="063fb-108">Factory Model Overview</span></span>](factory-model-overview.md)  
 <span data-ttu-id="063fb-109">Содержит общие сведения о шаблоне разработки и программном интерфейсе фабрики.</span><span class="sxs-lookup"><span data-stu-id="063fb-109">Provides an overview of the factory design pattern and programming interface.</span></span>  
  
 [<span data-ttu-id="063fb-110">Получение класса DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="063fb-110">Obtaining a DbProviderFactory</span></span>](obtaining-a-dbproviderfactory.md)  
 <span data-ttu-id="063fb-111">Показывает способ создания списка установленных поставщиков данных и соединения <xref:System.Data.Common.DbConnection> в фабрике `DbProviderFactory`.</span><span class="sxs-lookup"><span data-stu-id="063fb-111">Demonstrates how to list the installed data providers and create a <xref:System.Data.Common.DbConnection> from a `DbProviderFactory`.</span></span>  
  
 [<span data-ttu-id="063fb-112">DbConnection, DbCommand и DbException</span><span class="sxs-lookup"><span data-stu-id="063fb-112">DbConnection, DbCommand and DbException</span></span>](dbconnection-dbcommand-and-dbexception.md)  
 <span data-ttu-id="063fb-113">Показывает способ создания объектов <xref:System.Data.Common.DbCommand> и <xref:System.Data.Common.DbDataReader>, а также методы обработки ошибок с помощью исключения <xref:System.Data.Common.DbException>.</span><span class="sxs-lookup"><span data-stu-id="063fb-113">Demonstrates how to create a <xref:System.Data.Common.DbCommand> and <xref:System.Data.Common.DbDataReader>, and how to handle data errors using <xref:System.Data.Common.DbException>.</span></span>  
  
 [<span data-ttu-id="063fb-114">Изменение данных с помощью DbDataAdapter</span><span class="sxs-lookup"><span data-stu-id="063fb-114">Modifying Data with a DbDataAdapter</span></span>](modifying-data-with-a-dbdataadapter.md)  
 <span data-ttu-id="063fb-115">Показывает способ использования объектов <xref:System.Data.Common.DbCommandBuilder> совместно с <xref:System.Data.Common.DbDataAdapter> для получения и изменения данных.</span><span class="sxs-lookup"><span data-stu-id="063fb-115">Demonstrates how to use a <xref:System.Data.Common.DbCommandBuilder> with a <xref:System.Data.Common.DbDataAdapter> to retrieve and modify data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="063fb-116">См. также</span><span class="sxs-lookup"><span data-stu-id="063fb-116">See also</span></span>

- [<span data-ttu-id="063fb-117">Извлечение и изменение данных в ADO.NET</span><span class="sxs-lookup"><span data-stu-id="063fb-117">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="063fb-118">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="063fb-118">ADO.NET Overview</span></span>](ado-net-overview.md)
