---
description: Дополнительные сведения о членстве и поставщике ролей
title: Поставщик членства и ролей
ms.date: 03/30/2017
ms.assetid: 0d11a31c-e75f-4fcf-9cf4-b7f26e056bcd
ms.openlocfilehash: ec7c59729241f811b485195eb7e2f292fb604e03
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732388"
---
# <a name="membership-and-role-provider"></a><span data-ttu-id="58ea3-103">Поставщик членства и ролей</span><span class="sxs-lookup"><span data-stu-id="58ea3-103">Membership and Role Provider</span></span>

<span data-ttu-id="58ea3-104">В образце поставщика членства и роли показано, как служба может использовать поставщиков членства и ролей ASP.NET для проверки подлинности и авторизации клиентов.</span><span class="sxs-lookup"><span data-stu-id="58ea3-104">The Membership and Role Provider sample demonstrates how a service can use the ASP.NET membership and role providers to authenticate and authorize clients.</span></span>  
  
 <span data-ttu-id="58ea3-105">В этом образце клиентом является консольное приложение (EXE), а служба размещается в службах IIS.</span><span class="sxs-lookup"><span data-stu-id="58ea3-105">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="58ea3-106">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="58ea3-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="58ea3-107">В образце демонстрируются следующие возможности.</span><span class="sxs-lookup"><span data-stu-id="58ea3-107">The sample demonstrates how:</span></span>  
  
- <span data-ttu-id="58ea3-108">Клиент может проходить проверку подлинности по имени пользователя и паролю.</span><span class="sxs-lookup"><span data-stu-id="58ea3-108">A client can authenticate by using the username-password combination.</span></span>  
  
- <span data-ttu-id="58ea3-109">Сервер может проверить учетные данные клиента по отношению к поставщику членства ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="58ea3-109">The server can validate the client credentials against the ASP.NET membership provider.</span></span>  
  
- <span data-ttu-id="58ea3-110">Сервер может проходить проверку подлинности с помощью сертификата X.509 сервера.</span><span class="sxs-lookup"><span data-stu-id="58ea3-110">The server can be authenticated by using the server's X.509 certificate.</span></span>  
  
- <span data-ttu-id="58ea3-111">Сервер может сопоставлять прошедший проверку подлинности клиент с ролью с помощью поставщика роли ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="58ea3-111">The server can map the authenticated client to a role by using the ASP.NET role provider.</span></span>  
  
- <span data-ttu-id="58ea3-112">Сервер может использовать атрибут `PrincipalPermissionAttribute` для управления доступом к определенным методам, предоставляемым службой.</span><span class="sxs-lookup"><span data-stu-id="58ea3-112">The server can use the `PrincipalPermissionAttribute` to control access to certain methods that are exposed by the service.</span></span>  
  
 <span data-ttu-id="58ea3-113">Поставщики членства и ролей настраиваются на использование хранилища на базе SQL Server.</span><span class="sxs-lookup"><span data-stu-id="58ea3-113">The membership and role providers are configured to use a store backed by SQL Server.</span></span> <span data-ttu-id="58ea3-114">Строка подключения и другие параметры задаются в файле конфигурации службы.</span><span class="sxs-lookup"><span data-stu-id="58ea3-114">A connection string and various options are specified in the service configuration file.</span></span> <span data-ttu-id="58ea3-115">Поставщик участия получает имя `SqlMembershipProvider`, а поставщик ролей - имя `SqlRoleProvider`.</span><span class="sxs-lookup"><span data-stu-id="58ea3-115">The membership provider is given the name `SqlMembershipProvider` while the role provider is given the name `SqlRoleProvider`.</span></span>  
  
