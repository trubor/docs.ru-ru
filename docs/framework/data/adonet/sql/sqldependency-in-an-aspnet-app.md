---
description: 'Дополнительные сведения о: SqlDependency в приложении ASP.NET'
title: SqlDependency в приложении ASP.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
ms.openlocfilehash: 686586af834884f97ff8e62fdc792b3cdc23f507
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767028"
---
# <a name="sqldependency-in-an-aspnet-application"></a><span data-ttu-id="7d0b7-103">SqlDependency в приложении ASP.NET</span><span class="sxs-lookup"><span data-stu-id="7d0b7-103">SqlDependency in an ASP.NET Application</span></span>

<span data-ttu-id="7d0b7-104">В приведенном в этом разделе примере показано, как применять <xref:System.Data.SqlClient.SqlDependency> косвенно, используя объект <xref:System.Web.Caching.SqlCacheDependency> ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7d0b7-104">The example in this section shows how to use <xref:System.Data.SqlClient.SqlDependency> indirectly by leveraging the ASP.NET <xref:System.Web.Caching.SqlCacheDependency> object.</span></span> <span data-ttu-id="7d0b7-105">Объект <xref:System.Web.Caching.SqlCacheDependency> использует <xref:System.Data.SqlClient.SqlDependency> для прослушивания уведомлений и корректного обновления кэша.</span><span class="sxs-lookup"><span data-stu-id="7d0b7-105">The <xref:System.Web.Caching.SqlCacheDependency> object uses a <xref:System.Data.SqlClient.SqlDependency> to listen for notifications and correctly update the cache.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7d0b7-106">В примере кода предполагается, что вы включили уведомления о запросах, выполняя скрипты, [включив уведомления о запросах](enabling-query-notifications.md).</span><span class="sxs-lookup"><span data-stu-id="7d0b7-106">The sample code assumes that you have enabled query notifications by executing the scripts in [Enabling Query Notifications](enabling-query-notifications.md).</span></span>  
  
## <a name="about-the-sample-application"></a><span data-ttu-id="7d0b7-107">О примере приложения</span><span class="sxs-lookup"><span data-stu-id="7d0b7-107">About the Sample Application</span></span>  

 <span data-ttu-id="7d0b7-108">В примере приложения используется одна веб-страница ASP.NET для вывода сведений о продуктах из базы данных **AdventureWorks** SQL Server в элемент управления <xref:System.Web.UI.WebControls.GridView>.</span><span class="sxs-lookup"><span data-stu-id="7d0b7-108">The sample application uses a single ASP.NET Web page to display product information from the **AdventureWorks** SQL Server database in a <xref:System.Web.UI.WebControls.GridView> control.</span></span> <span data-ttu-id="7d0b7-109">При загрузке страницы код записывает текущее время в элемент управления <xref:System.Web.UI.WebControls.Label>.</span><span class="sxs-lookup"><span data-stu-id="7d0b7-109">When the page loads, the code writes the current time to a <xref:System.Web.UI.WebControls.Label> control.</span></span> <span data-ttu-id="7d0b7-110">Затем он определяет объект <xref:System.Web.Caching.SqlCacheDependency> и задает свойства объекта <xref:System.Web.Caching.Cache> для сохранения данных кэша до трех минут.</span><span class="sxs-lookup"><span data-stu-id="7d0b7-110">It then defines a <xref:System.Web.Caching.SqlCacheDependency> object and sets properties on the <xref:System.Web.Caching.Cache> object to store the cache data for up to three minutes.</span></span> <span data-ttu-id="7d0b7-111">Затем код подключается к базе данных и получает данные.</span><span class="sxs-lookup"><span data-stu-id="7d0b7-111">The code then connects to the database and retrieves the data.</span></span> <span data-ttu-id="7d0b7-112">При загрузке страницы и работе приложения ASP.NET будет получать данные из кэша, которые можно проверить, отметив, что время на странице не меняется.</span><span class="sxs-lookup"><span data-stu-id="7d0b7-112">When the page is loaded and the application is running ASP.NET will retrieve data from the cache, which you can verify by noting that the time on the page does not change.</span></span> <span data-ttu-id="7d0b7-113">Если наблюдаемые данные изменяются, ASP.NET делает недействительным кэш и повторно заполняет элемент управления `GridView` новыми данными, обновляя время в элементе управления `Label`.</span><span class="sxs-lookup"><span data-stu-id="7d0b7-113">If the data being monitored changes, ASP.NET invalidates the cache and repopulate the `GridView` control with fresh data, updating the time displayed in the `Label` control.</span></span>  
  
