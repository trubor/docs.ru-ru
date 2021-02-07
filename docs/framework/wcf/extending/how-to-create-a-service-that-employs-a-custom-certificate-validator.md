---
description: Дополнительные сведения о том, как создать службу, использующую настраиваемый проверяющий сертификат.
title: Практическое руководство. Создание службы, использующей пользовательский проверяющий элемент управления для сертификатов
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: bb0190ff-0738-4e54-8d22-c97d343708bf
ms.openlocfilehash: 8ed5d23143b7b69768cc556d9fd5663e46fd7da7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668985"
---
# <a name="how-to-create-a-service-that-employs-a-custom-certificate-validator"></a><span data-ttu-id="ce029-103">Практическое руководство. Создание службы, использующей пользовательский проверяющий элемент управления для сертификатов</span><span class="sxs-lookup"><span data-stu-id="ce029-103">How to: Create a Service that Employs a Custom Certificate Validator</span></span>

<span data-ttu-id="ce029-104">В данном разделе показано, как реализовать пользовательский проверяющий элемент управления для сертификата и как настроить учетные данные клиента или службы, чтобы заменить логику проверки сертификата по умолчанию пользовательским проверяющим элементом управления для сертификата.</span><span class="sxs-lookup"><span data-stu-id="ce029-104">This topic shows how to implement a custom certificate validator and how to configure client or service credentials to replace the default certificate validation logic with the custom certificate validator.</span></span>  
  
 <span data-ttu-id="ce029-105">Если сертификат X. 509 используется для проверки подлинности клиента или службы, Windows Communication Foundation (WCF) по умолчанию использует хранилище сертификатов Windows и API шифрования, чтобы проверить сертификат и убедиться, что он является доверенным.</span><span class="sxs-lookup"><span data-stu-id="ce029-105">If the X.509 certificate is used to authenticate a client or service, Windows Communication Foundation (WCF) by default uses the Windows certificate store and Crypto API to validate the certificate and to ensure that it is trusted.</span></span> <span data-ttu-id="ce029-106">Иногда встроенных функциональных возможностей проверки сертификатов недостаточно, их необходимо изменить.</span><span class="sxs-lookup"><span data-stu-id="ce029-106">Sometimes the built-in certificate validation functionality is not enough and must be changed.</span></span> <span data-ttu-id="ce029-107">WCF предоставляет простой способ изменения логики проверки, позволяя пользователям добавлять пользовательские средства проверки сертификатов.</span><span class="sxs-lookup"><span data-stu-id="ce029-107">WCF provides an easy way to change the validation logic by allowing users to add a custom certificate validator.</span></span> <span data-ttu-id="ce029-108">Если указан пользовательский проверяющий элемент управления для сертификата, WCF не использует встроенную логику проверки сертификата, но использует вместо этого пользовательский проверяющий элемент управления.</span><span class="sxs-lookup"><span data-stu-id="ce029-108">If a custom certificate validator is specified, WCF does not use the built-in certificate validation logic but relies on the custom validator instead.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="ce029-109">Процедуры</span><span class="sxs-lookup"><span data-stu-id="ce029-109">Procedures</span></span>  
  
#### <a name="to-create-a-custom-certificate-validator"></a><span data-ttu-id="ce029-110">Создание пользовательского проверяющего элемента управления для сертификата</span><span class="sxs-lookup"><span data-stu-id="ce029-110">To create a custom certificate validator</span></span>  
  
1. <span data-ttu-id="ce029-111">Определите новый производный класс на основе класса <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="ce029-111">Define a new class derived from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span>  
  
2. <span data-ttu-id="ce029-112">Реализуйте абстрактный метод <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="ce029-112">Implement the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> method.</span></span> <span data-ttu-id="ce029-113">Сертификат, который необходимо проверить, передается методу как аргумент.</span><span class="sxs-lookup"><span data-stu-id="ce029-113">The certificate that must be validated is passed as an argument to the method.</span></span> <span data-ttu-id="ce029-114">Если переданный сертификат недопустим согласно логике проверки, этот метод создает исключение <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>.</span><span class="sxs-lookup"><span data-stu-id="ce029-114">If the passed certificate is not valid according to the validation logic, this method throws a <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>.</span></span> <span data-ttu-id="ce029-115">Если сертификат действителен, метод возвращает его вызывающей стороне.</span><span class="sxs-lookup"><span data-stu-id="ce029-115">If the certificate is valid, the method returns to the caller.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ce029-116">Чтобы вернуть ошибки проверки подлинности клиенту, создайте исключение <xref:System.ServiceModel.FaultException> в методе <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="ce029-116">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### <a name="to-specify-a-custom-certificate-validator-in-service-configuration"></a><span data-ttu-id="ce029-117">Задание пользовательского проверяющего элемента управления для сертификата в конфигурации службы</span><span class="sxs-lookup"><span data-stu-id="ce029-117">To specify a custom certificate validator in service configuration</span></span>  
  
