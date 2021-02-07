---
description: 'Подробнее: Устранение неполадок при установке'
title: Устранение неполадок с установкой
ms.date: 03/30/2017
ms.assetid: 1644f885-c408-4d5f-a5c7-a1a907bc8acd
ms.openlocfilehash: 8beb404040c15ade8f435772fe1b947eef766702
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703475"
---
# <a name="troubleshoot-setup-issues"></a><span data-ttu-id="e290b-103">Устранение неполадок при установке</span><span class="sxs-lookup"><span data-stu-id="e290b-103">Troubleshoot setup issues</span></span>

<span data-ttu-id="e290b-104">В этой статье описывается, как устранять неполадки при установке Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e290b-104">This article describes how to troubleshoot Windows Communication Foundation (WCF) setup issues.</span></span>  
  
## <a name="some-windows-communication-foundation-registry-keys-are-not-repaired-by-performing-an-msi-repair-operation-on-the-net-framework-30"></a><span data-ttu-id="e290b-105">Некоторые разделы реестра Windows Communication Foundation невозможно восстановить с помощью операции восстановления MSI в .NET Framework 3.0</span><span class="sxs-lookup"><span data-stu-id="e290b-105">Some Windows Communication Foundation Registry Keys are not Repaired by Performing an MSI Repair Operation on the .NET Framework 3.0</span></span>  

 <span data-ttu-id="e290b-106">Если удалить какие-либо разделы реестра из следующего списка:</span><span class="sxs-lookup"><span data-stu-id="e290b-106">If you delete any of the following registry keys:</span></span>  
  
- <span data-ttu-id="e290b-107">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="e290b-107">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0</span></span>  
  
- <span data-ttu-id="e290b-108">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="e290b-108">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0</span></span>  
  
- <span data-ttu-id="e290b-109">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="e290b-109">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0</span></span>  
  
- <span data-ttu-id="e290b-110">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="e290b-110">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0</span></span>  
  
- <span data-ttu-id="e290b-111">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC Bridge 3.0.0.0</span><span class="sxs-lookup"><span data-stu-id="e290b-111">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC Bridge 3.0.0.0</span></span>  
  
 <span data-ttu-id="e290b-112">Ключи не создаются повторно, если вы запускаете восстановление с помощью установщика платформа .NET Framework 3,0, запускаемого из программы установки **и удаления программ** на **панели управления**.</span><span class="sxs-lookup"><span data-stu-id="e290b-112">The keys are not re-created if you run repair by using the .NET Framework 3.0 installer launched from the **Add/Remove Programs** applet in **Control Panel**.</span></span> <span data-ttu-id="e290b-113">Чтобы правильно восстановить эти разделы, необходимо удалить платформу .NET Framework 3.0, а затем установить ее снова.</span><span class="sxs-lookup"><span data-stu-id="e290b-113">To recreate these keys correctly, the user must uninstall and reinstall the .NET Framework 3.0.</span></span>  
  
## <a name="wmi-service-corruption-blocks-installation-of-the-wmi-provider"></a><span data-ttu-id="e290b-114">Повреждение службы WMI блокирует установку поставщика WMI</span><span class="sxs-lookup"><span data-stu-id="e290b-114">WMI Service Corruption Blocks Installation of the WMI provider</span></span>

 <span data-ttu-id="e290b-115">Повреждение службы WMI может заблокировать установку поставщика Windows Communication Foundation WMI при установке пакета платформа .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="e290b-115">WMI Service Corruption may block the installation of the Windows Communication Foundation WMI provider when installing the .NET Framework 3.0 package.</span></span> <span data-ttu-id="e290b-116">Во время установки Windows Communication Foundation Installer не удается зарегистрировать файл WCF *. mof* с помощью компонента *mofcomp.exe* .</span><span class="sxs-lookup"><span data-stu-id="e290b-116">During installation, the Windows Communication Foundation installer is unable to register the WCF *.mof* file using the *mofcomp.exe* component.</span></span> <span data-ttu-id="e290b-117">Ниже приведен список признаков возникновения такой ситуации.</span><span class="sxs-lookup"><span data-stu-id="e290b-117">The following is a list of symptoms:</span></span>  
  
