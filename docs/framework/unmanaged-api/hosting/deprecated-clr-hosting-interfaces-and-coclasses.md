---
description: 'Дополнительные сведения: устаревшие интерфейсы размещения CLR и коклассы'
title: Устаревшие интерфейсы размещения CLR и CoClasses
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 1
- .NET Framework 1.1, hosting interfaces
- hosting interfaces [.NET Framework], version 1
- .NET Framework 1.0, hosting interfaces
ms.assetid: 7b3d2755-cbab-4160-bc69-eb85791e38c7
ms.openlocfilehash: 3d5e8d545dadb4f84c29e2e03a6b23e3729bfe66
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785644"
---
# <a name="deprecated-clr-hosting-interfaces-and-coclasses"></a><span data-ttu-id="82beb-103">Устаревшие интерфейсы размещения CLR и CoClasses</span><span class="sxs-lookup"><span data-stu-id="82beb-103">Deprecated CLR Hosting Interfaces and Coclasses</span></span>

<span data-ttu-id="82beb-104">В этом разделе описываются интерфейсы, которые могут использоваться неуправляемыми узлами для интеграции среды CLR в платформа .NET Framework версии 1,0 и 1,1 в свои приложения.</span><span class="sxs-lookup"><span data-stu-id="82beb-104">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the .NET Framework versions 1.0 and 1.1 into their applications.</span></span> <span data-ttu-id="82beb-105">Эти интерфейсы предоставляют основному приложению методы для настройки и загрузки среды выполнения в процесс.</span><span class="sxs-lookup"><span data-stu-id="82beb-105">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="82beb-106">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="82beb-106">In This Section</span></span>  

 <span data-ttu-id="82beb-107">IAppDomainSetup</span><span class="sxs-lookup"><span data-stu-id="82beb-107">IAppDomainSetup</span></span>  
 <span data-ttu-id="82beb-108">Предоставляет для узла методы настройки <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="82beb-108">Provides methods for the host to configure an <xref:System.AppDomain>.</span></span>  
  
 [<span data-ttu-id="82beb-109">Класс ICeeFileGen</span><span class="sxs-lookup"><span data-stu-id="82beb-109">ICeeFileGen Class</span></span>](iceefilegen-class.md)  
 <span data-ttu-id="82beb-110">Не рекомендуется Предоставляет функциональные возможности для создания машинного переносимого исполняемого файла (PE).</span><span class="sxs-lookup"><span data-stu-id="82beb-110">(Deprecated) Provides functionality for creating a native portable executable (PE) file.</span></span>  
  
 [<span data-ttu-id="82beb-111">Интерфейс ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="82beb-111">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)  
 <span data-ttu-id="82beb-112">Предоставляет для узла методы настройки параметров среды CLR.</span><span class="sxs-lookup"><span data-stu-id="82beb-112">Provides methods for the host to configure CLR settings.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="82beb-113">См. также</span><span class="sxs-lookup"><span data-stu-id="82beb-113">Related Sections</span></span>  

 [<span data-ttu-id="82beb-114">Интерфейсы размещения CLR</span><span class="sxs-lookup"><span data-stu-id="82beb-114">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)  
 <span data-ttu-id="82beb-115">Содержит разделы, описывающие интерфейсы размещения, предоставляемые с платформа .NET Framework версии 2,0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="82beb-115">Contains topics that describe the hosting interfaces provided with the .NET Framework version 2.0 and later versions.</span></span>
