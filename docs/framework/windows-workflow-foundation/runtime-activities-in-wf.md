---
description: 'Дополнительные сведения: действия времени выполнения в WF'
title: Действия времени выполнения в WF
ms.date: 03/30/2017
ms.assetid: e5ae8c31-19bc-4655-88b3-6b75cd6a1bd5
ms.openlocfilehash: 5ff164539b9efd7b2b8a4e7cffd5239eae6145fe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792639"
---
# <a name="runtime-activities-in-wf"></a><span data-ttu-id="2f580-103">Действия времени выполнения в WF</span><span class="sxs-lookup"><span data-stu-id="2f580-103">Runtime Activities in WF</span></span>

[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <span data-ttu-id="2f580-104">содержит несколько предоставляемых системой действий для доступа к функциям среды выполнения рабочих процессов, например к функциям сохраняемости и завершения рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="2f580-104">provides several system-provided activities for accessing the features of the workflow runtime, such as persistence and termination.</span></span>  
  
|<span data-ttu-id="2f580-105">Действие</span><span class="sxs-lookup"><span data-stu-id="2f580-105">Activity</span></span>|<span data-ttu-id="2f580-106">Описание</span><span class="sxs-lookup"><span data-stu-id="2f580-106">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Persist>|<span data-ttu-id="2f580-107">Явно запрашивает сохранение состояния рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="2f580-107">Explicitly requests that the workflow persist its state.</span></span>|  
|<xref:System.Activities.Statements.TerminateWorkflow>|<span data-ttu-id="2f580-108">Завершает выполнение экземпляра рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="2f580-108">Terminates the running workflow instance.</span></span>|  
|<xref:System.Activities.Statements.NoPersistScope>|<span data-ttu-id="2f580-109">Действие контейнера, препятствующее сохранению дочерних действий.</span><span class="sxs-lookup"><span data-stu-id="2f580-109">A container activity that prevents child activities from persisting.</span></span>|