1. <span data-ttu-id="ce029-118">Добавьте [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) элемент и в [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) элемент.</span><span class="sxs-lookup"><span data-stu-id="ce029-118">Add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element and a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="ce029-119">Добавьте [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) и задайте `name` для атрибута соответствующее значение.</span><span class="sxs-lookup"><span data-stu-id="ce029-119">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>  
  
3. <span data-ttu-id="ce029-120">Добавьте в [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) `<behavior>` элемент.</span><span class="sxs-lookup"><span data-stu-id="ce029-120">Add a [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) to the `<behavior>` element.</span></span>  
  
4. <span data-ttu-id="ce029-121">Добавьте элемент `<clientCertificate>` в элемент `<serviceCredentials>`.</span><span class="sxs-lookup"><span data-stu-id="ce029-121">Add a `<clientCertificate>` element to the `<serviceCredentials>` element.</span></span>  
  
5. <span data-ttu-id="ce029-122">Добавьте [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) в `<clientCertificate>` элемент.</span><span class="sxs-lookup"><span data-stu-id="ce029-122">Add an [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) to the `<clientCertificate>` element.</span></span>  
  
6. <span data-ttu-id="ce029-123">Задайте для атрибута `customCertificateValidatorType` тип проверяющего элемента управления.</span><span class="sxs-lookup"><span data-stu-id="ce029-123">Set the `customCertificateValidatorType` attribute to the validator type.</span></span> <span data-ttu-id="ce029-124">В следующем примере для атрибута задано значение пространства имен и имени типа.</span><span class="sxs-lookup"><span data-stu-id="ce029-124">The following example sets the attribute to the namespace and name of the type.</span></span>  
  
