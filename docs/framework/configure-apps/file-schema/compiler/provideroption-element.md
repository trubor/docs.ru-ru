---
description: 'Дополнительные сведения о: <providerOption> element'
title: Элемент <providerOption>
ms.date: 03/30/2017
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
ms.openlocfilehash: 1fdca58830e8563ef28cbca28857127252928fd4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699042"
---
# <a name="provideroption-element"></a><span data-ttu-id="012c4-103">Элемент \<providerOption></span><span class="sxs-lookup"><span data-stu-id="012c4-103">\<providerOption> Element</span></span>

<span data-ttu-id="012c4-104">Указывает атрибуты версии компилятора для поставщика языка.</span><span class="sxs-lookup"><span data-stu-id="012c4-104">Specifies the compiler version attributes for a language provider.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<compiler>**](compiler-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<providerOption>**

## <a name="syntax"></a><span data-ttu-id="012c4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="012c4-105">Syntax</span></span>  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="012c4-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="012c4-106">Attributes and Elements</span></span>  

 <span data-ttu-id="012c4-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="012c4-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="012c4-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="012c4-108">Attributes</span></span>  
  
|<span data-ttu-id="012c4-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="012c4-109">Attribute</span></span>|<span data-ttu-id="012c4-110">Описание</span><span class="sxs-lookup"><span data-stu-id="012c4-110">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="012c4-111">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="012c4-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="012c4-112">Указывает имя параметра. Например, "Компилерверсион".</span><span class="sxs-lookup"><span data-stu-id="012c4-112">Specifies the name of the option; for example, "CompilerVersion".</span></span>|  
|`value`|<span data-ttu-id="012c4-113">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="012c4-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="012c4-114">Задает значение для параметра; Например, "v 3.5".</span><span class="sxs-lookup"><span data-stu-id="012c4-114">Specifies the value for the option; for example, "v3.5".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="012c4-115">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="012c4-115">Child Elements</span></span>  

 <span data-ttu-id="012c4-116">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="012c4-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="012c4-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="012c4-117">Parent Elements</span></span>  
  
|<span data-ttu-id="012c4-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="012c4-118">Element</span></span>|<span data-ttu-id="012c4-119">Описание</span><span class="sxs-lookup"><span data-stu-id="012c4-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="012c4-120">\<configuration> Элемент</span><span class="sxs-lookup"><span data-stu-id="012c4-120">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="012c4-121">Корневой элемент в любом файле конфигурации, который используется средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="012c4-121">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="012c4-122">\<system.codedom> Элемент</span><span class="sxs-lookup"><span data-stu-id="012c4-122">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="012c4-123">Задает параметры конфигурации компилятора для доступных поставщиков языков.</span><span class="sxs-lookup"><span data-stu-id="012c4-123">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="012c4-124">\<compilers> Элемент</span><span class="sxs-lookup"><span data-stu-id="012c4-124">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="012c4-125">Контейнер для элементов конфигурации компилятора; содержит ноль или более `<compiler>` элементов.</span><span class="sxs-lookup"><span data-stu-id="012c4-125">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
|[<span data-ttu-id="012c4-126">\<compiler> Элемент</span><span class="sxs-lookup"><span data-stu-id="012c4-126">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="012c4-127">Задает атрибуты конфигурации компилятора для поставщика языка.</span><span class="sxs-lookup"><span data-stu-id="012c4-127">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="012c4-128">Remarks</span><span class="sxs-lookup"><span data-stu-id="012c4-128">Remarks</span></span>  

 <span data-ttu-id="012c4-129">В платформа .NET Framework версии 3,5 поставщики кода Code Document Object Model (CodeDOM) могут поддерживать параметры, зависящие от поставщика, с помощью `<providerOption>` элемента.</span><span class="sxs-lookup"><span data-stu-id="012c4-129">In the .NET Framework version 3.5, Code Document Object Model (CodeDOM) code providers can support provider-specific options by using the `<providerOption>` element.</span></span>  
  
 <span data-ttu-id="012c4-130">Платформа .NET Framework 3,5 включает обновленные сборки платформа .NET Framework 2,0 и предоставляет новые сборки версии 3,5, содержащие новые типы.</span><span class="sxs-lookup"><span data-stu-id="012c4-130">The .NET Framework 3.5 includes updated .NET Framework 2.0 assemblies and provides new version 3.5 assemblies that contain new types.</span></span> <span data-ttu-id="012c4-131">Поставщики кода Microsoft C# и Visual Basic содержатся в сборках платформа .NET Framework 2,0, но были обновлены для поддержки компиляторов версии 3,5.</span><span class="sxs-lookup"><span data-stu-id="012c4-131">The Microsoft C# and Visual Basic code providers are contained in .NET Framework 2.0 assemblies but have been updated to support version 3.5 compilers.</span></span> <span data-ttu-id="012c4-132">По умолчанию обновленные поставщики кода создают код для компиляторов версии 2,0.</span><span class="sxs-lookup"><span data-stu-id="012c4-132">By default, the updated code providers generate code for version 2.0 compilers.</span></span> <span data-ttu-id="012c4-133">С помощью элемента можно `<providerOption>` изменить целевую версию компилятора на 3,5.</span><span class="sxs-lookup"><span data-stu-id="012c4-133">You can use the `<providerOption>` element to change the target compiler version to 3.5.</span></span> <span data-ttu-id="012c4-134">Для этого укажите для атрибута значение "Компилерверсион" `name` и "v 3.5" `value` .</span><span class="sxs-lookup"><span data-stu-id="012c4-134">To do this, specify "CompilerVersion" for the `name` attribute and "v3.5" for the `value` attribute.</span></span> <span data-ttu-id="012c4-135">Перед номером версии необходимо указать строчную букву "v".</span><span class="sxs-lookup"><span data-stu-id="012c4-135">You must precede the version number with a lower-case "v".</span></span>  
  
 <span data-ttu-id="012c4-136">Глобальную спецификацию версии можно сделать, добавив `<providerOption>` элемент в Machine.config платформа .NET Framework 2,0 или корневой Web.config файл.</span><span class="sxs-lookup"><span data-stu-id="012c4-136">You can make the version specification global by adding the `<providerOption>` element to the .NET Framework 2.0 Machine.config or root Web.config file.</span></span> <span data-ttu-id="012c4-137">Если вы обновляете версию компилятора по умолчанию до 3,5 в файле Machine.config, вы можете изменить ее обратно на 2,0 для каждого приложения, используя `<providerOption>` элемент в файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="012c4-137">If you update the default compiler version to 3.5 in the Machine.config file, you can change it back to 2.0 on a per-application basis by using the `<providerOption>` element in the application configuration file.</span></span>  
  
 <span data-ttu-id="012c4-138">Разработчики поставщика кода CodeDOM могут обрабатывать пользовательские параметры, предоставляя конструктор, принимающий `providerOptions` параметр типа <xref:System.Collections.Generic.IDictionary%602> .</span><span class="sxs-lookup"><span data-stu-id="012c4-138">CodeDOM code provider implementers can process custom options by providing a constructor that takes a `providerOptions` parameter of type <xref:System.Collections.Generic.IDictionary%602>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="012c4-139">Пример</span><span class="sxs-lookup"><span data-stu-id="012c4-139">Example</span></span>  

 <span data-ttu-id="012c4-140">В следующем примере показано, как указать, что должен использоваться поставщик кода C# версии 3,5.</span><span class="sxs-lookup"><span data-stu-id="012c4-140">The following example demonstrates how to specify that version 3.5 of the C# code provider should be used.</span></span>  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler  
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,
          Version=2.0.3600.0, Culture=neutral,
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions="/optimize"  
        warningLevel="1" >  
          <providerOption  
            name="CompilerVersion"  
            value="v3.5" />  
      </compiler>  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="012c4-141">См. также</span><span class="sxs-lookup"><span data-stu-id="012c4-141">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="012c4-142">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="012c4-142">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="012c4-143">\<compilers> Элемент</span><span class="sxs-lookup"><span data-stu-id="012c4-143">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="012c4-144">Указание полных имен типов</span><span class="sxs-lookup"><span data-stu-id="012c4-144">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="012c4-145">[Элемент compiler для элемента compilers для элемента compilation (схема параметров ASP.NET)](/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="012c4-145">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>