```xml  
<!-- Set the connection string for SQL Server -->  
<connectionStrings>  
  <add name="SqlConn"
       connectionString="Data Source=localhost;Integrated Security=SSPI;Initial Catalog=aspnetdb;" />  
</connectionStrings>  
  
<system.web>  
  <!-- Configure the Sql Membership Provider -->  
  <membership defaultProvider="SqlMembershipProvider" userIsOnlineTimeWindow="15">  
    <providers>  
      <clear />  
      <add
        name="SqlMembershipProvider"
        type="System.Web.Security.SqlMembershipProvider"
        connectionStringName="SqlConn"  
        applicationName="MembershipAndRoleProviderSample"  
        enablePasswordRetrieval="false"  
        enablePasswordReset="false"  
        requiresQuestionAndAnswer="false"  
        requiresUniqueEmail="true"  
        passwordFormat="Hashed" />  
    </providers>  
  </membership>  
  
  <!-- Configure the Sql Role Provider -->  
  <roleManager enabled ="true"
               defaultProvider ="SqlRoleProvider" >  
    <providers>  
      <add name ="SqlRoleProvider"
           type="System.Web.Security.SqlRoleProvider"
           connectionStringName="SqlConn"
           applicationName="MembershipAndRoleProviderSample"/>  
    </providers>  
  </roleManager>  
</system.web>  
```  
  
 <span data-ttu-id="58ea3-116">Служба предоставляет одну конечную точку для взаимодействия с ней. Эта точка задается в файле конфигурации Web.config.</span><span class="sxs-lookup"><span data-stu-id="58ea3-116">The service exposes a single endpoint for communicating with the service, which is defined by using the Web.config configuration file.</span></span> <span data-ttu-id="58ea3-117">Конечная точка состоит из адреса, привязки и контракта.</span><span class="sxs-lookup"><span data-stu-id="58ea3-117">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="58ea3-118">Привязка настраивается с помощью стандартного элемента `wsHttpBinding`, который по умолчанию использует проверку подлинности Windows.</span><span class="sxs-lookup"><span data-stu-id="58ea3-118">The binding is configured with a standard `wsHttpBinding`, which defaults to using Windows authentication.</span></span> <span data-ttu-id="58ea3-119">В этом образце стандартная привязка `wsHttpBinding` использует проверку подлинности имени пользователя.</span><span class="sxs-lookup"><span data-stu-id="58ea3-119">This sample sets the standard `wsHttpBinding` to use username authentication.</span></span> <span data-ttu-id="58ea3-120">Поведение определяет, что для проверки подлинности службы должен использоваться сертификат сервера.</span><span class="sxs-lookup"><span data-stu-id="58ea3-120">The behavior specifies that the server certificate is to be used for service authentication.</span></span> <span data-ttu-id="58ea3-121">Сертификат сервера должен содержать то же значение, что и `SubjectName` `findValue` атрибут в [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) элементе Configuration.</span><span class="sxs-lookup"><span data-stu-id="58ea3-121">The server certificate must contain the same value for the `SubjectName` as the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) configuration element.</span></span> <span data-ttu-id="58ea3-122">Кроме того, поведение указывает, что проверка подлинности пар "имя пользователя-пароль" выполняется поставщиком членства ASP.NET, а сопоставление ролей выполняется поставщиком роли ASP.NET путем указания имен, определенных для двух поставщиков.</span><span class="sxs-lookup"><span data-stu-id="58ea3-122">In addition the behavior specifies that authentication of username-password pairs is performed by the ASP.NET membership provider and role mapping is performed by the ASP.NET role provider by specifying the names defined for the two providers.</span></span>  
  
