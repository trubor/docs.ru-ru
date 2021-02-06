---
description: 'Дополнительные сведения: схема параметров приложения'
title: Схема параметров приложения
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: 24c5771e9d98d07bbdc8dab5fce0f1535bc9b582
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652904"
---
# <a name="application-settings-schema"></a><span data-ttu-id="eb355-103">Схема параметров приложения</span><span class="sxs-lookup"><span data-stu-id="eb355-103">Application Settings schema</span></span>

<span data-ttu-id="eb355-104">Параметры приложения позволяют Windows Forms или ASP.NET приложению сохранять и извлекать параметры приложения и области пользователя.</span><span class="sxs-lookup"><span data-stu-id="eb355-104">Application settings allow a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span> <span data-ttu-id="eb355-105">В этом контексте *параметр* — это любой фрагмент информации, который может быть специфичен для приложения или зависит от текущего пользователя — от строки подключения к базе данных до предпочитаемого пользователем размера окна по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="eb355-105">In this context, a *setting* is any piece of information that may be specific to the application or specific to the current user — anything from a database connection string to the user's preferred default window size.</span></span>

<span data-ttu-id="eb355-106">По умолчанию параметры приложения в Windows Formsном приложении используют <xref:System.Configuration.LocalFileSettingsProvider> класс, который использует систему конфигурации .NET для хранения параметров в XML-файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="eb355-106">By default, application settings in a Windows Forms application uses the <xref:System.Configuration.LocalFileSettingsProvider> class, which uses the .NET configuration system to store settings in an XML configuration file.</span></span> <span data-ttu-id="eb355-107">Дополнительные сведения о файлах, используемых параметрами приложения, см. в разделе [архитектура параметров приложения](/dotnet/desktop/winforms/advanced/application-settings-architecture).</span><span class="sxs-lookup"><span data-stu-id="eb355-107">For more information about the files used by application settings, see [Application Settings Architecture](/dotnet/desktop/winforms/advanced/application-settings-architecture).</span></span>

<span data-ttu-id="eb355-108">Параметры приложения определяют следующие элементы в составе файлов конфигурации, которые он использует.</span><span class="sxs-lookup"><span data-stu-id="eb355-108">Application settings defines the following elements as part of the configuration files it uses.</span></span>

| <span data-ttu-id="eb355-109">Элемент</span><span class="sxs-lookup"><span data-stu-id="eb355-109">Element</span></span>                    | <span data-ttu-id="eb355-110">Описание</span><span class="sxs-lookup"><span data-stu-id="eb355-110">Description</span></span>                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationSettings>** | <span data-ttu-id="eb355-111">Содержит все **\<setting>** теги, характерные для приложения.</span><span class="sxs-lookup"><span data-stu-id="eb355-111">Contains all **\<setting>** tags specific to the application.</span></span>                         |
| **\<userSettings>**        | <span data-ttu-id="eb355-112">Содержит все **\<setting>** теги, относящиеся к текущему пользователю.</span><span class="sxs-lookup"><span data-stu-id="eb355-112">Contains all **\<setting>** tags specific to the current user.</span></span>                        |
| **\<setting>**             | <span data-ttu-id="eb355-113">Определяет параметр.</span><span class="sxs-lookup"><span data-stu-id="eb355-113">Defines a setting.</span></span> <span data-ttu-id="eb355-114">Дочерний элемент либо **\<applicationSettings>** или **\<userSettings>** .</span><span class="sxs-lookup"><span data-stu-id="eb355-114">Child of either **\<applicationSettings>** or **\<userSettings>**.</span></span> |
| **\<value>**               | <span data-ttu-id="eb355-115">Определяет значение параметра.</span><span class="sxs-lookup"><span data-stu-id="eb355-115">Defines a setting's value.</span></span> <span data-ttu-id="eb355-116">Дочерний элемент **\<setting>** .</span><span class="sxs-lookup"><span data-stu-id="eb355-116">Child of **\<setting>**.</span></span>                                   |

## <a name="applicationsettings-element"></a><span data-ttu-id="eb355-117">Элемент \<applicationSettings></span><span class="sxs-lookup"><span data-stu-id="eb355-117">\<applicationSettings> element</span></span>

<span data-ttu-id="eb355-118">Этот элемент содержит все **\<setting>** теги, характерные для экземпляра приложения на клиентском компьютере.</span><span class="sxs-lookup"><span data-stu-id="eb355-118">This element contains all **\<setting>** tags that are specific to an instance of the application on a client computer.</span></span> <span data-ttu-id="eb355-119">Атрибуты не определяются.</span><span class="sxs-lookup"><span data-stu-id="eb355-119">It defines no attributes.</span></span>

## <a name="usersettings-element"></a><span data-ttu-id="eb355-120">Элемент \<userSettings></span><span class="sxs-lookup"><span data-stu-id="eb355-120">\<userSettings> element</span></span>

<span data-ttu-id="eb355-121">Этот элемент содержит все **\<setting>** теги, характерные для пользователя, который в настоящее время использует приложение.</span><span class="sxs-lookup"><span data-stu-id="eb355-121">This element contains all **\<setting>** tags that are specific to the user who is currently using the application.</span></span> <span data-ttu-id="eb355-122">Атрибуты не определяются.</span><span class="sxs-lookup"><span data-stu-id="eb355-122">It defines no attributes.</span></span>

## <a name="setting-element"></a><span data-ttu-id="eb355-123">Элемент \<setting></span><span class="sxs-lookup"><span data-stu-id="eb355-123">\<setting> element</span></span>

