---
description: 'Дополнительные сведения о: <System. serviceModel. Activation>'
title: <system.serviceModel.activation>
ms.date: 03/30/2017
ms.assetid: c0cae85f-56cb-4030-8807-6f96edff8d2d
ms.openlocfilehash: 4da87248426f5da3c53a03d5f307a174b2b0dfc7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682609"
---
# \<system.serviceModel.activation>

<span data-ttu-id="4d64e-103">В данном разделе конфигурации представлены параметры конфигурации для средства SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="4d64e-103">This configuration section represents the configuration settings for the SMSvcHost.exe tool.</span></span> <span data-ttu-id="4d64e-104">Элементы конфигурации можно задать в файле SMSvcHost.exe.config.</span><span class="sxs-lookup"><span data-stu-id="4d64e-104">The configuration elements can be configured in the SMSvcHost.exe.config file.</span></span> <span data-ttu-id="4d64e-105">В частности в нем содержатся все параметры компьютера, которые необходимо настроить.</span><span class="sxs-lookup"><span data-stu-id="4d64e-105">Specifically, it includes all machine-wide settings that must be configured.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.serviceModel.activation>**  
  
## <a name="sample-configuration-file"></a><span data-ttu-id="4d64e-106">Образец файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="4d64e-106">Sample Configuration File</span></span>  

 <span data-ttu-id="4d64e-107">Далее приведен образец файла конфигурации (SMSvcHost.exe.config), используемый процессом прослушивателя SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="4d64e-107">The following is a sample configuration file (SMSvcHost.exe.config), which is used by the listener process SMSvcHost.exe.</span></span>  
  
```xml  
<configuration>
  <runtime>
    <gcConcurrent enabled="false" />
  </runtime>
  <system.serviceModel.activation>
    <net.tcp listenBacklog="10"
             maxPendingAccepts="2"
             maxPendingConnections="100"
             receiveTimeout="00:00:10"
             teredoEnabled="false">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18"/>
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19"/>
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-20"/>
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only) -->
        <add securityIdentifier="S-1-5-32-568"/>
      </allowAccounts>
    </net.tcp>
    <net.pipe maxConnectionsPendingDispatch="100"
              maxPendingAccepts="2"
              receiveTimeout="00:00:10">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18" />
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19" />
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-20" />
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only) -->
        <add securityIdentifier="S-1-5-32-568" />
      </allowAccounts>
    </net.pipe>
    <diagnostics performanceCountersEnabled="true" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="4d64e-108">См. также</span><span class="sxs-lookup"><span data-stu-id="4d64e-108">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration>
