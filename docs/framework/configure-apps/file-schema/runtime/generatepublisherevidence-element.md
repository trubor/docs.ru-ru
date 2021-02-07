---
description: 'Дополнительные сведения о: <generatePublisherEvidence> element'
title: Элемент <generatePublisherEvidence>
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: 2a949b52abe5ec10872d2cade49a0556063b2018
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754528"
---
# <a name="generatepublisherevidence-element"></a><span data-ttu-id="ce3e4-103">Элемент \<generatePublisherEvidence></span><span class="sxs-lookup"><span data-stu-id="ce3e4-103">\<generatePublisherEvidence> Element</span></span>

<span data-ttu-id="ce3e4-104">Указывает, создает ли среда выполнения <xref:System.Security.Policy.Publisher> свидетельство для управления доступом для кода (CAS).</span><span class="sxs-lookup"><span data-stu-id="ce3e4-104">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<generatePublisherEvidence>**  
  
## <a name="syntax"></a><span data-ttu-id="ce3e4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ce3e4-105">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce3e4-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="ce3e4-106">Attributes and Elements</span></span>  

 <span data-ttu-id="ce3e4-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="ce3e4-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce3e4-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="ce3e4-108">Attributes</span></span>  
  
|<span data-ttu-id="ce3e4-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="ce3e4-109">Attribute</span></span>|<span data-ttu-id="ce3e4-110">Описание</span><span class="sxs-lookup"><span data-stu-id="ce3e4-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="ce3e4-111">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="ce3e4-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="ce3e4-112">Указывает, создает ли среда выполнения <xref:System.Security.Policy.Publisher> свидетельство.</span><span class="sxs-lookup"><span data-stu-id="ce3e4-112">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ce3e4-113">Атрибут enabled</span><span class="sxs-lookup"><span data-stu-id="ce3e4-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="ce3e4-114">Значение</span><span class="sxs-lookup"><span data-stu-id="ce3e4-114">Value</span></span>|<span data-ttu-id="ce3e4-115">Описание</span><span class="sxs-lookup"><span data-stu-id="ce3e4-115">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="ce3e4-116">Не создает <xref:System.Security.Policy.Publisher> свидетельство.</span><span class="sxs-lookup"><span data-stu-id="ce3e4-116">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="ce3e4-117">Создает <xref:System.Security.Policy.Publisher> свидетельство.</span><span class="sxs-lookup"><span data-stu-id="ce3e4-117">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="ce3e4-118">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ce3e4-118">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce3e4-119">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="ce3e4-119">Child Elements</span></span>  

 <span data-ttu-id="ce3e4-120">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="ce3e4-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ce3e4-121">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="ce3e4-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ce3e4-122">Элемент</span><span class="sxs-lookup"><span data-stu-id="ce3e4-122">Element</span></span>|<span data-ttu-id="ce3e4-123">Описание</span><span class="sxs-lookup"><span data-stu-id="ce3e4-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ce3e4-124">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ce3e4-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ce3e4-125">Содержит сведения о параметрах инициализации среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="ce3e4-125">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce3e4-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="ce3e4-126">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce3e4-127">В платформа .NET Framework 4 и более поздних версиях этот элемент не влияет на время загрузки сборки.</span><span class="sxs-lookup"><span data-stu-id="ce3e4-127">In the .NET Framework 4 and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="ce3e4-128">Дополнительные сведения см. в разделе "упрощение политики безопасности" раздела [изменения в системе безопасности](/previous-versions/dotnet/framework/security/security-changes).</span><span class="sxs-lookup"><span data-stu-id="ce3e4-128">For more information, see the "Security Policy Simplification" section in [Security Changes](/previous-versions/dotnet/framework/security/security-changes).</span></span>  
  
 <span data-ttu-id="ce3e4-129">Среда CLR пытается проверить подпись Authenticode во время загрузки, чтобы создать <xref:System.Security.Policy.Publisher> свидетельство для сборки.</span><span class="sxs-lookup"><span data-stu-id="ce3e4-129">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="ce3e4-130">Однако по умолчанию большинству приложений не требуется <xref:System.Security.Policy.Publisher> свидетельство.</span><span class="sxs-lookup"><span data-stu-id="ce3e4-130">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="ce3e4-131">Стандартная политика CAS не зависит от <xref:System.Security.Policy.PublisherMembershipCondition> .</span><span class="sxs-lookup"><span data-stu-id="ce3e4-131">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="ce3e4-132">Следует избегать ненужных затрат на запуск, связанных с проверкой подписи издателя, если приложение не выполняется на компьютере с настраиваемой политикой CAS или планирует удовлетворить требования к <xref:System.Security.Permissions.PublisherIdentityPermission> в среде с частичным доверием.</span><span class="sxs-lookup"><span data-stu-id="ce3e4-132">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="ce3e4-133">(Требования для разрешений идентификации всегда выполняются в среде с полным доверием.)</span><span class="sxs-lookup"><span data-stu-id="ce3e4-133">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce3e4-134">Рекомендуется, чтобы службы использовали `<generatePublisherEvidence>` элемент для повышения производительности при запуске.</span><span class="sxs-lookup"><span data-stu-id="ce3e4-134">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="ce3e4-135">Использование этого элемента также может помочь избежать задержек, которые могут привести к превышению времени ожидания и отмене запуска службы.</span><span class="sxs-lookup"><span data-stu-id="ce3e4-135">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="ce3e4-136">Файл конфигурации</span><span class="sxs-lookup"><span data-stu-id="ce3e4-136">Configuration File</span></span>  

 <span data-ttu-id="ce3e4-137">Этот элемент может использоваться только в файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="ce3e4-137">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce3e4-138">Пример</span><span class="sxs-lookup"><span data-stu-id="ce3e4-138">Example</span></span>  

 <span data-ttu-id="ce3e4-139">В следующем примере показано, как использовать `<generatePublisherEvidence>` элемент, чтобы отключить проверку политики ИЗДАТЕЛЯ CAS для приложения.</span><span class="sxs-lookup"><span data-stu-id="ce3e4-139">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ce3e4-140">См. также</span><span class="sxs-lookup"><span data-stu-id="ce3e4-140">See also</span></span>

- [<span data-ttu-id="ce3e4-141">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="ce3e4-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ce3e4-142">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="ce3e4-142">Configuration File Schema</span></span>](../index.md)
