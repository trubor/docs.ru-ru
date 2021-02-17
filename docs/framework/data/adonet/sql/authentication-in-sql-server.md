---
title: Аутентификация в SQL Server
description: Сведения о проверке подлинности с помощью SQL Server для ADO.NET, включая режим проверки подлинности Windows и смешанный режим.
ms.date: 05/22/2018
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
ms.openlocfilehash: a1ecc0debd584797f72a89318aadc6ccc8a41062
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/17/2021
ms.locfileid: "100581932"
---
# <a name="authentication-in-sql-server"></a><span data-ttu-id="d1a4c-103">Аутентификация в SQL Server</span><span class="sxs-lookup"><span data-stu-id="d1a4c-103">Authentication in SQL Server</span></span>

<span data-ttu-id="d1a4c-104">SQL Server поддерживает два режима проверки подлинности: режим проверки подлинности Windows и режим смешанной проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-104">SQL Server supports two authentication modes, Windows authentication mode and mixed mode.</span></span>  
  
- <span data-ttu-id="d1a4c-105">Режим проверки подлинности Windows является режимом по умолчанию. Поскольку эта модель безопасности SQL Server тесно интегрирована с Windows, часто ее называют встроенной функцией безопасности.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-105">Windows authentication is the default, and is often referred to as integrated security because this SQL Server security model is tightly integrated with Windows.</span></span> <span data-ttu-id="d1a4c-106">Для входа в SQL Server в список надежных элементов вносятся определенные учетные записи пользователей и группы Windows.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-106">Specific Windows user and group accounts are trusted to log in to SQL Server.</span></span> <span data-ttu-id="d1a4c-107">Пользователям Windows, которые уже прошли аутентификацию, не нужно представлять дополнительные учетные данные.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-107">Windows users who have already been authenticated do not have to present additional credentials.</span></span>  
  
- <span data-ttu-id="d1a4c-108">Режим смешанной аутентификации поддерживает проверку подлинности как средствами Windows, так и средствами SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-108">Mixed mode supports authentication both by Windows and by SQL Server.</span></span> <span data-ttu-id="d1a4c-109">Пары имен пользователей и паролей хранятся в SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-109">User name and password pairs are maintained within SQL Server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d1a4c-110">Мы рекомендуем использовать проверку подлинности Windows везде, где это возможно.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-110">We recommend using Windows authentication wherever possible.</span></span> <span data-ttu-id="d1a4c-111">При проверке подлинности Windows используется ряд зашифрованных сообщений для проверки подлинности пользователей в SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-111">Windows authentication uses a series of encrypted messages to authenticate users in SQL Server.</span></span> <span data-ttu-id="d1a4c-112">А при использовании имен входа SQL Server имена входа и зашифрованные пароли SQL Server передаются по сети, что делает их менее защищенными.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-112">When SQL Server logins are used, SQL Server login names and encrypted passwords are passed across the network, which makes them less secure.</span></span>  
  
 <span data-ttu-id="d1a4c-113">При использовании проверки подлинности Windows пользователи уже вошли в Windows и им не нужно отдельно входить еще и в SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-113">With Windows authentication, users are already logged onto Windows and do not have to log on separately to SQL Server.</span></span> <span data-ttu-id="d1a4c-114">Следующая строка `SqlConnection.ConnectionString` задает проверку подлинности Windows, не требуя имени пользователя или пароля.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-114">The following `SqlConnection.ConnectionString` specifies Windows authentication without requiring users to provide a user name or password.</span></span>  
  
```csharp  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;"
```  
  
> [!NOTE]
> <span data-ttu-id="d1a4c-115">Имена для входа отличаются от пользователей базы данных.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-115">Logins are distinct from database users.</span></span> <span data-ttu-id="d1a4c-116">Вы должны сопоставить имена для входа или группы Windows пользователям базы данных или ролям в отдельной операции.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-116">You must map logins or Windows groups to database users or roles in a separate operation.</span></span> <span data-ttu-id="d1a4c-117">Затем вы предоставляете пользователям или ролям разрешения на доступ к объектам базы данных.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-117">You then grant permissions to users or roles to access database objects.</span></span>  
  
## <a name="authentication-scenarios"></a><span data-ttu-id="d1a4c-118">Сценарии проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="d1a4c-118">Authentication Scenarios</span></span>  

 <span data-ttu-id="d1a4c-119">Проверка подлинности Windows обычно является лучшим выбором в следующих ситуациях:</span><span class="sxs-lookup"><span data-stu-id="d1a4c-119">Windows authentication is usually the best choice in the following situations:</span></span>  
  
