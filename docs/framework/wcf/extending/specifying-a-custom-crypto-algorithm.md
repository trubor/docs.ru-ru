---
description: 'Дополнительные сведения: Указание пользовательского алгоритма шифрования'
title: Задание пользовательского алгоритма шифрования
ms.date: 03/30/2017
ms.assetid: d662a305-8e09-451d-9a59-b0f12b012f1d
ms.openlocfilehash: 4d4cb525b46b33a0d0df8dd6a3db9e9fafe84f8f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643973"
---
# <a name="specifying-a-custom-crypto-algorithm"></a><span data-ttu-id="61db0-103">Задание пользовательского алгоритма шифрования</span><span class="sxs-lookup"><span data-stu-id="61db0-103">Specifying a Custom Crypto Algorithm</span></span>

<span data-ttu-id="61db0-104">WCF позволяет указывать пользовательский алгоритм шифрования для использования при шифровании данных или вычислении цифровых подписей.</span><span class="sxs-lookup"><span data-stu-id="61db0-104">WCF allows you to specify a custom crypto algorithm to use when encrypting data or computing digital signatures.</span></span> <span data-ttu-id="61db0-105">Для этого выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="61db0-105">This is done by the following steps:</span></span>  
  
1. <span data-ttu-id="61db0-106">Создайте производный класс от класса <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="61db0-106">Derive a class from <xref:System.ServiceModel.Security.SecurityAlgorithmSuite></span></span>  
  
2. <span data-ttu-id="61db0-107">Регистрация алгоритма</span><span class="sxs-lookup"><span data-stu-id="61db0-107">Register the algorithm</span></span>  
  
3. <span data-ttu-id="61db0-108">Настройте привязку с классом, который является производным от класса <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="61db0-108">Configure the binding with the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class.</span></span>  
  
## <a name="derive-a-class-from-securityalgorithmsuite"></a><span data-ttu-id="61db0-109">Создание производного класса от класса SecurityAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="61db0-109">Derive a class from SecurityAlgorithmSuite</span></span>  

 <span data-ttu-id="61db0-110"><xref:System.ServiceModel.Security.SecurityAlgorithmSuite> является абстрактным базовым классом, позволяющим указывать алгоритм, используемый при выполнении различных операций, связанных с безопасностью.</span><span class="sxs-lookup"><span data-stu-id="61db0-110">The <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> is an abstract base class that allows you to specify the algorithm to use when performing various security related operations.</span></span> <span data-ttu-id="61db0-111">Например, вычисление хэша для цифровой подписи или шифрование сообщения.</span><span class="sxs-lookup"><span data-stu-id="61db0-111">For example, computing a hash for a digital signature or encrypting a message.</span></span> <span data-ttu-id="61db0-112">В следующем коде показано, как наследовать класс от класса <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="61db0-112">The following code shows how to derive a class from <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>:</span></span>  
  
```csharp  
public class MyCustomAlgorithmSuite : SecurityAlgorithmSuite  
    {  
        public override string DefaultAsymmetricKeyWrapAlgorithm  
        {  
            get { return SecurityAlgorithms.RsaOaepKeyWrap; }  
        }  
  
        public override string DefaultAsymmetricSignatureAlgorithm  
        {  
            get { return SecurityAlgorithms.RsaSha1Signature; }  
        }  
  
        public override string DefaultCanonicalizationAlgorithm  
        {  
            get { return SecurityAlgorithms.ExclusiveC14n; ; }  
        }  
  
        public override string DefaultDigestAlgorithm  
        {  
            get { return SecurityAlgorithms.MyCustomHashAlgorithm; }  
        }  
  
        public override string DefaultEncryptionAlgorithm  
        {  
            get { return SecurityAlgorithms.Aes128Encryption; }  
        }  
  
        public override int DefaultEncryptionKeyDerivationLength  
        {  
            get { return 128; }  
        }  
  
        public override int DefaultSignatureKeyDerivationLength  
        {  
            get { return 128; }  
        }  
  
        public override int DefaultSymmetricKeyLength  
        {  
            get { return 128; }  
        }  
  
        public override string DefaultSymmetricKeyWrapAlgorithm  
        {  
            get { return SecurityAlgorithms.Aes128Encryption; }  
        }  
  
        public override string DefaultSymmetricSignatureAlgorithm  
        {  
            get { return SecurityAlgorithms.HmacSha1Signature; }  
        }  
  
        public override bool IsAsymmetricKeyLengthSupported(int length)  
        {  
            return length >= 1024 && length <= 4096;  
        }  
  
        public override bool IsSymmetricKeyLengthSupported(int length)  
        {  
            return length >= 128 && length <= 256;  
        }  
    }  
```  
  
