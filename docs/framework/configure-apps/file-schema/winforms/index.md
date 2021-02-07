---
description: Дополнительные сведения о Windows Forms разделе "Настройка"
title: Раздел конфигурации Windows Forms
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
ms.openlocfilehash: f1eaf2d74c7645d6cf4580d75e23d8910628cce0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697768"
---
# <a name="windows-forms-configuration-section"></a><span data-ttu-id="b510e-103">Раздел конфигурации Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b510e-103">Windows Forms Configuration Section</span></span>

<span data-ttu-id="b510e-104">Параметры конфигурации Windows Forms позволяют приложению Windows Forms хранить и извлекать сведения о настроенных параметрах приложения, таких как поддержка нескольких мониторов, поддержка высокого разрешения (DPI) и другие предопределенные параметры конфигурации.</span><span class="sxs-lookup"><span data-stu-id="b510e-104">Windows Forms configuration settings allow a Windows Forms app to store and retrieve information about customized application settings such as multi-monitor support, high DPI support, and other predefined configuration settings.</span></span>

<span data-ttu-id="b510e-105">Параметры конфигурации приложения Windows Forms хранятся в элементе `System.Windows.Forms.ApplicationConfigurationSection` файла конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="b510e-105">Windows Forms application configuration settings are stored in an application configuration file's `System.Windows.Forms.ApplicationConfigurationSection` element.</span></span>

## <a name="syntax"></a><span data-ttu-id="b510e-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b510e-106">Syntax</span></span>

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b510e-107">Элементы и атрибуты</span><span class="sxs-lookup"><span data-stu-id="b510e-107">Attributes and elements</span></span>

<span data-ttu-id="b510e-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="b510e-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b510e-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="b510e-109">Attributes</span></span>

<span data-ttu-id="b510e-110">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="b510e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b510e-111">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="b510e-111">Child elements</span></span>

<span data-ttu-id="b510e-112">Элемент</span><span class="sxs-lookup"><span data-stu-id="b510e-112">Element</span></span>  |<span data-ttu-id="b510e-113">Описание</span><span class="sxs-lookup"><span data-stu-id="b510e-113">Description</span></span> |
---------|---------|
[`<add>`](windows-forms-add-configuration-element.md) | <span data-ttu-id="b510e-114">Добавляет ключ параметра конфигурации с указанным значением.</span><span class="sxs-lookup"><span data-stu-id="b510e-114">Adds a configuration setting key with a specified value</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="b510e-115">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="b510e-115">Parent elements</span></span>

<span data-ttu-id="b510e-116">Элемент</span><span class="sxs-lookup"><span data-stu-id="b510e-116">Element</span></span>  |<span data-ttu-id="b510e-117">Описание</span><span class="sxs-lookup"><span data-stu-id="b510e-117">Description</span></span> |
---------|---------|
[\<configuration>](../configuration-element.md) | <span data-ttu-id="b510e-118">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b510e-118">The root element in every configuration file used by the common language runtime and Windows Forms applications</span></span> |

## <a name="remarks"></a><span data-ttu-id="b510e-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="b510e-119">Remarks</span></span>

<span data-ttu-id="b510e-120">Начиная с версии .NET Framework 4.7 элемент `<System.Windows.Forms.ApplicationConfigurationSection>` позволяет настраивать в приложениях Windows Forms функции, добавленные в последних выпусках .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b510e-120">Starting with the .NET Framework 4.7, the `<System.Windows.Forms.ApplicationConfigurationSection>` element allows you to configure Windows Forms applications to take advantage of features added in recent releases of the .NET Framework.</span></span>

<span data-ttu-id="b510e-121">`<System.Windows.Forms.ApplicationConfigurationSection>`Элемент может включать один или несколько дочерних [`<add>`](windows-forms-add-configuration-element.md) элементов, каждый из которых определяет конкретный параметр конфигурации.</span><span class="sxs-lookup"><span data-stu-id="b510e-121">The `<System.Windows.Forms.ApplicationConfigurationSection>` element can include one or more child [`<add>`](windows-forms-add-configuration-element.md) elements, each of which defines a specific configuration setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="b510e-122">См. также</span><span class="sxs-lookup"><span data-stu-id="b510e-122">See also</span></span>

- [<span data-ttu-id="b510e-123">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="b510e-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b510e-124">Поддержка высокого DPI в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b510e-124">High DPI Support in Windows Forms</span></span>](/dotnet/desktop/winforms/high-dpi-support-in-windows-forms)
