---
description: Дополнительные сведения см. в статье Схема файла конфигурации для платформа .NET Framework
title: Схема файлов конфигурации для .NET Framework
ms.date: 05/01/2017
helpviewer_keywords:
- .NET Framework application configuration, configuration schema
- machine configuration files
- application configuration files, schema
- app.config files, schema
- schema configuration settings
- schemas, configuration settings
- enterprisesec.config files
- well-formed XML
- enterprisesec configuration files
- security.config files
- security [.NET Framework], configuration files
- application development [.NET Framework], schema
- XML tags
- container tags
- machine.config files
- configuration schema [.NET Framework]
- configuration settings [.NET Framework], applications
- configuration file reference [.NET Framework]
ms.assetid: 69003d39-dc8a-460c-a6be-e6d93e690b38
ms.openlocfilehash: eac6d14f29f5ae0eeb65efe5a1416b8f40583be3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729957"
---
# <a name="configuration-file-schema-for-the-net-framework"></a><span data-ttu-id="1b029-103">Схема файлов конфигурации для .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1b029-103">Configuration file schema for the .NET Framework</span></span>

<span data-ttu-id="1b029-104">Файлы конфигурации — это стандартные XML-файлы, которые можно использовать для изменения параметров и установки политик для приложений.</span><span class="sxs-lookup"><span data-stu-id="1b029-104">Configuration files are standard XML files that you can use to change settings and set policies for your apps.</span></span> <span data-ttu-id="1b029-105">Схема конфигурации .NET Framework состоит из элементов, которые можно использовать в файлах конфигурации для управления поведением приложений.</span><span class="sxs-lookup"><span data-stu-id="1b029-105">The .NET Framework configuration schema consists of elements that you can use in configuration files to control the behavior of your apps.</span></span> <span data-ttu-id="1b029-106">Оглавление данного раздела отражает иерархию схемы для запуска, среды выполнения, сети и других типов параметров конфигурации.</span><span class="sxs-lookup"><span data-stu-id="1b029-106">The table of contents for this section reflects the schema hierarchy for startup, runtime, network, and other types of configuration settings.</span></span>

<span data-ttu-id="1b029-107">Сведения о типах, формате и расположении файлов конфигурации см. в разделе [Настройка приложений](../index.md).</span><span class="sxs-lookup"><span data-stu-id="1b029-107">For information about the types, format, and location of configuration files, see [Configure apps](../index.md).</span></span> <span data-ttu-id="1b029-108">Для редактирования файлов конфигурации напрямую необходимо иметь представление о языке XML.</span><span class="sxs-lookup"><span data-stu-id="1b029-108">Familiarize yourself with XML if you want to edit the configuration files directly.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1b029-109">В тегах и атрибутах XML в файлах конфигурации учитывается регистр.</span><span class="sxs-lookup"><span data-stu-id="1b029-109">XML tags and attributes in configuration files are case-sensitive.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="1b029-110">Содержание раздела</span><span class="sxs-lookup"><span data-stu-id="1b029-110">In this section</span></span>