<span data-ttu-id="eb355-124">Этот элемент определяет параметр.</span><span class="sxs-lookup"><span data-stu-id="eb355-124">This element defines a setting.</span></span> <span data-ttu-id="eb355-125">Он имеет следующие атрибуты.</span><span class="sxs-lookup"><span data-stu-id="eb355-125">It has the following attributes.</span></span>

| <span data-ttu-id="eb355-126">attribute</span><span class="sxs-lookup"><span data-stu-id="eb355-126">Attribute</span></span>        | <span data-ttu-id="eb355-127">Описание</span><span class="sxs-lookup"><span data-stu-id="eb355-127">Description</span></span> |
| ---------------- | ----------- |
| <span data-ttu-id="eb355-128">**name**</span><span class="sxs-lookup"><span data-stu-id="eb355-128">**name**</span></span>         | <span data-ttu-id="eb355-129">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="eb355-129">Required.</span></span> <span data-ttu-id="eb355-130">Уникальный идентификатор параметра.</span><span class="sxs-lookup"><span data-stu-id="eb355-130">The unique ID of the setting.</span></span> <span data-ttu-id="eb355-131">Параметры, созданные в Visual Studio, сохраняются с именем `ProjectName.Properties.Settings` .</span><span class="sxs-lookup"><span data-stu-id="eb355-131">Settings created through Visual Studio are saved with the name `ProjectName.Properties.Settings`.</span></span> |
| <span data-ttu-id="eb355-132">**serializeAs**</span><span class="sxs-lookup"><span data-stu-id="eb355-132">**serializeAs**</span></span> | <span data-ttu-id="eb355-133">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="eb355-133">Required.</span></span> <span data-ttu-id="eb355-134">Формат, используемый для сериализации значения в текст.</span><span class="sxs-lookup"><span data-stu-id="eb355-134">The format to use for serializing the value to text.</span></span> <span data-ttu-id="eb355-135">Допустимые значения:</span><span class="sxs-lookup"><span data-stu-id="eb355-135">Valid values are:</span></span><br><br><span data-ttu-id="eb355-136">- `string`.</span><span class="sxs-lookup"><span data-stu-id="eb355-136">- `string`.</span></span> <span data-ttu-id="eb355-137">Значение сериализуется в виде строки с помощью <xref:System.ComponentModel.TypeConverter> .</span><span class="sxs-lookup"><span data-stu-id="eb355-137">The value is serialized as a string using a <xref:System.ComponentModel.TypeConverter>.</span></span><br><span data-ttu-id="eb355-138">- `xml`.</span><span class="sxs-lookup"><span data-stu-id="eb355-138">- `xml`.</span></span> <span data-ttu-id="eb355-139">Значение сериализуется с помощью сериализации XML.</span><span class="sxs-lookup"><span data-stu-id="eb355-139">The value is serialized using XML serialization.</span></span><br><span data-ttu-id="eb355-140">- `binary`.</span><span class="sxs-lookup"><span data-stu-id="eb355-140">- `binary`.</span></span> <span data-ttu-id="eb355-141">Значение сериализуется как двоичный файл, закодированный в виде текста, с помощью двоичной сериализации.</span><span class="sxs-lookup"><span data-stu-id="eb355-141">The value is serialized as text-encoded binary using binary serialization.</span></span><br /><span data-ttu-id="eb355-142">- `custom`.</span><span class="sxs-lookup"><span data-stu-id="eb355-142">- `custom`.</span></span> <span data-ttu-id="eb355-143">Поставщик параметров обладает знаниями об этом параметре и сериализует и десериализует его.</span><span class="sxs-lookup"><span data-stu-id="eb355-143">The settings provider has inherent knowledge of this setting and serializes and de-serializes it.</span></span> |

## <a name="value-element"></a><span data-ttu-id="eb355-144">Элемент \<value></span><span class="sxs-lookup"><span data-stu-id="eb355-144">\<value> element</span></span>

<span data-ttu-id="eb355-145">Этот элемент содержит значение параметра.</span><span class="sxs-lookup"><span data-stu-id="eb355-145">This element contains the value of a setting.</span></span>

## <a name="example"></a><span data-ttu-id="eb355-146">Пример</span><span class="sxs-lookup"><span data-stu-id="eb355-146">Example</span></span>

<span data-ttu-id="eb355-147">В следующем примере показан файл параметров приложения, который определяет два параметра области приложения и два параметра уровня пользователя:</span><span class="sxs-lookup"><span data-stu-id="eb355-147">The following example shows an application settings file that defines two application-scoped settings and two user-scoped settings:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
    </sectionGroup>
    <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />
    </sectionGroup>
  </configSections>
  <applicationSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="Cursor" serializeAs="String">
        <value>Default</value>
      </setting>
      <setting name="DoubleBuffering" serializeAs="String">
        <value>False</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </applicationSettings>
  <userSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="FormTitle" serializeAs="String">
        <value>Form1</value>
      </setting>
      <setting name="FormSize" serializeAs="String">
        <value>595, 536</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </userSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="eb355-148">См. также</span><span class="sxs-lookup"><span data-stu-id="eb355-148">See also</span></span>

- [<span data-ttu-id="eb355-149">Общие сведения о параметрах приложений</span><span class="sxs-lookup"><span data-stu-id="eb355-149">Application Settings Overview</span></span>](/dotnet/desktop/winforms/advanced/application-settings-overview)
- [<span data-ttu-id="eb355-150">Архитектура параметров приложения</span><span class="sxs-lookup"><span data-stu-id="eb355-150">Application Settings Architecture</span></span>](/dotnet/desktop/winforms/advanced/application-settings-architecture)
