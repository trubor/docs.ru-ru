---
description: 'Дополнительные сведения: безопасность пользовательской привязки'
title: Безопасность пользовательской привязки
ms.date: 03/30/2017
ms.assetid: a6383dff-4308-46d2-bc6d-acd4e18b4b8d
ms.openlocfilehash: f0ed4b40fe4e0869f34a4f6016123dc9f0a57f45
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732635"
---
# <a name="custom-binding-security"></a><span data-ttu-id="af724-103">Безопасность пользовательской привязки</span><span class="sxs-lookup"><span data-stu-id="af724-103">Custom Binding Security</span></span>

<span data-ttu-id="af724-104">В этом образце показано, как настроить безопасность с помощью пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="af724-104">This sample demonstrates how to configure security by using a custom binding.</span></span> <span data-ttu-id="af724-105">Здесь показано, как использовать пользовательскую привязку для включения безопасности на уровне сообщений вместе с безопасным транспортом.</span><span class="sxs-lookup"><span data-stu-id="af724-105">It shows how to use a custom binding to enable message-level security together with a secure transport.</span></span> <span data-ttu-id="af724-106">Это полезно, когда требуется передавать сообщения между клиентом и службой с помощью безопасного транспорта с одновременным обеспечением безопасности на уровне сообщений.</span><span class="sxs-lookup"><span data-stu-id="af724-106">This is useful when a secure transport is required to transmit the messages between client and service and simultaneously the messages must be secure on the message level.</span></span> <span data-ttu-id="af724-107">Эта конфигурация не поддерживается привязками, предоставляемыми системой.</span><span class="sxs-lookup"><span data-stu-id="af724-107">This configuration is not supported by system-provided bindings.</span></span>

<span data-ttu-id="af724-108">Этот образец состоит из консольной программы клиента (EXE) и консольной программы службы (EXE).</span><span class="sxs-lookup"><span data-stu-id="af724-108">This sample consists of a client console program (EXE) and a service console program (EXE).</span></span> <span data-ttu-id="af724-109">Служба реализует дуплексный контракт.</span><span class="sxs-lookup"><span data-stu-id="af724-109">The service implements a duplex contract.</span></span> <span data-ttu-id="af724-110">Контракт определяется интерфейсом `ICalculatorDuplex`, который предоставляет математические операции (добавить, вычесть, умножить и разделить).</span><span class="sxs-lookup"><span data-stu-id="af724-110">The contract is defined by the `ICalculatorDuplex` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="af724-111">Интерфейс `ICalculatorDuplex` позволяет клиенту выполнять математические операции, вычисляя результат выполнения в сеансе.</span><span class="sxs-lookup"><span data-stu-id="af724-111">The `ICalculatorDuplex` interface allows the client to perform math operations, calculating a running result over a session.</span></span> <span data-ttu-id="af724-112">Независимо от этого служба может возвратить результаты в интерфейсе `ICalculatorDuplexCallback`.</span><span class="sxs-lookup"><span data-stu-id="af724-112">Independently, the service may return results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="af724-113">Для дуплексного контракта требуется сеанс, поскольку необходимо установить контекст для корреляции набора сообщений, передаваемых между клиентом и службой.</span><span class="sxs-lookup"><span data-stu-id="af724-113">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between the client and the service.</span></span> <span data-ttu-id="af724-114">Определяется пользовательская привязка, которая поддерживает дуплексное взаимодействие и является безопасной.</span><span class="sxs-lookup"><span data-stu-id="af724-114">A custom binding is defined that supports duplex communication and is secure.</span></span>

> [!NOTE]
> <span data-ttu-id="af724-115">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="af724-115">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="af724-116">Конфигурация службы определяет пользовательскую привязку, поддерживающую следующее.</span><span class="sxs-lookup"><span data-stu-id="af724-116">The service configuration defines a custom binding that supports the following:</span></span>

- <span data-ttu-id="af724-117">Обмен данными по протоколу TCP, защищенный с помощью протокола TLS/SSL.</span><span class="sxs-lookup"><span data-stu-id="af724-117">TCP communication protected by using the TLS/SSL protocol.</span></span>

