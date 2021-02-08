---
description: 'Дополнительные сведения о: интерфейс ICLRIoCompletionManager'
title: Интерфейс ICLRIoCompletionManager
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager
helpviewer_keywords:
- ICLRIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c6c3ace6-e5e7-4450-8cc5-a9a48208c493
topic_type:
- apiref
ms.openlocfilehash: b2d18f9c9900d448f0c6517520c303eb4258f8d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789897"
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="16c79-103">Интерфейс ICLRIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="16c79-103">ICLRIoCompletionManager Interface</span></span>

<span data-ttu-id="16c79-104">Реализует метод обратного вызова, который позволяет узлу уведомлять среду CLR о состоянии указанных запросов ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="16c79-104">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="16c79-105">Методы</span><span class="sxs-lookup"><span data-stu-id="16c79-105">Methods</span></span>  
  
|<span data-ttu-id="16c79-106">Метод</span><span class="sxs-lookup"><span data-stu-id="16c79-106">Method</span></span>|<span data-ttu-id="16c79-107">Описание</span><span class="sxs-lookup"><span data-stu-id="16c79-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="16c79-108">Метод OnComplete</span><span class="sxs-lookup"><span data-stu-id="16c79-108">OnComplete Method</span></span>](iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="16c79-109">Сообщает среде CLR о состоянии запроса ввода-вывода, сделанного с помощью вызова метода [IHostIoCompletionManager:: BIND](ihostiocompletionmanager-bind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="16c79-109">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16c79-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="16c79-110">Remarks</span></span>  

 <span data-ttu-id="16c79-111">Узел реализует абстракцию завершения ввода-вывода с помощью интерфейса [IHostIoCompletionManager](ihostiocompletionmanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="16c79-111">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="16c79-112">CLR выполняет запросы ввода-вывода через этот интерфейс, и узел уведомляет среду выполнения о результатах таких запросов с помощью `ICLRIoCompletionManager` интерфейса.</span><span class="sxs-lookup"><span data-stu-id="16c79-112">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16c79-113">Требования</span><span class="sxs-lookup"><span data-stu-id="16c79-113">Requirements</span></span>  

 <span data-ttu-id="16c79-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16c79-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16c79-115">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="16c79-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="16c79-116">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="16c79-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="16c79-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16c79-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16c79-118">См. также</span><span class="sxs-lookup"><span data-stu-id="16c79-118">See also</span></span>

- [<span data-ttu-id="16c79-119">Интерфейс IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="16c79-119">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="16c79-120">Интерфейс IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="16c79-120">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
- [<span data-ttu-id="16c79-121">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="16c79-121">Hosting Interfaces</span></span>](hosting-interfaces.md)