```xml  
<system.serviceModel>  
  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  
  <bindings>  
    <wsHttpBinding>  
      <!-- Set up a binding that uses Username as the client credential type -->  
      <binding>  
        <security mode ="Message">  
          <message clientCredentialType ="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <behaviors>  
    <serviceBehaviors>  
      <behavior>  
        <!-- Configure role based authorization to use the Role Provider -->  
        <serviceAuthorization principalPermissionMode ="UseAspNetRoles"  
                              roleProviderName ="SqlRoleProvider" />  
        <serviceCredentials>  
          <!-- Configure user name authentication to use the Membership Provider -->  
          <userNameAuthentication userNamePasswordValidationMode ="MembershipProvider"
                                  membershipProviderName ="SqlMembershipProvider"/>  
          <!-- Configure the service certificate -->  
          <serviceCertificate storeLocation ="LocalMachine"
                              storeName ="My"
                              x509FindType ="FindBySubjectName"  
                              findValue ="localhost" />  
        </serviceCredentials>  
        <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
        <serviceDebug includeExceptionDetailInFaults="false" />  
        <serviceMetadata httpGetEnabled="true"/>  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="58ea3-123">При запуске этого образца клиент вызывает различные операции службы от имени различных учетных записей пользователей: Alice, Bob и Charlie.</span><span class="sxs-lookup"><span data-stu-id="58ea3-123">When you run the sample, the client calls the various service operations under three different user accounts: Alice, Bob, and Charlie.</span></span> <span data-ttu-id="58ea3-124">Запросы и ответы операций появляются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="58ea3-124">The operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="58ea3-125">Все четыре вызова от имени пользователя Alice должны завершиться успешно.</span><span class="sxs-lookup"><span data-stu-id="58ea3-125">All four calls made as user "Alice" should succeed.</span></span> <span data-ttu-id="58ea3-126">Пользователь Bob должен получить отказ в доступе при попытке вызвать метод Divide.</span><span class="sxs-lookup"><span data-stu-id="58ea3-126">User "Bob" should get an access denied error when trying to call the Divide method.</span></span> <span data-ttu-id="58ea3-127">Пользователь Charlie должен получить отказ в доступе при попытке вызвать метод Multiply.</span><span class="sxs-lookup"><span data-stu-id="58ea3-127">User "Charlie" should get an access denied error when trying to call the Multiply method.</span></span> <span data-ttu-id="58ea3-128">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="58ea3-128">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="58ea3-129">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="58ea3-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="58ea3-130">Чтобы создать выпуск решения на C# или Visual Basic .NET, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="58ea3-130">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
2. <span data-ttu-id="58ea3-131">Убедитесь, что вы настроили [базу данных Службы приложений ASP.NET](https://go.microsoft.com/fwlink/?LinkId=94997).</span><span class="sxs-lookup"><span data-stu-id="58ea3-131">Ensure that you have configured the [ASP.NET Application Services Database](https://go.microsoft.com/fwlink/?LinkId=94997).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="58ea3-132">Если используется выпуск SQL Server Express Edition, то сервер имеет имя .\SQLEXPRESS.</span><span class="sxs-lookup"><span data-stu-id="58ea3-132">If you are running SQL Server Express Edition, your server name is .\SQLEXPRESS.</span></span> <span data-ttu-id="58ea3-133">Этот сервер следует использовать при настройке базы данных ASP.NET Службы приложений, а также в строке подключения Web.config.</span><span class="sxs-lookup"><span data-stu-id="58ea3-133">This server should be used when configuring the ASP.NET Application Services Database as well as in the Web.config connection string.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="58ea3-134">Учетная запись рабочего процесса ASP.NET должна иметь разрешения на базу данных, созданную на этом шаге.</span><span class="sxs-lookup"><span data-stu-id="58ea3-134">The ASP.NET worker process account must have permissions on the database that is created in this step.</span></span> <span data-ttu-id="58ea3-135">Для этого воспользуйтесь служебной программой sqlcmd или средой SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="58ea3-135">Use the sqlcmd utility or SQL Server Management Studio to do this.</span></span>  
  
3. <span data-ttu-id="58ea3-136">Чтобы запустить образец на одном или нескольких компьютерах, следуйте приведенным далее инструкциям.</span><span class="sxs-lookup"><span data-stu-id="58ea3-136">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="58ea3-137">Запуск образца на одном компьютере</span><span class="sxs-lookup"><span data-stu-id="58ea3-137">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="58ea3-138">Убедитесь, что путь включает папку, в которой хранится файл Makecert.exe.</span><span class="sxs-lookup"><span data-stu-id="58ea3-138">Make sure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2. <span data-ttu-id="58ea3-139">Запустите Setup.bat из папки примера установки в Командная строка разработчика для запуска Visual Studio с правами администратора.</span><span class="sxs-lookup"><span data-stu-id="58ea3-139">Run Setup.bat from the sample install folder in a Developer Command Prompt for Visual Studio run with administrator privileges.</span></span> <span data-ttu-id="58ea3-140">Он устанавливает сертификаты службы, необходимые для запуска образца.</span><span class="sxs-lookup"><span data-stu-id="58ea3-140">This installs the service certificates required for running the sample.</span></span>  
  
3. <span data-ttu-id="58ea3-141">Запустите программу Client.exe из каталога \client\bin.</span><span class="sxs-lookup"><span data-stu-id="58ea3-141">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="58ea3-142">Действия клиента отображаются в консольном приложении клиента.</span><span class="sxs-lookup"><span data-stu-id="58ea3-142">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="58ea3-143">Если клиент и служба не могут обмениваться данными, см. раздел [Советы по устранению неполадок для примеров WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="58ea3-143">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="58ea3-144">Запуск образца на нескольких компьютерах</span><span class="sxs-lookup"><span data-stu-id="58ea3-144">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="58ea3-145">Создайте каталог на компьютере службы.</span><span class="sxs-lookup"><span data-stu-id="58ea3-145">Create a directory on the service computer.</span></span> <span data-ttu-id="58ea3-146">Создайте для этого каталога виртуальное приложение servicemodelsamples, с помощью средства управления службами IIS.</span><span class="sxs-lookup"><span data-stu-id="58ea3-146">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="58ea3-147">Скопируйте файлы служебной программы из каталога «\inetpub\wwwroot\servicemodelsamples» в виртуальный каталог на компьютере службы.</span><span class="sxs-lookup"><span data-stu-id="58ea3-147">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="58ea3-148">Убедитесь, что скопированы все файлы из подкаталога \bin.</span><span class="sxs-lookup"><span data-stu-id="58ea3-148">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="58ea3-149">Кроме того, скопируйте на компьютер службы файлы Setup.bat, GetComputerName.vbs и Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="58ea3-149">Also copy the Setup.bat, GetComputerName.vbs, and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="58ea3-150">Создайте на клиентском компьютере каталог для двоичных файлов клиента.</span><span class="sxs-lookup"><span data-stu-id="58ea3-150">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="58ea3-151">Скопируйте в клиентский каталог на клиентском компьютере файлы программы клиента.</span><span class="sxs-lookup"><span data-stu-id="58ea3-151">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="58ea3-152">Кроме того, скопируйте на клиент файлы Setup.bat, Cleanup.bat и ImportServiceCert.bat.</span><span class="sxs-lookup"><span data-stu-id="58ea3-152">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="58ea3-153">На сервере откройте Командная строка разработчика для Visual Studio с правами администратора и выполните команду `setup.bat service` .</span><span class="sxs-lookup"><span data-stu-id="58ea3-153">On the server, open a Developer Command Prompt for Visual Studio with administrative privileges and run `setup.bat service`.</span></span> <span data-ttu-id="58ea3-154">`setup.bat`При запуске с `service` аргументом создается сертификат службы с полным доменным именем компьютера и экспортируется сертификат службы в файл с именем Service. cer.</span><span class="sxs-lookup"><span data-stu-id="58ea3-154">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="58ea3-155">Измените Web.config, чтобы отразить новое имя сертификата (в `findValue` атрибуте в [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) ), которое совпадает с полным доменным именем компьютера.</span><span class="sxs-lookup"><span data-stu-id="58ea3-155">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7. <span data-ttu-id="58ea3-156">Скопируйте файл Service.cer из каталога службы в клиентский каталог на клиентском компьютере.</span><span class="sxs-lookup"><span data-stu-id="58ea3-156">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="58ea3-157">В файле Client.exe.config на клиентском компьютере измените значение адреса конечной точки, чтобы оно соответствовало новому адресу службы.</span><span class="sxs-lookup"><span data-stu-id="58ea3-157">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="58ea3-158">На клиенте откройте Командная строка разработчика для Visual Studio с правами администратора и запустите ImportServiceCert.bat.</span><span class="sxs-lookup"><span data-stu-id="58ea3-158">On the client, open a Developer Command Prompt for Visual Studio with administrative privileges and run ImportServiceCert.bat.</span></span> <span data-ttu-id="58ea3-159">Он импортирует сертификат службы из файла Service.cer в хранилище CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="58ea3-159">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="58ea3-160">На клиентском компьютере из командной строки запустите программу Client.exe.</span><span class="sxs-lookup"><span data-stu-id="58ea3-160">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="58ea3-161">Если клиент и служба не могут обмениваться данными, см. раздел [Советы по устранению неполадок для примеров WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="58ea3-161">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="58ea3-162">Очистка после образца</span><span class="sxs-lookup"><span data-stu-id="58ea3-162">To clean up after the sample</span></span>  
  
- <span data-ttu-id="58ea3-163">После завершения работы образца запустите в папке образцов файл Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="58ea3-163">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="58ea3-164">Этот скрипт не удаляет сертификаты службы на клиенте при запуске образца на нескольких компьютерах.</span><span class="sxs-lookup"><span data-stu-id="58ea3-164">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="58ea3-165">Если вы выполнили примеры Windows Communication Foundation (WCF), использующие сертификаты на нескольких компьютерах, обязательно очистите сертификаты службы, установленные в хранилище CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="58ea3-165">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="58ea3-166">Для этого воспользуйтесь следующей командой: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`. Например: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="58ea3-166">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="the-setup-batch-file"></a><span data-ttu-id="58ea3-167">Файл Setup.bat</span><span class="sxs-lookup"><span data-stu-id="58ea3-167">The Setup Batch File</span></span>  

 <span data-ttu-id="58ea3-168">Входящий в состав образца файл Setup.bat позволяет настроить для сервера соответствующие сертификаты, необходимые для выполнения резидентного приложения, которое требует обеспечения безопасности на основе сертификата сервера.</span><span class="sxs-lookup"><span data-stu-id="58ea3-168">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="58ea3-169">Этот пакетный файл необходимо изменить, чтобы его можно было использовать на нескольких компьютерах или без размещения приложения.</span><span class="sxs-lookup"><span data-stu-id="58ea3-169">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="58ea3-170">Ниже представлены общие сведения о различных разделах пакетных файлов, позволяющие изменять их для выполнения в соответствующей конфигурации.</span><span class="sxs-lookup"><span data-stu-id="58ea3-170">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>  
  
