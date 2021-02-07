---
description: 'Дополнительные сведения о: <cryptographySettings> element'
title: Элемент <cryptographySettings>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptographySettings
helpviewer_keywords:
- cryptographySettings element
- <cryptographySettings> element
ms.assetid: 6201b7da-bcb7-49f7-b9f5-ba1fe05573b9
ms.openlocfilehash: afd4fdbc24dfaac60ce24b7a439a8d4d8a9427ea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730100"
---
# <a name="cryptographysettings-element"></a><span data-ttu-id="250d7-103">Элемент \<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="250d7-103">\<cryptographySettings> Element</span></span>

<span data-ttu-id="250d7-104">Содержит параметры шифрования.</span><span class="sxs-lookup"><span data-stu-id="250d7-104">Contains cryptography settings.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptographySettings>**

## <a name="syntax"></a><span data-ttu-id="250d7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="250d7-105">Syntax</span></span>  
  
```xml  
      <cryptographySettings>
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="250d7-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="250d7-106">Attributes and Elements</span></span>  

 <span data-ttu-id="250d7-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="250d7-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="250d7-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="250d7-108">Attributes</span></span>  

 <span data-ttu-id="250d7-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="250d7-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="250d7-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="250d7-110">Child Elements</span></span>  
  
|<span data-ttu-id="250d7-111">Элемент</span><span class="sxs-lookup"><span data-stu-id="250d7-111">Element</span></span>|<span data-ttu-id="250d7-112">Описание</span><span class="sxs-lookup"><span data-stu-id="250d7-112">Description</span></span>|  
|-------------|-----------------|  
|[\<cryptoNameMapping>](cryptonamemapping-element.md)|<span data-ttu-id="250d7-113">Содержит сопоставления классов с понятными именами.</span><span class="sxs-lookup"><span data-stu-id="250d7-113">Contains mappings of classes to friendly names.</span></span>|  
|[\<oidMap>](oidmap-element.md)|<span data-ttu-id="250d7-114">Содержит сопоставления идентификатора объекта (OID) ASN. 1 для классов.</span><span class="sxs-lookup"><span data-stu-id="250d7-114">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="250d7-115">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="250d7-115">Parent Elements</span></span>  
  
|<span data-ttu-id="250d7-116">Элемент</span><span class="sxs-lookup"><span data-stu-id="250d7-116">Element</span></span>|<span data-ttu-id="250d7-117">Описание</span><span class="sxs-lookup"><span data-stu-id="250d7-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="250d7-118">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="250d7-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="250d7-119">Содержит `cryptographySettings` элемент.</span><span class="sxs-lookup"><span data-stu-id="250d7-119">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="250d7-120">Пример</span><span class="sxs-lookup"><span data-stu-id="250d7-120">Example</span></span>  

 <span data-ttu-id="250d7-121">В следующем примере показано, как использовать **\<cryptographySettings>** элемент для хранения сопоставлений имен криптографии и СОПОСТАВЛЕНИЯ OID.</span><span class="sxs-lookup"><span data-stu-id="250d7-121">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="250d7-122">В этом примере среда выполнения настраивается таким образом, что <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> возвращает `MyHashClass` объект, а `MyCryptoClass` класс сопоставляется с идентификатором объекта 1.3.36.2.1.</span><span class="sxs-lookup"><span data-stu-id="250d7-122">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyHash="MyHashClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MyHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="250d7-123">См. также</span><span class="sxs-lookup"><span data-stu-id="250d7-123">See also</span></span>

- [<span data-ttu-id="250d7-124">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="250d7-124">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="250d7-125">Схема параметров шифрования</span><span class="sxs-lookup"><span data-stu-id="250d7-125">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="250d7-126">службы шифрования</span><span class="sxs-lookup"><span data-stu-id="250d7-126">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