- <span data-ttu-id="d1a4c-120">Есть контроллер домена.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-120">There is a domain controller.</span></span>  
  
- <span data-ttu-id="d1a4c-121">Приложение и база данных находятся на одном компьютере.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-121">The application and the database are on the same computer.</span></span>  
  
- <span data-ttu-id="d1a4c-122">Используется экземпляр SQL Server Express или LocalDB.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-122">You are using an instance of SQL Server Express or LocalDB.</span></span>  
  
 <span data-ttu-id="d1a4c-123">Имена для входа SQL-сервера часто используются в следующих ситуациях:</span><span class="sxs-lookup"><span data-stu-id="d1a4c-123">SQL Server logins are often used in the following situations:</span></span>  
  
- <span data-ttu-id="d1a4c-124">Если у вас есть рабочая группа.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-124">If you have a workgroup.</span></span>  
  
- <span data-ttu-id="d1a4c-125">Пользователи соединяются из разных, ненадежных доменов.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-125">Users connect from different, non-trusted domains.</span></span>  
  
- <span data-ttu-id="d1a4c-126">Существуют интернет-приложения, такие как ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-126">Internet applications, such as ASP.NET.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d1a4c-127">При использовании аутентификации Windows имена входа SQL Server не отключаются.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-127">Specifying Windows authentication does not disable SQL Server logins.</span></span> <span data-ttu-id="d1a4c-128">Чтобы отключить имена входа SQL Server с правами доступа, используйте инструкцию Transact-SQL ALTER LOGIN DISABLE.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-128">Use the ALTER LOGIN DISABLE Transact-SQL statement to disable highly-privileged SQL Server logins.</span></span>  
  
## <a name="login-types"></a><span data-ttu-id="d1a4c-129">Типы имен входа</span><span class="sxs-lookup"><span data-stu-id="d1a4c-129">Login Types</span></span>  

 <span data-ttu-id="d1a4c-130">В SQL Server существует три типа имен входа.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-130">SQL Server supports three types of logins:</span></span>  
  
- <span data-ttu-id="d1a4c-131">Локальная учетная запись пользователя Windows или доверенная учетная запись домена.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-131">A local Windows user account or trusted domain account.</span></span> <span data-ttu-id="d1a4c-132">SQL Server доверяет проверку подлинности учетных записей пользователей Windows самой системе Windows.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-132">SQL Server relies on Windows to authenticate the Windows user accounts.</span></span>  
  
- <span data-ttu-id="d1a4c-133">Группа Windows.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-133">Windows group.</span></span> <span data-ttu-id="d1a4c-134">Предоставление доступа группе Windows обеспечивает доступ ко всем именам входа пользователей Windows, которые являются членами группы.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-134">Granting access to a Windows group grants access to all Windows user logins that are members of the group.</span></span>  
  
- <span data-ttu-id="d1a4c-135">Имя входа SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-135">SQL Server login.</span></span> <span data-ttu-id="d1a4c-136">SQL Server хранит в базе данных master имя пользователя и хэш пароля путем использования внутренних методов проверки подлинности при попытке входа в базу данных.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-136">SQL Server stores both the username and a hash of the password in the master database, by using internal authentication methods to verify login attempts.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d1a4c-137">SQL Server предоставляет имена входа, созданные из сертификатов или асимметричных ключей, которые используются только для подписывания кода.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-137">SQL Server provides logins created from certificates or asymmetric keys that are used only for code signing.</span></span> <span data-ttu-id="d1a4c-138">Они не могут использоваться для подключения к SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-138">They cannot be used to connect to SQL Server.</span></span>  
  
