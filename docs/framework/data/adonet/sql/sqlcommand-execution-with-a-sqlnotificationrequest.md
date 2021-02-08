---
description: Дополнительные сведения о выполнении команды SqlCommand с помощью SqlNotificationRequest
title: Выполнение SqlCommand с помощью SqlNotificationRequest
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1776f48f-9bea-41f6-83a4-c990c7a2c991
ms.openlocfilehash: d3e82022794aa67d4bd20223cac852097f2be9dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767054"
---
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a><span data-ttu-id="55483-103">Выполнение SqlCommand с помощью SqlNotificationRequest</span><span class="sxs-lookup"><span data-stu-id="55483-103">SqlCommand Execution with a SqlNotificationRequest</span></span>

<span data-ttu-id="55483-104"><xref:System.Data.SqlClient.SqlCommand> можно настроить на генерацию уведомления об изменении данных после их получения с сервера, и в случае повторного выполнения запроса результирующий набор будет отличаться.</span><span class="sxs-lookup"><span data-stu-id="55483-104">A <xref:System.Data.SqlClient.SqlCommand> can be configured to generate a notification when data changes after it has been fetched from the server and the result set would be different if the query were executed again.</span></span> <span data-ttu-id="55483-105">Это полезно для сценариев, в которых необходимо использовать пользовательские очереди уведомлений на сервере, или если не требуется поддерживать активные объекты.</span><span class="sxs-lookup"><span data-stu-id="55483-105">This is useful for scenarios where you want to use custom notification queues on the server or when you do not want to maintain live objects.</span></span>

## <a name="creating-the-notification-request"></a><span data-ttu-id="55483-106">Создание уведомления о запросах</span><span class="sxs-lookup"><span data-stu-id="55483-106">Creating the Notification Request</span></span>

<span data-ttu-id="55483-107">Объект <xref:System.Data.Sql.SqlNotificationRequest> можно использовать для создания запроса на уведомление путем привязки его к объекту `SqlCommand`.</span><span class="sxs-lookup"><span data-stu-id="55483-107">You can use a <xref:System.Data.Sql.SqlNotificationRequest> object to create the notification request by binding it to a `SqlCommand` object.</span></span> <span data-ttu-id="55483-108">Объект `SqlNotificationRequest` больше не понадобится после создания запроса.</span><span class="sxs-lookup"><span data-stu-id="55483-108">Once the request is created, you no longer need the `SqlNotificationRequest` object.</span></span> <span data-ttu-id="55483-109">Вы можете запросить очередь для любых уведомлений и ответить соответствующим образом.</span><span class="sxs-lookup"><span data-stu-id="55483-109">You can query the queue for any notifications and respond appropriately.</span></span> <span data-ttu-id="55483-110">Уведомления могут возникать, даже если приложение завершает работу и впоследствии перезапускается.</span><span class="sxs-lookup"><span data-stu-id="55483-110">Notifications can occur even if the application is shut down and subsequently restarted.</span></span>

<span data-ttu-id="55483-111">Если выполняется команда со связанным уведомлением, любые изменения в исходном результирующем наборе инициируют отправку сообщения в очередь SQL Server, которая была указана в запросе уведомления.</span><span class="sxs-lookup"><span data-stu-id="55483-111">When the command with the associated notification is executed, any changes to the original result set trigger sending a message to the SQL Server queue that was configured in the notification request.</span></span>

<span data-ttu-id="55483-112">Опрос очереди SQL Server и интерпретация сообщения зависят от конкретного приложения.</span><span class="sxs-lookup"><span data-stu-id="55483-112">How you poll the SQL Server queue and interpret the message is specific to your application.</span></span> <span data-ttu-id="55483-113">Приложение отвечает за опрос очереди и реагирование на основе содержимого сообщения.</span><span class="sxs-lookup"><span data-stu-id="55483-113">The application is responsible for polling the queue and reacting based on the contents of the message.</span></span>

> [!NOTE]
> <span data-ttu-id="55483-114">При использовании запросов SQL Server на уведомления с помощью <xref:System.Data.SqlClient.SqlDependency>создайте свое собственное имя очереди вместо использования имени службы по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="55483-114">When using SQL Server notification requests with <xref:System.Data.SqlClient.SqlDependency>, create your own queue name instead of using the default service name.</span></span>

<span data-ttu-id="55483-115">Для<xref:System.Data.Sql.SqlNotificationRequest> не существует новых элементов безопасности на стороне клиента.</span><span class="sxs-lookup"><span data-stu-id="55483-115">There are no new client-side security elements for <xref:System.Data.Sql.SqlNotificationRequest>.</span></span> <span data-ttu-id="55483-116">Это, в первую очередь, функция сервера, и сервер создал специальные разрешения, которые необходимы пользователям, чтобы запрашивать уведомления.</span><span class="sxs-lookup"><span data-stu-id="55483-116">This is primarily a server feature, and the server has created special privileges that users must have to request a notification.</span></span>

### <a name="example"></a><span data-ttu-id="55483-117">Пример</span><span class="sxs-lookup"><span data-stu-id="55483-117">Example</span></span>

<span data-ttu-id="55483-118">В следующем фрагменте кода показано, как создать <xref:System.Data.Sql.SqlNotificationRequest> и связать его с <xref:System.Data.SqlClient.SqlCommand>.</span><span class="sxs-lookup"><span data-stu-id="55483-118">The following code fragment demonstrates how to create a <xref:System.Data.Sql.SqlNotificationRequest> and associate it with a <xref:System.Data.SqlClient.SqlCommand>.</span></span>

```vb
' Assume connection is an open SqlConnection.
' Create a new SqlCommand object.
Dim command As New SqlCommand( _
  "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection)

' Create a SqlNotificationRequest object.
Dim notifcationRequest As New SqlNotificationRequest()
notificationRequest.id = "NotificationID"
notificationRequest.Service = "mySSBQueue"

' Associate the notification request with the command.
command.Notification = notificationRequest
' Execute the command.
command.ExecuteReader()
' Process the DataReader.
' You can use Transact-SQL syntax to periodically poll the
' SQL Server queue to see if you have a new message.
```

```csharp
// Assume connection is an open SqlConnection.
// Create a new SqlCommand object.
SqlCommand command=new SqlCommand(
 "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection);

// Create a SqlNotificationRequest object.
SqlNotificationRequest notificationRequest=new SqlNotificationRequest();
notificationRequest.id="NotificationID";
notificationRequest.Service="mySSBQueue";

// Associate the notification request with the command.
command.Notification=notificationRequest;
// Execute the command.
command.ExecuteReader();
// Process the DataReader.
// You can use Transact-SQL syntax to periodically poll the
// SQL Server queue to see if you have a new message.
```

## <a name="see-also"></a><span data-ttu-id="55483-119">См. также</span><span class="sxs-lookup"><span data-stu-id="55483-119">See also</span></span>

- [<span data-ttu-id="55483-120">Уведомления о запросах в SQL Server</span><span class="sxs-lookup"><span data-stu-id="55483-120">Query Notifications in SQL Server</span></span>](query-notifications-in-sql-server.md)
- [<span data-ttu-id="55483-121">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="55483-121">ADO.NET Overview</span></span>](../ado-net-overview.md)
