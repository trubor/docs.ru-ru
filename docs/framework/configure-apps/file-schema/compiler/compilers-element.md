---
description: 'Дополнительные сведения о: <compilers> element'
title: Элемент <compilers>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
ms.openlocfilehash: 6ced6bc81bc7d829ccebab50e0a361985c970f5e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699172"
---
# <a name="compilers-element"></a><span data-ttu-id="f8b43-103">Элемент \<compilers></span><span class="sxs-lookup"><span data-stu-id="f8b43-103">\<compilers> Element</span></span>

<span data-ttu-id="f8b43-104">Контейнер для элементов конфигурации компилятора; содержит ноль или более [\<compiler>](compiler-element.md) элементов.</span><span class="sxs-lookup"><span data-stu-id="f8b43-104">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<compilers>**

## <a name="syntax"></a><span data-ttu-id="f8b43-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f8b43-105">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f8b43-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="f8b43-106">Attributes and Elements</span></span>  

 <span data-ttu-id="f8b43-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="f8b43-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f8b43-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="f8b43-108">Attributes</span></span>  

 <span data-ttu-id="f8b43-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="f8b43-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f8b43-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="f8b43-110">Child Elements</span></span>  
  
|<span data-ttu-id="f8b43-111">Элемент</span><span class="sxs-lookup"><span data-stu-id="f8b43-111">Element</span></span>|<span data-ttu-id="f8b43-112">Описание</span><span class="sxs-lookup"><span data-stu-id="f8b43-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f8b43-113">\<compiler> Элемент</span><span class="sxs-lookup"><span data-stu-id="f8b43-113">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="f8b43-114">Задает атрибуты конфигурации компилятора для поставщика языка.</span><span class="sxs-lookup"><span data-stu-id="f8b43-114">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f8b43-115">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="f8b43-115">Parent Elements</span></span>  
  
|<span data-ttu-id="f8b43-116">Элемент</span><span class="sxs-lookup"><span data-stu-id="f8b43-116">Element</span></span>|<span data-ttu-id="f8b43-117">Описание</span><span class="sxs-lookup"><span data-stu-id="f8b43-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f8b43-118">\<configuration> Элемент</span><span class="sxs-lookup"><span data-stu-id="f8b43-118">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="f8b43-119">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f8b43-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="f8b43-120">\<system.codedom> Элемент</span><span class="sxs-lookup"><span data-stu-id="f8b43-120">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="f8b43-121">Задает параметры конфигурации компилятора для доступных поставщиков языков.</span><span class="sxs-lookup"><span data-stu-id="f8b43-121">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8b43-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="f8b43-122">Remarks</span></span>  

 <span data-ttu-id="f8b43-123">[\<compilers>](compilers-element.md)Элемент содержит параметры конфигурации компилятора для поставщиков языков на компьютере.</span><span class="sxs-lookup"><span data-stu-id="f8b43-123">The [\<compilers>](compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="f8b43-124">Каждый [\<compiler>](compiler-element.md) элемент задает атрибуты конфигурации компилятора для конкретного поставщика языка.</span><span class="sxs-lookup"><span data-stu-id="f8b43-124">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="f8b43-125">Платформа .NET Framework определяет начальные параметры компилятора и языка в файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="f8b43-125">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="f8b43-126">Разработчики и поставщики компиляторов могут добавлять параметры конфигурации для новой реализации <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f8b43-126">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="f8b43-127">С помощью метода <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> можно осуществлять программное перечисление параметров конфигурации для поставщиков языков и компиляторов на компьютере.</span><span class="sxs-lookup"><span data-stu-id="f8b43-127">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="f8b43-128">Файл конфигурации</span><span class="sxs-lookup"><span data-stu-id="f8b43-128">Configuration File</span></span>  

 <span data-ttu-id="f8b43-129">Этот элемент можно использовать в файле конфигурации компьютера и файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="f8b43-129">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8b43-130">Пример</span><span class="sxs-lookup"><span data-stu-id="f8b43-130">Example</span></span>  

 <span data-ttu-id="f8b43-131">В приведенном ниже примере показан типичный элемент конфигурации компилятора.</span><span class="sxs-lookup"><span data-stu-id="f8b43-131">The following example illustrates a typical compiler configuration element.</span></span>  
  
```xml  
<configuration>  
   <system.codedom>  
     <compilers>  
       <!-- zero or more compiler elements -->  
       <compiler
          language="c#;cs;csharp"
          extension=".cs"  
          type="Microsoft.CSharp.CSharpCodeProvider, System, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
          compilerOptions=""
          warningLevel="1" />  
     </compilers>  
   </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f8b43-132">См. также</span><span class="sxs-lookup"><span data-stu-id="f8b43-132">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="f8b43-133">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="f8b43-133">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="f8b43-134">Схема параметров поставщика языка и компилятора</span><span class="sxs-lookup"><span data-stu-id="f8b43-134">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f8b43-135">\<compiler> Элемент</span><span class="sxs-lookup"><span data-stu-id="f8b43-135">\<compiler> Element</span></span>](compiler-element.md)
