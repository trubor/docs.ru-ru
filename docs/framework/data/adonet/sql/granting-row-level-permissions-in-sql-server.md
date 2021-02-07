---
description: 'Дополнительные сведения: предоставление Row-Level разрешений в SQL Server'
title: Предоставление разрешений уровня строки в SQL Server
ms.date: 03/30/2017
ms.assetid: a55aaa12-34ab-41cd-9dec-fd255b29258c
ms.openlocfilehash: fe69a023b5befbdb53473881647fff8bdf0e9795
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663304"
---
# <a name="granting-row-level-permissions-in-sql-server"></a><span data-ttu-id="539e3-103">Предоставление разрешений уровня строки в SQL Server</span><span class="sxs-lookup"><span data-stu-id="539e3-103">Granting Row-Level Permissions in SQL Server</span></span>

<span data-ttu-id="539e3-104">В некоторых случаях требуется более точное управление доступом к данным, чем простое предоставление, отзыв или отклонение предоставленных разрешений.</span><span class="sxs-lookup"><span data-stu-id="539e3-104">In some scenarios, there is a requirement to control access to data at a more granular level than what simply granting, revoking, or denying permissions provides.</span></span> <span data-ttu-id="539e3-105">Например, в приложении базы данных больницы может требоваться ограничение доступа отдельных врачей, чтобы они имели доступ к сведениям только о своих пациентах.</span><span class="sxs-lookup"><span data-stu-id="539e3-105">For example, a hospital database application may require individual Doctors to be restricted to accessing information related to only their patients.</span></span> <span data-ttu-id="539e3-106">Подобные требования существуют во многих областях, включая финансовые, юридические, правительственные и военные приложения.</span><span class="sxs-lookup"><span data-stu-id="539e3-106">Similar requirements exist in many environments, including finance, law, government, and military applications.</span></span> <span data-ttu-id="539e3-107">SQL Server 2016 помогает реализовать эти сценарии, предоставляя функциональность [безопасности на уровне строк](/sql/relational-databases/security/row-level-security) , которая упрощает и централизует логику доступа на уровне строк в политике безопасности.</span><span class="sxs-lookup"><span data-stu-id="539e3-107">To help address these scenarios, SQL Server 2016 provides a [Row-Level Security](/sql/relational-databases/security/row-level-security) feature that simplifies and centralizes row-level access logic in a security policy.</span></span> <span data-ttu-id="539e3-108">В более ранних версиях SQL Server аналогичная функциональность достигается путем использования представлений для внедрения фильтрации на уровне строк.</span><span class="sxs-lookup"><span data-stu-id="539e3-108">For earlier versions of SQL Server, similar functionality can be achieved by using views to enact row-level filtering.</span></span>

## <a name="implementing-row-level-filtering"></a><span data-ttu-id="539e3-109">Реализация фильтрации на уровне строк</span><span class="sxs-lookup"><span data-stu-id="539e3-109">Implementing Row-level Filtering</span></span>

<span data-ttu-id="539e3-110">Фильтрация на уровне строк используется для приложений, которые хранят сведения в одной таблице, как в приведенном выше примере приложения больницы.</span><span class="sxs-lookup"><span data-stu-id="539e3-110">Row-level filtering is used for applications storing information in a single table like in the hospital example above.</span></span> <span data-ttu-id="539e3-111">Для реализации фильтрации на уровне строк в каждой строке предусмотрен столбец, в котором задается отличительный параметр, например имя пользователя, метка или другой идентификатор.</span><span class="sxs-lookup"><span data-stu-id="539e3-111">To implement row-level filtering each row has a column that defines a differentiating parameter, such as a user name, label or other identifier.</span></span> <span data-ttu-id="539e3-112">Вы создаете политику безопасности или представление на основе этой таблицы для фильтрации строк, к которым пользователь имеет доступ.</span><span class="sxs-lookup"><span data-stu-id="539e3-112">You create either a security policy or a view on the table, which filters the rows that the user can access.</span></span> <span data-ttu-id="539e3-113">Затем вы создаете параметризованные хранимые процедуры, контролирующие типы запросов, которые может выполнять пользователь.</span><span class="sxs-lookup"><span data-stu-id="539e3-113">You then create parameterized stored procedures, which control the types of queries the user can execute.</span></span>

<span data-ttu-id="539e3-114">В следующем примере показывается, как настроить фильтрацию на уровне строк на основе имени пользователя или имени для входа.</span><span class="sxs-lookup"><span data-stu-id="539e3-114">The following example describes how to configure row-level filtering based on a user or login name:</span></span>

- <span data-ttu-id="539e3-115">Создайте таблицу и добавьте в нее столбец для хранения имени.</span><span class="sxs-lookup"><span data-stu-id="539e3-115">Create the table, adding a column to store the name.</span></span>

