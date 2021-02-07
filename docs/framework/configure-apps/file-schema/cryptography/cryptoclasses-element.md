---
description: 'Дополнительные сведения о: <cryptoClasses> element'
title: Элемент <cryptoClasses>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClasses
helpviewer_keywords:
- <cryptoClasses> element
- cryptoClasses element
ms.assetid: 290d5f96-946d-4f02-babb-1d31ec0b8295
ms.openlocfilehash: 5ae9b85d477a71eedc3c8b32bba2b4639414163c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698925"
---
# <a name="cryptoclasses-element"></a><span data-ttu-id="84cb5-103">Элемент \<cryptoClasses></span><span class="sxs-lookup"><span data-stu-id="84cb5-103">\<cryptoClasses> Element</span></span>

<span data-ttu-id="84cb5-104">Содержит список криптографических классов, сопоставленных с понятным именем в [\<nameEntry>](nameentry-element.md) элементе.</span><span class="sxs-lookup"><span data-stu-id="84cb5-104">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClasses>**  
  
## <a name="syntax"></a><span data-ttu-id="84cb5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="84cb5-105">Syntax</span></span>  
  
```xml  
<cryptoClasses>
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84cb5-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="84cb5-106">Attributes and Elements</span></span>  

 <span data-ttu-id="84cb5-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="84cb5-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84cb5-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="84cb5-108">Attributes</span></span>  

 <span data-ttu-id="84cb5-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="84cb5-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="84cb5-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="84cb5-110">Child Elements</span></span>  
  
|<span data-ttu-id="84cb5-111">Элемент</span><span class="sxs-lookup"><span data-stu-id="84cb5-111">Element</span></span>|<span data-ttu-id="84cb5-112">Описание</span><span class="sxs-lookup"><span data-stu-id="84cb5-112">Description</span></span>|  
|-------------|-----------------|  
|[\<cryptoClass>](cryptoclass-element.md)|<span data-ttu-id="84cb5-113">Содержит криптографический класс, сопоставленный с понятным именем в **\<nameEntry>** элементе.</span><span class="sxs-lookup"><span data-stu-id="84cb5-113">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="84cb5-114">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="84cb5-114">Parent Elements</span></span>  
  
|<span data-ttu-id="84cb5-115">Элемент</span><span class="sxs-lookup"><span data-stu-id="84cb5-115">Element</span></span>|<span data-ttu-id="84cb5-116">Описание</span><span class="sxs-lookup"><span data-stu-id="84cb5-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="84cb5-117">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="84cb5-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="84cb5-118">Содержит параметры шифрования.</span><span class="sxs-lookup"><span data-stu-id="84cb5-118">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="84cb5-119">Содержит сопоставления классов с понятными именами.</span><span class="sxs-lookup"><span data-stu-id="84cb5-119">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="84cb5-120">Содержит `cryptographySettings` элемент.</span><span class="sxs-lookup"><span data-stu-id="84cb5-120">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="84cb5-121">Пример</span><span class="sxs-lookup"><span data-stu-id="84cb5-121">Example</span></span>  

 <span data-ttu-id="84cb5-122">В следующем примере показано, как использовать **\<cryptoClass>** элемент для ссылки на криптографический класс и для настройки среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="84cb5-122">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="84cb5-123">Затем можно передать строку "RSA" в <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> метод и использовать <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> метод для возврата `MyCryptoRSAClass` объекта.</span><span class="sxs-lookup"><span data-stu-id="84cb5-123">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <!-- Other cryptography classes go here. -->  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
             <!-- Mappings to other cryptography classes go here. -->  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="84cb5-124">См. также</span><span class="sxs-lookup"><span data-stu-id="84cb5-124">See also</span></span>

- <xref:System.Security.Cryptography>
- [<span data-ttu-id="84cb5-125">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="84cb5-125">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="84cb5-126">Схема параметров шифрования</span><span class="sxs-lookup"><span data-stu-id="84cb5-126">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="84cb5-127">службы шифрования</span><span class="sxs-lookup"><span data-stu-id="84cb5-127">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="84cb5-128">System. Security. Cryptography. CryptoConfig. CreateFromName</span><span class="sxs-lookup"><span data-stu-id="84cb5-128">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A)
- [<span data-ttu-id="84cb5-129">Настройка криптографических классов</span><span class="sxs-lookup"><span data-stu-id="84cb5-129">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
