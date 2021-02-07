---
description: 'Дополнительные сведения <add> о: <serviceActivations>'
title: <add> из <serviceActivations>
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: 53c89321c8cde1966a04870c62fa0777610ff547
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750147"
---
# <a name="add-of-serviceactivations"></a><span data-ttu-id="65ad7-103">\<add> из \<serviceActivations></span><span class="sxs-lookup"><span data-stu-id="65ad7-103">\<add> of \<serviceActivations></span></span>

<span data-ttu-id="65ad7-104">Элемент конфигурации, позволяющий определить параметры активации виртуальной службы, которые сопоставляются с типами служб Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="65ad7-104">A configuration element that allows you to define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="65ad7-105">Это позволяет активировать службы, расположенные в WAS/IIS, без SVC-файла.</span><span class="sxs-lookup"><span data-stu-id="65ad7-105">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceActivations>**](serviceactivations.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  

## <a name="syntax"></a><span data-ttu-id="65ad7-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="65ad7-106">Syntax</span></span>

```xml
<serviceHostingEnvironment>
    <serviceActivations>
      <add factory="String"
           service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="65ad7-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="65ad7-107">Attributes and Elements</span></span>

<span data-ttu-id="65ad7-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="65ad7-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="65ad7-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="65ad7-109">Attributes</span></span>

|<span data-ttu-id="65ad7-110">Атрибут</span><span class="sxs-lookup"><span data-stu-id="65ad7-110">Attribute</span></span>|<span data-ttu-id="65ad7-111">Описание</span><span class="sxs-lookup"><span data-stu-id="65ad7-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="65ad7-112">фабрика</span><span class="sxs-lookup"><span data-stu-id="65ad7-112">factory</span></span>|<span data-ttu-id="65ad7-113">Строка, задающая имя типа CLR фабрики, которая формирует элемент активации службы.</span><span class="sxs-lookup"><span data-stu-id="65ad7-113">A string that specifies the CLR type name of the factory that generates a service activation element.</span></span>|
|<span data-ttu-id="65ad7-114">service</span><span class="sxs-lookup"><span data-stu-id="65ad7-114">service</span></span>|<span data-ttu-id="65ad7-115">ServiceType, реализующий службу (либо полное, либо короткое имя типа) (когда оно размещено в папке App_Code).</span><span class="sxs-lookup"><span data-stu-id="65ad7-115">The ServiceType that implements the service (either the full qualified Typename or the short Typename (when it is placed in the App_Code folder).</span></span>|
|<span data-ttu-id="65ad7-116">relativeAddress</span><span class="sxs-lookup"><span data-stu-id="65ad7-116">relativeAddress</span></span>|<span data-ttu-id="65ad7-117">Относительный адрес в текущем приложении IIS (например, «Service.svc»).</span><span class="sxs-lookup"><span data-stu-id="65ad7-117">The relative address within the current IIS application - for example "Service.svc".</span></span> <span data-ttu-id="65ad7-118">В WCF 4,0 этот относительный адрес должен содержать одно из известных расширений файлов (. svc,. xamlx,...). Для Релативеурл не существует физического файла.</span><span class="sxs-lookup"><span data-stu-id="65ad7-118">In WCF 4.0 this relative address has to contain one of the known file extensions (.svc, .xamlx, ...). No physical file has to exist for the relativeUrl</span></span>|

### <a name="child-elements"></a><span data-ttu-id="65ad7-119">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="65ad7-119">Child Elements</span></span>

<span data-ttu-id="65ad7-120">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="65ad7-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="65ad7-121">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="65ad7-121">Parent Elements</span></span>

|<span data-ttu-id="65ad7-122">Элемент</span><span class="sxs-lookup"><span data-stu-id="65ad7-122">Element</span></span>|<span data-ttu-id="65ad7-123">Описание</span><span class="sxs-lookup"><span data-stu-id="65ad7-123">Description</span></span>|
|-------------|-----------------|
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="65ad7-124">Раздел конфигурации, в котором описываются параметры активации.</span><span class="sxs-lookup"><span data-stu-id="65ad7-124">A configuration section that describes activation settings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="65ad7-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="65ad7-125">Remarks</span></span>

<span data-ttu-id="65ad7-126">В следующем примере показано, как настроить параметры активации в файле web.config.</span><span class="sxs-lookup"><span data-stu-id="65ad7-126">The following example shows how to configure activation settings within your web.config file.</span></span>

```xml
<configuration>
  <system.serviceModel>
    <serviceHostingEnvironment>
      <serviceActivations>
        <add service="GreetingService" />
      </serviceActivations>
    </serviceHostingEnvironment>
  </system.serviceModel>
</configuration>
```

<span data-ttu-id="65ad7-127">Использование этой конфигурации позволяет активировать GreetingService без SVC-файла.</span><span class="sxs-lookup"><span data-stu-id="65ad7-127">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="65ad7-128">Следует отметить, что `<serviceHostingEnvironment>` является конфигурацией на уровне приложения.</span><span class="sxs-lookup"><span data-stu-id="65ad7-128">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="65ad7-129">Необходимо разместить файл `web.config`, содержащий конфигурацию в корневом каталоге виртуального приложения.</span><span class="sxs-lookup"><span data-stu-id="65ad7-129">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="65ad7-130">Кроме того, `serviceHostingEnvironment` является machineToApplication наследуемым разделом.</span><span class="sxs-lookup"><span data-stu-id="65ad7-130">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="65ad7-131">Если зарегистрировать одну службу в корневом каталоге компьютера, каждая служба в приложении унаследует эту службу.</span><span class="sxs-lookup"><span data-stu-id="65ad7-131">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="65ad7-132">Активация на основе конфигурации поддерживает активацию как по протоколу HTTP, так и по протоколу, отличному от HTTP.</span><span class="sxs-lookup"><span data-stu-id="65ad7-132">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="65ad7-133">Для этого требуются расширения в Релативеаддресс, например. svc,. XOML или. xamlx.</span><span class="sxs-lookup"><span data-stu-id="65ad7-133">It requires extensions in the relativeAddress, i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="65ad7-134">Можно сопоставить пользовательские расширения с известными поставщиками buildProvider, что впоследствии позволит активировать службу через любое расширение.</span><span class="sxs-lookup"><span data-stu-id="65ad7-134">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="65ad7-135">При возникновении конфликта раздел `<serviceActivations>` переопределяет записи в SVC-файле.</span><span class="sxs-lookup"><span data-stu-id="65ad7-135">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="65ad7-136">См. также</span><span class="sxs-lookup"><span data-stu-id="65ad7-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