## <a name="creating-the-sample-application"></a><span data-ttu-id="7d0b7-114">Создание примера приложения</span><span class="sxs-lookup"><span data-stu-id="7d0b7-114">Creating the Sample Application</span></span>  

 <span data-ttu-id="7d0b7-115">Чтобы создать и запустить пример приложения, выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="7d0b7-115">Follow these steps to create and run the sample application:</span></span>  
  
1. <span data-ttu-id="7d0b7-116">Создание нового веб-сайта ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7d0b7-116">Create a new ASP.NET Web site.</span></span>  
  
2. <span data-ttu-id="7d0b7-117">Добавьте <xref:System.Web.UI.WebControls.Label> и элемент управления <xref:System.Web.UI.WebControls.GridView> на страницу Default.aspx.</span><span class="sxs-lookup"><span data-stu-id="7d0b7-117">Add a <xref:System.Web.UI.WebControls.Label> and a <xref:System.Web.UI.WebControls.GridView> control to the Default.aspx page.</span></span>  
  
3. <span data-ttu-id="7d0b7-118">Откройте модуль класса страницы и добавьте следующие директивы:</span><span class="sxs-lookup"><span data-stu-id="7d0b7-118">Open the page's class module and add the following directives:</span></span>  
  
    ```vb  
    Option Strict On  
    Option Explicit On  
  
    Imports System.Data.SqlClient  
    ```  
  
    ```csharp  
    using System.Data.SqlClient;  
    using System.Web.Caching;  
    ```  
  