<span data-ttu-id="1b029-111">[**\<configuration>** Дерев](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1b029-111">[**\<configuration>** Element](configuration-element.md)</span></span>\
<span data-ttu-id="1b029-112">Элемент верхнего уровня для всех файлов конфигурации.</span><span class="sxs-lookup"><span data-stu-id="1b029-112">The top-level element for all configuration files.</span></span>

<span data-ttu-id="1b029-113">[**\<assemblyBinding>** Дерев](assemblybinding-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="1b029-113">[**\<assemblyBinding>** Element](assemblybinding-element-for-configuration.md)</span></span>\
<span data-ttu-id="1b029-114">Определяет политику привязки сборок на уровне конфигурации.</span><span class="sxs-lookup"><span data-stu-id="1b029-114">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="1b029-115">[**\<linkedConfiguration>** Дерев](linkedconfiguration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1b029-115">[**\<linkedConfiguration>** Element](linkedconfiguration-element.md)</span></span>\
<span data-ttu-id="1b029-116">Указание файла конфигурации, который следует включить.</span><span class="sxs-lookup"><span data-stu-id="1b029-116">Specifies a configuration file to include.</span></span>

<span data-ttu-id="1b029-117">[Схема параметров запуска](./startup/index.md)</span><span class="sxs-lookup"><span data-stu-id="1b029-117">[Startup Settings Schema](./startup/index.md)</span></span>\
<span data-ttu-id="1b029-118">Элементы, указывающие используемую версию среды CLR.</span><span class="sxs-lookup"><span data-stu-id="1b029-118">Elements that specify which version of the common language runtime to use.</span></span>

<span data-ttu-id="1b029-119">[Схема параметров среды выполнения](./runtime/index.md)</span><span class="sxs-lookup"><span data-stu-id="1b029-119">[Runtime Settings Schema](./runtime/index.md)</span></span>\
<span data-ttu-id="1b029-120">Элементы, которые настраивают привязку сборки и поведение во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="1b029-120">Elements that configure assembly binding and runtime behavior.</span></span>

<span data-ttu-id="1b029-121">[Схема параметров сети](./network/index.md)</span><span class="sxs-lookup"><span data-stu-id="1b029-121">[Network Settings Schema](./network/index.md)</span></span>\
<span data-ttu-id="1b029-122">Элементы, указывающие, как платформа .NET Framework подключается к Интернету.</span><span class="sxs-lookup"><span data-stu-id="1b029-122">Elements that specify how the .NET Framework connects to the internet.</span></span>

<span data-ttu-id="1b029-123">[Схема параметров шифрования](./cryptography/index.md)</span><span class="sxs-lookup"><span data-stu-id="1b029-123">[Cryptography Settings Schema](./cryptography/index.md)</span></span>\
<span data-ttu-id="1b029-124">Элементы, которые сопоставляют понятные имена алгоритмов с классами, реализующими алгоритмы шифрования.</span><span class="sxs-lookup"><span data-stu-id="1b029-124">Elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>

<span data-ttu-id="1b029-125">[Схема разделов конфигурации](configuration-sections-schema.md)</span><span class="sxs-lookup"><span data-stu-id="1b029-125">[Configuration Sections Schema](configuration-sections-schema.md)</span></span>\
<span data-ttu-id="1b029-126">Элементы, используемые для создания и использования разделов конфигурации для пользовательских параметров.</span><span class="sxs-lookup"><span data-stu-id="1b029-126">Elements used to create and use configuration sections for custom settings.</span></span>

<span data-ttu-id="1b029-127">[Схема параметров трассировки и отладки](./trace-debug/index.md)</span><span class="sxs-lookup"><span data-stu-id="1b029-127">[Trace and Debug Settings Schema](./trace-debug/index.md)</span></span>\
<span data-ttu-id="1b029-128">Элементы, задающих переключатели и прослушиватели трассировки.</span><span class="sxs-lookup"><span data-stu-id="1b029-128">Elements that specify trace switches and listeners.</span></span>

<span data-ttu-id="1b029-129">[Схема параметров поставщика языка и компилятора](./compiler/index.md)</span><span class="sxs-lookup"><span data-stu-id="1b029-129">[Compiler and Language Provider Settings Schema](./compiler/index.md)</span></span>\
<span data-ttu-id="1b029-130">Элементы, задающих конфигурацию компилятора для доступных поставщиков языков.</span><span class="sxs-lookup"><span data-stu-id="1b029-130">Elements that specify compiler configuration for available language providers.</span></span>

<span data-ttu-id="1b029-131">[Схема параметров приложения](application-settings-schema.md)</span><span class="sxs-lookup"><span data-stu-id="1b029-131">[Application Settings Schema](application-settings-schema.md)</span></span>\
<span data-ttu-id="1b029-132">Элементы, которые позволяют приложению Windows Forms или ASP.NET сохранять и извлекать параметры приложения и области пользователя.</span><span class="sxs-lookup"><span data-stu-id="1b029-132">Elements that enable a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span>

<span data-ttu-id="1b029-133">[Схема параметров приложения](./appsettings/index.md)</span><span class="sxs-lookup"><span data-stu-id="1b029-133">[App Settings Schema](./appsettings/index.md)</span></span>\
<span data-ttu-id="1b029-134">Содержит пользовательские параметры приложения, такие как пути к файлам, URL-адреса XML-веб-служб и другие сведения о пользовательской конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="1b029-134">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="1b029-135">[Схема веб-параметров](./web/index.md)</span><span class="sxs-lookup"><span data-stu-id="1b029-135">[Web Settings Schema](./web/index.md)</span></span>\
<span data-ttu-id="1b029-136">Элементы для настройки работы ASP.NET с ведущим приложением, например IIS.</span><span class="sxs-lookup"><span data-stu-id="1b029-136">Elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="1b029-137">Используются в файлах *Aspnet.config*.</span><span class="sxs-lookup"><span data-stu-id="1b029-137">Used in *Aspnet.config* files.</span></span>

<span data-ttu-id="1b029-138">[Схема конфигурации Windows Forms](winforms/index.md)</span><span class="sxs-lookup"><span data-stu-id="1b029-138">[Windows Forms Configuration Schema](winforms/index.md)</span></span>\
<span data-ttu-id="1b029-139">Все элементы в разделе конфигурации приложения Windows Forms, включая настройки с поддержкой нескольких мониторов и высокого DPI.</span><span class="sxs-lookup"><span data-stu-id="1b029-139">All elements in the Windows Forms application configuration section, which includes customizations such as multi-monitor and high-DPI support.</span></span>

<span data-ttu-id="1b029-140">[Схема конфигурации WCF](./wcf/index.md)</span><span class="sxs-lookup"><span data-stu-id="1b029-140">[WCF Configuration Schema](./wcf/index.md)</span></span>\
<span data-ttu-id="1b029-141">Все элементы, которые позволяют настроить службу WCF и клиентские приложения.</span><span class="sxs-lookup"><span data-stu-id="1b029-141">All elements that enable you to configure WCF service and client applications.</span></span>

<span data-ttu-id="1b029-142">[Синтаксис директив WCF](./wcf-directive/index.md)</span><span class="sxs-lookup"><span data-stu-id="1b029-142">[WCF Directive Syntax](./wcf-directive/index.md)</span></span>\
<span data-ttu-id="1b029-143">Описывает `@ServiceHost` директиву, которая определяет атрибуты, зависящие от страницы, используемые компилятором SVC.</span><span class="sxs-lookup"><span data-stu-id="1b029-143">Describes the `@ServiceHost` directive, which defines page-specific attributes used by the .svc compiler.</span></span>

<span data-ttu-id="1b029-144">[Схема конфигурации WIF](windows-identity-foundation/index.md)</span><span class="sxs-lookup"><span data-stu-id="1b029-144">[WIF Configuration Schema](windows-identity-foundation/index.md)</span></span>\
<span data-ttu-id="1b029-145">Все элементы схемы конфигурации Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="1b029-145">All elements of the Windows Identity Foundation (WIF) configuration schema.</span></span>

## <a name="related-sections"></a><span data-ttu-id="1b029-146">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="1b029-146">Related sections</span></span>

<span data-ttu-id="1b029-147">[Схема параметров удаленного взаимодействия](/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1b029-147">[Remoting Settings Schema](/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span></span>\
<span data-ttu-id="1b029-148">Описание элементов, настраивающих клиентские и серверные приложения, реализующие удаленное взаимодействие.</span><span class="sxs-lookup"><span data-stu-id="1b029-148">Describes the elements that configure client and server applications that implement remoting.</span></span>

<span data-ttu-id="1b029-149">[Схема параметров ASP.NET](/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1b029-149">[ASP.NET Settings Schema](/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span></span>\
<span data-ttu-id="1b029-150">Описание элемента, управляющего поведением веб-приложений ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="1b029-150">Describes the elements that control the behavior of ASP.NET Web applications.</span></span>

<span data-ttu-id="1b029-151">[Схема параметров веб-служб](/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1b029-151">[Web Services Settings Schema](/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span></span>\
<span data-ttu-id="1b029-152">Описание элемента, управляющего поведением веб-служб ASP.NET Web и их клиентов.</span><span class="sxs-lookup"><span data-stu-id="1b029-152">Describes the elements that control the behavior of ASP.NET Web services and their clients.</span></span>

<span data-ttu-id="1b029-153">[Настройка приложений платформа .NET Framework](/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1b029-153">[Configuring .NET Framework Apps](/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100))</span></span>\
<span data-ttu-id="1b029-154">Описание способов настройки безопасности, привязки сборок и удаленного взаимодействия в платформе .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1b029-154">Describes how to configure security, assembly binding, and remoting in the .NET Framework.</span></span>
