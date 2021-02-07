---
description: Дополнительные сведения о переносе приложений удаленного взаимодействия .NET в WCF
title: Перенос приложений удаленного взаимодействия .NET на платформу WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 551ad759c11ab24d6ab83a466e8e94b8226bf4d4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733766"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a><span data-ttu-id="7497d-103">Перенос приложений удаленного взаимодействия .NET на платформу WCF</span><span class="sxs-lookup"><span data-stu-id="7497d-103">Migrating .NET Remoting Applications to WCF</span></span>

<span data-ttu-id="7497d-104">**Эта статья относится к устаревшей технологии, которая сохраняется для обеспечения обратной совместимости с существующими приложениями и не рекомендуется для новых разработчиков. Теперь распределенные приложения разрабатываются с помощью WCF.**</span><span class="sxs-lookup"><span data-stu-id="7497d-104">**This topic is specific to a legacy technology that is retained for backward compatibility with existing applications and is not recommended for new development. Distributed applications should now be developed using WCF.**</span></span>  
  
 <span data-ttu-id="7497d-105">Существует два способа использования преимуществ WCF с существующими приложениями удаленного взаимодействия .NET: интеграция и миграция.</span><span class="sxs-lookup"><span data-stu-id="7497d-105">There are two ways to take advantage of WCF with existing .NET Remoting applications: integration and migration.</span></span> <span data-ttu-id="7497d-106">Интеграция позволяет работать с .NET Remoting 2,0 и WCF параллельно, позволяя предоставлять одни и те же бизнес-объекты одновременно на обеих технологиях без необходимости изменения существующего кода .NET Remoting 2,0.</span><span class="sxs-lookup"><span data-stu-id="7497d-106">Integration allows you to have .NET Remoting 2.0 and WCF running side by side, letting you expose the same business objects over both technologies simultaneously without having to modify your existing .NET Remoting 2.0 code.</span></span> <span data-ttu-id="7497d-107">Для интеграции требуется, чтобы вы выполняли на платформа .NET Framework 2,0 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="7497d-107">Integration requires that you are running on .NET Framework 2.0 or greater.</span></span> <span data-ttu-id="7497d-108">Если вы хотите воспользоваться преимуществами функций WCF и не требуется совместимость с удаленными системами 2,0, вы можете перенести всю службу в WCF.</span><span class="sxs-lookup"><span data-stu-id="7497d-108">If you want to take advantage of WCF features and do not need wire compatibility with Remoting 2.0 systems, you can migrate your entire service to WCF.</span></span> <span data-ttu-id="7497d-109">Для миграции из .NET Remoting 2,0 в WCF требуются изменения в интерфейсе удаленного объекта и его параметрах конфигурации.</span><span class="sxs-lookup"><span data-stu-id="7497d-109">Migration from .NET Remoting 2.0 to WCF requires changes to the remote object's interface and its configuration settings.</span></span> <span data-ttu-id="7497d-110">Оба этих раздела рассматриваются в статье [удаленное взаимодействие с Windows Communication Foundation](/previous-versions/aa730857(v=vs.80)).</span><span class="sxs-lookup"><span data-stu-id="7497d-110">Both of these topics are covered in [From Remoting to the Windows Communication Foundation](/previous-versions/aa730857(v=vs.80)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7497d-111">См. также</span><span class="sxs-lookup"><span data-stu-id="7497d-111">See also</span></span>

- [<span data-ttu-id="7497d-112">Общие сведения об основных понятиях</span><span class="sxs-lookup"><span data-stu-id="7497d-112">Conceptual Overview</span></span>](../conceptual-overview.md)
