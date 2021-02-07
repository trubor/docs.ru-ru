---
description: 'Дополнительные сведения: перечисление экземпляров SQL Server (ADO.NET)'
title: Перечисление экземпляров SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
ms.openlocfilehash: dd52142a06d5c7203eb8a2a14d0e6fc48f1e2a27
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672313"
---
# <a name="enumerating-instances-of-sql-server-adonet"></a><span data-ttu-id="db447-103">Перечисление экземпляров SQL Server (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="db447-103">Enumerating Instances of SQL Server (ADO.NET)</span></span>

<span data-ttu-id="db447-104">SQL Server позволяет выполнять в приложениях поиск экземпляров SQL Server в используемой сети.</span><span class="sxs-lookup"><span data-stu-id="db447-104">SQL Server permits applications to find SQL Server instances within the current network.</span></span> <span data-ttu-id="db447-105">Класс <xref:System.Data.Sql.SqlDataSourceEnumerator> предоставляет эти сведения разработчику приложения, предоставляя <xref:System.Data.DataTable>, содержащий сведения обо всех видимых серверах.</span><span class="sxs-lookup"><span data-stu-id="db447-105">The <xref:System.Data.Sql.SqlDataSourceEnumerator> class exposes this information to the application developer, providing a <xref:System.Data.DataTable> containing information about all the visible servers.</span></span> <span data-ttu-id="db447-106">Эта возвращенная таблица содержит список экземпляров серверов, доступных в сети, который совпадает со списком, предоставляемым при попытке пользователя создать новое соединение, и дополняет раскрывающийся список, содержащий все доступные серверы, в диалоговом окне **Свойства соединения**.</span><span class="sxs-lookup"><span data-stu-id="db447-106">This returned table contains a list of server instances available on the network that matches the list provided when a user attempts to create a new connection, and expands the drop-down list containing all the available servers on the **Connection Properties** dialog box.</span></span> <span data-ttu-id="db447-107">Отображаемые результаты не всегда завершенные.</span><span class="sxs-lookup"><span data-stu-id="db447-107">The results displayed are not always complete.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="db447-108">Как и в большинстве служб Windows, службу обозревателя SQL рекомендуется запускать с минимальными возможными привилегиями.</span><span class="sxs-lookup"><span data-stu-id="db447-108">As with most Windows services, it is best to run the SQL Browser service with the least possible privileges.</span></span> <span data-ttu-id="db447-109">Дополнительные сведения о службе браузера SQL и о том, как управлять ее работой, см. в электронной документации на SQL Server.</span><span class="sxs-lookup"><span data-stu-id="db447-109">See SQL Server Books Online for more information on the SQL Browser service, and how to manage its behavior.</span></span>  
  
## <a name="retrieving-an-enumerator-instance"></a><span data-ttu-id="db447-110">Получение экземпляра перечислителя</span><span class="sxs-lookup"><span data-stu-id="db447-110">Retrieving an Enumerator Instance</span></span>  

 <span data-ttu-id="db447-111">Чтобы получить таблицу с данными о доступных экземплярах SQL Server, вначале необходимо получить перечислитель с помощью общего и (или) статического свойства <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A>:</span><span class="sxs-lookup"><span data-stu-id="db447-111">In order to retrieve the table containing information about the available SQL Server instances, you must first retrieve an enumerator, using the shared/static <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> property:</span></span>  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 <span data-ttu-id="db447-112">После получения статического экземпляра можно вызвать метод <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A>, который возвращает <xref:System.Data.DataTable>, содержащий сведения о доступных серверах.</span><span class="sxs-lookup"><span data-stu-id="db447-112">Once you have retrieved the static instance, you can call the <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> method, which returns a <xref:System.Data.DataTable> containing information about the available servers:</span></span>  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 <span data-ttu-id="db447-113">Таблица, возвращенная из вызова метода, содержит следующие столбцы, которые содержат значения `string`:</span><span class="sxs-lookup"><span data-stu-id="db447-113">The table returned from the method call contains the following columns, all of which contain `string` values:</span></span>  
  
