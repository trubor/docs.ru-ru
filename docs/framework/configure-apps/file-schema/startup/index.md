---
description: Дополнительные сведения о схеме параметров запуска
title: Схема параметров запуска
ms.date: 03/30/2017
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
ms.openlocfilehash: 268b8d8dc2598add61435dd6b07031aa06831737
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726095"
---
# <a name="startup-settings-schema"></a><span data-ttu-id="6ef11-103">Схема параметров запуска</span><span class="sxs-lookup"><span data-stu-id="6ef11-103">Startup settings schema</span></span>

<span data-ttu-id="6ef11-104">Параметры запуска определяют версию среды CLR, в которой должно выполняться приложение.</span><span class="sxs-lookup"><span data-stu-id="6ef11-104">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="6ef11-105">Элемент</span><span class="sxs-lookup"><span data-stu-id="6ef11-105">Element</span></span>|<span data-ttu-id="6ef11-106">Описание</span><span class="sxs-lookup"><span data-stu-id="6ef11-106">Description</span></span>|  
|-------------|-----------------|  
|[\<requiredRuntime>](requiredruntime-element.md)|<span data-ttu-id="6ef11-107">Указывает, что приложение поддерживает только версию 1.0 среды CLR.</span><span class="sxs-lookup"><span data-stu-id="6ef11-107">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="6ef11-108">Приложения, созданные с помощью среды выполнения версии 1,1, должны использовать **\<supportedRuntime>** элемент.</span><span class="sxs-lookup"><span data-stu-id="6ef11-108">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[\<supportedRuntime>](supportedruntime-element.md)|<span data-ttu-id="6ef11-109">Указывает, какие версии среды CLR поддерживает приложение.</span><span class="sxs-lookup"><span data-stu-id="6ef11-109">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[\<startup>](startup-element.md)|<span data-ttu-id="6ef11-110">Содержит **\<requiredRuntime>** элементы и **\<supportedRuntime>** .</span><span class="sxs-lookup"><span data-stu-id="6ef11-110">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6ef11-111">См. также</span><span class="sxs-lookup"><span data-stu-id="6ef11-111">See also</span></span>

- [<span data-ttu-id="6ef11-112">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="6ef11-112">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="6ef11-113">Практическое руководство. Настройка приложения для включения поддержки .NET Framework версии 4 и выше</span><span class="sxs-lookup"><span data-stu-id="6ef11-113">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
