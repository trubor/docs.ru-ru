---
description: Дополнительные сведения см. в статье схема параметров поставщика языка и компилятора.
title: Схема параметров поставщиков языков и компиляторов
ms.date: 03/30/2017
helpviewer_keywords:
- configuration settings [.NET Framework], compilers
- compiler configuration elements, schema
- compiler configuration elements
- language providers
- compiler configuration settings, schema
- configuration schema [.NET Framework], compiler settings
- language providers, settings schema
- compiler configuration settings
ms.assetid: c020b139-8699-4f0d-9ac9-70d0c5b2a8c8
ms.openlocfilehash: 64dd57581711358c9051cda5609e0c5ff4fc05bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699198"
---
# <a name="compiler-and-language-provider-settings-schema"></a><span data-ttu-id="c7d87-103">Схема параметров поставщиков языков и компиляторов</span><span class="sxs-lookup"><span data-stu-id="c7d87-103">Compiler and Language Provider Settings Schema</span></span>

<span data-ttu-id="c7d87-104">Параметры поставщиков языков и компиляторов определяют элементы конфигурации компиляторов для доступных поставщиков языков.</span><span class="sxs-lookup"><span data-stu-id="c7d87-104">Compiler and language provider settings specify compiler configuration elements for available language providers.</span></span> <span data-ttu-id="c7d87-105">Каждый элемент конфигурации компилятора определяет имя типа поставщика кода, параметры компилятора, названия поддерживаемых языков и поддерживаемые расширения имен файлов.</span><span class="sxs-lookup"><span data-stu-id="c7d87-105">Each compiler configuration element specifies the code provider type name, compiler parameters, supported language names, and supported file extensions.</span></span>  
  
<span data-ttu-id="c7d87-106">В .NET Framework начальные параметры компилятора определены файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="c7d87-106">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="c7d87-107">Разработчики и поставщики компиляторов могут добавлять параметры конфигурации для новой реализации <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="c7d87-107">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="c7d87-108">С помощью метода <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> можно осуществлять программное перечисление параметров конфигурации для поставщиков языков и компиляторов на компьютере.</span><span class="sxs-lookup"><span data-stu-id="c7d87-108">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<compiler>**](compiler-element.md)
  
|<span data-ttu-id="c7d87-109">Элемент</span><span class="sxs-lookup"><span data-stu-id="c7d87-109">Element</span></span>|<span data-ttu-id="c7d87-110">Описание</span><span class="sxs-lookup"><span data-stu-id="c7d87-110">Description</span></span>|  
|-------------|-----------------|  
|[\<system.codedom>](system-codedom-element.md)|<span data-ttu-id="c7d87-111">Задает параметры конфигурации компилятора для доступных поставщиков языков.</span><span class="sxs-lookup"><span data-stu-id="c7d87-111">Specifies compiler configuration settings for available language providers.</span></span>|  
|[\<compilers>](compilers-element.md)|<span data-ttu-id="c7d87-112">Контейнер для элементов конфигурации компилятора; содержит ноль или более [\<compiler>](compiler-element.md) элементов.</span><span class="sxs-lookup"><span data-stu-id="c7d87-112">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>|  
|[\<compiler>](compiler-element.md)|<span data-ttu-id="c7d87-113">Задает атрибуты конфигурации компилятора для поставщика языка.</span><span class="sxs-lookup"><span data-stu-id="c7d87-113">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c7d87-114">Пример</span><span class="sxs-lookup"><span data-stu-id="c7d87-114">Example</span></span>  

 <span data-ttu-id="c7d87-115">В приведенном ниже примере показан типичный элемент конфигурации компилятора.</span><span class="sxs-lookup"><span data-stu-id="c7d87-115">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c7d87-116">См. также</span><span class="sxs-lookup"><span data-stu-id="c7d87-116">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="c7d87-117">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="c7d87-117">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="c7d87-118">\<compiler> Элемент</span><span class="sxs-lookup"><span data-stu-id="c7d87-118">\<compiler> Element</span></span>](compiler-element.md)
