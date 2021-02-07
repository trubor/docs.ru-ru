---
description: 'Дополнительные сведения о: <remove> элемент для элемент connectionManagement (параметры сети)'
title: Элемент <remove> для connectionManagement (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- connectionManagement, remove element
- <remove> element, connectionManagement
- <connectionManagement>, remove element
- remove element, connectionManagement
ms.assetid: 94b81775-5a22-4975-8c47-8620c40c3f35
ms.openlocfilehash: 98916846fb5de93ee93a7e25530e983cbd3719ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740253"
---
# <a name="remove-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="badae-103">Элемент \<remove> для connectionManagement (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="badae-103">\<remove> Element for connectionManagement (Network Settings)</span></span>

<span data-ttu-id="badae-104">Удаляет IP-адрес или DNS-имя из списка управления подключениями.</span><span class="sxs-lookup"><span data-stu-id="badae-104">Removes an IP address or DNS name from the connection management list.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="badae-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="badae-105">Syntax</span></span>  
  
```xml  
<remove
  address="server name or IP address"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="badae-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="badae-106">Attributes and Elements</span></span>  

 <span data-ttu-id="badae-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="badae-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="badae-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="badae-108">Attributes</span></span>  
  
|<span data-ttu-id="badae-109">**Attribute**</span><span class="sxs-lookup"><span data-stu-id="badae-109">**Attribute**</span></span>|<span data-ttu-id="badae-110">**Описание**</span><span class="sxs-lookup"><span data-stu-id="badae-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="badae-111">IP-адрес или имя DNS.</span><span class="sxs-lookup"><span data-stu-id="badae-111">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="badae-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="badae-112">Child Elements</span></span>  

 <span data-ttu-id="badae-113">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="badae-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="badae-114">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="badae-114">Parent Elements</span></span>  
  
|<span data-ttu-id="badae-115">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="badae-115">**Element**</span></span>|<span data-ttu-id="badae-116">**Описание**</span><span class="sxs-lookup"><span data-stu-id="badae-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="badae-117">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="badae-117">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="badae-118">Задает максимальное число подключений к сетевому узлу.</span><span class="sxs-lookup"><span data-stu-id="badae-118">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="badae-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="badae-119">Remarks</span></span>  

 <span data-ttu-id="badae-120">`remove`Элемент удаляет запись списка управления подключениями для указанного сервера.</span><span class="sxs-lookup"><span data-stu-id="badae-120">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="badae-121">Значение `address` атрибута должно быть допустимым IP-адресом или именем узла.</span><span class="sxs-lookup"><span data-stu-id="badae-121">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="badae-122">Файлы конфигурации</span><span class="sxs-lookup"><span data-stu-id="badae-122">Configuration Files</span></span>  

 <span data-ttu-id="badae-123">Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="badae-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="badae-124">Пример</span><span class="sxs-lookup"><span data-stu-id="badae-124">Example</span></span>  

 <span data-ttu-id="badae-125">В следующем примере удаляются все записи списка управления подключениями для сервера `www.adventure-works.com` , а затем настраивается приложение для использования четырех подключений к серверу `www.contoso.com` и двух подключений ко всем остальным серверам.</span><span class="sxs-lookup"><span data-stu-id="badae-125">The following example removes any connection management list entries for the server `www.adventure-works.com` and then configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <remove address="http://www.adventure-works.com" />  
      <add address="http://www.contoso.com" maxconnection="4" />  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="badae-126">См. также</span><span class="sxs-lookup"><span data-stu-id="badae-126">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="badae-127">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="badae-127">Network Settings Schema</span></span>](index.md)
