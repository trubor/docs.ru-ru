---
description: Дополнительные сведения см. в статье Использование инструментарий управления Windows (WMI) для диагностики.
title: Использование Windows Management Instrumentation для диагностики
ms.date: 03/30/2017
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
ms.openlocfilehash: 2c3d79133b24c180f69d8ad015c1b08d9a9d188f
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494822"
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a><span data-ttu-id="2d7e4-103">Использование Windows Management Instrumentation для диагностики</span><span class="sxs-lookup"><span data-stu-id="2d7e4-103">Using Windows Management Instrumentation for Diagnostics</span></span>

<span data-ttu-id="2d7e4-104">Windows Communication Foundation (WCF) предоставляет данные проверки службы во время выполнения через поставщик WCF инструментарий управления Windows (WMI) (WMI).</span><span class="sxs-lookup"><span data-stu-id="2d7e4-104">Windows Communication Foundation (WCF) exposes inspection data of a service at runtime through a WCF Windows Management Instrumentation (WMI) provider.</span></span>  
  
## <a name="enabling-wmi"></a><span data-ttu-id="2d7e4-105">Реализация WMI</span><span class="sxs-lookup"><span data-stu-id="2d7e4-105">Enabling WMI</span></span>  

 <span data-ttu-id="2d7e4-106">Инструментарий WMI - это реализованный корпорацией Майкрософт стандарт управления предприятием через Интернет (WBEM).</span><span class="sxs-lookup"><span data-stu-id="2d7e4-106">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="2d7e4-107">Дополнительные сведения о пакете SDK для инструментария WMI см. в разделе [инструментарий управления Windows (WMI)](/windows/desktop/WmiSdk/wmi-start-page).</span><span class="sxs-lookup"><span data-stu-id="2d7e4-107">For more information about the WMI SDK, see [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span></span> <span data-ttu-id="2d7e4-108">WBEM является отраслевым стандартом предоставления приложениями инструментария управления для внешних средств управления.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-108">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="2d7e4-109">Поставщик инструментария WMI - это компонент, предоставляющий инструментарий в среде выполнения с помощью совместимого с WBEM интерфейса.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-109">A WMI provider is a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="2d7e4-110">Он состоит из набора объектов инструментария WMI, имеющих пары атрибут/значение.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-110">It consists of a set of WMI objects that have attribute/value pairs.</span></span> <span data-ttu-id="2d7e4-111">Пары могут быть нескольких простых типов.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-111">Pairs can be of a number of simple types.</span></span> <span data-ttu-id="2d7e4-112">Средства управления могут подключаться к службам через интерфейс во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-112">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="2d7e4-113">WCF предоставляет атрибуты служб, такие как адреса, привязки, поведения и прослушиватели.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-113">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="2d7e4-114">Встроенный поставщик инструментария WMI может быть активирован в файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-114">The built-in WMI provider can be activated in the configuration file of the application.</span></span> <span data-ttu-id="2d7e4-115">Это делается с помощью `wmiProviderEnabled` атрибута [\<diagnostics>](../../../configure-apps/file-schema/wcf/diagnostics.md) в [\<system.serviceModel>](../../../configure-apps/file-schema/wcf/system-servicemodel.md) разделе, как показано в следующем образце конфигурации.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-115">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration.</span></span>  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 <span data-ttu-id="2d7e4-116">Эта запись конфигурации предоставляет интерфейс инструментария WMI.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-116">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="2d7e4-117">Теперь приложения управления могут подключаться через этот интерфейс и обращаться к инструментарию управления приложения.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-117">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="accessing-wmi-data"></a><span data-ttu-id="2d7e4-118">Доступ к данным WMI</span><span class="sxs-lookup"><span data-stu-id="2d7e4-118">Accessing WMI Data</span></span>  

 <span data-ttu-id="2d7e4-119">Доступ к данным инструментария WMI может осуществляться несколькими различными способами.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-119">WMI data can be accessed in many different ways.</span></span> <span data-ttu-id="2d7e4-120">Корпорация Майкрософт предоставляет API-интерфейсы WMI для сценариев, Visual Basic приложений, приложений C++ и платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-120">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the .NET Framework.</span></span> <span data-ttu-id="2d7e4-121">Дополнительные сведения см. [в разделе Использование WMI](/windows/win32/wmisdk/using-wmi).</span><span class="sxs-lookup"><span data-stu-id="2d7e4-121">For more information, see [Using WMI](/windows/win32/wmisdk/using-wmi).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="2d7e4-122">При использовании предоставляемых .NET Framework методов для программного доступа к данным WMI следует помнить о том, что при установке подключения эти методы могут вызывать исключения.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-122">If you use the .NET Framework provided methods to programmatically access WMI data, you should be aware that such methods may throw exceptions when the connection is established.</span></span> <span data-ttu-id="2d7e4-123">Подключение устанавливается не во время создания экземпляра <xref:System.Management.ManagementObject>, а при получении первого запроса, при котором происходит реальный обмен данными.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-123">The connection is not established during the construction of the <xref:System.Management.ManagementObject> instance, but on the first request involving actual data exchange.</span></span> <span data-ttu-id="2d7e4-124">Следовательно, следует использовать блок `try..catch` для перехвата возможных исключений.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-124">Therefore, you should use a `try..catch` block to catch the possible exceptions.</span></span>  
  
 <span data-ttu-id="2d7e4-125">Можно изменить уровень ведения журнала сообщений и трассировок, а также параметры журнала сообщений для источника трассировки `System.ServiceModel` в инструментарии WMI.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-125">You can change the trace and message logging level, as well as message logging options for the `System.ServiceModel` trace source in WMI.</span></span> <span data-ttu-id="2d7e4-126">Это можно сделать, обратившись к экземпляру [аппдомаининфо](appdomaininfo.md) , который предоставляет эти логические свойства: `LogMessagesAtServiceLevel` , `LogMessagesAtTransportLevel` , `LogMalformedMessages` и `TraceLevel` .</span><span class="sxs-lookup"><span data-stu-id="2d7e4-126">This can be done by accessing the [AppDomainInfo](appdomaininfo.md) instance, which exposes these Boolean properties: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`, and `TraceLevel`.</span></span> <span data-ttu-id="2d7e4-127">Поэтому, если в файле конфигурации прослушиватель трассировки настроен на ведение журнала, но эти параметры имеют значение `false`, можно впоследствии изменить их значения на `true`, когда приложение будет выполняться.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-127">Therefore, if you configure a trace listener for message logging, but set these options to `false` in configuration, you can later change them to `true` when the application is running.</span></span> <span data-ttu-id="2d7e4-128">В результате ведение журнала будет включено во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-128">This will effectively enable message logging at runtime.</span></span> <span data-ttu-id="2d7e4-129">Аналогично, если ведение журнала было включено в файле конфигурации, его можно отключить во время выполнения с помощью инструментария WMI.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-129">Similarly, if you enable message logging in your configuration file, you can disable it at runtime using WMI.</span></span>  
  
 <span data-ttu-id="2d7e4-130">Необходимо помнить, что если прослушиватели трассировок журнала сообщений для журнала сообщений или прослушиватели трассировок `System.ServiceModel` для трассировок не заданы в файле конфигурации, ни одно из изменений не будет применено, даже если эти изменения принимаются инструментарием WMI.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-130">You should be aware that if no message logging trace listeners for message logging, or no `System.ServiceModel` trace listeners for tracing are specified in the configuration file, none of your changes are taken into effect, even though the changes are accepted by WMI.</span></span> <span data-ttu-id="2d7e4-131">Дополнительные сведения о правильной настройке соответствующих прослушивателей см. в разделе [Настройка ведения журнала сообщений](../configuring-message-logging.md) и [Настройка трассировки](../tracing/configuring-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="2d7e4-131">For more information on properly setting up the respective listeners, see [Configuring Message Logging](../configuring-message-logging.md) and [Configuring Tracing](../tracing/configuring-tracing.md).</span></span> <span data-ttu-id="2d7e4-132">Уровень трассировки всех остальных источников трассировки, заданных конфигурацией, действителен только при запуске приложения и не может быть изменен.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-132">The trace level of all other trace sources specified by configuration is effective when the application starts, and cannot be changed.</span></span>  
  
 <span data-ttu-id="2d7e4-133">WCF предоставляет `GetOperationCounterInstanceName` метод для создания скриптов.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-133">WCF exposes a `GetOperationCounterInstanceName` method for scripting.</span></span> <span data-ttu-id="2d7e4-134">Если передать этому методу имя операции, он возвращает имя экземпляра счетчика производительности.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-134">This method returns a performance counter instance name if you provide it with an operation name.</span></span> <span data-ttu-id="2d7e4-135">Однако он не проверяет входные данные.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-135">However, it does not validate your input.</span></span> <span data-ttu-id="2d7e4-136">Таким образом, если передать ему неправильное имя операции, возвращается неверное имя счетчика.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-136">Therefore, if you provide an incorrect operation name, an incorrect counter name is returned.</span></span>  
  
 <span data-ttu-id="2d7e4-137">`OutgoingChannel`Свойство `Service` экземпляра не учитывает каналы, открытые службой для подключения к другой службе, если клиент WCF для целевой службы не создан в `Service` методе.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-137">The `OutgoingChannel` property of the `Service` instance does not count channels opened by a service to connect to another service, if the WCF client to the destination service is not created within the `Service` method.</span></span>  
  
 <span data-ttu-id="2d7e4-138">**Внимание!** WMI поддерживает только <xref:System.TimeSpan> значение до 3 десятичных разделителей.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-138">**Caution** WMI only supports a <xref:System.TimeSpan> value up to 3 decimal points.</span></span> <span data-ttu-id="2d7e4-139">Например, если одному из свойств служба присваивает значение <xref:System.TimeSpan.MaxValue>, при просмотре через WMI это значение усекается до 3 знаков после десятичного разделителя.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-139">For example, if your service sets one of its properties to <xref:System.TimeSpan.MaxValue>, its value is truncated after 3 decimal points when viewed through WMI.</span></span>  
  
## <a name="security"></a><span data-ttu-id="2d7e4-140">Безопасность</span><span class="sxs-lookup"><span data-stu-id="2d7e4-140">Security</span></span>  

 <span data-ttu-id="2d7e4-141">Так как поставщик WMI WCF позволяет обнаруживать службы в среде, следует соблюдать особую осторожность при предоставлении доступа к ней.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-141">Because the WCF WMI provider allows the discovery of services in an environment, you should exercise extreme caution for granting access to it.</span></span> <span data-ttu-id="2d7e4-142">При изменении настроек по умолчанию, при которых доступ предоставляется только администратору, третьи лица с более низкой степенью доверия могут получить доступ к конфиденциальным данным в среде.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-142">If you relax the default administrator-only access, you may allow less-trusted parties access to sensitive data in your environment.</span></span> <span data-ttu-id="2d7e4-143">В частности, при расширении разрешений для удаленного доступа к WMI могут возникнуть атаки на переполнение.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-143">Specifically, if you loosen permissions on remote WMI access, flooding attacks can occur.</span></span> <span data-ttu-id="2d7e4-144">При переполнении процесса избыточными запросами WMI производительность процесса может снизится.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-144">If a process is flooded by excessive WMI requests, its performance can be degraded.</span></span>  
  
 <span data-ttu-id="2d7e4-145">Кроме того, при расширении прав доступа к файлу MOF третьи лица с более низкой степенью доверия могут управлять поведением WMI и изменять объекты, находящиеся в схеме WMI.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-145">In addition, if you relax access permissions for the MOF file, less-trusted parties can manipulate the behavior of WMI and alter the objects that are loaded in the WMI schema.</span></span> <span data-ttu-id="2d7e4-146">Например, поля могут быть удалены таким образом, что критические данные скрыты от администратора; или поля, которые не заполняются или вызывают исключения, добавляются в файл.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-146">For example, fields can be removed such that critical data is concealed from the administrator or that fields that do not populate or cause exceptions are added to the file.</span></span>  
  
 <span data-ttu-id="2d7e4-147">По умолчанию поставщик WMI WCF предоставляет разрешения "выполнить метод", "запись поставщика" и "включить учетную запись" для администратора, а также разрешение "включить учетную запись" для ASP.NET, локальной службы и сетевой службы.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-147">By default, the WCF WMI provider grants "execute method", "provider write", and "enable account" permission for Administrator, and "enable account" permission for ASP.NET, Local Service and Network Service.</span></span> <span data-ttu-id="2d7e4-148">В частности, на платформах, отличных от Windows Vista, учетная запись ASP.NET имеет доступ на чтение к пространству имен WMI ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-148">In particular, on non-Windows Vista platforms, the ASP.NET account has read access to the WMI ServiceModel namespace.</span></span> <span data-ttu-id="2d7e4-149">Если требуется не предоставлять эти привилегии определенной группе пользователей, нужно либо деактивировать поставщика инструментария WMI (по умолчанию он отключен), либо запретить доступ указанной группы пользователей.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-149">If you do not want to grant these privileges to a particular user group, you should either deactivate the WMI provider (it is disabled by default), or disable access for the specific user group.</span></span>  
  
 <span data-ttu-id="2d7e4-150">Возможно, поставщик инструментария WMI не удастся включить через конфигурацию по причине недостаточных привилегий пользователя.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-150">In addition, when you attempt to enable WMI through configuration, WMI may not be enabled due to insufficient user privilege.</span></span> <span data-ttu-id="2d7e4-151">Однако при возникновении этого сбоя никакой записи в журнале событий не делается.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-151">However, no event is written to the event log to record this failure.</span></span>  
  
 <span data-ttu-id="2d7e4-152">Для изменения уровней привилегий пользователя выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-152">To modify user privilege levels, use the following steps.</span></span>  
  
1. <span data-ttu-id="2d7e4-153">Нажмите кнопку Пуск, а затем запустите и введите **compmgmt. msc**.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-153">Click Start and then Run and type **compmgmt.msc**.</span></span>  
  
2. <span data-ttu-id="2d7e4-154">Щелкните правой кнопкой мыши **службы, приложения и элементы управления WMI** , чтобы выбрать **свойства**.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-154">Right-click **Services and Application/WMI Controls** to select **Properties**.</span></span>  
  
3. <span data-ttu-id="2d7e4-155">Откройте вкладку **Безопасность** и перейдите к пространству имен **root/ServiceModel** .</span><span class="sxs-lookup"><span data-stu-id="2d7e4-155">Select the **Security** Tab, and navigate to the **Root/ServiceModel** namespace.</span></span> <span data-ttu-id="2d7e4-156">Нажмите кнопку **Безопасность** .</span><span class="sxs-lookup"><span data-stu-id="2d7e4-156">Click the **Security** button.</span></span>  
  
4. <span data-ttu-id="2d7e4-157">Выберите конкретную группу или пользователя, которым требуется управлять доступом, и используйте флажок **Разрешить** или **запретить** для настройки разрешений.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-157">Select the specific group or user that you want to control access and use the **Allow** or **Deny** checkbox to configure permissions.</span></span>  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a><span data-ttu-id="2d7e4-158">Предоставление дополнительным пользователям разрешений на регистрацию WCF WMI</span><span class="sxs-lookup"><span data-stu-id="2d7e4-158">Granting WCF WMI Registration Permissions to Additional Users</span></span>  

 <span data-ttu-id="2d7e4-159">WCF предоставляет доступ к данным управления для WMI.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-159">WCF exposes management data to WMI.</span></span> <span data-ttu-id="2d7e4-160">Это достигается за счет размещения внутрипроцессного поставщика WMI, который иногда называется "несвязанным поставщиком".</span><span class="sxs-lookup"><span data-stu-id="2d7e4-160">It does so by hosting an in-process WMI provider, sometimes called a "decoupled provider".</span></span> <span data-ttu-id="2d7e4-161">Для предоставления доступа к данным управления учетная запись, которая регистрирует этот поставщик, должна иметь необходимые разрешения.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-161">For the management data to be exposed, the account that registers this provider must have the appropriate permissions.</span></span> <span data-ttu-id="2d7e4-162">В Windows регистрация несвязанных поставщиков по умолчанию доступна только небольшому числу привилегированных учетных записей.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-162">In Windows, only a small set of privileged accounts can register decoupled providers by default.</span></span> <span data-ttu-id="2d7e4-163">Это обстоятельство вызывает затруднения, поскольку пользователям обычно нужно предоставлять доступ к данным WMI из службы WCF, которая работает с учетной записью, не входящей в набор по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-163">This is a problem because users commonly want to expose WMI data from a WCF service running under an account that is not in the default set.</span></span>  
  
 <span data-ttu-id="2d7e4-164">Чтобы предоставить такой доступ, администратор должен предоставить дополнительной учетной записи следующие разрешения в указанном порядке:</span><span class="sxs-lookup"><span data-stu-id="2d7e4-164">To provide this access, an administrator must grant the following permissions to the additional account in the following order:</span></span>  
  
1. <span data-ttu-id="2d7e4-165">разрешение на доступ к пространству имен WCF WMI;</span><span class="sxs-lookup"><span data-stu-id="2d7e4-165">Permission to access to the WCF WMI Namespace.</span></span>  
  
2. <span data-ttu-id="2d7e4-166">разрешение на регистрацию несвязанного поставщика WMI для WCF.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-166">Permission to register the WCF Decoupled WMI Provider.</span></span>  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a><span data-ttu-id="2d7e4-167">Предоставление разрешения на доступ к пространству имен WMI</span><span class="sxs-lookup"><span data-stu-id="2d7e4-167">To grant WMI namespace access permission</span></span>  
  
1. <span data-ttu-id="2d7e4-168">Запустите следующий сценарий PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-168">Run the following PowerShell script.</span></span>  
  
    ```powershell  
    write-host ""  
    write-host "Granting Access to root/servicemodel WMI namespace to built in users group"  
    write-host ""  
  
    # Create the binary representation of the permissions to grant in SDDL  
    $newPermissions = "O:BAG:BAD:P(A;CI;CCDCLCSWRPWPRCWD;;;BA)(A;CI;CC;;;NS)(A;CI;CC;;;LS)(A;CI;CC;;;BU)"  
    $converter = new-object system.management.ManagementClass Win32_SecurityDescriptorHelper  
    $binarySD = $converter.SDDLToBinarySD($newPermissions)  
    $convertedPermissions = ,$binarySD.BinarySD  
  
    # Get the object used to set the permissions  
    $security = gwmi -namespace root/servicemodel -class __SystemSecurity  
  
    # Get and output the current settings  
    $binarySD = @($null)  
    $result = $security.PsBase.InvokeMethod("GetSD",$binarySD)  
  
    $outsddl = $converter.BinarySDToSDDL($binarySD[0])  
    write-host "Previous ACL: "$outsddl.SDDL  
  
    # Change the Access Control List (ACL) using SDDL  
    $result = $security.PsBase.InvokeMethod("SetSD",$convertedPermissions)
  
    # Get and output the current settings  
    $binarySD = @($null)  
    $result = $security.PsBase.InvokeMethod("GetSD",$binarySD)  
  
    $outsddl = $converter.BinarySDToSDDL($binarySD[0])  
    write-host "New ACL:      "$outsddl.SDDL  
    write-host ""  
    ```  
  
     <span data-ttu-id="2d7e4-169">Этот сценарий PowerShell использует язык определения дескрипторов безопасности (SDDL) для предоставления группе Built-In Users доступа к пространству имен WMI root/ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-169">This PowerShell script uses Security Descriptor Definition Language (SDDL) to grant the Built-In Users group access to the "root/servicemodel" WMI namespace.</span></span> <span data-ttu-id="2d7e4-170">В нем указываются следующие списки управления доступом.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-170">It specifies the following ACLs:</span></span>  
  
    - <span data-ttu-id="2d7e4-171">Встроенная учетная запись администратора (BA) - уже имеет доступ.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-171">Built-In Administrator (BA) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="2d7e4-172">Сетевая служба (NS) - уже имеет доступ.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-172">Network Service (NS) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="2d7e4-173">Локальная система (LS) - уже имеет доступ.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-173">Local System (LS) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="2d7e4-174">Встроенные пользователи - группа, которой предоставляется доступ.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-174">Built-In Users - The group to grant access to.</span></span>  
  
#### <a name="to-grant-provider-registration-access"></a><span data-ttu-id="2d7e4-175">Предоставление доступа к регистрации поставщика</span><span class="sxs-lookup"><span data-stu-id="2d7e4-175">To grant provider registration access</span></span>  
  
1. <span data-ttu-id="2d7e4-176">Запустите следующий сценарий PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-176">Run the following PowerShell script.</span></span>  
  
    ```powershell  
    write-host ""  
    write-host "Granting WCF provider registration access to built in users group"  
    write-host ""  
    # Set security on ServiceModel provider  
    $provider = get-WmiObject -namespace "root\servicemodel" __Win32Provider  
  
    write-host "Previous ACL: "$provider.SecurityDescriptor  
    $result = $provider.SecurityDescriptor = "O:BUG:BUD:(A;;0x1;;;BA)(A;;0x1;;;NS)(A;;0x1;;;LS)(A;;0x1;;;BU)"  
  
    # Commit the changes and display it to the console  
    $result = $provider.Put()  
    write-host "New ACL:      "$provider.SecurityDescriptor  
    write-host ""  
    ```  
  
### <a name="granting-access-to-arbitrary-users-or-groups"></a><span data-ttu-id="2d7e4-177">Предоставление доступа произвольным пользователям или группам</span><span class="sxs-lookup"><span data-stu-id="2d7e4-177">Granting Access to Arbitrary Users or Groups</span></span>  

 <span data-ttu-id="2d7e4-178">В примере из этого раздела всем локальным пользователям предоставляются права доступа к регистрации поставщика WMI.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-178">The example in this section grants WMI Provider registration privileges to all local users.</span></span> <span data-ttu-id="2d7e4-179">Если вы хотите предоставить доступ пользователю или группе, которые не являются встроенными, необходимо получить идентификатор безопасности (SID) этого пользователя или группы.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-179">If you want to grant access to a user or group that is not built in, then you must obtain that user or group's Security Identifier (SID).</span></span> <span data-ttu-id="2d7e4-180">Нет общего метода для получения идентификатора безопасности любого пользователя.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-180">There is no simple way to get the SID for an arbitrary user.</span></span> <span data-ttu-id="2d7e4-181">В качестве одного из решений можно выполнить вход от имени нужного пользователя, а затем выполнить следующую команду в командной оболочке.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-181">One method is to log on as the desired user and then issue the following shell command.</span></span>  
  
```console
Whoami /user  
```  
  
<span data-ttu-id="2d7e4-182">Дополнительные сведения см. в разделе [хорошо известные идентификаторы безопасности](/troubleshoot/windows-server/identity/security-identifiers-in-windows).</span><span class="sxs-lookup"><span data-stu-id="2d7e4-182">For more information, see [Well Known SIDs](/troubleshoot/windows-server/identity/security-identifiers-in-windows).</span></span>  
  
## <a name="accessing-remote-wmi-object-instances"></a><span data-ttu-id="2d7e4-183">Доступ к экземплярам удаленных объектов WMI</span><span class="sxs-lookup"><span data-stu-id="2d7e4-183">Accessing Remote WMI Object Instances</span></span>  

 <span data-ttu-id="2d7e4-184">Если необходимо получить доступ к экземплярам WMI WCF на удаленном компьютере, необходимо включить конфиденциальность пакетов для средств, используемых для доступа.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-184">If you need to access WCF WMI instances on a remote machine, you must enable packet privacy on the tools that you use for access.</span></span> <span data-ttu-id="2d7e4-185">В следующем разделе описывается, как это можно сделать с помощью WMI CIM Studio, тестера инструментария управления Windows или .NET SDK 2.0.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-185">The following section describes how to achieve these using the WMI CIM Studio, Windows Management Instrumentation Tester, as well as .NET SDK 2.0.</span></span>  
  
### <a name="wmi-cim-studio"></a><span data-ttu-id="2d7e4-186">WMI CIM Studio</span><span class="sxs-lookup"><span data-stu-id="2d7e4-186">WMI CIM Studio</span></span>

<span data-ttu-id="2d7e4-187">Если вы установили средства администрирования WMI, вы можете использовать WMI CIM Studio для доступа к экземплярам WMI.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-187">If you've installed WMI Administrative Tools, you can use the WMI CIM Studio to access WMI instances.</span></span> <span data-ttu-id="2d7e4-188">Эти средства находятся в следующей папке:</span><span class="sxs-lookup"><span data-stu-id="2d7e4-188">The tools are in the following folder:</span></span>
  
<span data-ttu-id="2d7e4-189">*Средства Филес\вми%Виндир%\програм\\*</span><span class="sxs-lookup"><span data-stu-id="2d7e4-189">*%windir%\Program Files\WMI Tools\\*</span></span>
  
1. <span data-ttu-id="2d7e4-190">В окне **Подключение к пространству имен:** введите **рут\сервицемодел** и нажмите кнопку **ОК.**</span><span class="sxs-lookup"><span data-stu-id="2d7e4-190">In the **Connect to namespace:** window, type **root\ServiceModel** and click **OK.**</span></span>  
  
2. <span data-ttu-id="2d7e4-191">В окне **входа WMI CIM Studio** нажмите кнопку **Параметры >>** , чтобы развернуть окно.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-191">In the **WMI CIM Studio Login** window, click the **Options >>** button to expand the window.</span></span> <span data-ttu-id="2d7e4-192">Выберите параметр **Конфиденциальность пакетов** для **уровня проверки подлинности** и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-192">Select **Packet privacy** for **Authentication level**, and click **OK**.</span></span>  
  
### <a name="windows-management-instrumentation-tester"></a><span data-ttu-id="2d7e4-193">Тестер инструментария управления Windows</span><span class="sxs-lookup"><span data-stu-id="2d7e4-193">Windows Management Instrumentation Tester</span></span>  

 <span data-ttu-id="2d7e4-194">Это средство установлено Windows.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-194">This tool is installed by Windows.</span></span> <span data-ttu-id="2d7e4-195">Запустите командную консоль, введя **cmd.exe** в диалоговом окне **Запуск/Запуск** и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-195">To run it, launch a command console by typing **cmd.exe** in the **Start/Run** dialog box and click **OK**.</span></span> <span data-ttu-id="2d7e4-196">Затем введите **wbemtest.exe** в командном окне.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-196">Then, type **wbemtest.exe** in the command window.</span></span> <span data-ttu-id="2d7e4-197">Запустится средство Тестер инструментария управления Windows.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-197">The Windows Management Instrumentation Tester tool is then launched.</span></span>  
  
1. <span data-ttu-id="2d7e4-198">Нажмите кнопку **подключить** в правом верхнем углу окна.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-198">Click the **Connect** button on the top right corner of the window.</span></span>  
  
2. <span data-ttu-id="2d7e4-199">В новом окне введите **рут\сервицемодел** в поле **пространство имен** и выберите параметр **Конфиденциальность пакетов** для **уровня проверки подлинности**.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-199">In the new window, enter **root\ServiceModel** for the **Namespace** field, and select **Packet privacy** for **Authentication level**.</span></span> <span data-ttu-id="2d7e4-200">Нажмите кнопку **Соединить**.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-200">Click **Connect**.</span></span>  
  
### <a name="using-managed-code"></a><span data-ttu-id="2d7e4-201">Использование управляемого кода</span><span class="sxs-lookup"><span data-stu-id="2d7e4-201">Using Managed Code</span></span>  

 <span data-ttu-id="2d7e4-202">Доступ к удаленным экземплярам WMI также может осуществляться программно с помощью классов, предоставляемых пространством имен <xref:System.Management>.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-202">You can also access remote WMI instances programmatically by using classes provided by the <xref:System.Management> namespace.</span></span> <span data-ttu-id="2d7e4-203">В следующем образце кода показано, как это сделать.</span><span class="sxs-lookup"><span data-stu-id="2d7e4-203">The following code sample demonstrates how to do this.</span></span>  
  
```csharp
String wcfNamespace = $@"\\{this.serviceMachineName}\Root\ServiceModel");
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```