- <span data-ttu-id="af724-118">Безопасность сообщений Windows.</span><span class="sxs-lookup"><span data-stu-id="af724-118">Windows message security.</span></span>

<span data-ttu-id="af724-119">Конфигурация пользовательской привязки предоставляет безопасный транспорт, одновременно обеспечивая безопасность на уровне сообщений.</span><span class="sxs-lookup"><span data-stu-id="af724-119">The custom binding configuration enables secure transport by simultaneously enabling the message-level security.</span></span> <span data-ttu-id="af724-120">Порядок элементов привязки важен для определения пользовательской привязки, так как каждый из них представляет слой в стеке каналов (см. раздел [пользовательские привязки](../extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="af724-120">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../extending/custom-bindings.md)).</span></span> <span data-ttu-id="af724-121">Пользовательская привязка определяется в файлах конфигурации службы и клиента, как показано в следующем образце конфигурации.</span><span class="sxs-lookup"><span data-stu-id="af724-121">The custom binding is defined in the service and client configuration files, as shown in the following sample configuration.</span></span>

```xml
<bindings>
  <!-- Configure a custom binding. -->
  <customBinding>
    <binding name="Binding1">
      <security authenticationMode="SecureConversation"
                 requireSecurityContextCancellation="true">
      </security>
      <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>
      <sslStreamSecurity requireClientCertificate="false"/>
      <tcpTransport/>
    </binding>
  </customBinding>
</bindings>
```

<span data-ttu-id="af724-122">Пользовательская привязка использует сертификат службы для проверки подлинности службы на уровне транспорта и для защиты сообщений при передаче между клиентом и службой.</span><span class="sxs-lookup"><span data-stu-id="af724-122">The custom binding uses a service certificate to authenticate the service on the transport level and to protect the messages during the transmission between client and service.</span></span> <span data-ttu-id="af724-123">Это возможно благодаря элементу привязки `sslStreamSecurity`.</span><span class="sxs-lookup"><span data-stu-id="af724-123">This is accomplished by the `sslStreamSecurity` binding element.</span></span> <span data-ttu-id="af724-124">Сертификат службы настраивается с помощью поведения службы, как показано в следующем образце конфигурации.</span><span class="sxs-lookup"><span data-stu-id="af724-124">The service's certificate is configured using a service behavior as shown in the following sample configuration.</span></span>

```xml
<behaviors>
    <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
        <serviceMetadata />
        <serviceDebug includeExceptionDetailInFaults="False" />
        <serviceCredentials>
        <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName"/>
        </serviceCredentials>
    </behavior>
    </serviceBehaviors>
</behaviors>
```

<span data-ttu-id="af724-125">Кроме того, пользовательская привязка использует безопасность сообщений с типом учетных данных Windows, который является типом учетных данных по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="af724-125">Additionally, the custom binding uses message security with Windows credential type - this is the default credential type.</span></span> <span data-ttu-id="af724-126">Это возможно благодаря элементу привязки `security`.</span><span class="sxs-lookup"><span data-stu-id="af724-126">This is accomplished by the `security` binding element.</span></span> <span data-ttu-id="af724-127">Если доступен механизм проверки подлинности Kerberos, то проверка подлинности как клиента, так и службы выполняется с использованием безопасности уровня сообщений.</span><span class="sxs-lookup"><span data-stu-id="af724-127">Both client and service are authenticated using message-level security if the Kerberos authentication mechanism is available.</span></span> <span data-ttu-id="af724-128">Это происходит при выполнении образца в среде Active Directory.</span><span class="sxs-lookup"><span data-stu-id="af724-128">This happens if the sample is run in the Active Directory environment.</span></span> <span data-ttu-id="af724-129">Если механизм проверки подлинности Kerberos недоступен, используется проверка подлинности NTLM.</span><span class="sxs-lookup"><span data-stu-id="af724-129">If the Kerberos authentication mechanism is not available, NTLM authentication is used.</span></span> <span data-ttu-id="af724-130">NTLM выполняет проверку подлинности клиента при подключении к службе, но не выполняет проверку подлинности службы при подключении к клиенту.</span><span class="sxs-lookup"><span data-stu-id="af724-130">NTLM authenticates the client to the service but does not authenticate the service to the client.</span></span> <span data-ttu-id="af724-131">`security`Элемент Binding настроен для использования `SecureConversation` `authenticationType` , что приводит к созданию сеанса безопасности на клиенте и в службе.</span><span class="sxs-lookup"><span data-stu-id="af724-131">The `security` binding element is configured to use `SecureConversation` `authenticationType`, which results in the creation of a security session on both the client and the service.</span></span> <span data-ttu-id="af724-132">Это требуется для обеспечения работы дуплексного контракта службы.</span><span class="sxs-lookup"><span data-stu-id="af724-132">This is required to enable the service's duplex contract to work.</span></span>

