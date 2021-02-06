---
description: 'Дополнительные сведения о <module> элементе: Element (параметры сети)'
title: Элемент <module> (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#module
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/module
helpviewer_keywords:
- module element
- <module> element
ms.assetid: 10318725-9666-4d65-ab61-b94c64e59f13
ms.openlocfilehash: d498b79ae6046367bc81add5ea387e178ab6c29d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652839"
---
# <a name="module-element-network-settings"></a><span data-ttu-id="d396f-103">Элемент \<module> (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="d396f-103">\<module> Element (Network Settings)</span></span>

<span data-ttu-id="d396f-104">Добавляет в приложение новый модуль прокси-сервера.</span><span class="sxs-lookup"><span data-stu-id="d396f-104">Adds a new proxy module to the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<module>**

## <a name="syntax"></a><span data-ttu-id="d396f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d396f-105">Syntax</span></span>  
  
```xml  
<module
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d396f-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="d396f-106">Attributes and Elements</span></span>  

 <span data-ttu-id="d396f-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="d396f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d396f-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="d396f-108">Attributes</span></span>  
  
|<span data-ttu-id="d396f-109">**Attribute**</span><span class="sxs-lookup"><span data-stu-id="d396f-109">**Attribute**</span></span>|<span data-ttu-id="d396f-110">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d396f-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="d396f-111">Полное имя типа (обозначенное <xref:System.Type.FullName%2A> свойством) и имя сборки (указывается <xref:System.Reflection.Assembly.FullName%2A> свойством), разделенные запятыми, которые реализуют прокси-сервер.</span><span class="sxs-lookup"><span data-stu-id="d396f-111">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d396f-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="d396f-112">Child Elements</span></span>  

 <span data-ttu-id="d396f-113">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="d396f-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d396f-114">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="d396f-114">Parent Elements</span></span>  
  
|<span data-ttu-id="d396f-115">**Элемент**</span><span class="sxs-lookup"><span data-stu-id="d396f-115">**Element**</span></span>|<span data-ttu-id="d396f-116">**Описание**</span><span class="sxs-lookup"><span data-stu-id="d396f-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d396f-117">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="d396f-117">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="d396f-118">Настраивает прокси-сервер протокола передачи гипертекста (HTTP).</span><span class="sxs-lookup"><span data-stu-id="d396f-118">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d396f-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="d396f-119">Remarks</span></span>  

 <span data-ttu-id="d396f-120">`module`Элемент регистрирует прокси-классы, реализующие <xref:System.Net.IWebProxy> интерфейс.</span><span class="sxs-lookup"><span data-stu-id="d396f-120">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="d396f-121">После регистрации прокси-класса элемент `module` может использоваться для запроса данных через поддерживаемый прокси.</span><span class="sxs-lookup"><span data-stu-id="d396f-121">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="d396f-122">Значение `type` атрибута должно быть именем класса модуля и именем соответствующей библиотеки динамической компоновки (DLL).</span><span class="sxs-lookup"><span data-stu-id="d396f-122">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d396f-123">Файлы конфигурации</span><span class="sxs-lookup"><span data-stu-id="d396f-123">Configuration Files</span></span>  

 <span data-ttu-id="d396f-124">Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="d396f-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d396f-125">Пример</span><span class="sxs-lookup"><span data-stu-id="d396f-125">Example</span></span>  

 <span data-ttu-id="d396f-126">В следующем примере регистрируется пользовательский прокси-класс.</span><span class="sxs-lookup"><span data-stu-id="d396f-126">The following example registers a custom proxy class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <module  
        type="Test.CustomWebProxy, TestProxy, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b23a5c561934e385"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d396f-127">См. также</span><span class="sxs-lookup"><span data-stu-id="d396f-127">See also</span></span>

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="d396f-128">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="d396f-128">Network Settings Schema</span></span>](index.md)
