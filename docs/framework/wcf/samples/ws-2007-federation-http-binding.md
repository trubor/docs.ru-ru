---
description: 'Дополнительные сведения: HTTP-привязка федерации WS 2007'
title: Привязка HTTP для федерации WS 2007
ms.date: 03/30/2017
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
ms.openlocfilehash: 12363abb1c8c503db8ec4aac9197276c8ec41c58
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715058"
---
# <a name="ws-2007-federation-http-binding"></a><span data-ttu-id="0bb27-103">Привязка HTTP для федерации WS 2007</span><span class="sxs-lookup"><span data-stu-id="0bb27-103">WS 2007 Federation HTTP Binding</span></span>

<span data-ttu-id="0bb27-104">В этом примере показано, как использовать <xref:System.ServiceModel.WS2007FederationHttpBinding> — стандартную привязку для создания федеративных сценариев, поддерживающих версию 1.3 спецификации WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="0bb27-104">This sample demonstrates the use of <xref:System.ServiceModel.WS2007FederationHttpBinding>, a standard binding that you can use to build federated scenarios that support version 1.3 of the WS-Trust specification.</span></span>

> [!NOTE]
> <span data-ttu-id="0bb27-105">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="0bb27-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="0bb27-106">Пример состоит из клиентской программы на основе консоли (*Client.exe*), программы службы маркеров безопасности на основе консоли (*Securitytokenservice.exe*) и программы службы на основе консоли (*Service.exe*).</span><span class="sxs-lookup"><span data-stu-id="0bb27-106">The sample consists of a console-based client program (*Client.exe*), a console-based security token service program (*Securitytokenservice.exe*), and a console-based service program (*Service.exe*).</span></span> <span data-ttu-id="0bb27-107">Служба реализует контракт, определяющий шаблон взаимодействия "запрос-ответ".</span><span class="sxs-lookup"><span data-stu-id="0bb27-107">The service implements a contract that defines a request/reply communication pattern.</span></span> <span data-ttu-id="0bb27-108">Контракт определяется интерфейсом `ICalculator`, который предоставляет математические операции (`Add`, `Subtract`, `Multiply` и `Divide`).</span><span class="sxs-lookup"><span data-stu-id="0bb27-108">The contract is defined by the `ICalculator` interface, which exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="0bb27-109">Клиент получает маркер безопасности от службы маркеров безопасности (STS) и осуществляет синхронные вызовы службы для заданной математической операции.</span><span class="sxs-lookup"><span data-stu-id="0bb27-109">The client obtains a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation.</span></span> <span data-ttu-id="0bb27-110">Служба отправляет в ответ результат.</span><span class="sxs-lookup"><span data-stu-id="0bb27-110">The service then replies with the result.</span></span> <span data-ttu-id="0bb27-111">Действия клиента отображаются в окне консоли.</span><span class="sxs-lookup"><span data-stu-id="0bb27-111">Client activity is visible in the console window.</span></span>

<span data-ttu-id="0bb27-112">В этом образце контракт `ICalculator` делается доступным с помощью элемента `ws2007FederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="0bb27-112">The sample makes the `ICalculator` contract available using the `ws2007FederationHttpBinding` element.</span></span> <span data-ttu-id="0bb27-113">Конфигурация этой привязки на клиенте показана в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="0bb27-113">The configuration of this binding on the client is shown in the following code:</span></span>

```xml
<bindings>
  <ws2007FederationHttpBinding>
    <binding name="ServiceFed" >
      <security mode ="Message">
        <message issuedKeyType ="SymmetricKey"
                 issuedTokenType ="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" >
          <!-- Endpoint address and binding for Security Token Service -->
          <issuer address ="http://localhost:8000/sts/windows"
                  binding ="ws2007HttpBinding" />
        </message>
      </security>
    </binding>
  </ws2007FederationHttpBinding>
</bindings>
```

<span data-ttu-id="0bb27-114">На странице [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md) `security` значение указывает, какой режим безопасности следует использовать.</span><span class="sxs-lookup"><span data-stu-id="0bb27-114">On the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="0bb27-115">В этом примере `message` используется безопасность, поэтому она [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) указана в [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="0bb27-115">In this sample, `message` security is used, which is why the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="0bb27-116">[\<issuer>](../../configure-apps/file-schema/wcf/issuer.md)Элемент внутри [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) определяет адрес и привязку для STS, которая выдает клиенту маркер безопасности, чтобы клиент мог пройти проверку подлинности в `ICalculator` службе.</span><span class="sxs-lookup"><span data-stu-id="0bb27-116">The [\<issuer>](../../configure-apps/file-schema/wcf/issuer.md) element inside the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and binding for the STS that issues a security token to the client so that the client can authenticate to the `ICalculator` service.</span></span>
  
<span data-ttu-id="0bb27-117">Конфигурация этой привязки в службе показана в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="0bb27-117">The configuration of this binding on the service is shown in the following code:</span></span>

```xml
<bindings>
  <ws2007FederationHttpBinding>
    <binding name="ServiceFed" >
      <security mode ="Message">
        <message issuedKeyType ="SymmetricKey"
                 issuedTokenType ="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" >
          <!-- Metadata address for Security Token Service -->
          <issuerMetadata address ="http://localhost:8000/sts/mex" >
            <identity>
              <certificateReference storeLocation ="CurrentUser"
                                    storeName="TrustedPeople"
                                    x509FindType ="FindBySubjectDistinguishedName"
                                    findValue ="CN=STS" />
            </identity>
          </issuerMetadata>
        </message>
      </security>
    </binding>
  </ws2007FederationHttpBinding>