<span data-ttu-id="af724-133">При выполнении образца запросы и ответы операций отображаются в окне консоли клиента.</span><span class="sxs-lookup"><span data-stu-id="af724-133">When you run the sample, the operation requests and responses are displayed in the client's console window.</span></span> <span data-ttu-id="af724-134">Чтобы закрыть клиент, нажмите клавишу ВВОД в окне клиента.</span><span class="sxs-lookup"><span data-stu-id="af724-134">Press ENTER in the client window to shut down the client.</span></span>

```console
Press <ENTER> to terminate client.
Result(100)
Result(50)
Result(882.5)
Result(441.25)
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)
```

<span data-ttu-id="af724-135">При выполнении образца видны отправляемые службой сообщения, возвращаемые клиенту в интерфейсе обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="af724-135">When you run the sample, you see the messages returned to the client on the callback interface sent from the service.</span></span> <span data-ttu-id="af724-136">Отображается каждый промежуточный результат с последующим отображением всей формулы после завершения всех операций.</span><span class="sxs-lookup"><span data-stu-id="af724-136">Each intermediate result is displayed, followed by the entire equation upon completion of all operations.</span></span> <span data-ttu-id="af724-137">Чтобы закрыть клиент, нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="af724-137">Press ENTER to shut down the client.</span></span>

<span data-ttu-id="af724-138">Входящий в состав образца файл Setup.bat позволяет настроить для клиента и сервера соответствующий сертификат службы, необходимый для выполнения резидентного приложения, которое требует обеспечения безопасности на основе сертификата.</span><span class="sxs-lookup"><span data-stu-id="af724-138">The included Setup.bat file enables you to configure the client and server with the relevant service certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="af724-139">Этот пакетный файл необходимо изменить, чтобы его можно было использовать на нескольких компьютерах или без размещения приложения.</span><span class="sxs-lookup"><span data-stu-id="af724-139">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

<span data-ttu-id="af724-140">Ниже представлены общие сведения о различных разделах пакетных файлов, применимых к этому образцу, которые можно изменить для выполнения в соответствующей конфигурации.</span><span class="sxs-lookup"><span data-stu-id="af724-140">The following provides a brief overview of the different sections of the batch files that apply to this sample so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="af724-141">Создание сертификата сервера.</span><span class="sxs-lookup"><span data-stu-id="af724-141">Creating the server certificate.</span></span>

  <span data-ttu-id="af724-142">Следующие строки из файла Setup.bat создают используемый в дальнейшем сертификат сервера.</span><span class="sxs-lookup"><span data-stu-id="af724-142">The following lines from the Setup.bat file create the server certificate to be used.</span></span> <span data-ttu-id="af724-143">Переменная `%SERVER_NAME%`задает имя сервера.</span><span class="sxs-lookup"><span data-stu-id="af724-143">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="af724-144">Измените эту переменную, чтобы задать собственное имя сервера.</span><span class="sxs-lookup"><span data-stu-id="af724-144">Change this variable to specify your own server name.</span></span> <span data-ttu-id="af724-145">По умолчанию в этом пакетном файле используется имя localhost.</span><span class="sxs-lookup"><span data-stu-id="af724-145">This batch file defaults the server name to localhost.</span></span>

  <span data-ttu-id="af724-146">Сертификат хранится в хранилище CurrentUser для служб, размещенных на веб-сервере.</span><span class="sxs-lookup"><span data-stu-id="af724-146">The certificate is stored in the CurrentUser store for the Web-hosted services.</span></span>

  ```bat
  echo ************
  echo Server cert setup starting
  echo %SERVER_NAME%
  echo ************
  echo making server cert
  echo ************
  makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
  ```

