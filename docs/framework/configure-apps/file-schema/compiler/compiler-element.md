---
description: 'Дополнительные сведения о: <compiler> element'
title: Элемент <compiler>
ms.date: 08/14/2018
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compiler
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers/compiler
helpviewer_keywords:
- compiler configuration elements, <compiler> element
- <compiler> element
- compiler configuration attributes
- compiler element
ms.assetid: 7a151659-b803-4c27-b5ce-1c4aa0d5a823
ms.openlocfilehash: 91540d2217320b225ae67a48d616720ef2a0b679
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699224"
---
# <a name="compiler-element"></a><span data-ttu-id="4b78d-103">Элемент \<compiler></span><span class="sxs-lookup"><span data-stu-id="4b78d-103">\<compiler> Element</span></span>

<span data-ttu-id="4b78d-104">Задает атрибуты конфигурации компилятора для поставщика языка.</span><span class="sxs-lookup"><span data-stu-id="4b78d-104">Specifies the compiler configuration attributes for a language provider.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<compiler>**

## <a name="syntax"></a><span data-ttu-id="4b78d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4b78d-105">Syntax</span></span>

```xml
<compiler
  language="languageName[;...;...]"
  extension="fileExtension[;...;...]"
  type="typeName, assemblyName"
  warningLevel="number"
  compilerOptions="option1 option2"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4b78d-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="4b78d-106">Attributes and Elements</span></span>

<span data-ttu-id="4b78d-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="4b78d-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="4b78d-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="4b78d-108">Attributes</span></span>

|<span data-ttu-id="4b78d-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="4b78d-109">Attribute</span></span>|<span data-ttu-id="4b78d-110">Описание</span><span class="sxs-lookup"><span data-stu-id="4b78d-110">Description</span></span>|
|---------------|-----------------|
|`compilerOptions`|<span data-ttu-id="4b78d-111">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="4b78d-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="4b78d-112">Задает дополнительные зависящие от компилятора аргументы для компиляции.</span><span class="sxs-lookup"><span data-stu-id="4b78d-112">Specifies additional compiler-specific arguments for compilation.</span></span> <span data-ttu-id="4b78d-113">Значения для `compilerOptions` атрибута обычно перечислены в разделе параметров компилятора для компилятора.</span><span class="sxs-lookup"><span data-stu-id="4b78d-113">The values for the `compilerOptions` attribute are typically listed in a compiler options topic for the compiler.</span></span>|
|`extension`|<span data-ttu-id="4b78d-114">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="4b78d-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="4b78d-115">Предоставляет разделенный точками с запятой список расширений имен файлов, используемых исходными файлами для поставщика языка.</span><span class="sxs-lookup"><span data-stu-id="4b78d-115">Provides a semicolon-separated list of file name extensions used by source files for the language provider.</span></span> <span data-ttu-id="4b78d-116">Например, ".cs".</span><span class="sxs-lookup"><span data-stu-id="4b78d-116">For example, ".cs".</span></span>|
|`language`|<span data-ttu-id="4b78d-117">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="4b78d-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="4b78d-118">Предоставляет разделенный точками с запятой список имен языков, поддерживаемых поставщиком языка.</span><span class="sxs-lookup"><span data-stu-id="4b78d-118">Provides a semicolon-separated list of language names supported by the language provider.</span></span> <span data-ttu-id="4b78d-119">Например, "C#;cs;csharp".</span><span class="sxs-lookup"><span data-stu-id="4b78d-119">For example, "c#;cs;csharp".</span></span>|
|`type`|<span data-ttu-id="4b78d-120">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="4b78d-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="4b78d-121">Указывает имя типа поставщика языка, включая имя сборки, содержащей реализацию поставщика.</span><span class="sxs-lookup"><span data-stu-id="4b78d-121">Specifies the type name of the language provider, including the name of the assembly containing the provider implementation.</span></span> <span data-ttu-id="4b78d-122">Имя типа должно соответствовать требованиям, определенным при [указании полных имен типов](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="4b78d-122">The type name must meet the requirements defined in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|
|`warningLevel`|<span data-ttu-id="4b78d-123">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="4b78d-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="4b78d-124">Задает уровень предупреждений компилятора по умолчанию. Определяет уровень, на котором поставщик языка рассматривает предупреждения компиляции как ошибки.</span><span class="sxs-lookup"><span data-stu-id="4b78d-124">Specifies the default compiler warning level; determines the level at which the language provider treats compilation warnings as errors.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="4b78d-125">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="4b78d-125">Child Elements</span></span>

|<span data-ttu-id="4b78d-126">Элемент</span><span class="sxs-lookup"><span data-stu-id="4b78d-126">Element</span></span>|<span data-ttu-id="4b78d-127">Описание</span><span class="sxs-lookup"><span data-stu-id="4b78d-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4b78d-128">\<providerOption> Элемент</span><span class="sxs-lookup"><span data-stu-id="4b78d-128">\<providerOption> Element</span></span>](provideroption-element.md)|<span data-ttu-id="4b78d-129">Указывает атрибуты версии компилятора для поставщика языка.</span><span class="sxs-lookup"><span data-stu-id="4b78d-129">Specifies compiler version attributes for a language provider.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4b78d-130">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="4b78d-130">Parent Elements</span></span>

|<span data-ttu-id="4b78d-131">Элемент</span><span class="sxs-lookup"><span data-stu-id="4b78d-131">Element</span></span>|<span data-ttu-id="4b78d-132">Описание</span><span class="sxs-lookup"><span data-stu-id="4b78d-132">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4b78d-133">\<configuration> Элемент</span><span class="sxs-lookup"><span data-stu-id="4b78d-133">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="4b78d-134">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4b78d-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|[<span data-ttu-id="4b78d-135">\<system.codedom> Элемент</span><span class="sxs-lookup"><span data-stu-id="4b78d-135">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="4b78d-136">Задает параметры конфигурации компилятора для доступных поставщиков языков.</span><span class="sxs-lookup"><span data-stu-id="4b78d-136">Specifies compiler configuration settings for available language providers.</span></span>|
|[<span data-ttu-id="4b78d-137">\<compilers> Элемент</span><span class="sxs-lookup"><span data-stu-id="4b78d-137">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="4b78d-138">Контейнер для элементов конфигурации компилятора; содержит ноль или более `<compiler>` элементов.</span><span class="sxs-lookup"><span data-stu-id="4b78d-138">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4b78d-139">Remarks</span><span class="sxs-lookup"><span data-stu-id="4b78d-139">Remarks</span></span>

<span data-ttu-id="4b78d-140">Каждый `<compiler>` элемент задает атрибуты конфигурации компилятора для конкретного поставщика языка.</span><span class="sxs-lookup"><span data-stu-id="4b78d-140">Each `<compiler>` element specifies the compiler configuration attributes for a specific language provider.</span></span> <span data-ttu-id="4b78d-141">Поставщик расширяет <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> класс для конкретного языка; `<compiler>` элемент определяет параметры компилятора и генератора кода для поставщика языка.</span><span class="sxs-lookup"><span data-stu-id="4b78d-141">The provider extends the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> class for a specific language; the `<compiler>` element defines the compiler and code generator settings for the language provider.</span></span>

<span data-ttu-id="4b78d-142">В .NET Framework начальные параметры компилятора определены файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="4b78d-142">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="4b78d-143">Разработчики и поставщики компиляторов могут добавлять параметры конфигурации для новой реализации <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="4b78d-143">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="4b78d-144">С помощью метода <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> можно осуществлять программное перечисление параметров конфигурации для поставщиков языков и компиляторов на компьютере.</span><span class="sxs-lookup"><span data-stu-id="4b78d-144">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>

<span data-ttu-id="4b78d-145">Элементы компилятора в файле приложения или веб-конфигурации могут дополнять или переопределять параметры в файле конфигурации компьютера.</span><span class="sxs-lookup"><span data-stu-id="4b78d-145">Compiler elements in the application or Web configuration file can supplement or override the settings in the machine configuration file.</span></span> <span data-ttu-id="4b78d-146">Если для одного и того же имени языка или одного расширения файла настроено несколько реализаций поставщика, последняя конфигурация сопоставления переопределяет все предыдущие настроенные поставщики для этого имени языка или расширения файла.</span><span class="sxs-lookup"><span data-stu-id="4b78d-146">If more than one provider implementation is configured for the same language name or the same file extension, the last matching configuration overrides any previous configured providers for that language name or file extension.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="4b78d-147">Файл конфигурации</span><span class="sxs-lookup"><span data-stu-id="4b78d-147">Configuration File</span></span>

<span data-ttu-id="4b78d-148">Этот элемент можно использовать в файле конфигурации компьютера и файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="4b78d-148">This element can be used in the machine configuration file and the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="4b78d-149">Пример</span><span class="sxs-lookup"><span data-stu-id="4b78d-149">Example</span></span>

<span data-ttu-id="4b78d-150">В следующем примере показан типичный элемент конфигурации компилятора:</span><span class="sxs-lookup"><span data-stu-id="4b78d-150">The following example illustrates a typical compiler configuration element:</span></span>

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
        warningLevel="1" />
    </compilers>
  </system.codedom>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="4b78d-151">См. также</span><span class="sxs-lookup"><span data-stu-id="4b78d-151">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="4b78d-152">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="4b78d-152">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="4b78d-153">\<compilers> Элемент</span><span class="sxs-lookup"><span data-stu-id="4b78d-153">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="4b78d-154">Указание полных имен типов</span><span class="sxs-lookup"><span data-stu-id="4b78d-154">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="4b78d-155">[Элемент compiler для элемента compilers для элемента compilation (схема параметров ASP.NET)](/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4b78d-155">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>