4. <span data-ttu-id="7d0b7-119">Добавьте следующий код в событие `Page_Load` страницы:</span><span class="sxs-lookup"><span data-stu-id="7d0b7-119">Add the following code in the page's `Page_Load` event:</span></span>  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#1)]
     [!code-vb[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#1)]  
  
5. <span data-ttu-id="7d0b7-120">Добавьте два вспомогательных метода: `GetConnectionString` и `GetSQL`.</span><span class="sxs-lookup"><span data-stu-id="7d0b7-120">Add two helper methods, `GetConnectionString` and `GetSQL`.</span></span> <span data-ttu-id="7d0b7-121">В определенной строке соединения используются интегрированные средства безопасности.</span><span class="sxs-lookup"><span data-stu-id="7d0b7-121">The connection string defined uses integrated security.</span></span> <span data-ttu-id="7d0b7-122">Необходимо будет убедиться, что используемая учетная запись обладает необходимыми разрешениями для базы данных, а в образце базы данных **AdventureWorks** включены уведомления.</span><span class="sxs-lookup"><span data-stu-id="7d0b7-122">You will need to verify that the account you are using has the necessary database permissions and that the sample database, **AdventureWorks**, has notifications enabled.</span></span>
  
     [!code-csharp[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#2)]
     [!code-vb[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#2)]  
  
### <a name="testing-the-application"></a><span data-ttu-id="7d0b7-123">Тестирование приложения</span><span class="sxs-lookup"><span data-stu-id="7d0b7-123">Testing the Application</span></span>  

 <span data-ttu-id="7d0b7-124">Приложение кэширует данные, отображаемые в веб-форме, и обновляет их каждые три минуты, если нет действий.</span><span class="sxs-lookup"><span data-stu-id="7d0b7-124">The application caches the data displayed on the Web form and refreshes it every three minutes if there is no activity.</span></span> <span data-ttu-id="7d0b7-125">Если в базе данных происходит изменение, кэш обновляется немедленно.</span><span class="sxs-lookup"><span data-stu-id="7d0b7-125">If a change occurs to the database, the cache is refreshed immediately.</span></span> <span data-ttu-id="7d0b7-126">Запустите приложение из Visual Studio, чтобы загрузить страницу в браузер.</span><span class="sxs-lookup"><span data-stu-id="7d0b7-126">Run the application from Visual Studio, which loads the page into the browser.</span></span> <span data-ttu-id="7d0b7-127">Отображаемое время обновления кэша указывает, когда кэш был обновлен последний раз.</span><span class="sxs-lookup"><span data-stu-id="7d0b7-127">The cache refresh time displayed indicates when the cache was last refreshed.</span></span> <span data-ttu-id="7d0b7-128">Подождите три минуты, а затем обновите страницу, в результате чего произойдет событие обратной передачи.</span><span class="sxs-lookup"><span data-stu-id="7d0b7-128">Wait three minutes, and then refresh the page, causing a postback event to occur.</span></span> <span data-ttu-id="7d0b7-129">Обратите внимание, что время, отображаемое на странице, изменилось.</span><span class="sxs-lookup"><span data-stu-id="7d0b7-129">Note that the time displayed on the page has changed.</span></span> <span data-ttu-id="7d0b7-130">Если обновить страницу меньше чем через три минуты, время, отображаемое на странице, останется прежним.</span><span class="sxs-lookup"><span data-stu-id="7d0b7-130">If you refresh the page in less than three minutes, the time displayed on the page will remain the same.</span></span>  
  
 <span data-ttu-id="7d0b7-131">Теперь обновите данные в базе данных, используя команду Transact-SQL UPDATE, и обновите страницу.</span><span class="sxs-lookup"><span data-stu-id="7d0b7-131">Now update the data in the database, using a Transact-SQL UPDATE command and refresh the page.</span></span> <span data-ttu-id="7d0b7-132">Отображаемое время теперь указывает, что кэш был обновлен с учетом новых данных из базы данных.</span><span class="sxs-lookup"><span data-stu-id="7d0b7-132">The time displayed now indicates that the cache was refreshed with the new data from the database.</span></span> <span data-ttu-id="7d0b7-133">Обратите внимание, что хотя кэш обновляется, время на странице не изменяется, пока не произойдет событие обратной передачи.</span><span class="sxs-lookup"><span data-stu-id="7d0b7-133">Note that although the cache is updated, the time displayed on the page does not change until a postback event occurs.</span></span>  

## <a name="distributed-cache-synchronization-using-sql-dependency"></a><span data-ttu-id="7d0b7-134">Синхронизация распределенного кэша с использованием зависимости SQL</span><span class="sxs-lookup"><span data-stu-id="7d0b7-134">Distributed cache synchronization using SQL Dependency</span></span>

<span data-ttu-id="7d0b7-135">Некоторые из таких распределенных кэшей, как [NCache](https://www.alachisoft.com/ncache) , обеспечивают поддержку синхронизации базы данных SQL и кэша с помощью [зависимости SQL](https://www.alachisoft.com/resources/docs/ncache/prog-guide/sql-dependency.html).</span><span class="sxs-lookup"><span data-stu-id="7d0b7-135">Some of the third-party distributed caches such as [NCache](https://www.alachisoft.com/ncache) provide support to synchronize the SQL database and cache using [SQL Dependency](https://www.alachisoft.com/resources/docs/ncache/prog-guide/sql-dependency.html).</span></span> <span data-ttu-id="7d0b7-136">Дополнительные сведения и пример реализации исходного кода см. в разделе [Пример использования зависимости SQL для распределенного кэша](https://github.com/Alachisoft/NCache-Samples/tree/master/dotnet/Dependencies/SQLDependency).</span><span class="sxs-lookup"><span data-stu-id="7d0b7-136">For more information and an example source code implementation, see [Distributed cache SQL Dependency sample](https://github.com/Alachisoft/NCache-Samples/tree/master/dotnet/Dependencies/SQLDependency).</span></span>

## <a name="see-also"></a><span data-ttu-id="7d0b7-137">См. также</span><span class="sxs-lookup"><span data-stu-id="7d0b7-137">See also</span></span>

- [<span data-ttu-id="7d0b7-138">Уведомления о запросах в SQL Server</span><span class="sxs-lookup"><span data-stu-id="7d0b7-138">Query Notifications in SQL Server</span></span>](query-notifications-in-sql-server.md)
- [<span data-ttu-id="7d0b7-139">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7d0b7-139">ADO.NET Overview</span></span>](../ado-net-overview.md)
