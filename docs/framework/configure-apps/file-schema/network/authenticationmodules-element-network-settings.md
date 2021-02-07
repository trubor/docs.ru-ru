---
description: 'Дополнительные сведения о <authenticationModules> элементе: Element (параметры сети)'
title: Элемент <authenticationModules> (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#authenticationModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules
helpviewer_keywords:
- authenticationModules element
- <authenticationModules> element
ms.assetid: 10fcfaad-82ef-4692-871a-0aec9dfbe75e
ms.openlocfilehash: 2c2dc3c6a3d8fc064bb24c3d86a4441c269e43f0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698618"
---
# <a name="authenticationmodules-element-network-settings"></a><span data-ttu-id="d7c5a-103">Элемент \<authenticationModules> (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="d7c5a-103">\<authenticationModules> Element (Network Settings)</span></span>

<span data-ttu-id="d7c5a-104">Указывает модули, используемые для проверки подлинности сетевых запросов.</span><span class="sxs-lookup"><span data-stu-id="d7c5a-104">Specifies modules used to authenticate network requests.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<authenticationModules>**

## <a name="syntax"></a><span data-ttu-id="d7c5a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d7c5a-105">Syntax</span></span>  
  
```xml  
<authenticationModules>
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7c5a-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="d7c5a-106">Attributes and Elements</span></span>  

 <span data-ttu-id="d7c5a-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="d7c5a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7c5a-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="d7c5a-108">Attributes</span></span>  

 <span data-ttu-id="d7c5a-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="d7c5a-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d7c5a-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="d7c5a-110">Child Elements</span></span>  
  
|<span data-ttu-id="d7c5a-111">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="d7c5a-111">**Element**</span></span>|<span data-ttu-id="d7c5a-112">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d7c5a-112">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d7c5a-113">add</span><span class="sxs-lookup"><span data-stu-id="d7c5a-113">add</span></span>](add-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="d7c5a-114">Добавляет модуль проверки подлинности в приложение.</span><span class="sxs-lookup"><span data-stu-id="d7c5a-114">Adds an authentication module to the application.</span></span>|  
|[<span data-ttu-id="d7c5a-115">пусто</span><span class="sxs-lookup"><span data-stu-id="d7c5a-115">clear</span></span>](clear-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="d7c5a-116">Удаляет из приложения все модули проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="d7c5a-116">Clears all authentication modules from the application.</span></span>|  
|[<span data-ttu-id="d7c5a-117">remove</span><span class="sxs-lookup"><span data-stu-id="d7c5a-117">remove</span></span>](remove-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="d7c5a-118">Удаляет модуль проверки подлинности из приложения.</span><span class="sxs-lookup"><span data-stu-id="d7c5a-118">Removes an authentication module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d7c5a-119">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="d7c5a-119">Parent Elements</span></span>  
  
|<span data-ttu-id="d7c5a-120">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="d7c5a-120">**Element**</span></span>|<span data-ttu-id="d7c5a-121">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d7c5a-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d7c5a-122">system.net</span><span class="sxs-lookup"><span data-stu-id="d7c5a-122">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="d7c5a-123">Содержит параметры сети, определяющие способ подключения .NET Framework к Интернету.</span><span class="sxs-lookup"><span data-stu-id="d7c5a-123">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7c5a-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="d7c5a-124">Remarks</span></span>  

 <span data-ttu-id="d7c5a-125">`authenticationModule`Элемент указывает модули проверки подлинности, которые выполняют процесс проверки подлинности с сервером.</span><span class="sxs-lookup"><span data-stu-id="d7c5a-125">The `authenticationModule` element specifies the authentication modules that conduct the authentication process with a server.</span></span> <span data-ttu-id="d7c5a-126">Модуль проверки подлинности должен реализовывать <xref:System.Net.IAuthenticationModule> интерфейс.</span><span class="sxs-lookup"><span data-stu-id="d7c5a-126">An authentication module must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d7c5a-127">Файлы конфигурации</span><span class="sxs-lookup"><span data-stu-id="d7c5a-127">Configuration Files</span></span>  

 <span data-ttu-id="d7c5a-128">Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="d7c5a-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7c5a-129">Пример</span><span class="sxs-lookup"><span data-stu-id="d7c5a-129">Example</span></span>  

 <span data-ttu-id="d7c5a-130">В следующем примере включается модуль проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="d7c5a-130">The following example enables an authentication module.</span></span> <span data-ttu-id="d7c5a-131">Необходимо заменить значения для Version и PublicKeyToken правильными значениями для указанного модуля.</span><span class="sxs-lookup"><span data-stu-id="d7c5a-131">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d7c5a-132">См. также</span><span class="sxs-lookup"><span data-stu-id="d7c5a-132">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="d7c5a-133">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="d7c5a-133">Network Settings Schema</span></span>](index.md)