- <span data-ttu-id="af724-147">Установка сертификата сервера в хранилище доверенных сертификатов клиента.</span><span class="sxs-lookup"><span data-stu-id="af724-147">Installing the server certificate into the client's trusted certificate store.</span></span>

  <span data-ttu-id="af724-148">Следующие строки из файла Setup.bat копируют сертификат сервера в хранилище доверенных лиц клиента.</span><span class="sxs-lookup"><span data-stu-id="af724-148">The following lines in the Setup.bat file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="af724-149">Этот шаг является обязательным, поскольку сертификаты, созданные с помощью программы Makecert.exe, не получают неявного доверия со стороны клиентской системы.</span><span class="sxs-lookup"><span data-stu-id="af724-149">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="af724-150">Если уже имеется сертификат, имеющий доверенный корневой сертификат клиента, например сертификат, выпущенный корпорацией Майкрософт, выполнять этот шаг по добавлению сертификата сервера в хранилище сертификатов клиента не требуется.</span><span class="sxs-lookup"><span data-stu-id="af724-150">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

  ```console
  certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
  ```

  > [!NOTE]
  > <span data-ttu-id="af724-151">Пакетный файл Setup.bat предназначен для запуска из командной строки Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="af724-151">The Setup.bat batch file is designed to be run from a Visual Studio 2010 Command Prompt.</span></span> <span data-ttu-id="af724-152">Требуется, чтобы переменная среды MSSDK указывала на каталог, в котором установлен пакет SDK.</span><span class="sxs-lookup"><span data-stu-id="af724-152">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="af724-153">Эта переменная среды автоматически устанавливается в командной строке Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="af724-153">This environment variable is automatically set within a Visual Studio 2010 Command Prompt.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="af724-154">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="af724-154">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="af724-155">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="af724-155">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="af724-156">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="af724-156">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="af724-157">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="af724-157">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="af724-158">Запуск образца на одном компьютере</span><span class="sxs-lookup"><span data-stu-id="af724-158">To run the sample on the same computer</span></span>

1. <span data-ttu-id="af724-159">Откройте окно Командная строка разработчика для Visual Studio с правами администратора и запустите Setup.bat из примера установочной папки.</span><span class="sxs-lookup"><span data-stu-id="af724-159">Open a Developer Command Prompt for Visual Studio window with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="af724-160">При этом устанавливаются все сертификаты, необходимые для выполнения образца.</span><span class="sxs-lookup"><span data-stu-id="af724-160">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="af724-161">Пакетный файл Setup.bat предназначен для запуска из командной строки Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="af724-161">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="af724-162">Переменная среды PATH, заданная в командной строке Visual Studio 2012, указывает на каталог, содержащий исполняемые файлы, необходимые для скрипта Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="af724-162">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>

2. <span data-ttu-id="af724-163">Запустите программу Service.exe из каталога \service\bin.</span><span class="sxs-lookup"><span data-stu-id="af724-163">Launch Service.exe from \service\bin.</span></span>

3. <span data-ttu-id="af724-164">Запустите программу Client.exe из каталога \client\bin.</span><span class="sxs-lookup"><span data-stu-id="af724-164">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="af724-165">Действия клиента отображаются в консольном приложении клиента.</span><span class="sxs-lookup"><span data-stu-id="af724-165">Client activity is displayed on the client console application.</span></span>