|<span data-ttu-id="db447-114">Столбец</span><span class="sxs-lookup"><span data-stu-id="db447-114">Column</span></span>|<span data-ttu-id="db447-115">Описание</span><span class="sxs-lookup"><span data-stu-id="db447-115">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="db447-116">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="db447-116">**ServerName**</span></span>|<span data-ttu-id="db447-117">Имя сервера.</span><span class="sxs-lookup"><span data-stu-id="db447-117">Name of the server.</span></span>|  
|<span data-ttu-id="db447-118">**InstanceName**</span><span class="sxs-lookup"><span data-stu-id="db447-118">**InstanceName**</span></span>|<span data-ttu-id="db447-119">Имя экземпляра сервера.</span><span class="sxs-lookup"><span data-stu-id="db447-119">Name of the server instance.</span></span> <span data-ttu-id="db447-120">Если сервер работает как экземпляр по умолчанию, то поле остается пустым.</span><span class="sxs-lookup"><span data-stu-id="db447-120">Blank if the server is running as the default instance.</span></span>|  
|<span data-ttu-id="db447-121">**IsClustered**</span><span class="sxs-lookup"><span data-stu-id="db447-121">**IsClustered**</span></span>|<span data-ttu-id="db447-122">Указывает, является ли сервер частью кластера.</span><span class="sxs-lookup"><span data-stu-id="db447-122">Indicates whether the server is part of a cluster.</span></span>|  
|<span data-ttu-id="db447-123">**Version**</span><span class="sxs-lookup"><span data-stu-id="db447-123">**Version**</span></span>|<span data-ttu-id="db447-124">Версия сервера.</span><span class="sxs-lookup"><span data-stu-id="db447-124">Version of the server.</span></span> <span data-ttu-id="db447-125">Пример:</span><span class="sxs-lookup"><span data-stu-id="db447-125">For example:</span></span><br /><br /> <span data-ttu-id="db447-126">-9.00.x (SQL Server 2005)</span><span class="sxs-lookup"><span data-stu-id="db447-126">-   9.00.x (SQL Server 2005)</span></span><br /><span data-ttu-id="db447-127">-10.0.xx (SQL Server 2008)</span><span class="sxs-lookup"><span data-stu-id="db447-127">-   10.0.xx (SQL Server 2008)</span></span><br /><span data-ttu-id="db447-128">-10.50.x (SQL Server 2008 R2)</span><span class="sxs-lookup"><span data-stu-id="db447-128">-   10.50.x (SQL Server 2008 R2)</span></span><br /><span data-ttu-id="db447-129">-11.0.xx (SQL Server 2012)</span><span class="sxs-lookup"><span data-stu-id="db447-129">-   11.0.xx (SQL Server 2012)</span></span>|  
  
