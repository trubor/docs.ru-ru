---
description: 'Дополнительные сведения о: <mscorlib> элемент для параметров шифрования'
title: Элемент <mscorlib> для параметров шифрования
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mscorlib
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib
helpviewer_keywords:
- mscorlib element
- <mscorlib> element
ms.assetid: d549668f-31f1-4b92-8021-a9135c09ca3c
ms.openlocfilehash: 7606cdd1349c7594b5303832eed59ac51c1ddfe6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698899"
---
# <a name="mscorlib-element-for-cryptography-settings"></a><span data-ttu-id="f415b-103">Элемент \<mscorlib> для параметров шифрования</span><span class="sxs-lookup"><span data-stu-id="f415b-103">\<mscorlib> Element for Cryptography Settings</span></span>

<span data-ttu-id="f415b-104">Содержит [ \<cryptographySettings> элемент](cryptographysettings-element.md).</span><span class="sxs-lookup"><span data-stu-id="f415b-104">Contains the [\<cryptographySettings> element](cryptographysettings-element.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<mscorlib>**  
  
## <a name="syntax"></a><span data-ttu-id="f415b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f415b-105">Syntax</span></span>  
  
```xml  
      <mscorlib>
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f415b-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="f415b-106">Attributes and Elements</span></span>  

 <span data-ttu-id="f415b-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="f415b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f415b-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="f415b-108">Attributes</span></span>  

 <span data-ttu-id="f415b-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="f415b-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f415b-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="f415b-110">Child Elements</span></span>  
  
|<span data-ttu-id="f415b-111">Элемент</span><span class="sxs-lookup"><span data-stu-id="f415b-111">Element</span></span>|<span data-ttu-id="f415b-112">Описание</span><span class="sxs-lookup"><span data-stu-id="f415b-112">Description</span></span>|  
|-------------|-----------------|  
|`cryptographySettings`|<span data-ttu-id="f415b-113">Содержит параметры шифрования.</span><span class="sxs-lookup"><span data-stu-id="f415b-113">Contains cryptography settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f415b-114">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="f415b-114">Parent Elements</span></span>  
  
|<span data-ttu-id="f415b-115">Элемент</span><span class="sxs-lookup"><span data-stu-id="f415b-115">Element</span></span>|<span data-ttu-id="f415b-116">Описание</span><span class="sxs-lookup"><span data-stu-id="f415b-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f415b-117">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f415b-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f415b-118">Пример</span><span class="sxs-lookup"><span data-stu-id="f415b-118">Example</span></span>  

 <span data-ttu-id="f415b-119">В следующем примере показано, как использовать **\<mscorlib>** элемент для ссылки на криптографический класс и настройки среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="f415b-119">The following example shows how to use the **\<mscorlib>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="f415b-120">Затем можно передать строку "RSA" в <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> метод и использовать <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> метод для возврата `MyCryptoRSAClass` объекта.</span><span class="sxs-lookup"><span data-stu-id="f415b-120">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f415b-121">См. также</span><span class="sxs-lookup"><span data-stu-id="f415b-121">See also</span></span>

- <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>
- <xref:System.Security.Cryptography>
- [<span data-ttu-id="f415b-122">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="f415b-122">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="f415b-123">Схема параметров шифрования</span><span class="sxs-lookup"><span data-stu-id="f415b-123">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f415b-124">службы шифрования</span><span class="sxs-lookup"><span data-stu-id="f415b-124">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="f415b-125">Настройка криптографических классов</span><span class="sxs-lookup"><span data-stu-id="f415b-125">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
