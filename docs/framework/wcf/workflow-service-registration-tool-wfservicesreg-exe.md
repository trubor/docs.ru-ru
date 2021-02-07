---
description: 'Дополнительные сведения: средство регистрации службы рабочих процессов (WFServicesReg.exe)'
title: Программа регистрации служб WorkFlow (WFServicesReg.exe)
ms.date: 03/30/2017
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
ms.openlocfilehash: 302da7e6e62db771472f95dc422cc7e97408600b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99676330"
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a><span data-ttu-id="f7484-103">Программа регистрации служб WorkFlow (WFServicesReg.exe)</span><span class="sxs-lookup"><span data-stu-id="f7484-103">WorkFlow Service Registration Tool (WFServicesReg.exe)</span></span>

<span data-ttu-id="f7484-104">Средство регистрации служб Workflow Services (WFServicesReg.exe) - это автономное средство, которое можно использовать для добавления, удаления или восстановления элементов конфигурации для служб Windows Workflow Foundation.</span><span class="sxs-lookup"><span data-stu-id="f7484-104">Workflow Services Registration tool (WFServicesReg.exe) is a stand-alone tool that can be used to add, remove, or repair the configuration elements for Windows Workflow Foundation (WF) services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7484-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f7484-105">Syntax</span></span>  
  
