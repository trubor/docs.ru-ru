---
description: 'Дополнительные сведения о: <PreferComInsteadOfManagedRemoting> element'
title: Элемент <PreferComInsteadOfManagedRemoting>
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
ms.openlocfilehash: b621af9b584d1ea2623ffe5a44f74b5b7bd520e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782277"
---
# <a name="prefercominsteadofmanagedremoting-element"></a><span data-ttu-id="f8229-103">Элемент \<PreferComInsteadOfManagedRemoting></span><span class="sxs-lookup"><span data-stu-id="f8229-103">\<PreferComInsteadOfManagedRemoting> Element</span></span>

<span data-ttu-id="f8229-104">Указывает, будет ли среда выполнения использовать COM-взаимодействие вместо удаленного взаимодействия для всех вызовов через границы домена приложения.</span><span class="sxs-lookup"><span data-stu-id="f8229-104">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<PreferComInsteadOfManagedRemoting>**  
  
## <a name="syntax"></a><span data-ttu-id="f8229-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f8229-105">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f8229-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="f8229-106">Attributes and Elements</span></span>  

 <span data-ttu-id="f8229-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="f8229-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f8229-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="f8229-108">Attributes</span></span>  
  
|<span data-ttu-id="f8229-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="f8229-109">Attribute</span></span>|<span data-ttu-id="f8229-110">Описание</span><span class="sxs-lookup"><span data-stu-id="f8229-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="f8229-111">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="f8229-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="f8229-112">Указывает, будет ли среда выполнения использовать COM-взаимодействие вместо удаленного взаимодействия через границы домена приложения.</span><span class="sxs-lookup"><span data-stu-id="f8229-112">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="f8229-113">Атрибут enabled</span><span class="sxs-lookup"><span data-stu-id="f8229-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="f8229-114">Значение</span><span class="sxs-lookup"><span data-stu-id="f8229-114">Value</span></span>|<span data-ttu-id="f8229-115">Описание</span><span class="sxs-lookup"><span data-stu-id="f8229-115">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="f8229-116">Среда выполнения будет использовать удаленное взаимодействие через границы домена приложения.</span><span class="sxs-lookup"><span data-stu-id="f8229-116">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="f8229-117">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f8229-117">This is the default.</span></span>|  
|`true`|<span data-ttu-id="f8229-118">Среда выполнения будет использовать COM-взаимодействие через границы домена приложения.</span><span class="sxs-lookup"><span data-stu-id="f8229-118">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f8229-119">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="f8229-119">Child Elements</span></span>  

 <span data-ttu-id="f8229-120">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="f8229-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f8229-121">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="f8229-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f8229-122">Элемент</span><span class="sxs-lookup"><span data-stu-id="f8229-122">Element</span></span>|<span data-ttu-id="f8229-123">Описание</span><span class="sxs-lookup"><span data-stu-id="f8229-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f8229-124">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f8229-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f8229-125">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="f8229-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8229-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="f8229-126">Remarks</span></span>  

 <span data-ttu-id="f8229-127">Если `enabled` для атрибута задано значение `true` , среда выполнения ведет себя следующим образом:</span><span class="sxs-lookup"><span data-stu-id="f8229-127">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
- <span data-ttu-id="f8229-128">Среда выполнения не вызывает [IUnknown:: QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) для интерфейса [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) , когда интерфейс [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) входит в домен через интерфейс COM.</span><span class="sxs-lookup"><span data-stu-id="f8229-128">The runtime does not call [IUnknown::QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="f8229-129">Вместо этого он формирует [вызываемую оболочку времени выполнения](../../../../standard/native-interop/runtime-callable-wrapper.md) (RCW) вокруг объекта.</span><span class="sxs-lookup"><span data-stu-id="f8229-129">Instead, it constructs a [Runtime Callable Wrapper](../../../../standard/native-interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
- <span data-ttu-id="f8229-130">Среда выполнения возвращает E_NOINTERFACE при получении `QueryInterface` вызова для интерфейса [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) для любой [вызываемой оболочки com](../../../../standard/native-interop/com-callable-wrapper.md) (CCW), созданной в этом домене.</span><span class="sxs-lookup"><span data-stu-id="f8229-130">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../standard/native-interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="f8229-131">Эти два поведения гарантируют, что все вызовы через COM-интерфейсы между управляемыми объектами в границах доменов приложений используют COM и COM-взаимодействие вместо удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="f8229-131">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8229-132">Пример</span><span class="sxs-lookup"><span data-stu-id="f8229-132">Example</span></span>  

 <span data-ttu-id="f8229-133">В следующем примере показано, как указать, что среда выполнения должна использовать COM-взаимодействие через границы изоляции:</span><span class="sxs-lookup"><span data-stu-id="f8229-133">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f8229-134">См. также</span><span class="sxs-lookup"><span data-stu-id="f8229-134">See also</span></span>

- [<span data-ttu-id="f8229-135">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="f8229-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f8229-136">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="f8229-136">Configuration File Schema</span></span>](../index.md)
