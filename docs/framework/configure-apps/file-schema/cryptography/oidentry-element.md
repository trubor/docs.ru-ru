---
description: 'Дополнительные сведения о: <oidEntry> element'
title: Элемент <oidEntry>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry
helpviewer_keywords:
- <oidEntry> element
- oidEntry element
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
ms.openlocfilehash: d5fe22018377e247ffa0b6addb58cbeee7119e66
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698756"
---
# <a name="oidentry-element"></a><span data-ttu-id="98212-103">Элемент \<oidEntry></span><span class="sxs-lookup"><span data-stu-id="98212-103">\<oidEntry> Element</span></span>

<span data-ttu-id="98212-104">Сопоставляет идентификатор объекта (OID) ASN.1 с понятным именем.</span><span class="sxs-lookup"><span data-stu-id="98212-104">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidEntry>**

## <a name="syntax"></a><span data-ttu-id="98212-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="98212-105">Syntax</span></span>  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="98212-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="98212-106">Attributes and Elements</span></span>  

 <span data-ttu-id="98212-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="98212-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="98212-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="98212-108">Attributes</span></span>  
  
|<span data-ttu-id="98212-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="98212-109">Attribute</span></span>|<span data-ttu-id="98212-110">Описание</span><span class="sxs-lookup"><span data-stu-id="98212-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="98212-111">**КОДА**</span><span class="sxs-lookup"><span data-stu-id="98212-111">**OID**</span></span>|<span data-ttu-id="98212-112">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="98212-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="98212-113">Указывает идентификатор объекта ASN. 1, соответствующий алгоритму, реализуемому вашим классом.</span><span class="sxs-lookup"><span data-stu-id="98212-113">Specifies the ASN.1 OID corresponding to the algorithm implemented by your class.</span></span>|  
|<span data-ttu-id="98212-114">**name**</span><span class="sxs-lookup"><span data-stu-id="98212-114">**name**</span></span>|<span data-ttu-id="98212-115">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="98212-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="98212-116">Задает значение для атрибута **Name** в [\<nameEntry>](nameentry-element.md) теге.</span><span class="sxs-lookup"><span data-stu-id="98212-116">Specifies the value for the **name** attribute in the [\<nameEntry>](nameentry-element.md) tag.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="98212-117">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="98212-117">Child Elements</span></span>  

 <span data-ttu-id="98212-118">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="98212-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="98212-119">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="98212-119">Parent Elements</span></span>  
  
|<span data-ttu-id="98212-120">Элемент</span><span class="sxs-lookup"><span data-stu-id="98212-120">Element</span></span>|<span data-ttu-id="98212-121">Описание</span><span class="sxs-lookup"><span data-stu-id="98212-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="98212-122">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="98212-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="98212-123">Содержит параметры шифрования.</span><span class="sxs-lookup"><span data-stu-id="98212-123">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="98212-124">Содержит `cryptographySettings` элемент.</span><span class="sxs-lookup"><span data-stu-id="98212-124">Contains the `cryptographySettings` element.</span></span>|  
|`oidMap`|<span data-ttu-id="98212-125">Содержит сопоставления идентификатора объекта (OID) ASN. 1 для классов.</span><span class="sxs-lookup"><span data-stu-id="98212-125">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98212-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="98212-126">Remarks</span></span>  

 <span data-ttu-id="98212-127">Идентификаторы объектов ASN. 1 обозначают алгоритмы в некоторых криптографических форматах.</span><span class="sxs-lookup"><span data-stu-id="98212-127">ASN.1 object identifiers identify algorithms in some cryptographic formats.</span></span> <span data-ttu-id="98212-128">Сопоставьте идентификаторы объектов с понятными именами для алгоритмов, которые необходимо опознать.</span><span class="sxs-lookup"><span data-stu-id="98212-128">Map object identifiers to friendly names for the algorithms you want to identify.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98212-129">Пример</span><span class="sxs-lookup"><span data-stu-id="98212-129">Example</span></span>  

 <span data-ttu-id="98212-130">В следующем примере показано, как с помощью **\<oidEntry>** элемента сопоставлять идентификатор объекта для алгоритма хэширования RIPEMD-160 к реализации этого хэш-алгоритма.</span><span class="sxs-lookup"><span data-stu-id="98212-130">The following example shows how to use the **\<oidEntry>** element to map an object identifier for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="98212-131">См. также</span><span class="sxs-lookup"><span data-stu-id="98212-131">See also</span></span>

- [<span data-ttu-id="98212-132">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="98212-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="98212-133">Схема параметров шифрования</span><span class="sxs-lookup"><span data-stu-id="98212-133">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="98212-134">службы шифрования</span><span class="sxs-lookup"><span data-stu-id="98212-134">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="98212-135">Настройка криптографических классов</span><span class="sxs-lookup"><span data-stu-id="98212-135">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="98212-136">Отображение идентификаторов объектов на криптографические алгоритмы</span><span class="sxs-lookup"><span data-stu-id="98212-136">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