</bindings>
```

<span data-ttu-id="0bb27-118">На странице [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md) `security` значение указывает, какой режим безопасности следует использовать.</span><span class="sxs-lookup"><span data-stu-id="0bb27-118">On the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), the `security` value specifies which security mode should be used.</span></span> <span data-ttu-id="0bb27-119">В этом примере `message` используется безопасность, поэтому она [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) указана в [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="0bb27-119">In this sample, `message` security is used, which is why the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) is specified inside the [\<security>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md).</span></span> <span data-ttu-id="0bb27-120">[\<issuerMetadata>](../../configure-apps/file-schema/wcf/issuermetadata.md)Элемент `ws2007FederationHttpBinding` внутри [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) определяет адрес и идентификатор для конечной точки, которые можно использовать для получения метаданных для службы маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="0bb27-120">The [\<issuerMetadata>](../../configure-apps/file-schema/wcf/issuermetadata.md) element of `ws2007FederationHttpBinding` inside the [\<message>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifies the address and identity for an endpoint that can be used to retrieve metadata for the STS.</span></span>

<span data-ttu-id="0bb27-121">Поведение службы показано в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="0bb27-121">The behavior for the service is shown in the following code:</span></span>

```xml
<behaviors>
  <serviceBehaviors>
    <behavior name ="ServiceBehaviour" >
      <serviceDebug includeExceptionDetailInFaults ="true"/>
      <serviceMetadata httpGetEnabled ="true"/>
      <serviceCredentials>
        <issuedTokenAuthentication>
          <knownCertificates>
            <add storeLocation ="LocalMachine"
                 storeName="TrustedPeople"
                 x509FindType="FindBySubjectDistinguishedName"
                 findValue="CN=STS" />
          </knownCertificates>
        </issuedTokenAuthentication>
        <serviceCertificate storeLocation ="LocalMachine"
                            storeName ="My"
                            x509FindType ="FindBySubjectDistinguishedName"
                            findValue ="CN=localhost"/>
      </serviceCredentials>
    </behavior>
  </serviceBehaviors>
