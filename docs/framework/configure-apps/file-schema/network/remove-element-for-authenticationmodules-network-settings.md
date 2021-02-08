---
description: 'Дополнительные сведения о: <remove> элемент для authenticationModules (параметры сети)'
title: Элемент <remove> для authenticationModules (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, authenticationModules
- <authenticationModules>, remove element
- <remove> element, authenticationModules
- authenticationModules, remove element
ms.assetid: abf79949-b05c-465a-b51c-bbeda9a74173
ms.openlocfilehash: 7c97cd20717e6e0945cf77ad6584b319120ec6a1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804092"
---
# <a name="remove-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="08bee-103">Элемент \<remove> для authenticationModules (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="08bee-103">\<remove> Element for authenticationModules (Network Settings)</span></span>

<span data-ttu-id="08bee-104">Удаляет модуль проверки подлинности из приложения.</span><span class="sxs-lookup"><span data-stu-id="08bee-104">Removes an authentication module from the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="08bee-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="08bee-105">Syntax</span></span>  
  
```xml  
<remove
   type="authentication module name"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08bee-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="08bee-106">Attributes and Elements</span></span>  

 <span data-ttu-id="08bee-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="08bee-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08bee-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="08bee-108">Attributes</span></span>  
  
|<span data-ttu-id="08bee-109">**Attribute**</span><span class="sxs-lookup"><span data-stu-id="08bee-109">**Attribute**</span></span>|<span data-ttu-id="08bee-110">**Описание**</span><span class="sxs-lookup"><span data-stu-id="08bee-110">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="08bee-111">**type**</span><span class="sxs-lookup"><span data-stu-id="08bee-111">**type**</span></span>|<span data-ttu-id="08bee-112">Имя удаляемого модуля проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="08bee-112">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="08bee-113">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="08bee-113">Child Elements</span></span>  

 <span data-ttu-id="08bee-114">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="08bee-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="08bee-115">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="08bee-115">Parent Elements</span></span>  
  
|<span data-ttu-id="08bee-116">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="08bee-116">**Element**</span></span>|<span data-ttu-id="08bee-117">**Описание**</span><span class="sxs-lookup"><span data-stu-id="08bee-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="08bee-118">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="08bee-118">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="08bee-119">Указывает модули, используемые для проверки подлинности сетевых запросов.</span><span class="sxs-lookup"><span data-stu-id="08bee-119">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08bee-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="08bee-120">Remarks</span></span>  

 <span data-ttu-id="08bee-121">`remove`Элемент удаляет модули проверки подлинности, которые были определены ранее в файле конфигурации или на более высоком уровне иерархии конфигурации.</span><span class="sxs-lookup"><span data-stu-id="08bee-121">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="08bee-122">Значение `type` атрибута должно быть допустимым именем класса.</span><span class="sxs-lookup"><span data-stu-id="08bee-122">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="08bee-123">Файлы конфигурации</span><span class="sxs-lookup"><span data-stu-id="08bee-123">Configuration Files</span></span>  

 <span data-ttu-id="08bee-124">Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="08bee-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="08bee-125">Пример</span><span class="sxs-lookup"><span data-stu-id="08bee-125">Example</span></span>  

 <span data-ttu-id="08bee-126">В следующем примере удаляется модуль проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="08bee-126">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="08bee-127">См. также</span><span class="sxs-lookup"><span data-stu-id="08bee-127">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="08bee-128">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="08bee-128">Network Settings Schema</span></span>](index.md)
