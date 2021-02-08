---
description: 'Дополнительные сведения: безопасность'
title: Безопасность
ms.date: 03/30/2017
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
ms.openlocfilehash: 8f095292deac77c1c72cf87a93064569f7dab982
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798099"
---
# <a name="security"></a><span data-ttu-id="dcbf6-103">Безопасность</span><span class="sxs-lookup"><span data-stu-id="dcbf6-103">Security</span></span>

<span data-ttu-id="dcbf6-104">Хранилище экземпляров рабочих процессов SQL использует следующие роли безопасности базы данных для обеспечения безопасного доступа к сведениям о состоянии экземпляров в базе данных сохраняемости.</span><span class="sxs-lookup"><span data-stu-id="dcbf6-104">The SQL Workflow Instance Store uses the following database security roles to secure access to instance state information in the persistence database.</span></span>  
  
- <span data-ttu-id="dcbf6-105">**System. activitys. DurableInstancing. инстанцестореусерс**.</span><span class="sxs-lookup"><span data-stu-id="dcbf6-105">**System.Activities.DurableInstancing.InstanceStoreUsers**.</span></span> <span data-ttu-id="dcbf6-106">Эта роль имеет доступ на чтение и запись для всех открытых представлений и права на выполнение хранимых процедур, участвующих в создании, загрузке и сохранении экземпляров.</span><span class="sxs-lookup"><span data-stu-id="dcbf6-106">This role has read and write access to public views and execution rights to stored procedures that are involved in creating, loading and saving instances.</span></span>  
  
- <span data-ttu-id="dcbf6-107">**System. activitys. DurableInstancing. инстанцестореобсерверс**.</span><span class="sxs-lookup"><span data-stu-id="dcbf6-107">**System.Activities.DurableInstancing.InstanceStoreObservers**.</span></span> <span data-ttu-id="dcbf6-108">Эта роль имеет доступ только для чтения открытых представлений.</span><span class="sxs-lookup"><span data-stu-id="dcbf6-108">This role has read-only access to public views.</span></span>  
  
- <span data-ttu-id="dcbf6-109">**System. activitys. DurableInstancing. воркфловактиватионусерс**.</span><span class="sxs-lookup"><span data-stu-id="dcbf6-109">**System.Activities.DurableInstancing.WorkflowActivationUsers**.</span></span> <span data-ttu-id="dcbf6-110">Эта роль имеет права на выполнение хранимых процедур, участвующих в процессе активации экземпляра.</span><span class="sxs-lookup"><span data-stu-id="dcbf6-110">This role has execution rights to stored procedures that are involved in the instance activation process.</span></span> <span data-ttu-id="dcbf6-111">Дополнительные сведения об активации экземпляра см. в разделе [Активация экземпляра](instance-activation.md).</span><span class="sxs-lookup"><span data-stu-id="dcbf6-111">For more information about instance activation, see [Instance Activation](instance-activation.md).</span></span> <span data-ttu-id="dcbf6-112">Учетная запись пользователя, под которой выполняются универсальные узлы (например, служба управления рабочими процессами компонентов Windows Server AppFabric), должна быть добавлена к этой роли базы данных.</span><span class="sxs-lookup"><span data-stu-id="dcbf6-112">The user account under which a generic host (such as the Workflow Management Service of the hosting features of Windows Server AppFabric) runs should be added to this database role.</span></span>  
  
 <span data-ttu-id="dcbf6-113">Дополнительные сведения о безопасности хранилищ сохраняемости в Windows Server App Fabric см. в статье [Настройка безопасности для хранилищ сохраняемости в App Fabric](/previous-versions/appfabric/ff431727(v=azure.10)) .</span><span class="sxs-lookup"><span data-stu-id="dcbf6-113">For more information about security for persistence stores with Windows Server App Fabric, see [Security Configuration for Persistence Stores in App Fabric](/previous-versions/appfabric/ff431727(v=azure.10))</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="dcbf6-114">Клиент, имеющий доступ к данным собственного экземпляра в хранилище экземпляров, также получает доступ и ко всем другим экземплярам в этом хранилище экземпляров.</span><span class="sxs-lookup"><span data-stu-id="dcbf6-114">A client that has access to its own instance data in the instance store has access to all other instances in the same instance store.</span></span> <span data-ttu-id="dcbf6-115">Хранилище экземпляров не поддерживает указание прав доступа на уровне экземпляра.</span><span class="sxs-lookup"><span data-stu-id="dcbf6-115">The instance store does not support specifying security permissions at the instance level.</span></span> <span data-ttu-id="dcbf6-116">Для обеспечения доступа к различным хранилищам экземпляров необходимо создать отдельные хранилища экземпляров и настроить доступ к ним различных групп и пользователей.</span><span class="sxs-lookup"><span data-stu-id="dcbf6-116">You should create separate instance stores and map different groups/users to have access to different stores.</span></span>