4. <span data-ttu-id="af724-166">Если клиент и служба не могут обмениваться данными, см. раздел [Советы по устранению неполадок для примеров WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="af724-166">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="af724-167">Запуск образца на нескольких компьютерах</span><span class="sxs-lookup"><span data-stu-id="af724-167">To run the sample across computers</span></span>

1. <span data-ttu-id="af724-168">На компьютере службы выполните следующее.</span><span class="sxs-lookup"><span data-stu-id="af724-168">On the service computer:</span></span>

    1. <span data-ttu-id="af724-169">Создайте на компьютере службы виртуальный каталог с именем servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="af724-169">Create a virtual directory named servicemodelsamples on the service computer.</span></span>

    2. <span data-ttu-id="af724-170">Скопируйте файлы служебной программы из каталога «\inetpub\wwwroot\servicemodelsamples» в виртуальный каталог на компьютере службы.</span><span class="sxs-lookup"><span data-stu-id="af724-170">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="af724-171">Убедитесь, что скопированы все файлы из подкаталога \bin.</span><span class="sxs-lookup"><span data-stu-id="af724-171">Ensure that you copy the files in the \bin subdirectory.</span></span>

    3. <span data-ttu-id="af724-172">Скопируйте файлы Setup.bat и Cleanup.bat на компьютер службы.</span><span class="sxs-lookup"><span data-stu-id="af724-172">Copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>

    4. <span data-ttu-id="af724-173">Выполните следующую команду в Командная строка разработчика для Visual Studio, открытой с правами администратора: `Setup.bat service` .</span><span class="sxs-lookup"><span data-stu-id="af724-173">Run the following command in a Developer Command Prompt for Visual Studio opened with administrator privileges: `Setup.bat service`.</span></span> <span data-ttu-id="af724-174">При этом создается сертификат службы с именем субъекта, соответствующим имени компьютера, на котором запущен пакетный файл.</span><span class="sxs-lookup"><span data-stu-id="af724-174">This creates the service certificate with the subject name matching the name of the computer the batch file was run on.</span></span>

        > [!NOTE]
        > <span data-ttu-id="af724-175">Пакетный файл Setup.bat предназначен для запуска из командной строки Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="af724-175">The Setup.bat batch file is designed to be run from a Visual Studio 2010 Command Prompt.</span></span> <span data-ttu-id="af724-176">Необходимо, чтобы переменная среды path указывала на каталог, в котором установлен пакет SDK.</span><span class="sxs-lookup"><span data-stu-id="af724-176">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="af724-177">Эта переменная среды автоматически устанавливается в командной строке Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="af724-177">This environment variable is automatically set within a Visual Studio 2010 Command Prompt.</span></span>

    5. <span data-ttu-id="af724-178">Измените [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) содержимое файла Service.exe.config, чтобы оно отражало имя субъекта сертификата, созданного на предыдущем шаге.</span><span class="sxs-lookup"><span data-stu-id="af724-178">Change the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) inside the Service.exe.config file to reflect the subject name of the certificate generated in the previous step.</span></span>

    6. <span data-ttu-id="af724-179">Запустите файл Service.exe из командной строки.</span><span class="sxs-lookup"><span data-stu-id="af724-179">Run Service.exe from a command prompt.</span></span>

