---
description: 'Дополнительные сведения о: Configuration-Based активации в IIS и WAS'
title: Активация на основе конфигурации в IIS и WAS
ms.date: 03/30/2017
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
ms.openlocfilehash: 7515e3f0d3035e1ab93c67980bd00eeb0a063d17
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743373"
---
# <a name="configuration-based-activation-in-iis-and-was"></a><span data-ttu-id="59d6d-103">Активация на основе конфигурации в IIS и WAS</span><span class="sxs-lookup"><span data-stu-id="59d6d-103">Configuration-Based Activation in IIS and WAS</span></span>

<span data-ttu-id="59d6d-104">Обычно при размещении службы Windows Communication Foundation (WCF) в службы IIS (IIS) или службе активации Windows (WAS) необходимо предоставить SVC-файл.</span><span class="sxs-lookup"><span data-stu-id="59d6d-104">Normally when hosting a Windows Communication Foundation (WCF) service under Internet Information Services (IIS) or Windows Process Activation Service (WAS), you must provide a .svc file.</span></span> <span data-ttu-id="59d6d-105">SVC-файл содержит имя службы, а также дополнительную пользовательскую фабрику узла службы.</span><span class="sxs-lookup"><span data-stu-id="59d6d-105">The .svc file contains the name of the service and an optional custom service host factory.</span></span> <span data-ttu-id="59d6d-106">С помощью этого дополнительного файла добавляются служебные данные по управлению.</span><span class="sxs-lookup"><span data-stu-id="59d6d-106">This additional file adds manageability overhead.</span></span> <span data-ttu-id="59d6d-107">Возможность активации на основе конфигурации снимает требование по наличию SVC-файла и, следовательно, по наличию связанных служебных данных.</span><span class="sxs-lookup"><span data-stu-id="59d6d-107">The configuration-based activation feature removes the requirement to have a .svc file and therefore the associated overhead.</span></span>

## <a name="configuration-based-activation"></a><span data-ttu-id="59d6d-108">Активация на основе конфигурации</span><span class="sxs-lookup"><span data-stu-id="59d6d-108">Configuration-Based Activation</span></span>

<span data-ttu-id="59d6d-109">Активация на основе конфигурации принимает метаданные, которые используются для размещения в SVC-файле, и помещает их в файл Web.config.</span><span class="sxs-lookup"><span data-stu-id="59d6d-109">Configuration-based activation takes the metadata that used to be placed in the .svc file and places it in the Web.config file.</span></span> <span data-ttu-id="59d6d-110">В `serviceHostingEnvironment` элементе><имеется `serviceActivations` элемент <>.</span><span class="sxs-lookup"><span data-stu-id="59d6d-110">Within the<`serviceHostingEnvironment`> element there is a <`serviceActivations`> element.</span></span> <span data-ttu-id="59d6d-111">В элементе <`serviceActivations`> — один или несколько элементов <`add`>, по одному для каждой размещенной службы.</span><span class="sxs-lookup"><span data-stu-id="59d6d-111">Within the <`serviceActivations`> element are one or more <`add`> elements, one for each hosted service.</span></span> <span data-ttu-id="59d6d-112">`add`Элемент> <содержит атрибуты, позволяющие задать относительный адрес для службы, а также тип службы или фабрику узла службы.</span><span class="sxs-lookup"><span data-stu-id="59d6d-112">The <`add`> element contains attributes that let you set the relative address for the service and the service type or a service host factory.</span></span> <span data-ttu-id="59d6d-113">В следующем примере конфигурации показано, каким образом используется этот раздел.</span><span class="sxs-lookup"><span data-stu-id="59d6d-113">The following configuration example code shows how this section is used.</span></span>

> [!NOTE]
> <span data-ttu-id="59d6d-114">Каждый `add` элемент> <должен указывать атрибут Service или Factory.</span><span class="sxs-lookup"><span data-stu-id="59d6d-114">Each <`add`> element must specify a service or a factory attribute.</span></span> <span data-ttu-id="59d6d-115">Можно указать и атрибут службы, и атрибут фабрики.</span><span class="sxs-lookup"><span data-stu-id="59d6d-115">Specifying both service and factory attributes is allowed.</span></span>

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>
  </serviceActivations>
