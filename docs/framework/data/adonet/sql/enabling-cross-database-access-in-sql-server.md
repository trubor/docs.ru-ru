---
description: 'Дополнительные сведения: Включение межбазовых доступа в SQL Server'
title: Организация межбазового доступа в SQL Server
ms.date: 03/30/2017
ms.assetid: 10663fb6-434c-4c81-8178-ec894b9cf895
ms.openlocfilehash: 4e818b4f0294fdc7edd351a1e60203357579a320
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695870"
---
# <a name="enabling-cross-database-access-in-sql-server"></a><span data-ttu-id="71540-103">Организация межбазового доступа в SQL Server</span><span class="sxs-lookup"><span data-stu-id="71540-103">Enabling Cross-Database Access in SQL Server</span></span>

<span data-ttu-id="71540-104">Межбазовые цепочки владения возникают, когда процедура в одной базе данных зависит от объектов в другой базе данных.</span><span class="sxs-lookup"><span data-stu-id="71540-104">Cross-database ownership chaining occurs when a procedure in one database depends on objects in another database.</span></span> <span data-ttu-id="71540-105">Межбазовая цепочка владения работает так же, как цепочка владения внутри единой базы данных, но для непрерывной цепочки владения необходимо, чтобы все владельцы объекта были сопоставлены с одной учетной записью входа.</span><span class="sxs-lookup"><span data-stu-id="71540-105">A cross-database ownership chain works in the same way as ownership chaining within a single database, except that an unbroken ownership chain requires that all the object owners are mapped to the same login account.</span></span> <span data-ttu-id="71540-106">Если одна учетная запись входа является владельцем исходного объекта в исходной базе данных и целевых объектов в целевых базах данных, то SQL Server не проверяет наличие разрешений в целевых объектах.</span><span class="sxs-lookup"><span data-stu-id="71540-106">If the source object in the source database and the target objects in the target databases are owned by the same login account, SQL Server does not check permissions on the target objects.</span></span>  
  
## <a name="off-by-default"></a><span data-ttu-id="71540-107">Отключено по умолчанию</span><span class="sxs-lookup"><span data-stu-id="71540-107">Off By Default</span></span>  

 <span data-ttu-id="71540-108">Формирование межбазовых цепочек владения отключено по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="71540-108">Ownership chaining across databases is turned off by default.</span></span> <span data-ttu-id="71540-109">Майкрософт рекомендует отключить межбазовые цепочки владения, так как с ними связаны следующие угрозы безопасности:</span><span class="sxs-lookup"><span data-stu-id="71540-109">Microsoft recommends that you disable cross-database ownership chaining because it exposes you to the following security risks:</span></span>  
  
- <span data-ttu-id="71540-110">Владельцы баз данных и члены ролей базы данных `db_ddladmin` или `db_owners` могут создавать объекты, владельцами которых являются другие пользователи.</span><span class="sxs-lookup"><span data-stu-id="71540-110">Database owners and members of the `db_ddladmin` or the `db_owners` database roles can create objects that are owned by other users.</span></span> <span data-ttu-id="71540-111">Эти объекты потенциально могут обращаться к объектам в другой базе данных.</span><span class="sxs-lookup"><span data-stu-id="71540-111">These objects can potentially target objects in other databases.</span></span> <span data-ttu-id="71540-112">Это значит, что при включенных межбазовых цепочках владения этим пользователям необходимо полностью доверять при доступе к данным во всех базах данных.</span><span class="sxs-lookup"><span data-stu-id="71540-112">This means that if you enable cross-database ownership chaining, you must fully trust these users with data in all databases.</span></span>  
  
- <span data-ttu-id="71540-113">Пользователи с разрешением CREATE DATABASE могут создавать новые базы данных и присоединять существующие базы данных.</span><span class="sxs-lookup"><span data-stu-id="71540-113">Users with CREATE DATABASE permission can create new databases and attach existing databases.</span></span> <span data-ttu-id="71540-114">Если межбазовые цепочки владения включены, то эти пользователи могут обращаться к объектам в других базах данных, в которых у них нет прав доступа, из вновь созданных или присоединенных баз данных, которые они создали.</span><span class="sxs-lookup"><span data-stu-id="71540-114">If cross-database ownership chaining is enabled, these users can access objects in other databases that they might not have privileges in from the newly created or attached databases that they create.</span></span>  
  
## <a name="enabling-cross-database-ownership-chaining"></a><span data-ttu-id="71540-115">Включение межбазовых цепочек владения</span><span class="sxs-lookup"><span data-stu-id="71540-115">Enabling Cross-database Ownership Chaining</span></span>  

 <span data-ttu-id="71540-116">Межбазовые цепочки владения нужно включать только в среде с привилегированными пользователями, имеющими полный уровень доверия.</span><span class="sxs-lookup"><span data-stu-id="71540-116">Cross-database ownership chaining should only be enabled in environments where you can fully trust highly-privileged users.</span></span> <span data-ttu-id="71540-117">Их можно настроить во время установки всех баз данных или выборочно для определенных баз данных с помощью команд Transact-SQL `sp_configure` и `ALTER DATABASE`.</span><span class="sxs-lookup"><span data-stu-id="71540-117">It can be configured during setup for all databases, or selectively for specific databases using the Transact-SQL commands `sp_configure` and `ALTER DATABASE`.</span></span>  
  
 <span data-ttu-id="71540-118">Для выборочной настройки межбазовых цепочек владения служит хранимая процедура `sp_configure`, с помощью которой эти цепочки отключаются для сервера.</span><span class="sxs-lookup"><span data-stu-id="71540-118">To selectively configure cross-database ownership chaining, use `sp_configure` to turn it off for the server.</span></span> <span data-ttu-id="71540-119">Затем с помощью команды ALTER DATABASE с параметром SET DB_CHAINING ON настраиваются межбазовые цепочки владения только в требуемых базах данных.</span><span class="sxs-lookup"><span data-stu-id="71540-119">Then use the ALTER DATABASE command with SET DB_CHAINING ON to configure cross-database ownership chaining for only the databases that require it.</span></span>  
  
 <span data-ttu-id="71540-120">В следующем примере включены межбазовые цепочки владения для всех баз данных.</span><span class="sxs-lookup"><span data-stu-id="71540-120">The following sample turns on cross-database ownership chaining for all databases:</span></span>  
  
