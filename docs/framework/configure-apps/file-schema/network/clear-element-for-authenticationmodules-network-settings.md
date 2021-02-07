---
description: 'Дополнительные сведения о: <clear> элемент для authenticationModules (параметры сети)'
title: Элемент <clear> для authenticationModules (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, authenticationModules
- <authenticationModules>, clear element
- <clear> element, authenticationModules
- authenticationModules, clear element
ms.assetid: dc522c45-4a80-4831-8955-f7b68a47edfd
ms.openlocfilehash: ccfc9f53ef53268cdb1155673fc47a862a63419c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698574"
---
# <a name="clear-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="ba7a8-103">Элемент \<clear> для authenticationModules (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="ba7a8-103">\<clear> Element for authenticationModules (Network Settings)</span></span>

<span data-ttu-id="ba7a8-104">Удаляет из приложения все модули проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="ba7a8-104">Clears all authentication modules from the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="ba7a8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ba7a8-105">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ba7a8-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="ba7a8-106">Attributes and Elements</span></span>  

 <span data-ttu-id="ba7a8-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="ba7a8-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ba7a8-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="ba7a8-108">Attributes</span></span>  

 <span data-ttu-id="ba7a8-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="ba7a8-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ba7a8-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="ba7a8-110">Child Elements</span></span>  

 <span data-ttu-id="ba7a8-111">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="ba7a8-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ba7a8-112">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="ba7a8-112">Parent Elements</span></span>  
  
|<span data-ttu-id="ba7a8-113">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="ba7a8-113">**Element**</span></span>|<span data-ttu-id="ba7a8-114">**Описание**</span><span class="sxs-lookup"><span data-stu-id="ba7a8-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ba7a8-115">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="ba7a8-115">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="ba7a8-116">Указывает модули, используемые для проверки подлинности сетевых запросов.</span><span class="sxs-lookup"><span data-stu-id="ba7a8-116">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba7a8-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="ba7a8-117">Remarks</span></span>  

 <span data-ttu-id="ba7a8-118">`clear`Элемент удаляет все модули проверки подлинности, определенные ранее в файле конфигурации или на более высоком уровне иерархии конфигурации.</span><span class="sxs-lookup"><span data-stu-id="ba7a8-118">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="ba7a8-119">Файлы конфигурации</span><span class="sxs-lookup"><span data-stu-id="ba7a8-119">Configuration Files</span></span>  

 <span data-ttu-id="ba7a8-120">Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="ba7a8-120">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba7a8-121">Пример</span><span class="sxs-lookup"><span data-stu-id="ba7a8-121">Example</span></span>  

 <span data-ttu-id="ba7a8-122">В следующем примере удаляются все настроенные модули проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="ba7a8-122">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba7a8-123">См. также</span><span class="sxs-lookup"><span data-stu-id="ba7a8-123">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="ba7a8-124">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="ba7a8-124">Network Settings Schema</span></span>](index.md)