7. <span data-ttu-id="ce029-125">Задайте для атрибута `certificateValidationMode` значение `Custom`.</span><span class="sxs-lookup"><span data-stu-id="ce029-125">Set the `certificateValidationMode` attribute to `Custom`.</span></span>  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
       <serviceBehaviors>  
        <behavior name="ServiceBehavior">  
         <serviceCredentials>  
          <clientCertificate>  
          <authentication certificateValidationMode="Custom" customCertificateValidatorType="Samples.MyValidator, service" />  
          </clientCertificate>  
         </serviceCredentials>  
        </behavior>  
       </serviceBehaviors>  
      </behaviors>  
    </system.serviceModel>  
    </configuration>  
    ```  
  
#### <a name="to-specify-a-custom-certificate-validator-using-configuration-on-the-client"></a><span data-ttu-id="ce029-126">Задание пользовательского проверяющего элемента управления для сертификата с использованием конфигурации на стороне клиента</span><span class="sxs-lookup"><span data-stu-id="ce029-126">To specify a custom certificate validator using configuration on the client</span></span>  
  
1. <span data-ttu-id="ce029-127">Добавьте [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) элемент и в [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) элемент.</span><span class="sxs-lookup"><span data-stu-id="ce029-127">Add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element and a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="ce029-128">Добавьте [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) элемент.</span><span class="sxs-lookup"><span data-stu-id="ce029-128">Add an [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) element.</span></span>  
  
3. <span data-ttu-id="ce029-129">Добавьте элемент `<behavior>` и присвойте атрибуту `name` соответствующее значение.</span><span class="sxs-lookup"><span data-stu-id="ce029-129">Add a `<behavior>` element and set the `name` attribute to an appropriate value.</span></span>  
  
4. <span data-ttu-id="ce029-130">Добавьте [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) элемент.</span><span class="sxs-lookup"><span data-stu-id="ce029-130">Add a [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span>  
  
5. <span data-ttu-id="ce029-131">Добавьте [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) .</span><span class="sxs-lookup"><span data-stu-id="ce029-131">Add a [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md).</span></span>  
  
6. <span data-ttu-id="ce029-132">Добавьте, [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="ce029-132">Add an [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) as shown on the following example.</span></span>  
  
7. <span data-ttu-id="ce029-133">Задайте для атрибута `customCertificateValidatorType` тип проверяющего элемента управления.</span><span class="sxs-lookup"><span data-stu-id="ce029-133">Set the `customCertificateValidatorType` attribute to the validator type.</span></span>  
  
8. <span data-ttu-id="ce029-134">Задайте для атрибута `certificateValidationMode` значение `Custom`.</span><span class="sxs-lookup"><span data-stu-id="ce029-134">Set the `certificateValidationMode` attribute to `Custom`.</span></span> <span data-ttu-id="ce029-135">В следующем примере для атрибута задано значение пространства имен и имени типа.</span><span class="sxs-lookup"><span data-stu-id="ce029-135">The following example sets the attribute to the namespace and name of the type.</span></span>  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
       <endpointBehaviors>  
        <behavior name="clientBehavior">  
         <clientCredentials>  
          <serviceCertificate>  
           <authentication certificateValidationMode="Custom"
                  customCertificateValidatorType=  
             "Samples.CustomX509CertificateValidator, client"/>  
          </serviceCertificate>  
         </clientCredentials>  
        </behavior>  
       </endpointBehaviors>  
      </behaviors>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-service"></a><span data-ttu-id="ce029-136">Задание пользовательского проверяющего элемента управления для сертификата с использованием кода на стороне службы</span><span class="sxs-lookup"><span data-stu-id="ce029-136">To specify a custom certificate validator using code on the service</span></span>  
  
1. <span data-ttu-id="ce029-137">Задайте пользовательский проверяющий элемент управления для сертификата в свойстве <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>.</span><span class="sxs-lookup"><span data-stu-id="ce029-137">Specify the custom certificate validator on the <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> property.</span></span> <span data-ttu-id="ce029-138">Получить доступ к учетным данным службы можно с помощью свойства <xref:System.ServiceModel.ServiceHostBase.Credentials%2A>.</span><span class="sxs-lookup"><span data-stu-id="ce029-138">You can access the service credentials using the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property.</span></span>  
  
2. <span data-ttu-id="ce029-139">Задайте для свойства <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> значение <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="ce029-139">Set the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> property to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span></span>  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-client"></a><span data-ttu-id="ce029-140">Задание пользовательского проверяющего элемента управления для сертификата с использованием кода на стороне клиента</span><span class="sxs-lookup"><span data-stu-id="ce029-140">To specify a custom certificate validator using code on the client</span></span>  
  
1. <span data-ttu-id="ce029-141">Задайте пользовательский проверяющий элемент управления для сертификата в свойстве <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A>.</span><span class="sxs-lookup"><span data-stu-id="ce029-141">Specify the custom certificate validator using the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> property.</span></span> <span data-ttu-id="ce029-142">Получить доступ к учетным данным клиента можно с помощью свойства <xref:System.ServiceModel.ServiceHostBase.Credentials%2A>.</span><span class="sxs-lookup"><span data-stu-id="ce029-142">You can access the client credentials using the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property.</span></span> <span data-ttu-id="ce029-143">(Клиентский класс, созданный с помощью [служебной программы метаданных ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) , всегда является производным от <xref:System.ServiceModel.ClientBase%601> класса.)</span><span class="sxs-lookup"><span data-stu-id="ce029-143">(The client class generated by [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) always derives from the <xref:System.ServiceModel.ClientBase%601> class.)</span></span>  
  
2. <span data-ttu-id="ce029-144">Задайте для свойства <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> значение <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="ce029-144">Set the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> property to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce029-145">Пример</span><span class="sxs-lookup"><span data-stu-id="ce029-145">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="ce029-146">Описание</span><span class="sxs-lookup"><span data-stu-id="ce029-146">Description</span></span>  

 <span data-ttu-id="ce029-147">В следующем примере показана реализация пользовательского проверяющего элемента управления для сертификата и его использование на стороне службы.</span><span class="sxs-lookup"><span data-stu-id="ce029-147">The following sample shows an implementation of a custom certificate validator and its usage on the service.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ce029-148">Код</span><span class="sxs-lookup"><span data-stu-id="ce029-148">Code</span></span>  

 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="ce029-149">См. также</span><span class="sxs-lookup"><span data-stu-id="ce029-149">See also</span></span>

- <xref:System.IdentityModel.Selectors.X509CertificateValidator>