## <a name="mixed-mode-authentication"></a><span data-ttu-id="d1a4c-139">Режим смешанной проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="d1a4c-139">Mixed Mode Authentication</span></span>  

 <span data-ttu-id="d1a4c-140">При необходимости использовать режим смешанной проверки подлинности следует создать имена входа SQL Server, которые хранятся в SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-140">If you must use mixed mode authentication, you must create SQL Server logins, which are stored in SQL Server.</span></span> <span data-ttu-id="d1a4c-141">Затем имя пользователя и пароль SQL Server нужно будет вводить во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-141">You then have to supply the SQL Server user name and password at run time.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d1a4c-142">SQL Server устанавливается с логином SQL Server с именем `sa`. (сокращение от "system administrator").</span><span class="sxs-lookup"><span data-stu-id="d1a4c-142">SQL Server installs with a SQL Server login named `sa` (an abbreviation of "system administrator").</span></span> <span data-ttu-id="d1a4c-143">Назначьте надежный пароль для имени входа `sa` и не используйте имя входа `sa` в вашем приложении.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-143">Assign a strong password to the `sa` login and do not use the `sa` login in your application.</span></span> <span data-ttu-id="d1a4c-144">Карты входа `sa` на фиксированную серверную роль `sysadmin`, которая имеет безотзывные административные учетные данные на всем сервере.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-144">The `sa` login maps to the `sysadmin` fixed server role, which has irrevocable administrative credentials on the whole server.</span></span> <span data-ttu-id="d1a4c-145">Нет никаких ограничений на потенциальный ущерб, если злоумышленник получит доступ в качестве системного администратора.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-145">There are no limits to the potential damage if an attacker gains access as a system administrator.</span></span>
  
 <span data-ttu-id="d1a4c-146">SQL Server предоставляет механизмы политики паролей Windows для имен входа SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-146">SQL Server provides Windows password policy mechanisms for SQL Server logins.</span></span> <span data-ttu-id="d1a4c-147">Политика сложности паролей позволяет отражать атаки, использующие простой перебор, путем увеличения числа возможных паролей.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-147">Password complexity policies are designed to deter brute force attacks by increasing the number of possible passwords.</span></span> <span data-ttu-id="d1a4c-148">SQL Server могут применять те же политики сложности и срока действия к паролям, которые используются в SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-148">SQL Server can apply the same complexity and expiration policies to passwords used inside SQL Server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d1a4c-149">Сосредоточение строк соединения из пользовательского ввода может сделать ваш сервер уязвимым к атаке путем внедрения строки подключения.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-149">Concatenating connection strings from user input can leave you vulnerable to a connection string injection attack.</span></span> <span data-ttu-id="d1a4c-150">Используйте <xref:System.Data.SqlClient.SqlConnectionStringBuilder> для создания синтаксически корректных строк подключения во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-150">Use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="d1a4c-151">Дополнительные сведения см. в статье [Connection String Builders](../connection-string-builders.md) (Построители строк подключения).</span><span class="sxs-lookup"><span data-stu-id="d1a4c-151">For more information, see [Connection String Builders](../connection-string-builders.md).</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="d1a4c-152">Внешние ресурсы</span><span class="sxs-lookup"><span data-stu-id="d1a4c-152">External Resources</span></span>  

 <span data-ttu-id="d1a4c-153">Для получения дополнительных сведений см. следующие ресурсы.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-153">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="d1a4c-154">Ресурс</span><span class="sxs-lookup"><span data-stu-id="d1a4c-154">Resource</span></span>|<span data-ttu-id="d1a4c-155">Description</span><span class="sxs-lookup"><span data-stu-id="d1a4c-155">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="d1a4c-156">Субъекты</span><span class="sxs-lookup"><span data-stu-id="d1a4c-156">Principals</span></span>](/sql/relational-databases/security/authentication-access/principals-database-engine)|<span data-ttu-id="d1a4c-157">Описывает имена входа и других участников безопасности, имеющихся в SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d1a4c-157">Describes logins and other security principals in SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d1a4c-158">См. также</span><span class="sxs-lookup"><span data-stu-id="d1a4c-158">See also</span></span>

- [<span data-ttu-id="d1a4c-159">Защита приложений ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d1a4c-159">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="d1a4c-160">Сценарии безопасности приложений в SQL Server</span><span class="sxs-lookup"><span data-stu-id="d1a4c-160">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="d1a4c-161">Подключение к источнику данных</span><span class="sxs-lookup"><span data-stu-id="d1a4c-161">Connecting to a Data Source</span></span>](../connecting-to-a-data-source.md)
- [<span data-ttu-id="d1a4c-162">Строки подключения</span><span class="sxs-lookup"><span data-stu-id="d1a4c-162">Connection Strings</span></span>](../connection-strings.md)
- [<span data-ttu-id="d1a4c-163">Общие сведения об ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d1a4c-163">ADO.NET Overview</span></span>](../ado-net-overview.md)