1. <span data-ttu-id="e290b-118">Установка .NET Framework 3.0 завершается успешно, но поставщик инструментария WMI для WCF не зарегистрирован.</span><span class="sxs-lookup"><span data-stu-id="e290b-118">.NET Framework 3.0 installation completes successfully, but the WCF WMI provider is not registered.</span></span>  
  
2. <span data-ttu-id="e290b-119">В журнале событий приложения появляется запись об ошибке, связанной с проблемами при регистрации поставщика инструментария WMI для WCF или при запуске средства mofcomp.exe.</span><span class="sxs-lookup"><span data-stu-id="e290b-119">An error event appears in the application event log that references problems registering the WMI provider for WCF, or running mofcomp.exe.</span></span>  
  
3. <span data-ttu-id="e290b-120">В файле журнала установки с именем dd_wcf_retCA\* в каталоге %temp% пользователя содержатся сведения о том, что не удалось зарегистрировать поставщик инструментария WMI для WCF.</span><span class="sxs-lookup"><span data-stu-id="e290b-120">The setup log file named dd_wcf_retCA\* in the user's %temp% directory contains references to failure to register the WCF WMI provider.</span></span>  
  
4. <span data-ttu-id="e290b-121">В журнале событий или в файле журнала трассировки установки может быть зарегистрировано исключение, например одно из приведенных ниже.</span><span class="sxs-lookup"><span data-stu-id="e290b-121">An exception such as one the following may be listed in the event log or setup trace log file:</span></span>  
  
     <span data-ttu-id="e290b-122">ServiceModelReg [11:09:59:046]: System.ApplicationException: Неожиданный результат 3, ожидается E:\WINDOWS\system32\wbem\mofcomp.exe с «E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModel.mof»</span><span class="sxs-lookup"><span data-stu-id="e290b-122">ServiceModelReg [11:09:59:046]: System.ApplicationException: Unexpected result 3 executing E:\WINDOWS\system32\wbem\mofcomp.exe with "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModel.mof"</span></span>  
  
     <span data-ttu-id="e290b-123">или</span><span class="sxs-lookup"><span data-stu-id="e290b-123">or:</span></span>  
  
     <span data-ttu-id="e290b-124">ServiceModelReg [07:19:33:843]: System.TypeInitializationException: Инициализатор типа 'System.Management.ManagementPath' выдал исключение.</span><span class="sxs-lookup"><span data-stu-id="e290b-124">ServiceModelReg [07:19:33:843]: System.TypeInitializationException: The type initializer for 'System.Management.ManagementPath' threw an exception.</span></span> <span data-ttu-id="e290b-125">---> System. Runtime. InteropServices. COMException (0x80040154): не удалось получить фабрику класса COM для компонента с CLSID {CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA} из-за следующей ошибки: 80040154.</span><span class="sxs-lookup"><span data-stu-id="e290b-125">---> System.Runtime.InteropServices.COMException (0x80040154): Retrieving the COM class factory for component with CLSID {CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA} failed due to the following error: 80040154.</span></span>  
  
     <span data-ttu-id="e290b-126">или</span><span class="sxs-lookup"><span data-stu-id="e290b-126">or:</span></span>  
  
     <span data-ttu-id="e290b-127">ServiceModelReg [07:19:32:750]: System.IO.FileNotFoundException: Невозможно загрузить файл или сборку 'C:\WINDOWS\system32\wbem\mofcomp.exe' или один из зависимых от них компонентов.</span><span class="sxs-lookup"><span data-stu-id="e290b-127">ServiceModelReg [07:19:32:750]: System.IO.FileNotFoundException: Could not load file or assembly 'C:\WINDOWS\system32\wbem\mofcomp.exe' or one of its dependencies.</span></span> <span data-ttu-id="e290b-128">Системе не удается найти указанный файл.</span><span class="sxs-lookup"><span data-stu-id="e290b-128">The system cannot find the file specified.</span></span>  
  
     <span data-ttu-id="e290b-129">Имя файла: 'C:\WINDOWS\system32\wbem\mofcomp.exe</span><span class="sxs-lookup"><span data-stu-id="e290b-129">File name: 'C:\WINDOWS\system32\wbem\mofcomp.exe</span></span>  
  
 <span data-ttu-id="e290b-130">Чтобы решить описанную выше проблему, необходимо выполнить следующие действия.</span><span class="sxs-lookup"><span data-stu-id="e290b-130">The following steps must be followed to resolve the problem described previously.</span></span>  
  
