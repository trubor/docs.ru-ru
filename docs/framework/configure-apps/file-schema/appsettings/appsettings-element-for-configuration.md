---
title: Элемент <appSettings> для <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
ms.openlocfilehash: 66260d15768781b7fa3d9397b8e8a7d9ad68ab95
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009798"
---
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="53495-102">Элемент \<appSettings> для \<configuration></span><span class="sxs-lookup"><span data-stu-id="53495-102">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="53495-103">Содержит пользовательские параметры приложения.</span><span class="sxs-lookup"><span data-stu-id="53495-103">Contains custom application settings.</span></span> <span data-ttu-id="53495-104">Это предварительно определенный раздел конфигурации, предоставляемый .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="53495-104">This is a predefined configuration section provided by the .NET Framework.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<appSettings>**

## <a name="syntax"></a><span data-ttu-id="53495-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="53495-105">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="53495-106">attribute</span><span class="sxs-lookup"><span data-stu-id="53495-106">Attribute</span></span>

|           | <span data-ttu-id="53495-107">Описание</span><span class="sxs-lookup"><span data-stu-id="53495-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="53495-108">**file**</span><span class="sxs-lookup"><span data-stu-id="53495-108">**file**</span></span>  | <span data-ttu-id="53495-109">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="53495-109">Optional attribute.</span></span><br><br><span data-ttu-id="53495-110">Указывает относительный путь к внешнему файлу, содержащему настраиваемые параметры конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="53495-110">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="53495-111">Указанный файл содержит те же параметры, что указаны в **\<add>** **\<remove>** элементах, и, **\<clear>** и использует тот же формат пар "ключ-значение", что и эти элементы.</span><span class="sxs-lookup"><span data-stu-id="53495-111">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="53495-112">Путь указан относительно основного файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="53495-112">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="53495-113">Для Windows Forms приложения это двоичная папка (например, */бин/дебуг*), а не расположение файла конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="53495-113">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="53495-114">Для приложений веб-форм путь определяется относительно корневого каталога приложения, где расположен файл *web.config* .</span><span class="sxs-lookup"><span data-stu-id="53495-114">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="53495-115">Среда выполнения игнорирует атрибут, если не удается найти указанный файл.</span><span class="sxs-lookup"><span data-stu-id="53495-115">The runtime ignores the attribute if the specified file can't be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="53495-116">Родительский элемент</span><span class="sxs-lookup"><span data-stu-id="53495-116">Parent element</span></span>

|     | <span data-ttu-id="53495-117">Описание</span><span class="sxs-lookup"><span data-stu-id="53495-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="53495-118">**\<configuration>** Элемент</span><span class="sxs-lookup"><span data-stu-id="53495-118">**\<configuration>** Element</span></span>](../configuration-element.md) | <span data-ttu-id="53495-119">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="53495-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="53495-120">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="53495-120">Child elements</span></span>

|     | <span data-ttu-id="53495-121">Описание</span><span class="sxs-lookup"><span data-stu-id="53495-121">Description</span></span> |
| --- | ----------- |
| [**\<add>**](add-element-for-appsettings.md) | <span data-ttu-id="53495-122">Добавляет пользовательский параметр приложения.</span><span class="sxs-lookup"><span data-stu-id="53495-122">Adds a custom application setting.</span></span> |
| [**\<clear>**](clear-element-for-appsettings.md) | <span data-ttu-id="53495-123">Удаляет все ранее определенные параметры приложения.</span><span class="sxs-lookup"><span data-stu-id="53495-123">Clears all previously defined application settings.</span></span> |
| [**\<remove>**](remove-element-for-appsettings.md) | <span data-ttu-id="53495-124">Удаляет ранее определенный параметр приложения.</span><span class="sxs-lookup"><span data-stu-id="53495-124">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="53495-125">Комментарии</span><span class="sxs-lookup"><span data-stu-id="53495-125">Remarks</span></span>

<span data-ttu-id="53495-126">**\<appSettings>** Элемент хранит сведения о конфигурации пользовательского приложения, такие как строки подключения к базе данных, пути к файлам, URL-адреса XML или другие пользовательские сведения о конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="53495-126">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="53495-127">Пары "ключ-значение", указанные в **\<appSettings>** элементе, доступны в коде с помощью <xref:System.Configuration.ConfigurationSettings> класса.</span><span class="sxs-lookup"><span data-stu-id="53495-127">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="53495-128">Атрибут **File** можно использовать в **\<appSettings>** элементе *Web.config* и файлах конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="53495-128">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="53495-129">Этот атрибут задает файл конфигурации, предоставляющий дополнительные параметры или переопределяющий параметры, указанные в **\<appSettings>** элементе.</span><span class="sxs-lookup"><span data-stu-id="53495-129">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="53495-130">Атрибут **File** может использоваться в сценариях разработки группы управления исходным кодом, например, когда пользователь хочет переопределить параметры проекта, указанные в файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="53495-130">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="53495-131">Файлы конфигурации, заданные атрибутом **File** , должны иметь корневой узел, **\<appSettings>** а не **\<configuration>** .</span><span class="sxs-lookup"><span data-stu-id="53495-131">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="53495-132">Пример</span><span class="sxs-lookup"><span data-stu-id="53495-132">Example</span></span>

<span data-ttu-id="53495-133">В приведенном ниже примере показан внешний файл параметров приложения (*custom.config*), в котором определен пользовательский параметр приложения.</span><span class="sxs-lookup"><span data-stu-id="53495-133">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="53495-134">В приведенном ниже примере показан файл конфигурации приложения, в котором используется параметр из внешнего файла параметров и задается собственный параметр приложения.</span><span class="sxs-lookup"><span data-stu-id="53495-134">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="53495-135">Файл конфигурации</span><span class="sxs-lookup"><span data-stu-id="53495-135">Configuration file</span></span>

<span data-ttu-id="53495-136">Этот элемент можно использовать в файле конфигурации приложения, файле конфигурации компьютера (*Machine.config*) и *Web.config* файлах, которые не находятся на уровне каталога приложений.</span><span class="sxs-lookup"><span data-stu-id="53495-136">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="53495-137">См. также</span><span class="sxs-lookup"><span data-stu-id="53495-137">See also</span></span>

- [<span data-ttu-id="53495-138">Схема файла конфигурации для .NET Framework</span><span class="sxs-lookup"><span data-stu-id="53495-138">Configuration file schema for the .NET Framework</span></span>](../index.md)
