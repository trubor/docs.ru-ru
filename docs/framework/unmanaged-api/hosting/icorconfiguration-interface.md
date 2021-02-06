---
description: 'Дополнительные сведения о: интерфейс ICorConfiguration'
title: Интерфейс ICorConfiguration
ms.date: 03/30/2017
api_name:
- ICorConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorConfiguration
helpviewer_keywords:
- ICorConfiguration interface [.NET Framework hosting]
ms.assetid: aaf96116-372b-4538-afb1-9e0fcdac1f98
topic_type:
- apiref
ms.openlocfilehash: f75e9e445c7fe4615abcae27756bcc420b5255b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636693"
---
# <a name="icorconfiguration-interface"></a><span data-ttu-id="4f6b7-103">Интерфейс ICorConfiguration</span><span class="sxs-lookup"><span data-stu-id="4f6b7-103">ICorConfiguration Interface</span></span>

<span data-ttu-id="4f6b7-104">Предоставляет методы для настройки среды CLR.</span><span class="sxs-lookup"><span data-stu-id="4f6b7-104">Provides methods for configuring the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4f6b7-105">Методы</span><span class="sxs-lookup"><span data-stu-id="4f6b7-105">Methods</span></span>  
  
|<span data-ttu-id="4f6b7-106">Метод</span><span class="sxs-lookup"><span data-stu-id="4f6b7-106">Method</span></span>|<span data-ttu-id="4f6b7-107">Описание</span><span class="sxs-lookup"><span data-stu-id="4f6b7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4f6b7-108">Метод AddDebuggerSpecialThread</span><span class="sxs-lookup"><span data-stu-id="4f6b7-108">AddDebuggerSpecialThread Method</span></span>](icorconfiguration-adddebuggerspecialthread-method.md)|<span data-ttu-id="4f6b7-109">Указывает службам отладки, что определенному потоку должен быть разрешено продолжать выполнение, пока отладчик не остановит работу приложения во время управляемых или неуправляемых сценариев отладки.</span><span class="sxs-lookup"><span data-stu-id="4f6b7-109">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>|  
|[<span data-ttu-id="4f6b7-110">Метод SetDebuggerThreadControl</span><span class="sxs-lookup"><span data-stu-id="4f6b7-110">SetDebuggerThreadControl Method</span></span>](icorconfiguration-setdebuggerthreadcontrol-method.md)|<span data-ttu-id="4f6b7-111">Задает интерфейс обратного вызова, который службы отладки будут вызывать как потоки CLR, блокируются и разблокируются для отладки.</span><span class="sxs-lookup"><span data-stu-id="4f6b7-111">Sets the callback interface that the debugging services will call as CLR threads are blocked and unblocked for debugging.</span></span>|  
|[<span data-ttu-id="4f6b7-112">Метод SetGCHostControl</span><span class="sxs-lookup"><span data-stu-id="4f6b7-112">SetGCHostControl Method</span></span>](icorconfiguration-setgchostcontrol-method.md)|<span data-ttu-id="4f6b7-113">Задает интерфейс обратного вызова, используемый сборщиком мусора для запроса изменения ограничения виртуальной памяти на узле.</span><span class="sxs-lookup"><span data-stu-id="4f6b7-113">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>|  
|[<span data-ttu-id="4f6b7-114">Метод SetGCThreadControl</span><span class="sxs-lookup"><span data-stu-id="4f6b7-114">SetGCThreadControl Method</span></span>](icorconfiguration-setgcthreadcontrol-method.md)|<span data-ttu-id="4f6b7-115">Задает интерфейс обратного вызова для потоков планирования для задач, не относящихся к среде выполнения, которые в противном случае были бы заблокированы для сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="4f6b7-115">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4f6b7-116">Требования</span><span class="sxs-lookup"><span data-stu-id="4f6b7-116">Requirements</span></span>  

 <span data-ttu-id="4f6b7-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f6b7-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f6b7-118">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4f6b7-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4f6b7-119">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4f6b7-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4f6b7-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f6b7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f6b7-121">См. также</span><span class="sxs-lookup"><span data-stu-id="4f6b7-121">See also</span></span>

- [<span data-ttu-id="4f6b7-122">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="4f6b7-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="4f6b7-123">Компонентный класс CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="4f6b7-123">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
