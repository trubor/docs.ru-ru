---
description: 'Дополнительные сведения о: <cryptoNameMapping> element'
title: Элемент <cryptoNameMapping>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoNameMapping
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping
helpviewer_keywords:
- <cryptoNameMapping> element
- cryptoNameMapping element
ms.assetid: c59c9494-149b-4ce6-b38d-371f896ae85c
ms.openlocfilehash: b7dac458fdda0aabf36df96b43dca1529ffe4743
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698912"
---
# <a name="cryptonamemapping-element"></a><span data-ttu-id="da6af-103">Элемент \<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="da6af-103">\<cryptoNameMapping> Element</span></span>

<span data-ttu-id="da6af-104">Содержит сопоставления классов с понятными именами.</span><span class="sxs-lookup"><span data-stu-id="da6af-104">Contains mappings of classes to friendly names.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoNameMapping>**

## <a name="syntax"></a><span data-ttu-id="da6af-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="da6af-105">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="da6af-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="da6af-106">Attributes and Elements</span></span>  

 <span data-ttu-id="da6af-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="da6af-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="da6af-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="da6af-108">Attributes</span></span>  

 <span data-ttu-id="da6af-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="da6af-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="da6af-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="da6af-110">Child Elements</span></span>  
  
|<span data-ttu-id="da6af-111">Элемент</span><span class="sxs-lookup"><span data-stu-id="da6af-111">Element</span></span>|<span data-ttu-id="da6af-112">Описание</span><span class="sxs-lookup"><span data-stu-id="da6af-112">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="da6af-113">Содержит список криптографических классов, сопоставленных с понятным именем в **\<nameEntry>** элементе.</span><span class="sxs-lookup"><span data-stu-id="da6af-113">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="da6af-114">Сопоставляет имя класса с понятным именем алгоритма, что позволяет одному классу иметь несколько понятных имен.</span><span class="sxs-lookup"><span data-stu-id="da6af-114">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="da6af-115">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="da6af-115">Parent Elements</span></span>  
  
|<span data-ttu-id="da6af-116">Элемент</span><span class="sxs-lookup"><span data-stu-id="da6af-116">Element</span></span>|<span data-ttu-id="da6af-117">Описание</span><span class="sxs-lookup"><span data-stu-id="da6af-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="da6af-118">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="da6af-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="da6af-119">Содержит параметры шифрования.</span><span class="sxs-lookup"><span data-stu-id="da6af-119">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="da6af-120">Содержит сопоставления классов с понятными именами.</span><span class="sxs-lookup"><span data-stu-id="da6af-120">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="da6af-121">Содержит \<cryptographySettings> элемент.</span><span class="sxs-lookup"><span data-stu-id="da6af-121">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="da6af-122">Пример</span><span class="sxs-lookup"><span data-stu-id="da6af-122">Example</span></span>  

 <span data-ttu-id="da6af-123">В следующем примере показано, как использовать **\<cryptoNameMapping>** элемент для ссылки на криптографический класс и настройки среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="da6af-123">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="da6af-124">Затем можно передать строку "RSA" в <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> метод и использовать <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> метод для возврата `MyCryptoRSAClass` объекта.</span><span class="sxs-lookup"><span data-stu-id="da6af-124">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="da6af-125">См. также</span><span class="sxs-lookup"><span data-stu-id="da6af-125">See also</span></span>

- [<span data-ttu-id="da6af-126">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="da6af-126">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="da6af-127">Схема параметров шифрования</span><span class="sxs-lookup"><span data-stu-id="da6af-127">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="da6af-128">службы шифрования</span><span class="sxs-lookup"><span data-stu-id="da6af-128">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="da6af-129">Настройка криптографических классов</span><span class="sxs-lookup"><span data-stu-id="da6af-129">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
