---
description: 'Дополнительные сведения о: <clear> элемент для элемент connectionManagement (параметры сети)'
title: Элемент <clear> для connectionManagement (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- <clear> element, connectionManagement
- connectionManagement, clear element
- clear element, connectionManagement
- <connectionManagement>, clear element
ms.assetid: fb259282-84c4-4dc4-a226-78d904a6edc3
ms.openlocfilehash: e6e756e1065e48e79d59e02858963ded70d30f7e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698592"
---
# <a name="clear-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="fd5a1-103">Элемент \<clear> для connectionManagement (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="fd5a1-103">\<clear> Element for connectionManagement (Network Settings)</span></span>

<span data-ttu-id="fd5a1-104">Очищает список управления подключениями.</span><span class="sxs-lookup"><span data-stu-id="fd5a1-104">Clears the connection management list.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="fd5a1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fd5a1-105">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd5a1-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="fd5a1-106">Attributes and Elements</span></span>  

 <span data-ttu-id="fd5a1-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="fd5a1-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd5a1-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="fd5a1-108">Attributes</span></span>  

 <span data-ttu-id="fd5a1-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="fd5a1-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fd5a1-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="fd5a1-110">Child Elements</span></span>  

 <span data-ttu-id="fd5a1-111">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="fd5a1-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fd5a1-112">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="fd5a1-112">Parent Elements</span></span>  
  
|<span data-ttu-id="fd5a1-113">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="fd5a1-113">**Element**</span></span>|<span data-ttu-id="fd5a1-114">**Описание**</span><span class="sxs-lookup"><span data-stu-id="fd5a1-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="fd5a1-115">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="fd5a1-115">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="fd5a1-116">Задает максимальное число подключений к сетевому узлу.</span><span class="sxs-lookup"><span data-stu-id="fd5a1-116">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd5a1-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="fd5a1-117">Remarks</span></span>  

 <span data-ttu-id="fd5a1-118">`clear`Элемент удаляет все записи из списка управления подключениями.</span><span class="sxs-lookup"><span data-stu-id="fd5a1-118">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="fd5a1-119">Файлы конфигурации</span><span class="sxs-lookup"><span data-stu-id="fd5a1-119">Configuration Files</span></span>  

 <span data-ttu-id="fd5a1-120">Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="fd5a1-120">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd5a1-121">Пример</span><span class="sxs-lookup"><span data-stu-id="fd5a1-121">Example</span></span>  

 <span data-ttu-id="fd5a1-122">В следующем примере очищается список управления подключениями, а затем добавляются новые записи управления подключениями для сервера `www.contoso.com` и всех остальных сетевых узлов.</span><span class="sxs-lookup"><span data-stu-id="fd5a1-122">The following example clears the connection management list and then adds new connection management entries for the server `www.contoso.com` and all other network hosts.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <clear/>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fd5a1-123">См. также</span><span class="sxs-lookup"><span data-stu-id="fd5a1-123">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="fd5a1-124">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="fd5a1-124">Network Settings Schema</span></span>](index.md)
