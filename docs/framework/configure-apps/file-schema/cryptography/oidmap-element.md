---
description: 'Дополнительные сведения о: <oidMap> element'
title: Элемент <oidMap>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidMap
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap
helpviewer_keywords:
- <oidMap> element
- oidMap element
ms.assetid: 7f0c2246-c070-4748-b96a-2f66a296c539
ms.openlocfilehash: 9a71cc54546f49fcada90a0f9915d44d1fc65e89
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729996"
---
# <a name="oidmap-element"></a><span data-ttu-id="b4bfc-103">Элемент \<oidMap></span><span class="sxs-lookup"><span data-stu-id="b4bfc-103">\<oidMap> Element</span></span>

<span data-ttu-id="b4bfc-104">Содержит сопоставления идентификатора объекта (OID) ASN. 1 для классов.</span><span class="sxs-lookup"><span data-stu-id="b4bfc-104">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidMap>**

## <a name="syntax"></a><span data-ttu-id="b4bfc-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b4bfc-105">Syntax</span></span>  
  
```xml  
<oidMap>
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b4bfc-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="b4bfc-106">Attributes and Elements</span></span>  

 <span data-ttu-id="b4bfc-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="b4bfc-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b4bfc-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="b4bfc-108">Attributes</span></span>  

 <span data-ttu-id="b4bfc-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="b4bfc-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b4bfc-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="b4bfc-110">Child Elements</span></span>  
  
|<span data-ttu-id="b4bfc-111">Элемент</span><span class="sxs-lookup"><span data-stu-id="b4bfc-111">Element</span></span>|<span data-ttu-id="b4bfc-112">Описание</span><span class="sxs-lookup"><span data-stu-id="b4bfc-112">Description</span></span>|  
|-------------|-----------------|  
|[\<oidEntry>](oidentry-element.md)|<span data-ttu-id="b4bfc-113">Сопоставляет идентификатор объекта ASN. 1 с понятным именем.</span><span class="sxs-lookup"><span data-stu-id="b4bfc-113">Maps an ASN.1 OID to a friendly name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b4bfc-114">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="b4bfc-114">Parent Elements</span></span>  
  
|<span data-ttu-id="b4bfc-115">Элемент</span><span class="sxs-lookup"><span data-stu-id="b4bfc-115">Element</span></span>|<span data-ttu-id="b4bfc-116">Описание</span><span class="sxs-lookup"><span data-stu-id="b4bfc-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b4bfc-117">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b4bfc-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="b4bfc-118">Содержит параметры шифрования.</span><span class="sxs-lookup"><span data-stu-id="b4bfc-118">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="b4bfc-119">Содержит `cryptographySettings` элемент.</span><span class="sxs-lookup"><span data-stu-id="b4bfc-119">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b4bfc-120">Пример</span><span class="sxs-lookup"><span data-stu-id="b4bfc-120">Example</span></span>  

 <span data-ttu-id="b4bfc-121">В следующем примере показано, как использовать **\<oidMap>** элемент для включения СОПОСТАВЛЕНИЯ OID для алгоритма хэширования RIPEMD-160 к реализации этого хэш-алгоритма.</span><span class="sxs-lookup"><span data-stu-id="b4bfc-121">The following example shows how to use the **\<oidMap>** element to contain a mapping of an OID for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RIPEMD-160" class="MyCrypto"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"  name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b4bfc-122">См. также</span><span class="sxs-lookup"><span data-stu-id="b4bfc-122">See also</span></span>

- [<span data-ttu-id="b4bfc-123">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="b4bfc-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b4bfc-124">Схема параметров шифрования</span><span class="sxs-lookup"><span data-stu-id="b4bfc-124">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b4bfc-125">службы шифрования</span><span class="sxs-lookup"><span data-stu-id="b4bfc-125">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="b4bfc-126">Настройка криптографических классов</span><span class="sxs-lookup"><span data-stu-id="b4bfc-126">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="b4bfc-127">Отображение идентификаторов объектов на криптографические алгоритмы</span><span class="sxs-lookup"><span data-stu-id="b4bfc-127">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