```console  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a><span data-ttu-id="f7484-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="f7484-106">Remarks</span></span>  

 <span data-ttu-id="f7484-107">Это средство можно найти в каталоге установки платформа .NET Framework 3,5, в частности, в%windir%\Microsoft.NET\Framework\v3.5 или%windir%\Microsoft.NET\Framework64\v3.5 на 64-разрядных компьютерах.</span><span class="sxs-lookup"><span data-stu-id="f7484-107">The tool can be found at the .NET Framework 3.5 installation location, specifically, %windir%\Microsoft.NET\Framework\v3.5, or at %windir%\Microsoft.NET\Framework64\v3.5 in 64-bit machines.</span></span>  
  
 <span data-ttu-id="f7484-108">В следующей таблице представлены параметры, которые могут использоваться со средством регистрации служб Workflow Services (WFServicesReg.exe).</span><span class="sxs-lookup"><span data-stu-id="f7484-108">The following tables describe the options that can be used with the Workflow Services Registration tool (WFServicesReg.exe).</span></span>  
  
|<span data-ttu-id="f7484-109">Параметр</span><span class="sxs-lookup"><span data-stu-id="f7484-109">Option</span></span>|<span data-ttu-id="f7484-110">Описание</span><span class="sxs-lookup"><span data-stu-id="f7484-110">Description</span></span>|  
|------------|-----------------|  
|`/c`|<span data-ttu-id="f7484-111">Настраивает службы Windows Workflow Services.</span><span class="sxs-lookup"><span data-stu-id="f7484-111">Configures Windows Workflow Services.</span></span> <span data-ttu-id="f7484-112">Используется в сценариях установки и восстановления.</span><span class="sxs-lookup"><span data-stu-id="f7484-112">Used in install and repair scenarios.</span></span>|  
|`/r`|<span data-ttu-id="f7484-113">Удаляет конфигурацию служб Windows Workflow Services.</span><span class="sxs-lookup"><span data-stu-id="f7484-113">Removes Windows Workflow Services Configuration.</span></span>|  
|`/v`|<span data-ttu-id="f7484-114">Отображает подробную выходную информацию (при настройке или удалении).</span><span class="sxs-lookup"><span data-stu-id="f7484-114">Print verbose information (for either configuration or removal).</span></span>|  
|`/m`|<span data-ttu-id="f7484-115">Включает формат ведения журнала MSI.</span><span class="sxs-lookup"><span data-stu-id="f7484-115">Enables MSI logging format.</span></span>|  
|`/i`|<span data-ttu-id="f7484-116">Сворачивает окно при выполнении приложения.</span><span class="sxs-lookup"><span data-stu-id="f7484-116">Minimizes the window when the application runs.</span></span>|  
  
## <a name="registration"></a><span data-ttu-id="f7484-117">Регистрация</span><span class="sxs-lookup"><span data-stu-id="f7484-117">Registration</span></span>  

 <span data-ttu-id="f7484-118">Средство проверяет файл Web.config и регистрирует следующие объекты.</span><span class="sxs-lookup"><span data-stu-id="f7484-118">The tool inspects the Web.config file and registers the following:</span></span>  
  
- <span data-ttu-id="f7484-119">Ссылочные сборки платформа .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="f7484-119">.NET Framework 3.5 reference assemblies.</span></span>  
  
- <span data-ttu-id="f7484-120">Поставщик построения для XOML-файлов.</span><span class="sxs-lookup"><span data-stu-id="f7484-120">A build provider for .xoml files.</span></span>  
  
- <span data-ttu-id="f7484-121">Обработчики HTTP-данных для XOML- и RULES-файлов.</span><span class="sxs-lookup"><span data-stu-id="f7484-121">HTTP handlers for .xoml and .rules files.</span></span>  
  
 <span data-ttu-id="f7484-122">Средство проверяет файл Machine.config и регистрирует следующие расширения.</span><span class="sxs-lookup"><span data-stu-id="f7484-122">The tool inspects the Machine.config file and registers the following extensions:</span></span>  
  
- <span data-ttu-id="f7484-123">behaviorExtensions</span><span class="sxs-lookup"><span data-stu-id="f7484-123">behaviorExtensions</span></span>  
  
- <span data-ttu-id="f7484-124">bindingElementExtensions</span><span class="sxs-lookup"><span data-stu-id="f7484-124">bindingElementExtensions</span></span>  
  
- <span data-ttu-id="f7484-125">bindingExtensions</span><span class="sxs-lookup"><span data-stu-id="f7484-125">bindingExtensions</span></span>  
  
 <span data-ttu-id="f7484-126">Средство также регистрирует следующие средства импорта метаданных клиента.</span><span class="sxs-lookup"><span data-stu-id="f7484-126">The tool also registers the following client metadata importers:</span></span>  
  
- <span data-ttu-id="f7484-127">policyImporters</span><span class="sxs-lookup"><span data-stu-id="f7484-127">policyImporters</span></span>  
  
- <span data-ttu-id="f7484-128">wsdlImporters</span><span class="sxs-lookup"><span data-stu-id="f7484-128">wsdlImporters</span></span>  
  
 <span data-ttu-id="f7484-129">Средство также регистрирует карты скриптов и обработчики XOML и RULES в метабазе IIS.</span><span class="sxs-lookup"><span data-stu-id="f7484-129">The tool also registers .xoml and .rules scriptmaps and handlers in the IIS metabase.</span></span>  
  
 <span data-ttu-id="f7484-130">На компьютерах под управлением Windows Server 2003 и Windows XP (IIS 5,1 и IIS 6,0) регистрируется один набор сценариев. XOML и Rules.</span><span class="sxs-lookup"><span data-stu-id="f7484-130">On Windows Server 2003 and Windows XP machines (IIS 5.1 and IIS 6.0), one set of .xoml and .rules scriptmaps are registered.</span></span>  
  
 <span data-ttu-id="f7484-131">На 64-разрядных компьютерах средство регистрирует карты скриптов режима WOW, если включен переключатель `Enable32BitAppOnWin64`, или собственные 64-разрядные карты скриптов, если переключатель `Enable32BitAppOnWin64` отключен.</span><span class="sxs-lookup"><span data-stu-id="f7484-131">On 64-bit machines, the tool registers WOW mode scriptmaps if the `Enable32BitAppOnWin64` switch is enabled, or native 64-bit scriptmaps if the `Enable32BitAppOnWin64` switch is disabled.</span></span>  
  
 <span data-ttu-id="f7484-132">На компьютерах с Windows Vista и Windows Server 2008 (IIS 7,0 и более поздних версий) зарегистрированы два набора обработчиков. XOML и. rules: один для интегрированного режима и один для классического режима.</span><span class="sxs-lookup"><span data-stu-id="f7484-132">On Windows Vista and Windows Server 2008 (IIS 7.0 and above) machines, two sets of .xoml and .rules handlers are registered: one for Integrated mode and one for Classic mode.</span></span>  
  
 <span data-ttu-id="f7484-133">На 64-разрядных компьютерах регистрируется три набора обработчиков (независимо от состояния переключателя `Enable32BitAppOnWin64`): один для интегрированного режима, один для классического режима WOW и один для собственного 64-разрядного классического режима.</span><span class="sxs-lookup"><span data-stu-id="f7484-133">On 64-bit machines, three sets of handlers are registered (regardless of the state of the `Enable32BitAppOnWin64` switch): one for Integrated mode, one for WOW Classic mode and one for native 64-bit Classic mode.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f7484-134">В отличие от ServiceModelreg.exe средство WFServicesReg.exe не позволяет добавлять, удалять или восстанавливать карты скриптов или обработчики для конкретного веб-сайта.</span><span class="sxs-lookup"><span data-stu-id="f7484-134">Unlike ServiceModelreg.exe, WFServicesReg.exe does not allow adding, removing, or repairing scriptmaps or handlers for a particular Web site.</span></span> <span data-ttu-id="f7484-135">Пути обхода данной проблемы см. в разделе "Восстановление карт скриптов".</span><span class="sxs-lookup"><span data-stu-id="f7484-135">For a workaround to this issue, see the "Repairing the Scriptmaps" section.</span></span>  
  
## <a name="usage-scenarios"></a><span data-ttu-id="f7484-136">Сценарии использования</span><span class="sxs-lookup"><span data-stu-id="f7484-136">Usage Scenarios</span></span>  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a><span data-ttu-id="f7484-137">Установка IIS после установки .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="f7484-137">Installing IIS after .NET Framework 3.5 is installed</span></span>  

 <span data-ttu-id="f7484-138">На компьютере под Windows Server 2003 платформа .NET Framework 3,5 устанавливается до установки IIS.</span><span class="sxs-lookup"><span data-stu-id="f7484-138">On a Windows Server 2003 machine, .NET Framework 3.5 is installed prior to IIS installation.</span></span> <span data-ttu-id="f7484-139">Из-за недоступности метабазы IIS установка платформа .NET Framework 3,5 будет выполнена без установки скриптов scriptmap и Rules.</span><span class="sxs-lookup"><span data-stu-id="f7484-139">Due to the unavailability of the IIS metabase, installation of .NET Framework 3.5 succeeds without installing .xoml and .rules scriptmaps.</span></span>  
  
 <span data-ttu-id="f7484-140">После установки IIS можно воспользоваться средством WFServicesReg.exe с переключателем `/c` для установки этих карт скриптов.</span><span class="sxs-lookup"><span data-stu-id="f7484-140">After IIS is installed, you can use the WFServicesReg.exe tool with the `/c` switch to install these specific scriptmaps.</span></span>  
  
### <a name="repairing-the-scriptmaps"></a><span data-ttu-id="f7484-141">Восстановление карт скриптов</span><span class="sxs-lookup"><span data-stu-id="f7484-141">Repairing the Scriptmaps</span></span>  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a><span data-ttu-id="f7484-142">Карта скрипта удалена из узла "Веб-сайты"</span><span class="sxs-lookup"><span data-stu-id="f7484-142">Scriptmap deleted under Web Sites node</span></span>  

 <span data-ttu-id="f7484-143">На компьютере с Windows Server 2003. XOML или. rules случайно удаляются из узла "веб-сайты".</span><span class="sxs-lookup"><span data-stu-id="f7484-143">On a Windows Server 2003 machine, .xoml or .rules is accidentally deleted from the Web Sites node.</span></span> <span data-ttu-id="f7484-144">Чтобы выполнить восстановление, запустите средство WFServicesReg.exe с переключателем `/c`.</span><span class="sxs-lookup"><span data-stu-id="f7484-144">This can be repaired by running the WFServicesReg.exe tool with the `/c` switch.</span></span>  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a><span data-ttu-id="f7484-145">Карта скрипта удалена из конкретного веб-сайта</span><span class="sxs-lookup"><span data-stu-id="f7484-145">Scriptmap deleted under a particular Web site</span></span>  

 <span data-ttu-id="f7484-146">На компьютере с Windows Server 2003. XOML или. rules случайно удаляются с определенного веб-сайта (например, веб-сайта по умолчанию), а не из узла веб-сайты.</span><span class="sxs-lookup"><span data-stu-id="f7484-146">On a Windows Server 2003 machine, .xoml or .rules is accidentally deleted from a particular Web site (for example, the Default Web Site) rather than from the Web Sites node.</span></span>  
  
 <span data-ttu-id="f7484-147">Чтобы восстановить удаленные обработчики для определенного веб-сайта, следует выполнить команду "WFServicesReg.exe/r", чтобы удалить обработчики со всех веб-сайтов, а затем выполнить команду "WFServicesReg.exe/c", чтобы создать соответствующие обработчики для всех веб-сайтов.</span><span class="sxs-lookup"><span data-stu-id="f7484-147">To repair deleted handlers for a particular Web site, you should run "WFServicesReg.exe /r" to remove handlers from all Web sites, then run "WFServicesReg.exe /c" to create the appropriate handlers for all Web sites.</span></span>  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a><span data-ttu-id="f7484-148">Настройка обработчиков после переключения режима IIS</span><span class="sxs-lookup"><span data-stu-id="f7484-148">Configuring handlers after switching IIS mode</span></span>  

 <span data-ttu-id="f7484-149">Если службы IIS находятся в режиме общей конфигурации и установлено платформа .NET Framework 3,5, метабаза IIS настраивается в общем расположении.</span><span class="sxs-lookup"><span data-stu-id="f7484-149">When IIS is in shared configuration mode and .NET Framework 3.5 is installed, the IIS metabase is configured under a shared location.</span></span> <span data-ttu-id="f7484-150">Если переключить IIS в режим, отличный от режима общей конфигурации, в локальной метабазе не будут содержаться необходимые обработчики.</span><span class="sxs-lookup"><span data-stu-id="f7484-150">If you switch IIS to non-shared configuration mode, the local metabase will not contain the required handlers.</span></span> <span data-ttu-id="f7484-151">Чтобы правильно настроить локальный метабазу, можно либо импортировать общий метабазу в локальную, либо выполнить команду "WFServicesReg.exe/c", которая настраивает локальный метабазу.</span><span class="sxs-lookup"><span data-stu-id="f7484-151">To configure the local metabase properly, you can either import the shared metabase to local, or run "WFServicesReg.exe /c", which configures the local metabase.</span></span>
