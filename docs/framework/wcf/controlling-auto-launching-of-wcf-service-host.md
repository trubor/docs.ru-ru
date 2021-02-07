---
description: 'Дополнительные сведения: Управление автоматическим запуском узла службы WCF'
title: Управление автозапуском узла службы WCF
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: f0e9a4e79a403920c0bc6a512b30fb038b2aa1f4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677396"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a><span data-ttu-id="fcff0-103">Управление автозапуском узла службы WCF</span><span class="sxs-lookup"><span data-stu-id="fcff0-103">Controlling Auto-launching of WCF Service Host</span></span>

<span data-ttu-id="fcff0-104">Можно управлять возможностью автоматического запуска узла службы Windows Communication Foundation (WCF) (WcfSvcHost.exe) для проекта библиотеки служб WCF при отладке другого проекта в том же решении Visual Studio, которое содержит несколько проектов.</span><span class="sxs-lookup"><span data-stu-id="fcff0-104">You can control the auto-launching capability of Windows Communication Foundation (WCF) Service Host (WcfSvcHost.exe) for a WCF Service Library project, when you debug another project in the same Visual Studio solution containing multiple projects.</span></span>  
  
 <span data-ttu-id="fcff0-105">Для этого щелкните правой кнопкой мыши проект службы WCF в **Обозреватель решений**, выберите пункт **Свойства** и щелкните вкладку **параметры WCF** . Флажок **запустить узел службы WCF при отладке другого проекта в том же решении** включен по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="fcff0-105">To do so, right-click the WCF Service Project in **Solution Explorer**, choose **Properties**, and click **WCF Options** tab. The **Start WCF Service Host when debugging another project in the same solution** check box is enabled by default.</span></span> <span data-ttu-id="fcff0-106">Можно снять флажок, чтобы узел службы WCF для этого конкретного проекта не запускался при отладке другого проекта в том же решении.</span><span class="sxs-lookup"><span data-stu-id="fcff0-106">You can clear the box so that WCF Service Host for this specific project is not launched when another project is debugged in the same solution.</span></span>  
  
 <span data-ttu-id="fcff0-107">Это поведение не оказывает влияние на отладку по клавише F5 или на функциональные возможности добавления ссылки на службу для этого проекта.</span><span class="sxs-lookup"><span data-stu-id="fcff0-107">This behavior does not affect the F5 debugging, or Add Service Reference functionalities for this project.</span></span>  
  
 <span data-ttu-id="fcff0-108">Эта возможность доступна в следующих проектах.</span><span class="sxs-lookup"><span data-stu-id="fcff0-108">This option is available to the following projects:</span></span>  
  
- <span data-ttu-id="fcff0-109">Проект библиотеки службы WCF.</span><span class="sxs-lookup"><span data-stu-id="fcff0-109">WCF Service Library Project.</span></span>  
  
- <span data-ttu-id="fcff0-110">Проект библиотеки службы последовательного рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="fcff0-110">Sequential Workflow Service Library Project.</span></span>  
  
- <span data-ttu-id="fcff0-111">Проект библиотеки рабочего процесса конечного автомата.</span><span class="sxs-lookup"><span data-stu-id="fcff0-111">State Machine Workflow Service Library Project.</span></span>  
  
- <span data-ttu-id="fcff0-112">Проект библиотеки служб синдикации.</span><span class="sxs-lookup"><span data-stu-id="fcff0-112">Syndication Service Library Project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcff0-113">См. также</span><span class="sxs-lookup"><span data-stu-id="fcff0-113">See also</span></span>

- [<span data-ttu-id="fcff0-114">Узел службы WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="fcff0-114">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)
