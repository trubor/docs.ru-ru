---
description: 'Подробнее о: Коррунтимехост coclass'
title: Компонентный класс CorRuntimeHost
ms.date: 03/30/2017
api_name:
- CorRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRuntimeHost
helpviewer_keywords:
- CoRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 5833740b-7d67-44b4-865c-b5bf45e291e3
topic_type:
- apiref
ms.openlocfilehash: cd2d01075e5c8264337e1e989b3d9fdc6bf68962
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760645"
---
# <a name="corruntimehost-coclass"></a><span data-ttu-id="fa174-103">Компонентный класс CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="fa174-103">CorRuntimeHost Coclass</span></span>

<span data-ttu-id="fa174-104">Предоставляет интерфейсы для управления приложениями, которые выполняются средой CLR.</span><span class="sxs-lookup"><span data-stu-id="fa174-104">Provides interfaces for managing applications that are being executed by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa174-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fa174-105">Syntax</span></span>  
  
```cpp  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="fa174-106">Интерфейсы</span><span class="sxs-lookup"><span data-stu-id="fa174-106">Interfaces</span></span>  
  
|<span data-ttu-id="fa174-107">Интерфейс</span><span class="sxs-lookup"><span data-stu-id="fa174-107">Interface</span></span>|<span data-ttu-id="fa174-108">Описание</span><span class="sxs-lookup"><span data-stu-id="fa174-108">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="fa174-109">Интерфейс ICorConfiguration</span><span class="sxs-lookup"><span data-stu-id="fa174-109">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)|<span data-ttu-id="fa174-110">Предоставляет методы для настройки среды CLR.</span><span class="sxs-lookup"><span data-stu-id="fa174-110">Provides methods for configuring the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="fa174-111">Интерфейс ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="fa174-111">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)|<span data-ttu-id="fa174-112">Предоставляет методы, позволяющие основному приложению запускать и прекращать работу среды CLR, создавать и настраивать домены приложений, получать доступ к домену по умолчанию и перечислять все домены, выполняющиеся в процессе.</span><span class="sxs-lookup"><span data-stu-id="fa174-112">Provides methods that enable the host to start and stop the common language runtime explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>|  
|[<span data-ttu-id="fa174-113">Интерфейс IDebuggerInfo</span><span class="sxs-lookup"><span data-stu-id="fa174-113">IDebuggerInfo Interface</span></span>](idebuggerinfo-interface.md)|<span data-ttu-id="fa174-114">Предоставляет методы для получения сведений о состоянии служб отладки.</span><span class="sxs-lookup"><span data-stu-id="fa174-114">Provides methods for obtaining information about the state of the debugging services.</span></span>|  
|[<span data-ttu-id="fa174-115">Интерфейс IGCHost</span><span class="sxs-lookup"><span data-stu-id="fa174-115">IGCHost Interface</span></span>](igchost-interface.md)|<span data-ttu-id="fa174-116">Предоставляет методы для получения сведений о системе сборки мусора и для управления некоторыми аспектами сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="fa174-116">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>|  
|<span data-ttu-id="fa174-117">IValidator</span><span class="sxs-lookup"><span data-stu-id="fa174-117">"IValidator"</span></span>|<span data-ttu-id="fa174-118">Предоставляет методы для проверки переносимых исполняемых образов и подробных отчетов об ошибках проверки.</span><span class="sxs-lookup"><span data-stu-id="fa174-118">Provides methods for validation of portable executable images and detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fa174-119">Требования</span><span class="sxs-lookup"><span data-stu-id="fa174-119">Requirements</span></span>  

 <span data-ttu-id="fa174-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa174-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa174-121">**Заголовок:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="fa174-121">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="fa174-122">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fa174-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fa174-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa174-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa174-124">См. также</span><span class="sxs-lookup"><span data-stu-id="fa174-124">See also</span></span>

- [<span data-ttu-id="fa174-125">Размещение коклассов</span><span class="sxs-lookup"><span data-stu-id="fa174-125">Hosting Coclasses</span></span>](hosting-coclasses.md)