</serviceHostingEnvironment>
```

 <span data-ttu-id="59d6d-116">Такой код, показанный в файле Web.config, позволяет поместить исходный код службы в каталог App_Code приложения или откомпилированную сборку в каталог Bin приложения.</span><span class="sxs-lookup"><span data-stu-id="59d6d-116">With this in the Web.config file, you can place the service source code in the App_Code directory of the application or a complied assembly in the Bin directory of the application.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="59d6d-117">При использовании активации на основе конфигурации, встроенный программный код в SVC-файлах не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="59d6d-117">When using configuration-based activation, inline code in .svc files is not supported.</span></span>
> - <span data-ttu-id="59d6d-118">`relativeAddress`Для атрибута необходимо задать относительный адрес, например " \<sub-directory> /сервице.СВК" или "~/ \< суб-директори/Service. svc".</span><span class="sxs-lookup"><span data-stu-id="59d6d-118">The `relativeAddress` attribute must be set to a relative address such as "\<sub-directory>/service.svc" or "~/\<sub-directory/service.svc".</span></span>
> - <span data-ttu-id="59d6d-119">Если зарегистрирован относительный адрес, который не содержит известного расширения имени, связанного с WCF, то будет создано исключение конфигурации.</span><span class="sxs-lookup"><span data-stu-id="59d6d-119">A configuration exception is thrown if you register a relative address that does not have a known extension associated with WCF.</span></span>
> - <span data-ttu-id="59d6d-120">Относительный адрес указывается относительно корневого каталога виртуального приложения.</span><span class="sxs-lookup"><span data-stu-id="59d6d-120">The relative address specified is relative to the root of the virtual application.</span></span>
> - <span data-ttu-id="59d6d-121">Поскольку модель конфигурации имеет иерархическую структуру, относительный адрес, который зарегистрирован на уровне компьютера и узла, наследуется виртуальными приложениями.</span><span class="sxs-lookup"><span data-stu-id="59d6d-121">Due to the hierarchical model of configuration, the registered relative addresses at machine and site level are inherited by virtual applications.</span></span>
> - <span data-ttu-id="59d6d-122">Регистрация в файле конфигурации имеет более высокий приоритет, чем параметры в SVC-файле, XAMLX-файле, XOML-файле и других файлах.</span><span class="sxs-lookup"><span data-stu-id="59d6d-122">Registrations in a configuration file take precedence over settings in a .svc, .xamlx, .xoml, or other file.</span></span>
> - <span data-ttu-id="59d6d-123">Все символы обратной косой черты «\» в URI, отправляемых в IIS/WAS, автоматически преобразуются в символы косой черты «/».</span><span class="sxs-lookup"><span data-stu-id="59d6d-123">Any ‘\’ (backslashes) in a URI sent to IIS/WAS are automatically converted to a ‘/’ (forward slash).</span></span> <span data-ttu-id="59d6d-124">Если добавляемый относительный адрес содержит символ «\», а в IIS отправлен URI, который использует относительный адрес, то символ обратной косой черты преобразуется в символ косой черты и IIS не может сопоставить его с относительным адресом.</span><span class="sxs-lookup"><span data-stu-id="59d6d-124">If a relative address is added that contains a ‘\’ and you send IIS a URI that uses the relative address, the backslash is converted to a forward slash and IIS cannot match it to the relative address.</span></span> <span data-ttu-id="59d6d-125">Службы IIS отправляют сведения трассировки, которые указывают, что соответствие не найдено.</span><span class="sxs-lookup"><span data-stu-id="59d6d-125">IIS sends out trace information that indicates that there are no matches found.</span></span>

## <a name="see-also"></a><span data-ttu-id="59d6d-126">См. также</span><span class="sxs-lookup"><span data-stu-id="59d6d-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>
- [<span data-ttu-id="59d6d-127">Размещение служб</span><span class="sxs-lookup"><span data-stu-id="59d6d-127">Hosting Services</span></span>](../hosting-services.md)
- [<span data-ttu-id="59d6d-128">Общие сведения о размещении служб рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="59d6d-128">Hosting Workflow Services Overview</span></span>](hosting-workflow-services-overview.md)
- [\<serviceHostingEnvironment>](../../configure-apps/file-schema/wcf/servicehostingenvironment.md)
- <span data-ttu-id="59d6d-129">[Функции размещения Windows Server App Fabric](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="59d6d-129">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
