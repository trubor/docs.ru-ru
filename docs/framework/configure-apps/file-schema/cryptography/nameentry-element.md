---
description: 'Дополнительные сведения о: <nameEntry> element'
title: Элемент <nameEntry>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry
helpviewer_keywords:
- <nameEntry> element
- nameEntry element
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
ms.openlocfilehash: 0ca227a2ba17a6b1e67fb75ec91aac9194b54737
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730009"
---
# <a name="nameentry-element"></a><span data-ttu-id="e81cd-103">Элемент \<nameEntry></span><span class="sxs-lookup"><span data-stu-id="e81cd-103">\<nameEntry> Element</span></span>

<span data-ttu-id="e81cd-104">Сопоставляет имя класса с понятным именем алгоритма, что позволяет одному классу иметь несколько понятных имен.</span><span class="sxs-lookup"><span data-stu-id="e81cd-104">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nameEntry>**  
  
## <a name="syntax"></a><span data-ttu-id="e81cd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e81cd-105">Syntax</span></span>  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e81cd-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="e81cd-106">Attributes and Elements</span></span>  

 <span data-ttu-id="e81cd-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="e81cd-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e81cd-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="e81cd-108">Attributes</span></span>  
  
|<span data-ttu-id="e81cd-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="e81cd-109">Attribute</span></span>|<span data-ttu-id="e81cd-110">Описание</span><span class="sxs-lookup"><span data-stu-id="e81cd-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e81cd-111">**name**</span><span class="sxs-lookup"><span data-stu-id="e81cd-111">**name**</span></span>|<span data-ttu-id="e81cd-112">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="e81cd-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="e81cd-113">Указывает понятное имя алгоритма, реализуемого криптографическим классом.</span><span class="sxs-lookup"><span data-stu-id="e81cd-113">Specifies the friendly name of the algorithm that the cryptography class implements.</span></span>|  
|<span data-ttu-id="e81cd-114">**class**</span><span class="sxs-lookup"><span data-stu-id="e81cd-114">**class**</span></span>|<span data-ttu-id="e81cd-115">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="e81cd-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="e81cd-116">Задает значение для атрибута **Name** в [\<cryptoClass>](cryptoclass-element.md) элементе.</span><span class="sxs-lookup"><span data-stu-id="e81cd-116">Specifies the value for the **name** attribute in the [\<cryptoClass>](cryptoclass-element.md) element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e81cd-117">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="e81cd-117">Child Elements</span></span>  

 <span data-ttu-id="e81cd-118">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="e81cd-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e81cd-119">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="e81cd-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e81cd-120">Элемент</span><span class="sxs-lookup"><span data-stu-id="e81cd-120">Element</span></span>|<span data-ttu-id="e81cd-121">Описание</span><span class="sxs-lookup"><span data-stu-id="e81cd-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e81cd-122">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e81cd-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.web`|<span data-ttu-id="e81cd-123">Задает корневой элемент для раздела конфигурации ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e81cd-123">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e81cd-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="e81cd-124">Remarks</span></span>  

 <span data-ttu-id="e81cd-125">Атрибут **Name** может быть именем одного из абстрактных классов, найденных в <xref:System.Security.Cryptography> пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="e81cd-125">The **name** attribute can be the name of one of the abstract classes found in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="e81cd-126">При вызове метода **CREATE** для абстрактного криптографического класса имя абстрактного класса передается в <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> метод.</span><span class="sxs-lookup"><span data-stu-id="e81cd-126">When you call the **Create** method on an abstract cryptography class, the abstract class name is passed to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> method.</span></span> <span data-ttu-id="e81cd-127">**CreateFromName** возвращает экземпляр типа, указанного атрибутом **класса** .</span><span class="sxs-lookup"><span data-stu-id="e81cd-127">**CreateFromName** returns an instance of the type indicated by the **class** attribute.</span></span> <span data-ttu-id="e81cd-128">Если атрибут **Name** имеет короткое имя, например RSA, это имя можно использовать при вызове метода **CreateFromName** .</span><span class="sxs-lookup"><span data-stu-id="e81cd-128">If the **name** attribute is a short name, such as RSA, you can use that name when calling the **CreateFromName** method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e81cd-129">Пример</span><span class="sxs-lookup"><span data-stu-id="e81cd-129">Example</span></span>  

 <span data-ttu-id="e81cd-130">В следующем примере показано, как использовать **\<nameEntry>** элемент для ссылки на криптографический класс и настройки среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="e81cd-130">The following example shows how to use the **\<nameEntry>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="e81cd-131">Затем можно передать строку "RSA" в <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> метод и использовать <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> метод для возврата `MyCryptoRSAClass` объекта.</span><span class="sxs-lookup"><span data-stu-id="e81cd-131">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e81cd-132">См. также</span><span class="sxs-lookup"><span data-stu-id="e81cd-132">See also</span></span>

- [<span data-ttu-id="e81cd-133">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="e81cd-133">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e81cd-134">Схема параметров шифрования</span><span class="sxs-lookup"><span data-stu-id="e81cd-134">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e81cd-135">службы шифрования</span><span class="sxs-lookup"><span data-stu-id="e81cd-135">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="e81cd-136">Настройка криптографических классов</span><span class="sxs-lookup"><span data-stu-id="e81cd-136">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
