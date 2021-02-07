---
description: 'Дополнительные сведения о: <cryptoClass> element'
title: Элемент <cryptoClass>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses/cryptoClass
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClass
helpviewer_keywords:
- cryptoClass element
- <cryptoClass> element
ms.assetid: 03db52ef-010e-44ea-b6fd-b9c900ecad50
ms.openlocfilehash: 503a079ea78a71a11e4c750a629cf67c9244a25d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698940"
---
# <a name="cryptoclass-element"></a><span data-ttu-id="b2227-103">Элемент \<cryptoClass></span><span class="sxs-lookup"><span data-stu-id="b2227-103">\<cryptoClass> Element</span></span>

<span data-ttu-id="b2227-104">Содержит криптографический класс, сопоставленный с понятным именем в [\<nameEntry>](nameentry-element.md) элементе.</span><span class="sxs-lookup"><span data-stu-id="b2227-104">Contains a cryptography class that has a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClass>**

## <a name="syntax"></a><span data-ttu-id="b2227-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b2227-105">Syntax</span></span>  
  
```xml  
<cryptoClass customClassName="fully qualified type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b2227-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="b2227-106">Attributes and Elements</span></span>  

 <span data-ttu-id="b2227-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="b2227-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b2227-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="b2227-108">Attributes</span></span>  
  
|<span data-ttu-id="b2227-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="b2227-109">Attribute</span></span>|<span data-ttu-id="b2227-110">Описание</span><span class="sxs-lookup"><span data-stu-id="b2227-110">Description</span></span>|  
|---------------|-----------------|  
|`customClassName`|<span data-ttu-id="b2227-111">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="b2227-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="b2227-112">Содержит сведения о классе шифрования.</span><span class="sxs-lookup"><span data-stu-id="b2227-112">Contains the information for the cryptography class.</span></span> <span data-ttu-id="b2227-113">Используйте этот атрибут, чтобы указать короткое имя для класса.</span><span class="sxs-lookup"><span data-stu-id="b2227-113">Use this attribute to provide a short name for your class.</span></span> <span data-ttu-id="b2227-114">Необходимо указать строку, которая соответствует требованиям, указанным в [указании полных имен типов](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="b2227-114">You must specify a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b2227-115">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="b2227-115">Child Elements</span></span>  

 <span data-ttu-id="b2227-116">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="b2227-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b2227-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="b2227-117">Parent Elements</span></span>  
  
|<span data-ttu-id="b2227-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="b2227-118">Element</span></span>|<span data-ttu-id="b2227-119">Описание</span><span class="sxs-lookup"><span data-stu-id="b2227-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b2227-120">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b2227-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptoClasses`|<span data-ttu-id="b2227-121">Содержит список криптографических классов, сопоставленных с понятным именем в [\<nameEntry>](nameentry-element.md) элементе.</span><span class="sxs-lookup"><span data-stu-id="b2227-121">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="b2227-122">Содержит параметры шифрования.</span><span class="sxs-lookup"><span data-stu-id="b2227-122">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="b2227-123">Содержит сопоставления классов с понятными именами.</span><span class="sxs-lookup"><span data-stu-id="b2227-123">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="b2227-124">Содержит [\<cryptographySettings>](cryptographysettings-element.md) элемент.</span><span class="sxs-lookup"><span data-stu-id="b2227-124">Contains the [\<cryptographySettings>](cryptographysettings-element.md) element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b2227-125">Пример</span><span class="sxs-lookup"><span data-stu-id="b2227-125">Example</span></span>  

 <span data-ttu-id="b2227-126">В следующем примере показано, как использовать **\<cryptoClass>** элемент для ссылки на криптографический класс и для настройки среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="b2227-126">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="b2227-127">Затем можно передать строку "RSA" в <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> метод и использовать <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> метод для возврата `MyCryptoRSAClass` объекта.</span><span class="sxs-lookup"><span data-stu-id="b2227-127">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b2227-128">См. также</span><span class="sxs-lookup"><span data-stu-id="b2227-128">See also</span></span>

- [<span data-ttu-id="b2227-129">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="b2227-129">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b2227-130">Схема параметров шифрования</span><span class="sxs-lookup"><span data-stu-id="b2227-130">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b2227-131">службы шифрования</span><span class="sxs-lookup"><span data-stu-id="b2227-131">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="b2227-132">Настройка криптографических классов</span><span class="sxs-lookup"><span data-stu-id="b2227-132">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