## <a name="register-the-custom-algorithm"></a><span data-ttu-id="61db0-113">Регистрация пользовательского алгоритма</span><span class="sxs-lookup"><span data-stu-id="61db0-113">Register the Custom Algorithm</span></span>  

 <span data-ttu-id="61db0-114">Регистрацию можно выполнить в файле конфигурации или в императивном коде.</span><span class="sxs-lookup"><span data-stu-id="61db0-114">Registration can be done in a configuration file or in imperative code.</span></span> <span data-ttu-id="61db0-115">Регистрация пользовательского алгоритма выполняется путем создания сопоставления между классом, реализующим поставщик службы шифрования, и псевдонимом.</span><span class="sxs-lookup"><span data-stu-id="61db0-115">Registering a custom algorithm is done by creating a mapping between a class that implements a crypto service provider and an alias.</span></span> <span data-ttu-id="61db0-116">Затем псевдоним сопоставляется с URI, который используется при указании алгоритма в привязке службы WCF.</span><span class="sxs-lookup"><span data-stu-id="61db0-116">The alias is then mapped to a URI which is used when specifying the algorithm in the WCF service’s binding.</span></span> <span data-ttu-id="61db0-117">Следующий фрагмент конфигурации показывает, как зарегистрировать пользовательский алгоритм в конфигурации.</span><span class="sxs-lookup"><span data-stu-id="61db0-117">The following configuration snippet illustrates how to register a custom algorithm in config:</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
           <cryptoClasses>  
              <cryptoClass SHA256CSP="System.Security.Cryptography.SHA256CryptoServiceProvider, System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
           </cryptoClasses>  
           <nameEntry name="http://contoso.com/CustomAlgorithms/CustomHashAlgorithm"  
              class="SHA256CSP" />  
           </cryptoNameMapping>  
        </cryptographySettings>  
    </mscorlib>  
</configuration>  
```  
  
 <span data-ttu-id="61db0-118">В разделе `cryptoClasses` элемента> <создается сопоставление между SHA256CryptoServiceProvider и псевдонимом «SHA256CSP».</span><span class="sxs-lookup"><span data-stu-id="61db0-118">The section under the <`cryptoClasses`> element creates the mapping between the SHA256CryptoServiceProvider and the alias "SHA256CSP".</span></span> <span data-ttu-id="61db0-119">`nameEntry`Элемент> <создает сопоставление между псевдонимом "SHA256CSP" и указанным URL-адресом `http://contoso.com/CustomAlgorithms/CustomHashAlgorithm` .</span><span class="sxs-lookup"><span data-stu-id="61db0-119">The <`nameEntry`> element creates the mapping between the "SHA256CSP" alias and the specified URL `http://contoso.com/CustomAlgorithms/CustomHashAlgorithm`.</span></span>  
  
 <span data-ttu-id="61db0-120">Для регистрации пользовательского алгоритма в коде используйте метод <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])>.</span><span class="sxs-lookup"><span data-stu-id="61db0-120">To register the custom algorithm in code use the <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> method.</span></span> <span data-ttu-id="61db0-121">Этот метод создает и оба сопоставления.</span><span class="sxs-lookup"><span data-stu-id="61db0-121">This method creates both mappings.</span></span> <span data-ttu-id="61db0-122">В следующем примере показано, как вызвать этот метод.</span><span class="sxs-lookup"><span data-stu-id="61db0-122">The following example shows how to call this method:</span></span>  
  
```csharp
// Register the custom URI string defined for the hashAlgorithm in MyCustomAlgorithmSuite class to create the
// SHA256CryptoServiceProvider hash algorithm object.  
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), "http://contoso.com/CustomAlgorithms/CustomHashAlgorithm");  
```  
  
## <a name="configure-the-binding"></a><span data-ttu-id="61db0-123">Настройка привязки</span><span class="sxs-lookup"><span data-stu-id="61db0-123">Configure the Binding</span></span>  

 <span data-ttu-id="61db0-124">Привязка настраивается путем указания пользовательского класса, являющегося производным от класса <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, в параметрах привязки, как показано в следующем фрагменте кода.</span><span class="sxs-lookup"><span data-stu-id="61db0-124">You configure the binding by specifying the custom <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>-derived class in the binding settings as shown in the following code snippet:</span></span>  
  
```csharp  
WSHttpBinding binding = new WSHttpBinding();  
            binding.Security.Message.AlgorithmSuite = new MyCustomAlgorithmSuite();  
```  
  
 <span data-ttu-id="61db0-125">Полный пример кода см. в разделе [гибкость криптографии в WCF Security](../samples/cryptographic-agility-in-wcf-security.md) .</span><span class="sxs-lookup"><span data-stu-id="61db0-125">For a complete code example, see the [Cryptographic Agility in WCF Security](../samples/cryptographic-agility-in-wcf-security.md) sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61db0-126">См. также</span><span class="sxs-lookup"><span data-stu-id="61db0-126">See also</span></span>

- [<span data-ttu-id="61db0-127">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="61db0-127">Securing Services and Clients</span></span>](../feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="61db0-128">Защита служб</span><span class="sxs-lookup"><span data-stu-id="61db0-128">Securing Services</span></span>](../securing-services.md)
- [<span data-ttu-id="61db0-129">Обзор безопасности</span><span class="sxs-lookup"><span data-stu-id="61db0-129">Security Overview</span></span>](../feature-details/security-overview.md)
- [<span data-ttu-id="61db0-130">Основные понятия безопасности</span><span class="sxs-lookup"><span data-stu-id="61db0-130">Security Concepts</span></span>](../feature-details/security-concepts.md)