</behaviors>
```
  
<span data-ttu-id="0bb27-122">[\<issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> позволяет службе указывать ограничения на токены, которые она позволяет клиентам предоставлять во время проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="0bb27-122">The [\<issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="0bb27-123">Эта конфигурация указывает, что маркеры, подписанные сертификатом, у которых имя субъекта CN=STS, принимаются службой.</span><span class="sxs-lookup"><span data-stu-id="0bb27-123">This configuration specifies that tokens signed by a certificate whose subject name is CN=STS are accepted by the service.</span></span>

<span data-ttu-id="0bb27-124">Служба маркеров безопасности делает единственную конечную точку доступной с помощью стандартной привязки <xref:System.ServiceModel.WS2007HttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="0bb27-124">STS makes a single endpoint available using the standard <xref:System.ServiceModel.WS2007HttpBinding>.</span></span> <span data-ttu-id="0bb27-125">Служба отвечает на запросы маркеров от клиентов.</span><span class="sxs-lookup"><span data-stu-id="0bb27-125">The service responds to requests from clients for tokens.</span></span> <span data-ttu-id="0bb27-126">Если клиент прошел проверку подлинности с использованием учетной записи Windows, служба выдает маркер, содержащий имя пользователя клиента в качестве утверждения.</span><span class="sxs-lookup"><span data-stu-id="0bb27-126">If the client is authenticated using a Windows account, the service issues a token that contains the client's user name as a claim.</span></span> <span data-ttu-id="0bb27-127">В одной из частей процедуры создания маркера служба маркеров безопасности подписывает маркер с использованием закрытого ключа, связанного с сертификатом CN=STS.</span><span class="sxs-lookup"><span data-stu-id="0bb27-127">As part of creating the token, STS signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="0bb27-128">Дополнительно она создает симметричный ключ и шифрует его с использованием открытого ключа, связанного с сертификатом CN=localhost.</span><span class="sxs-lookup"><span data-stu-id="0bb27-128">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="0bb27-129">При возврате маркера клиенту служба маркеров безопасности также возвращает симметричный ключ.</span><span class="sxs-lookup"><span data-stu-id="0bb27-129">In returning the token to the client, STS also returns the symmetric key.</span></span> <span data-ttu-id="0bb27-130">Клиент предъявляет выданный маркер службе `ICalculator` и подтверждает свое знание симметричного ключа, подписывая сообщение этим ключом.</span><span class="sxs-lookup"><span data-stu-id="0bb27-130">The client presents the issued token to the `ICalculator` service and proves that it knows the symmetric key by signing the message with that key.</span></span>

<span data-ttu-id="0bb27-131">При выполнении примера запрос маркера безопасности показан в окне консоли службы маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="0bb27-131">When you run the sample, the request for the security token is shown in the STS console window.</span></span> <span data-ttu-id="0bb27-132">Запросы и ответы операций появляются в окнах консоли клиента и службы.</span><span class="sxs-lookup"><span data-stu-id="0bb27-132">The operation's requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="0bb27-133">Чтобы закрыть приложение, нажмите клавишу ВВОД в любом из окон консоли.</span><span class="sxs-lookup"><span data-stu-id="0bb27-133">Press ENTER in any of the console windows to shut down the application.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

<span data-ttu-id="0bb27-134">Файл *Setup.bat* , включенный в этот пример, позволяет настроить сервер и STS с соответствующими сертификатами для запуска приложения, размещенного на собственном сервере.</span><span class="sxs-lookup"><span data-stu-id="0bb27-134">The *Setup.bat* file included with this sample allows you to configure the server and STS with the relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="0bb27-135">Пакетный файл создает два сертификата в хранилище сертификатов LocalMachine/TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="0bb27-135">The batch file creates two certificates in the LocalMachine/TrustedPeople certificate store.</span></span> <span data-ttu-id="0bb27-136">Имя субъекта первого сертификата CN=STS, он используется службой маркеров безопасности, чтобы подписывать маркеры безопасности, выдаваемые клиенту.</span><span class="sxs-lookup"><span data-stu-id="0bb27-136">The first certificate has a subject name of CN=STS and is used by STS to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="0bb27-137">Имя субъекта второго сертификата CN=localhost, он используется службой маркеров безопасности для шифрования ключа таким образом, чтобы служба могла его расшифровать.</span><span class="sxs-lookup"><span data-stu-id="0bb27-137">The second certificate has a subject name of CN=localhost and is used by STS to encrypt a key in a way that the service can decrypt.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0bb27-138">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="0bb27-138">To set up, build, and run the sample</span></span>
  
1. <span data-ttu-id="0bb27-139">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0bb27-139">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="0bb27-140">Откройте Командная строка разработчика для Visual Studio с правами администратора и запустите файл Setup.bat, чтобы создать необходимые сертификаты.</span><span class="sxs-lookup"><span data-stu-id="0bb27-140">Open a Developer Command Prompt for Visual Studio with administrator privileges and run the Setup.bat file to create the required certificates.</span></span>

 <span data-ttu-id="0bb27-141">Этот пакетный файл использует *Certmgr.exe* и Makecert.exe, которые распространяются вместе с Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="0bb27-141">This batch file uses *Certmgr.exe* and Makecert.exe, which are distributed with the Windows SDK.</span></span> <span data-ttu-id="0bb27-142">Однако необходимо запустить *Setup.bat* из командной строки Visual Studio, чтобы разрешить сценарию найти эти средства.</span><span class="sxs-lookup"><span data-stu-id="0bb27-142">However, you must run *Setup.bat* from within a Visual Studio command prompt to enable the script to find these tools.</span></span>

1. <span data-ttu-id="0bb27-143">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0bb27-143">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

2. <span data-ttu-id="0bb27-144">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0bb27-144">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span> <span data-ttu-id="0bb27-145">При использовании Windows Vista необходимо запустить *Service.exe*, *Client.exe* и *SecurityTokenService.exe* с повышенными привилегиями (щелкните правой кнопкой мыши файлы и выберите команду **Запуск от имени администратора**).</span><span class="sxs-lookup"><span data-stu-id="0bb27-145">If you are using Windows Vista, you must run *Service.exe*, *Client.exe*, and *SecurityTokenService.exe* with elevated privileges (right-click the files and then click **Run as administrator**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0bb27-146">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="0bb27-146">The samples may already be installed on your computer.</span></span> <span data-ttu-id="0bb27-147">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="0bb27-147">Check for the following (default) directory before continuing:</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="0bb27-148">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="0bb27-148">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0bb27-149">Этот образец находится в следующем каталоге:</span><span class="sxs-lookup"><span data-stu-id="0bb27-149">This sample is located in the following directory:</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`