2. <span data-ttu-id="af724-180">На клиентском компьютере</span><span class="sxs-lookup"><span data-stu-id="af724-180">On the client computer:</span></span>

    1. <span data-ttu-id="af724-181">Скопируйте на клиентский компьютер файлы программы клиента из папки \client\bin\.</span><span class="sxs-lookup"><span data-stu-id="af724-181">Copy the client program files from the \client\bin\ folder to the client computer.</span></span> <span data-ttu-id="af724-182">Также скопируйте файл Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="af724-182">Also copy the Cleanup.bat file.</span></span>

    2. <span data-ttu-id="af724-183">Запустите файл Cleanup.bat, чтобы удалить все старые сертификаты из предыдущих образцов.</span><span class="sxs-lookup"><span data-stu-id="af724-183">Run Cleanup.bat to remove any old certificates from previous samples.</span></span>

    3. <span data-ttu-id="af724-184">Экспортируйте сертификат службы, открыв Командная строка разработчика для Visual Studio с правами администратора и выполнив следующую команду на компьютере службы (замените полным `%SERVER_NAME%` именем компьютера, на котором запущена служба):</span><span class="sxs-lookup"><span data-stu-id="af724-184">Export the service's certificate by opening a Developer Command Prompt for Visual Studio with administrative privileges, and running the following command on the service computer (substitute `%SERVER_NAME%` with the fully-qualified name of the computer where the service is running):</span></span>

        ```console
        certmgr -put -r LocalMachine -s My -c -n %SERVER_NAME% %SERVER_NAME%.cer
        ```

    4. <span data-ttu-id="af724-185">Скопируйте файл %SERVER_NAME%.cer на клиентский компьютер (замените %SERVER_NAME% на полное имя компьютера, на котором выполняется служба).</span><span class="sxs-lookup"><span data-stu-id="af724-185">Copy %SERVER_NAME%.cer to the client computer (substitute %SERVER_NAME% with the fully-qualified name of the computer where the service is running).</span></span>

    5. <span data-ttu-id="af724-186">Импортируйте сертификат службы, открыв Командная строка разработчика для Visual Studio с правами администратора и выполнив следующую команду на клиентском компьютере (замените% SERVER_NAME% на полное имя компьютера, на котором запущена служба):</span><span class="sxs-lookup"><span data-stu-id="af724-186">Import the service's certificate by opening a Developer Command Prompt for Visual Studio with administrative privileges, and running the following command on the client computer (substitute %SERVER_NAME% with the fully-qualified name of the computer where the service is running):</span></span>

        ```console
        certmgr.exe -add -c %SERVER_NAME%.cer -s -r CurrentUser TrustedPeople
        ```

        <span data-ttu-id="af724-187">Шаги c, d и e выполнять не обязательно, если сертификат выдан доверенным издателем.</span><span class="sxs-lookup"><span data-stu-id="af724-187">Steps c, d, and e are not necessary if the certificate is issued by a Trusted Issuer.</span></span>

    6. <span data-ttu-id="af724-188">Измените файл App.config клиента следующим образом.</span><span class="sxs-lookup"><span data-stu-id="af724-188">Modify the client’s App.config file as follows:</span></span>

        ```xml
        <client>
            <endpoint name="default"
                address="net.tcp://ReplaceThisWithServiceMachineName:8000/ServiceModelSamples/Service"
                binding="customBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex"
                behaviorConfiguration="CalculatorClientBehavior" />
        </client>
        ```

    7. <span data-ttu-id="af724-189">Если служба выполняется от имени учетной записи, отличной от NetworkService или LocalSystem, в среде домена, возможно, потребуется изменить идентификацию конечной точки для конечной точки службы в файле App.config клиента, чтобы задать соответствующее имя участника-пользователя или имя участника-службы на основании учетной записи, используемой для выполнения службы.</span><span class="sxs-lookup"><span data-stu-id="af724-189">If the service is running under an account other than the NetworkService or LocalSystem account in a domain environment, you might need to modify the endpoint identity for the service endpoint inside the client's App.config file to set the appropriate UPN or SPN based on the account that is used to run the service.</span></span> <span data-ttu-id="af724-190">Дополнительные сведения об удостоверении конечной точки см. в разделе [удостоверение службы и проверка подлинности](../feature-details/service-identity-and-authentication.md) .</span><span class="sxs-lookup"><span data-stu-id="af724-190">For more information about endpoint identity, see the [Service Identity and Authentication](../feature-details/service-identity-and-authentication.md) topic.</span></span>

    8. <span data-ttu-id="af724-191">Запустите файл Client.exe из командной строки.</span><span class="sxs-lookup"><span data-stu-id="af724-191">Run Client.exe from a command prompt.</span></span>

### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="af724-192">Очистка после образца</span><span class="sxs-lookup"><span data-stu-id="af724-192">To clean up after the sample</span></span>

- <span data-ttu-id="af724-193">После завершения работы образца запустите в папке образцов файл Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="af724-193">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>
