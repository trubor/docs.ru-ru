---
description: 'Дополнительные сведения о: <enforceFIPSPolicy> element'
title: Элемент <enforceFIPSPolicy>
ms.date: 03/30/2017
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
ms.openlocfilehash: d445570db634867a15b6d97d4e20186bd0641c2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787075"
---
# <a name="enforcefipspolicy-element"></a><span data-ttu-id="ae969-103">Элемент \<enforceFIPSPolicy></span><span class="sxs-lookup"><span data-stu-id="ae969-103">\<enforceFIPSPolicy> Element</span></span>

<span data-ttu-id="ae969-104">Указывает, нужно ли принудительно обеспечивать соблюдение требования конфигурации компьютера о том, что криптографические алгоритмы должны соответствовать стандартам FIPS.</span><span class="sxs-lookup"><span data-stu-id="ae969-104">Specifies whether to enforce a computer configuration requirement that cryptographic algorithms must comply with the Federal Information Processing Standards (FIPS).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<enforceFIPSPolicy>**  
  
## <a name="syntax"></a><span data-ttu-id="ae969-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ae969-105">Syntax</span></span>  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae969-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="ae969-106">Attributes and Elements</span></span>  

 <span data-ttu-id="ae969-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="ae969-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae969-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="ae969-108">Attributes</span></span>  
  
|<span data-ttu-id="ae969-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="ae969-109">Attribute</span></span>|<span data-ttu-id="ae969-110">Описание</span><span class="sxs-lookup"><span data-stu-id="ae969-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ae969-111">Включено</span><span class="sxs-lookup"><span data-stu-id="ae969-111">enabled</span></span>|<span data-ttu-id="ae969-112">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="ae969-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="ae969-113">Указывает, следует ли включить принудительное применение конфигурации компьютера, чтобы алгоритмы шифрования должны соответствовать стандарту FIPS.</span><span class="sxs-lookup"><span data-stu-id="ae969-113">Specifies whether to enable the enforcement of a computer configuration requirement that cryptographic algorithms must be compliant with FIPS.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ae969-114">Атрибут enabled</span><span class="sxs-lookup"><span data-stu-id="ae969-114">enabled Attribute</span></span>  
  
|<span data-ttu-id="ae969-115">Значение</span><span class="sxs-lookup"><span data-stu-id="ae969-115">Value</span></span>|<span data-ttu-id="ae969-116">Описание</span><span class="sxs-lookup"><span data-stu-id="ae969-116">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="ae969-117">Если компьютер настроен для использования алгоритмов шифрования, совместимых с FIPS, это требование применяется принудительно.</span><span class="sxs-lookup"><span data-stu-id="ae969-117">If your computer is configured to require cryptographic algorithms to be FIPS compliant, that requirement is enforced.</span></span> <span data-ttu-id="ae969-118">Если класс реализует алгоритм, не соответствующий стандарту FIPS, конструкторы или `Create` методы этого класса создают исключения при запуске на этом компьютере.</span><span class="sxs-lookup"><span data-stu-id="ae969-118">If a class implements an algorithm that is not compliant with FIPS, the constructors or `Create` methods for that class throw exceptions when they are run on that computer.</span></span> <span data-ttu-id="ae969-119">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ae969-119">This is the default.</span></span>|  
|`false`|<span data-ttu-id="ae969-120">Алгоритмы шифрования, используемые приложением, не должны соответствовать требованиям FIPS, независимо от конфигурации компьютера.</span><span class="sxs-lookup"><span data-stu-id="ae969-120">Cryptographic algorithms that are used by the application are not required to be compliant with FIPS, regardless of computer configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ae969-121">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="ae969-121">Child Elements</span></span>  

 <span data-ttu-id="ae969-122">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="ae969-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ae969-123">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="ae969-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ae969-124">Элемент</span><span class="sxs-lookup"><span data-stu-id="ae969-124">Element</span></span>|<span data-ttu-id="ae969-125">Описание</span><span class="sxs-lookup"><span data-stu-id="ae969-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ae969-126">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ae969-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ae969-127">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="ae969-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae969-128">Remarks</span><span class="sxs-lookup"><span data-stu-id="ae969-128">Remarks</span></span>  

 <span data-ttu-id="ae969-129">Начиная с платформа .NET Framework 2,0, создание классов, реализующих алгоритмы шифрования, управляется конфигурацией компьютера.</span><span class="sxs-lookup"><span data-stu-id="ae969-129">Starting with the .NET Framework 2.0, the creation of classes that implement cryptographic algorithms is controlled by the configuration of the computer.</span></span> <span data-ttu-id="ae969-130">Если компьютер настроен на требование соответствия алгоритмам FIPS, а класс реализует алгоритм, который не соответствует стандарту FIPS, любая попытка создать экземпляр этого класса вызывает исключение.</span><span class="sxs-lookup"><span data-stu-id="ae969-130">If the computer is configured to require algorithms to be compliant with FIPS, and a class implements an algorithm that is not compliant with FIPS, any attempt to create an instance of that class throws an exception.</span></span> <span data-ttu-id="ae969-131">Конструкторы создают <xref:System.InvalidOperationException> исключение, а `Create` методы вызывают <xref:System.Reflection.TargetInvocationException> исключение с внутренним <xref:System.InvalidOperationException> исключением.</span><span class="sxs-lookup"><span data-stu-id="ae969-131">Constructors throw an <xref:System.InvalidOperationException> exception, and `Create` methods throw a <xref:System.Reflection.TargetInvocationException> exception with an inner <xref:System.InvalidOperationException> exception.</span></span>  
  
 <span data-ttu-id="ae969-132">Если приложение выполняется на компьютерах, конфигурация которых требует соответствия стандарту FIPS, а приложение использует алгоритм, не соответствующий стандарту FIPS, этот элемент можно использовать в файле конфигурации, чтобы среда CLR не могла принудительно применять соответствие FIPS.</span><span class="sxs-lookup"><span data-stu-id="ae969-132">If your application runs on computers whose configurations require compliance with FIPS, and your application uses an algorithm that is not compliant with FIPS, you can use this element in your configuration file to prevent the common language runtime (CLR) from enforcing FIPS compliance.</span></span> <span data-ttu-id="ae969-133">Этот элемент появился в платформа .NET Framework 2,0 с пакетом обновления 1 (SP1).</span><span class="sxs-lookup"><span data-stu-id="ae969-133">This element was introduced in the .NET Framework 2.0 Service Pack 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae969-134">Пример</span><span class="sxs-lookup"><span data-stu-id="ae969-134">Example</span></span>  

 <span data-ttu-id="ae969-135">В следующем примере показано, как запретить среде CLR принудительно применять соответствие FIPS.</span><span class="sxs-lookup"><span data-stu-id="ae969-135">The following example shows how to prevent the CLR from enforcing FIPS compliance.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ae969-136">См. также</span><span class="sxs-lookup"><span data-stu-id="ae969-136">See also</span></span>

- [<span data-ttu-id="ae969-137">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="ae969-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ae969-138">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="ae969-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ae969-139">Модель криптографии</span><span class="sxs-lookup"><span data-stu-id="ae969-139">Cryptography Model</span></span>](../../../../standard/security/cryptography-model.md)