- <span data-ttu-id="58ea3-171">Создание сертификата сервера.</span><span class="sxs-lookup"><span data-stu-id="58ea3-171">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="58ea3-172">Следующие строки из файла Setup.bat создают используемый в дальнейшем сертификат сервера.</span><span class="sxs-lookup"><span data-stu-id="58ea3-172">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="58ea3-173">Переменная %SERVER_NAME% задает имя сервера.</span><span class="sxs-lookup"><span data-stu-id="58ea3-173">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="58ea3-174">Измените эту переменную, чтобы задать собственное имя сервера.</span><span class="sxs-lookup"><span data-stu-id="58ea3-174">Change this variable to specify your own server name.</span></span> <span data-ttu-id="58ea3-175">По умолчанию в этом пакетном файле используется имя localhost.</span><span class="sxs-lookup"><span data-stu-id="58ea3-175">This batch file defaults it to localhost.</span></span>  
  
     <span data-ttu-id="58ea3-176">Сертификат хранится в хранилище «My store (Личном хранилище)» в расположении LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="58ea3-176">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span>  
  
    ```console
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
- <span data-ttu-id="58ea3-177">Установка сертификата сервера в хранилище доверенных сертификатов клиента.</span><span class="sxs-lookup"><span data-stu-id="58ea3-177">Installing the server certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="58ea3-178">Следующие строки из файла Setup.bat копируют сертификат сервера в хранилище доверенных лиц клиента.</span><span class="sxs-lookup"><span data-stu-id="58ea3-178">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="58ea3-179">Этот шаг является обязательным, поскольку сертификаты, созданные с помощью программы Makecert.exe, не получают неявного доверия со стороны клиентской системы.</span><span class="sxs-lookup"><span data-stu-id="58ea3-179">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="58ea3-180">Если уже имеется сертификат, имеющий доверенный корневой сертификат клиента, например сертификат, выпущенный корпорацией Майкрософт, выполнять этот шаг по добавлению сертификата сервера в хранилище сертификатов клиента не требуется.</span><span class="sxs-lookup"><span data-stu-id="58ea3-180">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```bat  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```
