---
description: 'Дополнительные сведения о: <System. CodeDom> элемент'
title: Элемент <system.codedom>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom
helpviewer_keywords:
- compiler configuration elements, <system.codedom> element
- system.codedom element
- <system.codedom> element
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
ms.openlocfilehash: 4761f971255b8ff7d60edfb8d9f5789c2e545aef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699016"
---
# <a name="systemcodedom-element"></a><span data-ttu-id="e4583-103">Элемент \<system.codedom></span><span class="sxs-lookup"><span data-stu-id="e4583-103">\<system.codedom> Element</span></span>

<span data-ttu-id="e4583-104">Задает параметры конфигурации компилятора для доступных поставщиков языков.</span><span class="sxs-lookup"><span data-stu-id="e4583-104">Specifies compiler configuration settings for available language providers.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.codedom>**  
  
## <a name="syntax"></a><span data-ttu-id="e4583-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e4583-105">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4583-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="e4583-106">Attributes and Elements</span></span>  

 <span data-ttu-id="e4583-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="e4583-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4583-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="e4583-108">Attributes</span></span>  

 <span data-ttu-id="e4583-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="e4583-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e4583-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="e4583-110">Child Elements</span></span>  
  
|<span data-ttu-id="e4583-111">Элемент</span><span class="sxs-lookup"><span data-stu-id="e4583-111">Element</span></span>|<span data-ttu-id="e4583-112">Описание</span><span class="sxs-lookup"><span data-stu-id="e4583-112">Description</span></span>|  
|-------------|-----------------|  
|[\<compilers>](compilers-element.md)|<span data-ttu-id="e4583-113">Контейнер для элементов конфигурации компилятора; содержит ноль или более [\<compiler>](compiler-element.md) элементов.</span><span class="sxs-lookup"><span data-stu-id="e4583-113">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e4583-114">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="e4583-114">Parent Elements</span></span>  
  
|<span data-ttu-id="e4583-115">Элемент</span><span class="sxs-lookup"><span data-stu-id="e4583-115">Element</span></span>|<span data-ttu-id="e4583-116">Описание</span><span class="sxs-lookup"><span data-stu-id="e4583-116">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="e4583-117">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e4583-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4583-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="e4583-118">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="e4583-119">Платформа .NET Framework версии 2,0</span><span class="sxs-lookup"><span data-stu-id="e4583-119">.NET Framework Version 2.0</span></span>  

 <span data-ttu-id="e4583-120">[\<system.codedom>](system-codedom-element.md)Элемент содержит параметры конфигурации компилятора для поставщиков языков, установленных на компьютере в дополнение к поставщикам по умолчанию, которые устанавливаются вместе с платформа .NET Framework, например <xref:Microsoft.CSharp.CSharpCodeProvider> и <xref:Microsoft.VisualBasic.VBCodeProvider> .</span><span class="sxs-lookup"><span data-stu-id="e4583-120">The [\<system.codedom>](system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="e4583-121">[\<compilers>](compilers-element.md)Элемент содержит ноль или более [\<compiler>](compiler-element.md) элементов.</span><span class="sxs-lookup"><span data-stu-id="e4583-121">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="e4583-122">Каждый [\<compiler>](compiler-element.md) элемент задает атрибуты конфигурации компилятора для конкретного поставщика языка.</span><span class="sxs-lookup"><span data-stu-id="e4583-122">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="e4583-123">Разработчики и поставщики компиляторов могут добавлять параметры конфигурации в файл конфигурации компьютера (Machine.config) для новой <xref:System.CodeDom.Compiler.CodeDomProvider> реализации.</span><span class="sxs-lookup"><span data-stu-id="e4583-123">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="e4583-124">Используйте <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> метод для программного перечисления поставщиков языка по умолчанию и поставщиков языков, определенных параметрами конфигурации компилятора на компьютере.</span><span class="sxs-lookup"><span data-stu-id="e4583-124">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e4583-125">В платформа .NET Framework версиях 1,0 и 1,1 поставщики языка по умолчанию, предоставляемые платформа .NET Framework, идентифицируются в [\<compilers>](compilers-element.md) элементе.</span><span class="sxs-lookup"><span data-stu-id="e4583-125">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](compilers-element.md) element.</span></span> <span data-ttu-id="e4583-126">В платформа .NET Framework версии 2,0 поставщики языка по умолчанию не определяются в [\<compilers>](compilers-element.md) элементе, но их можно перечислить с помощью <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> метода.</span><span class="sxs-lookup"><span data-stu-id="e4583-126">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="e4583-127">Платформа .NET Framework версии 1,0 и 1,1</span><span class="sxs-lookup"><span data-stu-id="e4583-127">.NET Framework Versions 1.0 and 1.1</span></span>  

 <span data-ttu-id="e4583-128">[\<system.codedom>](system-codedom-element.md)Элемент содержит параметры конфигурации компилятора для поставщиков языков на компьютере.</span><span class="sxs-lookup"><span data-stu-id="e4583-128">The [\<system.codedom>](system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="e4583-129">[\<compilers>](compilers-element.md)Элемент содержит ноль или более [\<compiler>](compiler-element.md) элементов.</span><span class="sxs-lookup"><span data-stu-id="e4583-129">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="e4583-130">Каждый [\<compiler>](compiler-element.md) элемент задает атрибуты конфигурации компилятора для конкретного поставщика языка.</span><span class="sxs-lookup"><span data-stu-id="e4583-130">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="e4583-131">В .NET Framework начальные параметры компилятора определены файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="e4583-131">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="e4583-132">Разработчики и поставщики компиляторов могут добавлять параметры конфигурации для новой реализации <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="e4583-132">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="e4583-133">С помощью метода <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> можно осуществлять программное перечисление параметров конфигурации для поставщиков языков и компиляторов на компьютере.</span><span class="sxs-lookup"><span data-stu-id="e4583-133">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="e4583-134">Файл конфигурации</span><span class="sxs-lookup"><span data-stu-id="e4583-134">Configuration File</span></span>  

 <span data-ttu-id="e4583-135">Этот элемент можно использовать в файле конфигурации компьютера и файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="e4583-135">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4583-136">Пример</span><span class="sxs-lookup"><span data-stu-id="e4583-136">Example</span></span>  

 <span data-ttu-id="e4583-137">В следующем примере показана типичная конфигурация компилятора.</span><span class="sxs-lookup"><span data-stu-id="e4583-137">The following example illustrates a typical compiler configuration.</span></span>  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,
          Version=1.0.5000.0, Culture=neutral,
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions=""  
        warningLevel="1" />  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e4583-138">См. также</span><span class="sxs-lookup"><span data-stu-id="e4583-138">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="e4583-139">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="e4583-139">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e4583-140">Схема параметров поставщика языка и компилятора</span><span class="sxs-lookup"><span data-stu-id="e4583-140">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e4583-141">\<compiler> Элемент</span><span class="sxs-lookup"><span data-stu-id="e4583-141">\<compiler> Element</span></span>](compiler-element.md)
