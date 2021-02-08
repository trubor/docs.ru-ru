---
description: 'Дополнительные сведения о: <codeBase> element'
title: Элемент <codeBase>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase
helpviewer_keywords:
- <codeBase> element
- container tags, <codeBase> element
- codeBase element
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
ms.openlocfilehash: 714392444d3ee3db9126e9fe67832cb5f0bf5e3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795122"
---
# <a name="codebase-element"></a><span data-ttu-id="4ce21-103">Элемент \<codeBase></span><span class="sxs-lookup"><span data-stu-id="4ce21-103">\<codeBase> Element</span></span>

<span data-ttu-id="4ce21-104">Указывает, где среда CLR может найти сборку.</span><span class="sxs-lookup"><span data-stu-id="4ce21-104">Specifies where the common language runtime can find an assembly.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<codeBase>**

## <a name="syntax"></a><span data-ttu-id="4ce21-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4ce21-105">Syntax</span></span>

```xml
   <codeBase
        version="Assembly version"
        href="URL of assembly"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4ce21-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="4ce21-106">Attributes and Elements</span></span>

<span data-ttu-id="4ce21-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="4ce21-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="4ce21-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="4ce21-108">Attributes</span></span>

|<span data-ttu-id="4ce21-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="4ce21-109">Attribute</span></span>|<span data-ttu-id="4ce21-110">Описание</span><span class="sxs-lookup"><span data-stu-id="4ce21-110">Description</span></span>|
|---------------|-----------------|
|`href`|<span data-ttu-id="4ce21-111">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="4ce21-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="4ce21-112">Указывает URL-адрес, по которому среда выполнения может найти указанную версию сборки.</span><span class="sxs-lookup"><span data-stu-id="4ce21-112">Specifies the URL where the runtime can find the specified version of the assembly.</span></span>|
|`version`|<span data-ttu-id="4ce21-113">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="4ce21-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="4ce21-114">Указывает версию сборки, к которой применяется база кода.</span><span class="sxs-lookup"><span data-stu-id="4ce21-114">Specifies the version of the assembly the codebase applies to.</span></span> <span data-ttu-id="4ce21-115">Номер версии сборки имеет формат *основной. дополнительный. сборка. Редакция*.</span><span class="sxs-lookup"><span data-stu-id="4ce21-115">The format of an assembly version number is *major.minor.build.revision*.</span></span>|

## <a name="version-attribute"></a><span data-ttu-id="4ce21-116">Атрибут версии</span><span class="sxs-lookup"><span data-stu-id="4ce21-116">version Attribute</span></span>

|<span data-ttu-id="4ce21-117">Значение</span><span class="sxs-lookup"><span data-stu-id="4ce21-117">Value</span></span>|<span data-ttu-id="4ce21-118">Описание</span><span class="sxs-lookup"><span data-stu-id="4ce21-118">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="4ce21-119">Допустимые значения для каждой части номера версии — от 0 до 65535.</span><span class="sxs-lookup"><span data-stu-id="4ce21-119">Valid values for each part of the version number are 0 to 65535.</span></span>|<span data-ttu-id="4ce21-120">Не применяется</span><span class="sxs-lookup"><span data-stu-id="4ce21-120">Not applicable.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="4ce21-121">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="4ce21-121">Child Elements</span></span>

<span data-ttu-id="4ce21-122">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="4ce21-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4ce21-123">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="4ce21-123">Parent Elements</span></span>

|<span data-ttu-id="4ce21-124">Элемент</span><span class="sxs-lookup"><span data-stu-id="4ce21-124">Element</span></span>|<span data-ttu-id="4ce21-125">Описание</span><span class="sxs-lookup"><span data-stu-id="4ce21-125">Description</span></span>|
|-------------|-----------------|
|`buildproviders`|<span data-ttu-id="4ce21-126">Определяет набор поставщиков построения, которые используются для компиляции пользовательских файлов ресурсов.</span><span class="sxs-lookup"><span data-stu-id="4ce21-126">Defines a collection of build providers used to compile custom resource files.</span></span> <span data-ttu-id="4ce21-127">Можно использовать любое число поставщиков построения.</span><span class="sxs-lookup"><span data-stu-id="4ce21-127">You can have any number of build providers.</span></span>|
|`compilation`|<span data-ttu-id="4ce21-128">Настраивает все параметры компиляции, используемые ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="4ce21-128">Configures all the compilation settings that ASP.NET uses.</span></span>|
|`configuration`|<span data-ttu-id="4ce21-129">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4ce21-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`System.web`|<span data-ttu-id="4ce21-130">Задает корневой элемент для раздела конфигурации ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="4ce21-130">Specifies the root element for the ASP.NET configuration section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4ce21-131">Remarks</span><span class="sxs-lookup"><span data-stu-id="4ce21-131">Remarks</span></span>

<span data-ttu-id="4ce21-132">Чтобы среда выполнения использовала **\<codeBase>** параметр в файле конфигурации компьютера или файле политики издателя, файл должен также перенаправлять версию сборки.</span><span class="sxs-lookup"><span data-stu-id="4ce21-132">For the runtime to use the **\<codeBase>** setting in a machine configuration file or publisher policy file, the file must also redirect the assembly version.</span></span> <span data-ttu-id="4ce21-133">Файлы конфигурации приложения могут иметь параметр базы кода без перенаправления версии сборки.</span><span class="sxs-lookup"><span data-stu-id="4ce21-133">Application configuration files can have a codebase setting without redirecting the assembly version.</span></span> <span data-ttu-id="4ce21-134">После определения используемой версии сборки среда выполнения применяет параметр базы кода из файла, определяющего версию.</span><span class="sxs-lookup"><span data-stu-id="4ce21-134">After determining which assembly version to use, the runtime applies the codebase setting from the file that determines the version.</span></span> <span data-ttu-id="4ce21-135">Если база кода не указана, среда выполнения проверяет наличие сборки обычным способом.</span><span class="sxs-lookup"><span data-stu-id="4ce21-135">If no codebase is indicated, the runtime probes for the assembly in the usual way.</span></span>

<span data-ttu-id="4ce21-136">Если сборка имеет строгое имя, параметр базы кода может находиться в любом месте локальной интрасети или в Интернете.</span><span class="sxs-lookup"><span data-stu-id="4ce21-136">If the assembly has a strong name, the codebase setting can be anywhere on the local intranet or the Internet.</span></span> <span data-ttu-id="4ce21-137">Если сборка является закрытой, параметр базы кода должен быть путем относительно каталога приложения.</span><span class="sxs-lookup"><span data-stu-id="4ce21-137">If the assembly is a private assembly, the codebase setting must be a path relative to the application's directory.</span></span>

<span data-ttu-id="4ce21-138">Для сборок без строгого имени версия игнорируется, а загрузчик использует первый внешний вид \<codebase> внутри \<dependentAssembly> .</span><span class="sxs-lookup"><span data-stu-id="4ce21-138">For assemblies without a strong name, version is ignored and the loader uses the first appearance of \<codebase> inside \<dependentAssembly>.</span></span> <span data-ttu-id="4ce21-139">Если в файле конфигурации приложения имеется запись, которая перенаправляет привязку к другой сборке, перенаправление будет иметь приоритет, даже если версия сборки не соответствует запросу привязки.</span><span class="sxs-lookup"><span data-stu-id="4ce21-139">If there is an entry in the application configuration file that redirects binding to another assembly, the redirection will take precedence even if the assembly version doesn't match the binding request.</span></span>

## <a name="example"></a><span data-ttu-id="4ce21-140">Пример</span><span class="sxs-lookup"><span data-stu-id="4ce21-140">Example</span></span>

<span data-ttu-id="4ce21-141">В следующем примере показано, как указать, где среда выполнения может найти сборку.</span><span class="sxs-lookup"><span data-stu-id="4ce21-141">The following example shows how to specify where the runtime can find an assembly.</span></span>

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
         <dependentAssembly>
            <assemblyIdentity name="myAssembly"
                              publicKeyToken="32ab4ba45e0a69a1"
                              culture="neutral" />
            <codeBase version="2.0.0.0"
                      href="http://www.litwareinc.com/myAssembly.dll"/>
         </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="4ce21-142">См. также</span><span class="sxs-lookup"><span data-stu-id="4ce21-142">See also</span></span>

- [<span data-ttu-id="4ce21-143">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="4ce21-143">Runtime settings schema</span></span>](index.md)
- [<span data-ttu-id="4ce21-144">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="4ce21-144">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="4ce21-145">Укажите расположение сборки</span><span class="sxs-lookup"><span data-stu-id="4ce21-145">Specify an assembly's location</span></span>](../../../../standard/assembly/location.md)
- [<span data-ttu-id="4ce21-146">Обнаружение сборок в среде выполнения</span><span class="sxs-lookup"><span data-stu-id="4ce21-146">How the runtime locates assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