- <span data-ttu-id="539e3-116">Включите фильтрацию на уровне строк следующим образом.</span><span class="sxs-lookup"><span data-stu-id="539e3-116">Enable row-level filtering:</span></span>

  - <span data-ttu-id="539e3-117">Если вы используете SQL Server версии не ниже 2016 или [базу данных SQL Azure](/azure/sql-database/), создайте политику безопасности, которая добавляет в таблицу предикат, ограничивающий возвращаемые строки теми, которые соответствуют либо текущему пользователю базы данных (с помощью встроенной функции CURRENT_USER()), либо текущему имени для входа (с помощью встроенной функции SUSER_SNAME()).</span><span class="sxs-lookup"><span data-stu-id="539e3-117">If you are using SQL Server 2016 or higher, or [Azure SQL Database](/azure/sql-database/), create a security policy that adds a predicate on the table restricting the rows returned to those that match either the current database user (using the CURRENT_USER() built-in function) or the current login name (using the SUSER_SNAME() built-in function):</span></span>

      ```sql
      CREATE SCHEMA Security
      GO

      CREATE FUNCTION Security.userAccessPredicate(@UserName sysname)
          RETURNS TABLE
          WITH SCHEMABINDING
      AS
          RETURN SELECT 1 AS accessResult
          WHERE @UserName = SUSER_SNAME()
      GO

      CREATE SECURITY POLICY Security.userAccessPolicy
          ADD FILTER PREDICATE Security.userAccessPredicate(UserName) ON dbo.MyTable,
          ADD BLOCK PREDICATE Security.userAccessPredicate(UserName) ON dbo.MyTable
      GO
      ```

  - <span data-ttu-id="539e3-118">При использовании версии SQL Server до 2016 аналогичную функциональность можно реализовать с помощью представления:</span><span class="sxs-lookup"><span data-stu-id="539e3-118">If you are using a version of SQL Server prior to 2016, you can achieve similar functionality using a view:</span></span>

      ```sql
      CREATE VIEW vw_MyTable
      AS
          RETURN SELECT * FROM MyTable
          WHERE UserName = SUSER_SNAME()
      GO
      ```

- <span data-ttu-id="539e3-119">Создайте хранимые процедуры для выбора, вставки, обновления и удаления данных.</span><span class="sxs-lookup"><span data-stu-id="539e3-119">Create stored procedures to select, insert, update, and delete data.</span></span> <span data-ttu-id="539e3-120">Если фильтрация осуществляется с помощью политики безопасности, хранимые процедуры должны выполнять эти операции непосредственно в базовой таблице; если же фильтрация осуществляется с помощью представления, хранимые процедуры должны работать с представлением.</span><span class="sxs-lookup"><span data-stu-id="539e3-120">If the filtering is enacted by a security policy, the stored procedures should perform these operations on the base table directly; otherwise, if the filtering is enacted by a view, the stored procedures should instead operate against the view.</span></span> <span data-ttu-id="539e3-121">Политика безопасности или представление будет автоматически фильтровать строки, возвращаемые или изменяемые по запросам пользователя, а хранимая процедура будет обеспечивать более жесткую границу безопасности, чтобы предотвратить прямой доступ пользователей через успешно выполняемые запросы, которые могут определять наличие отфильтрованных данных.</span><span class="sxs-lookup"><span data-stu-id="539e3-121">The security policy or view will automatically filter the rows returned or modified by user queries, and the stored procedure will provide a harder security boundary to prevent users with direct query access from successfully running queries that can infer the existence of filtered data.</span></span>

- <span data-ttu-id="539e3-122">Для хранимых процедур, которые вставляют данные, получайте имя пользователя при помощи той же функции, которая указана в политике безопасности или в представлении, и вставляйте это значение в столбец UserName.</span><span class="sxs-lookup"><span data-stu-id="539e3-122">For stored procedures that insert data, capture the user name using the same function specified in the security policy or view, and insert that value into the UserName column.</span></span>

- <span data-ttu-id="539e3-123">Запретите роли `public` всякий доступ к таблицам (и представлениям, если они применяются).</span><span class="sxs-lookup"><span data-stu-id="539e3-123">Deny all permissions on the tables (and views, if applicable) to the `public` role.</span></span> <span data-ttu-id="539e3-124">Пользователи не смогут наследовать права доступа от других ролей базы данных, поскольку предикат фильтра основан на имени пользователя или имени для входа, а не на ролях.</span><span class="sxs-lookup"><span data-stu-id="539e3-124">Users will not be able to inherit permissions from other database roles, because the filter predicate is based on user or login names, not on roles.</span></span>

- <span data-ttu-id="539e3-125">Предоставьте ролям базы данных право доступа EXECUTE для хранимых процедур.</span><span class="sxs-lookup"><span data-stu-id="539e3-125">Grant EXECUTE on the stored procedures to database roles.</span></span> <span data-ttu-id="539e3-126">Пользователи смогут иметь доступ к данным только через предоставленные хранимые процедуры.</span><span class="sxs-lookup"><span data-stu-id="539e3-126">Users can only access data through the stored procedures provided.</span></span>

## <a name="see-also"></a><span data-ttu-id="539e3-127">См. также</span><span class="sxs-lookup"><span data-stu-id="539e3-127">See also</span></span>

- [<span data-ttu-id="539e3-128">Безопасность на уровне строк</span><span class="sxs-lookup"><span data-stu-id="539e3-128">Row-Level Security</span></span>](/sql/relational-databases/security/row-level-security)
- [<span data-ttu-id="539e3-129">Защита приложений ADO.NET</span><span class="sxs-lookup"><span data-stu-id="539e3-129">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="539e3-130">Общие сведения о безопасности SQL Server</span><span class="sxs-lookup"><span data-stu-id="539e3-130">Overview of SQL Server Security</span></span>](overview-of-sql-server-security.md)
- [<span data-ttu-id="539e3-131">Сценарии безопасности приложений в SQL Server</span><span class="sxs-lookup"><span data-stu-id="539e3-131">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="539e3-132">Управление разрешениями с использованием хранимых процедур в SQL Server</span><span class="sxs-lookup"><span data-stu-id="539e3-132">Managing Permissions with Stored Procedures in SQL Server</span></span>](managing-permissions-with-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="539e3-133">Написание безопасного динамического кода SQL в SQL Server</span><span class="sxs-lookup"><span data-stu-id="539e3-133">Writing Secure Dynamic SQL in SQL Server</span></span>](writing-secure-dynamic-sql-in-sql-server.md)
- [<span data-ttu-id="539e3-134">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="539e3-134">ADO.NET Overview</span></span>](../ado-net-overview.md)
