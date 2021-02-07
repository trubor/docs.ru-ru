---
description: 'Дополнительные сведения о: <add> элемент для элемент connectionManagement (параметры сети)'
title: Элемент <add> для connectionManagement (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/add
helpviewer_keywords:
- <add> element, connectionManagement
- <connectionManagement>, add element
- add element, connectionManagement
- connectionManagement, add element
ms.assetid: 856bf57d-1c63-46c7-a178-03d97b0a4149
ms.openlocfilehash: 646d9fcfb73cfd8f4f533672c1a92883274f6e39
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729944"
---
# <a name="add-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="a628f-103">Элемент \<add> для connectionManagement (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="a628f-103">\<add> Element for connectionManagement (Network Settings)</span></span>

<span data-ttu-id="a628f-104">Добавляет IP-адрес или DNS-имя в список управления подключениями.</span><span class="sxs-lookup"><span data-stu-id="a628f-104">Adds an IP address or DNS name to the connection management list.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="a628f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a628f-105">Syntax</span></span>  
  
```xml  
<add
  address="address expression"
  maxconnection="integer"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a628f-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="a628f-106">Attributes and Elements</span></span>  

 <span data-ttu-id="a628f-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="a628f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a628f-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="a628f-108">Attributes</span></span>  
  
|<span data-ttu-id="a628f-109">**Attribute**</span><span class="sxs-lookup"><span data-stu-id="a628f-109">**Attribute**</span></span>|<span data-ttu-id="a628f-110">**Описание**</span><span class="sxs-lookup"><span data-stu-id="a628f-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="a628f-111">Строка, описывающая IP-адрес или DNS-имя.</span><span class="sxs-lookup"><span data-stu-id="a628f-111">A string describing an IP address or DNS name.</span></span>|  
|`maxconnection`|<span data-ttu-id="a628f-112">Максимальное число разрешенных подключений к серверу.</span><span class="sxs-lookup"><span data-stu-id="a628f-112">The maximum number of connections allowed to a server.</span></span> <span data-ttu-id="a628f-113">Если значение не предоставлено, используется значение по умолчанию 2.</span><span class="sxs-lookup"><span data-stu-id="a628f-113">If not supplied, the default is 2.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a628f-114">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="a628f-114">Child Elements</span></span>  

 <span data-ttu-id="a628f-115">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="a628f-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a628f-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="a628f-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a628f-117">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="a628f-117">**Element**</span></span>|<span data-ttu-id="a628f-118">**Описание**</span><span class="sxs-lookup"><span data-stu-id="a628f-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a628f-119">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="a628f-119">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="a628f-120">Задает максимальное число подключений к сетевому узлу.</span><span class="sxs-lookup"><span data-stu-id="a628f-120">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a628f-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="a628f-121">Remarks</span></span>  

 <span data-ttu-id="a628f-122">В качестве значения атрибута `address` должна быть задана либо звездочка, указывающая все подключения, либо строка в форме `<schema>://<idn_hostname>[:<port>]`.</span><span class="sxs-lookup"><span data-stu-id="a628f-122">The value of the `address` attribute should be either an asterisk to indicate all connections, or a string of the form `<schema>://<idn_hostname>[:<port>]`.</span></span>  
  
 <span data-ttu-id="a628f-123">Если URI, переданный в какие-либо API HTTP, содержит символы Юникода, то имя будет преобразовано внутренним образом с помощью свойства <xref:System.Uri.DnsSafeHost%2A>, которое может возвращать строку Punycode (поведение, зависящее от текущей конфигурации IDN).</span><span class="sxs-lookup"><span data-stu-id="a628f-123">If the URI passed to any HTTP APIs contains Unicode, the name will be converted internally using <xref:System.Uri.DnsSafeHost%2A> which might return a punicode string (behavior dependent on the current IDN configuration).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a628f-124">Файлы конфигурации</span><span class="sxs-lookup"><span data-stu-id="a628f-124">Configuration Files</span></span>  

 <span data-ttu-id="a628f-125">Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="a628f-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a628f-126">Пример</span><span class="sxs-lookup"><span data-stu-id="a628f-126">Example</span></span>  

 <span data-ttu-id="a628f-127">В следующем примере приложение настраивается для использования четырех подключений к серверу `www.contoso.com` и двух подключений ко всем остальным серверам.</span><span class="sxs-lookup"><span data-stu-id="a628f-127">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address="http://www.contoso.com" maxconnection="4" />  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a628f-128">См. также</span><span class="sxs-lookup"><span data-stu-id="a628f-128">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="a628f-129">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="a628f-129">Network Settings Schema</span></span>](index.md)