```sql
EXECUTE sp_configure 'show advanced', 1;  
RECONFIGURE;  
EXECUTE sp_configure 'cross db ownership chaining', 1;  
RECONFIGURE;  
```  
  
 <span data-ttu-id="71540-121">В следующем примере включены межбазовые цепочки владения для конкретных баз данных.</span><span class="sxs-lookup"><span data-stu-id="71540-121">The following sample turns on cross-database ownership chaining for specific databases:</span></span>  
  
```sql
ALTER DATABASE Database1 SET DB_CHAINING ON;  
ALTER DATABASE Database2 SET DB_CHAINING ON;  
```  
  
### <a name="dynamic-sql"></a><span data-ttu-id="71540-122">Динамический SQL</span><span class="sxs-lookup"><span data-stu-id="71540-122">Dynamic SQL</span></span>  

 <span data-ttu-id="71540-123">Межбазовые цепочки владения неприменимы в тех случаях, когда выполняются динамически созданные инструкции SQL, если только один и тот же пользователь не присутствует в обеих базах данных.</span><span class="sxs-lookup"><span data-stu-id="71540-123">Cross-database ownership chaining does not work in cases where dynamically created SQL statements are executed unless the same user exists in both databases.</span></span> <span data-ttu-id="71540-124">Это можно обойти в SQL Server, создав хранимую процедуру для доступа к данным другой базы данных и подписав эту процедуру сертификатом, существующим в обеих базах данных.</span><span class="sxs-lookup"><span data-stu-id="71540-124">You can work around this in SQL Server by creating a stored procedure that accesses data in another database and signing the procedure with a certificate that exists in both databases.</span></span> <span data-ttu-id="71540-125">Это дает пользователям доступ к ресурсам базы данных, используемым процедурой, без предоставления им разрешений или доступа к базе данных.</span><span class="sxs-lookup"><span data-stu-id="71540-125">This gives users access to the database resources used by the procedure without granting them database access or permissions.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="71540-126">Внешние ресурсы</span><span class="sxs-lookup"><span data-stu-id="71540-126">External Resources</span></span>  

 <span data-ttu-id="71540-127">Для получения дополнительных сведений см. следующие ресурсы.</span><span class="sxs-lookup"><span data-stu-id="71540-127">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="71540-128">Ресурс</span><span class="sxs-lookup"><span data-stu-id="71540-128">Resource</span></span>|<span data-ttu-id="71540-129">Описание</span><span class="sxs-lookup"><span data-stu-id="71540-129">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="71540-130">[Расширение олицетворения базы данных с помощью параметра выполнить как](/previous-versions/sql/sql-server-2008-r2/ms188304(v=sql.105)) и [перекрестный межбазовые цепочки владения](/sql/database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option).</span><span class="sxs-lookup"><span data-stu-id="71540-130">[Extending Database Impersonation by Using EXECUTE AS](/previous-versions/sql/sql-server-2008-r2/ms188304(v=sql.105)) and [Cross DB Ownership Chaining Option](/sql/database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option).</span></span>|<span data-ttu-id="71540-131">В статьях описано, как настроить межбазовые цепочки владения для экземпляра SQL Server.</span><span class="sxs-lookup"><span data-stu-id="71540-131">Articles describe how to configure cross-database ownership chaining for an instance of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="71540-132">См. также</span><span class="sxs-lookup"><span data-stu-id="71540-132">See also</span></span>

- [<span data-ttu-id="71540-133">Защита приложений ADO.NET</span><span class="sxs-lookup"><span data-stu-id="71540-133">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="71540-134">Общие сведения о безопасности SQL Server</span><span class="sxs-lookup"><span data-stu-id="71540-134">Overview of SQL Server Security</span></span>](overview-of-sql-server-security.md)
- [<span data-ttu-id="71540-135">Управление разрешениями с использованием хранимых процедур в SQL Server</span><span class="sxs-lookup"><span data-stu-id="71540-135">Managing Permissions with Stored Procedures in SQL Server</span></span>](managing-permissions-with-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="71540-136">Написание безопасного динамического кода SQL в SQL Server</span><span class="sxs-lookup"><span data-stu-id="71540-136">Writing Secure Dynamic SQL in SQL Server</span></span>](writing-secure-dynamic-sql-in-sql-server.md)
- [<span data-ttu-id="71540-137">Подписывание хранимых процедур в SQL Server</span><span class="sxs-lookup"><span data-stu-id="71540-137">Signing Stored Procedures in SQL Server</span></span>](signing-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="71540-138">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="71540-138">ADO.NET Overview</span></span>](../ado-net-overview.md)