## <a name="enumeration-limitations"></a><span data-ttu-id="db447-130">Ограничения перечисления</span><span class="sxs-lookup"><span data-stu-id="db447-130">Enumeration Limitations</span></span>  

 <span data-ttu-id="db447-131">Все доступные серверы могут быть или не быть перечислены.</span><span class="sxs-lookup"><span data-stu-id="db447-131">All of the available servers may or may not be listed.</span></span> <span data-ttu-id="db447-132">Список может различаться в зависимости от таких факторов, как время ожидания и сетевой трафик.</span><span class="sxs-lookup"><span data-stu-id="db447-132">The list can vary depending on factors such as timeouts and network traffic.</span></span> <span data-ttu-id="db447-133">Это может привести к тому, что список будет отличаться для двух последовательных вызовов.</span><span class="sxs-lookup"><span data-stu-id="db447-133">This can cause the list to be different on two consecutive calls.</span></span> <span data-ttu-id="db447-134">Будут перечислены только серверы в одной сети.</span><span class="sxs-lookup"><span data-stu-id="db447-134">Only servers on the same network will be listed.</span></span> <span data-ttu-id="db447-135">Широковещательные пакеты обычно не проходят через маршрутизаторы, поэтому сервер может не отображаться в списке, но он будет стабильным во всех вызовах.</span><span class="sxs-lookup"><span data-stu-id="db447-135">Broadcast packets typically won't traverse routers, which is why you may not see a server listed, but it will be stable across calls.</span></span>  
  
 <span data-ttu-id="db447-136">Перечисленные серверы могут содержать дополнительные сведения, такие как `IsClustered` и версия.</span><span class="sxs-lookup"><span data-stu-id="db447-136">Listed servers may or may not have additional information such as `IsClustered` and version.</span></span> <span data-ttu-id="db447-137">Это зависит от того, каким способом был получен список.</span><span class="sxs-lookup"><span data-stu-id="db447-137">This is dependent on how the list was obtained.</span></span> <span data-ttu-id="db447-138">В списках серверов, полученных с помощью службы браузера SQL Server, присутствует больше сведений, чем в списках серверов, найденных с помощью инфраструктуры Windows и содержащих только имена.</span><span class="sxs-lookup"><span data-stu-id="db447-138">Servers listed through the SQL Server browser service will have more details than those found through the Windows infrastructure, which will list only the name.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="db447-139">Перечисление серверов доступно только при выполнении в режиме полного доверия.</span><span class="sxs-lookup"><span data-stu-id="db447-139">Server enumeration is only available when running in full-trust.</span></span> <span data-ttu-id="db447-140">Сборки, работающие в среде с частичным доверием, не смогут использовать их, даже если у них есть разрешение на Управление доступом для кода (CAS) <xref:System.Data.SqlClient.SqlClientPermission>.</span><span class="sxs-lookup"><span data-stu-id="db447-140">Assemblies running in a partially-trusted environment will not be able to use it, even if they have the <xref:System.Data.SqlClient.SqlClientPermission> Code Access Security (CAS) permission.</span></span>  
  
 <span data-ttu-id="db447-141">В SQL Server сведения для <xref:System.Data.Sql.SqlDataSourceEnumerator> предоставляются с использованием внешней службы Windows, называемой браузером SQL.</span><span class="sxs-lookup"><span data-stu-id="db447-141">SQL Server provides information for the <xref:System.Data.Sql.SqlDataSourceEnumerator> through the use of an external Windows service named SQL Browser.</span></span> <span data-ttu-id="db447-142">Эта служба включена по умолчанию, но администраторы могут отключить ее, что делает этот экземпляр сервера невидимым для этого класса.</span><span class="sxs-lookup"><span data-stu-id="db447-142">This service is enabled by default, but administrators may turn it off or disable it, making the server instance invisible to this class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db447-143">Пример</span><span class="sxs-lookup"><span data-stu-id="db447-143">Example</span></span>  

 <span data-ttu-id="db447-144">Следующее консольное приложение получает сведения обо всех видимых экземплярах SQL Server и отображает эти сведения в окне консоли.</span><span class="sxs-lookup"><span data-stu-id="db447-144">The following console application retrieves information about all of the visible SQL Server instances and displays the information in the console window.</span></span>  
  
```vb  
Imports System.Data.Sql  
  
Module Module1  
  Sub Main()  
    ' Retrieve the enumerator instance and then the data.  
    Dim instance As SqlDataSourceEnumerator = _  
     SqlDataSourceEnumerator.Instance  
    Dim table As System.Data.DataTable = instance.GetDataSources()  
  
    ' Display the contents of the table.  
    DisplayData(table)  
  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Sub  
  
  Private Sub DisplayData(ByVal table As DataTable)  
    For Each row As DataRow In table.Rows  
      For Each col As DataColumn In table.Columns  
        Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
      Next  
      Console.WriteLine("============================")  
    Next  
  End Sub  
End Module  
```  
  
```csharp  
using System.Data.Sql;  
  
class Program  
{  
  static void Main()  
  {  
    // Retrieve the enumerator instance and then the data.  
    SqlDataSourceEnumerator instance =  
      SqlDataSourceEnumerator.Instance;  
    System.Data.DataTable table = instance.GetDataSources();  
  
    // Display the contents of the table.  
    DisplayData(table);  
  
    Console.WriteLine("Press any key to continue.");  
    Console.ReadKey();  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
    foreach (System.Data.DataRow row in table.Rows)  
    {  
      foreach (System.Data.DataColumn col in table.Columns)  
      {  
        Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
      }  
      Console.WriteLine("============================");  
    }  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="db447-145">См. также</span><span class="sxs-lookup"><span data-stu-id="db447-145">See also</span></span>

- [<span data-ttu-id="db447-146">SQL Server и ADO.NET</span><span class="sxs-lookup"><span data-stu-id="db447-146">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="db447-147">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="db447-147">ADO.NET Overview</span></span>](../ado-net-overview.md)
