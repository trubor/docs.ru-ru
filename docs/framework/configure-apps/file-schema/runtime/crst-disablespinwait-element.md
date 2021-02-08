---
description: 'Дополнительные сведения: <Crst_DisableSpinWait элемент>'
title: Элемент <Crst_DisableSpinWait>
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
ms.openlocfilehash: fca6fed2dabc3d1319ad030bb13bbb35a561b9aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795109"
---
# <a name="crst_disablespinwait-element"></a><span data-ttu-id="e992e-103">\<Crst_DisableSpinWait> - элемент</span><span class="sxs-lookup"><span data-stu-id="e992e-103">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="e992e-104">Указывает, следует ли отключать режим ожидания для критической секции, если это не так.</span><span class="sxs-lookup"><span data-stu-id="e992e-104">Specifies whether to disable spin-waiting for a critical section when contended.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<Crst_DisableSpinWait>**  
  
## <a name="syntax"></a><span data-ttu-id="e992e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e992e-105">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e992e-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="e992e-106">Attributes and Elements</span></span>

<span data-ttu-id="e992e-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="e992e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e992e-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="e992e-108">Attributes</span></span>  
  
|<span data-ttu-id="e992e-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="e992e-109">Attribute</span></span>|<span data-ttu-id="e992e-110">Описание</span><span class="sxs-lookup"><span data-stu-id="e992e-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e992e-111">**доступной**</span><span class="sxs-lookup"><span data-stu-id="e992e-111">**enabled**</span></span>|<span data-ttu-id="e992e-112">Указывает, отключен ли режим ожидания для критических разделов, если они не включены.</span><span class="sxs-lookup"><span data-stu-id="e992e-112">Specifies whether spin-waiting for critical sections when they are contended is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="e992e-113">Атрибут enabled</span><span class="sxs-lookup"><span data-stu-id="e992e-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="e992e-114">Значение</span><span class="sxs-lookup"><span data-stu-id="e992e-114">Value</span></span>|<span data-ttu-id="e992e-115">Описание</span><span class="sxs-lookup"><span data-stu-id="e992e-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e992e-116">1</span><span class="sxs-lookup"><span data-stu-id="e992e-116">1</span></span>|<span data-ttu-id="e992e-117">Отключите режим ожидания, если критическая секция не может быть получена.</span><span class="sxs-lookup"><span data-stu-id="e992e-117">Disable spin-waiting when a critical section cannot be acquired.</span></span>|  
|<span data-ttu-id="e992e-118">0</span><span class="sxs-lookup"><span data-stu-id="e992e-118">0</span></span>|<span data-ttu-id="e992e-119">Не отключайте режим ожидания, если критическая секция не может быть получена.</span><span class="sxs-lookup"><span data-stu-id="e992e-119">Do not disable spin-waiting when a critical section cannot be acquired.</span></span> <span data-ttu-id="e992e-120">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="e992e-120">This is the default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e992e-121">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="e992e-121">Child Elements</span></span>  

 <span data-ttu-id="e992e-122">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="e992e-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e992e-123">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="e992e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e992e-124">Элемент</span><span class="sxs-lookup"><span data-stu-id="e992e-124">Element</span></span>|<span data-ttu-id="e992e-125">Описание</span><span class="sxs-lookup"><span data-stu-id="e992e-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e992e-126">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e992e-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e992e-127">Содержит сведения о различных параметрах конфигурации среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="e992e-127">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e992e-128">Пример</span><span class="sxs-lookup"><span data-stu-id="e992e-128">Example</span></span>  

<span data-ttu-id="e992e-129">В следующем примере отключается ожидание в критических разделах, если это не так.</span><span class="sxs-lookup"><span data-stu-id="e992e-129">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e992e-130">См. также</span><span class="sxs-lookup"><span data-stu-id="e992e-130">See also</span></span>

- [<span data-ttu-id="e992e-131">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="e992e-131">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e992e-132">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="e992e-132">Configuration File Schema</span></span>](../index.md)
