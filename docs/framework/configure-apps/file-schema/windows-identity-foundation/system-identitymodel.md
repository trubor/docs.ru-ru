---
description: 'Дополнительные сведения о: <System. identityModel>'
title: <system.identityModel>
ms.date: 03/30/2017
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
author: BrucePerlerMS
ms.openlocfilehash: c597f2a849248366f9cf3847c8ef369c13d7a286
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786529"
---
# \<system.identityModel>

<span data-ttu-id="e694f-103">Предоставляет конфигурацию для включения параметров Windows Identity Foundation (WIF) в приложениях.</span><span class="sxs-lookup"><span data-stu-id="e694f-103">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.identityModel>**  
  
## <a name="syntax"></a><span data-ttu-id="e694f-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e694f-104">Syntax</span></span>  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e694f-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="e694f-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e694f-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="e694f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e694f-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="e694f-107">Attributes</span></span>  

 <span data-ttu-id="e694f-108">None</span><span class="sxs-lookup"><span data-stu-id="e694f-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e694f-109">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="e694f-109">Child Elements</span></span>  
  
|<span data-ttu-id="e694f-110">Элемент</span><span class="sxs-lookup"><span data-stu-id="e694f-110">Element</span></span>|<span data-ttu-id="e694f-111">Описание</span><span class="sxs-lookup"><span data-stu-id="e694f-111">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="e694f-112">Задает параметры удостоверений уровня службы.</span><span class="sxs-lookup"><span data-stu-id="e694f-112">Specifies service-level identity settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e694f-113">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="e694f-113">Parent Elements</span></span>  
  
|<span data-ttu-id="e694f-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="e694f-114">Element</span></span>|<span data-ttu-id="e694f-115">Описание</span><span class="sxs-lookup"><span data-stu-id="e694f-115">Description</span></span>|  
|-------------|-----------------|  
|`<configuration>`|<span data-ttu-id="e694f-116">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e694f-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e694f-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="e694f-117">Remarks</span></span>  

 <span data-ttu-id="e694f-118">Добавьте `<system.identityModel>` раздел в файл конфигурации, чтобы настроить службу или приложение для использования Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="e694f-118">Add a `<system.identityModel>` section to the configuration file to configure a service or application to use Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="e694f-119">`<system.identityModel>`Элемент представлен <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> классом.</span><span class="sxs-lookup"><span data-stu-id="e694f-119">The `<system.identityModel>` element is represented by the <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e694f-120">Пример</span><span class="sxs-lookup"><span data-stu-id="e694f-120">Example</span></span>  

 <span data-ttu-id="e694f-121">В следующем примере показано, как добавить `<system.identityModel>` раздел в файл конфигурации.</span><span class="sxs-lookup"><span data-stu-id="e694f-121">The following example shows how to add a `<system.identityModel>` section to a configuration file.</span></span> <span data-ttu-id="e694f-122">Сначала необходимо добавить раздел конфигурации и объявление пространства имен в `<configSections>` элемент.</span><span class="sxs-lookup"><span data-stu-id="e694f-122">You must first add the configuration section and namespace declaration under the `<configSections>` element.</span></span> <span data-ttu-id="e694f-123">Затем можно добавить `<system.IdentityModel>` элемент в файл конфигурации, чтобы указать одну или несколько конфигураций удостоверений.</span><span class="sxs-lookup"><span data-stu-id="e694f-123">Then you can add the `<system.IdentityModel>` element to your configuration file to specify one or more identity configurations.</span></span>  
  
```xml  
<configuration>  
  <configSections>  
    <!--WIF 4.5 sections -->  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
  </configSections>  
  
  ...  
  
  <system.identityModel>  
    <identityConfiguration>  
      <audienceUris>  
        <add value="http://localhost/WebApplication1/" />  
      </audienceUris>  
      <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089">  
        <trustedIssuers>  
          <add thumbprint="313D3B … 9106A9EC" name="SelfSTS" />  
        </trustedIssuers>  
      </issuerNameRegistry>  
      <certificateValidation certificateValidationMode="None"/>  
    </identityConfiguration>  
  </system.identityModel>  
  
  ...  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e694f-124">См. также</span><span class="sxs-lookup"><span data-stu-id="e694f-124">See also</span></span>

- <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