1. <span data-ttu-id="e290b-131">Запустите служебная программа для диагностики WMI, чтобы восстановить службу WMI.</span><span class="sxs-lookup"><span data-stu-id="e290b-131">Run the WMI Diagnosis Utility to repair the WMI service.</span></span> <span data-ttu-id="e290b-132">Дополнительные сведения об использовании этого средства см. в разделе [служебная программа для диагностики WMI](/previous-versions/tn-archive/ff404265(v%3dmsdn.10)).</span><span class="sxs-lookup"><span data-stu-id="e290b-132">For more information about using this tool, see [WMI Diagnosis Utility](/previous-versions/tn-archive/ff404265(v%3dmsdn.10)).</span></span>  
  
 <span data-ttu-id="e290b-133">Восстановите установку платформа .NET Framework 3,0 с помощью приложения **Установка и удаление программ** , расположенного в **панели управления**, или удалите или переустановите платформа .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="e290b-133">Repair the .NET Framework 3.0 installation by using the **Add/Remove Programs** applet located in **Control Panel**, or uninstall/reinstall the .NET Framework 3.0.</span></span>  
  
## <a name="repair-net-framework-30-after-net-framework-35-installation"></a><span data-ttu-id="e290b-134">Исправление платформа .NET Framework 3,0 после установки платформа .NET Framework 3,5</span><span class="sxs-lookup"><span data-stu-id="e290b-134">Repair .NET Framework 3.0 after .NET Framework 3.5 Installation</span></span>

 <span data-ttu-id="e290b-135">При восстановлении платформа .NET Framework 3,0 после установки платформа .NET Framework 3,5 элементы конфигурации, появившиеся платформа .NET Framework 3,5 в *machine.config* , удаляются.</span><span class="sxs-lookup"><span data-stu-id="e290b-135">If you do a repair of .NET Framework 3.0 after you installed .NET Framework 3.5, configuration elements introduced by .NET Framework 3.5 in *machine.config* are removed.</span></span> <span data-ttu-id="e290b-136">Однако файл *web.config* остается неизменным.</span><span class="sxs-lookup"><span data-stu-id="e290b-136">However, the *web.config* file remains intact.</span></span> <span data-ttu-id="e290b-137">Чтобы решить эту проблему, восстановите платформа .NET Framework 3,5 после этого через ARP или используйте [средство регистрации службы рабочего процесса (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) с `/c` параметром.</span><span class="sxs-lookup"><span data-stu-id="e290b-137">The workaround is to repair .NET Framework 3.5 after this via ARP, or use the [WorkFlow Service Registration Tool (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) with the `/c` switch.</span></span>  
  
 <span data-ttu-id="e290b-138">[Средство регистрации служб рабочего процесса (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) можно найти по адресу%windir%\Microsoft.NET\framework\v3.5\ или%WINDIR%\Microsoft.NET\framework64\v3.5\.</span><span class="sxs-lookup"><span data-stu-id="e290b-138">[WorkFlow Service Registration Tool (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) can be found at %windir%\Microsoft.NET\framework\v3.5\ or %windir%\Microsoft.NET\framework64\v3.5\</span></span>  
  
## <a name="configure-iis-properly-for-wcfwf-webhost-after-installing-net-framework-35"></a><span data-ttu-id="e290b-139">Правильная настройка узла WCF/WF в службах IIS после установки .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="e290b-139">Configure IIS Properly for WCF/WF Webhost after Installing .NET Framework 3.5</span></span>  

 <span data-ttu-id="e290b-140">Если при установке платформа .NET Framework 3,5 не удается настроить дополнительные параметры конфигурации IIS, связанные с WCF, в журнал установки заносится ошибка и выполняется продолжение.</span><span class="sxs-lookup"><span data-stu-id="e290b-140">When .NET Framework 3.5 installation fails to configure additional WCF-related IIS configuration settings, it logs an error in the installation log and continues.</span></span> <span data-ttu-id="e290b-141">Все попытки запуска приложений WorkflowServices будут неудачными, поскольку отсутствуют обязательные параметры конфигурации.</span><span class="sxs-lookup"><span data-stu-id="e290b-141">Any attempt to run WorkflowServices applications will fail, since the required configuration settings are missing.</span></span> <span data-ttu-id="e290b-142">Например, не удастся загрузить службы правил или XOML.</span><span class="sxs-lookup"><span data-stu-id="e290b-142">For example, loading xoml or rules service can fail.</span></span>  
  
 <span data-ttu-id="e290b-143">Чтобы решить эту проблему, используйте [средство регистрации службы рабочего процесса (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) с `/c` параметром, чтобы правильно настроить карты сценариев IIS на компьютере.</span><span class="sxs-lookup"><span data-stu-id="e290b-143">To workaround this problem, use the [WorkFlow Service Registration Tool (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) with the `/c` switch to properly configure IIS script maps on the machine.</span></span> <span data-ttu-id="e290b-144">[Средство регистрации служб рабочего процесса (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) можно найти по адресу%windir%\Microsoft.NET\framework\v3.5\ или%WINDIR%\Microsoft.NET\framework64\v3.5\.</span><span class="sxs-lookup"><span data-stu-id="e290b-144">[WorkFlow Service Registration Tool (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) can be found at %windir%\Microsoft.NET\framework\v3.5\ or %windir%\Microsoft.NET\framework64\v3.5\</span></span>  
  
## <a name="could-not-load-type-systemservicemodelactivationhttpmodule"></a><span data-ttu-id="e290b-145">Не удалось загрузить тип "System. ServiceModel. Activation. HttpModule"</span><span class="sxs-lookup"><span data-stu-id="e290b-145">Could not load type 'System.ServiceModel.Activation.HttpModule'</span></span>

<span data-ttu-id="e290b-146">**Не удалось загрузить тип "System. ServiceModel. Activation. HttpModule" из сборки "System. ServiceModel, версия 3.0.0.0, язык и региональные параметры = нейтральный, PublicKeyToken = b77a5c561934e089»"**</span><span class="sxs-lookup"><span data-stu-id="e290b-146">**Could not load type 'System.ServiceModel.Activation.HttpModule' from assembly 'System.ServiceModel, Version 3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'**</span></span>

 <span data-ttu-id="e290b-147">Эта ошибка возникает, если установлена платформа .NET Framework 4, а затем включена активация WCF HTTP.</span><span class="sxs-lookup"><span data-stu-id="e290b-147">This error occurs if .NET Framework 4 is installed and then WCF HTTP Activation is enabled.</span></span> <span data-ttu-id="e290b-148">Чтобы устранить эту проблему, выполните следующую команду в Командная строка разработчика для Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="e290b-148">To resolve the issue, run the following command from inside the Developer Command Prompt for Visual Studio:</span></span>  
  
```console
aspnet_regiis.exe -i -enable  
```  
  
## <a name="see-also"></a><span data-ttu-id="e290b-149">См. также</span><span class="sxs-lookup"><span data-stu-id="e290b-149">See also</span></span>

- [<span data-ttu-id="e290b-150">Инструкции по установке</span><span class="sxs-lookup"><span data-stu-id="e290b-150">Set-Up Instructions</span></span>](./samples/set-up-instructions.md)
