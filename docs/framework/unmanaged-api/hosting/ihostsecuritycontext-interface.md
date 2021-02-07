---
description: 'Дополнительные сведения о: Интерфейс IHostSecurityContext'
title: Интерфейс IHostSecurityContext
ms.date: 03/30/2017
api_name:
- IHostSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext
helpviewer_keywords:
- IHostSecurityContext interface [.NET Framework hosting]
ms.assetid: 88e2eac0-8ccb-404f-abbc-287d55159842
topic_type:
- apiref
ms.openlocfilehash: c4c1be00a8b1c9df58797a0f2fc7e60abcab9673
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671650"
---
# <a name="ihostsecuritycontext-interface"></a><span data-ttu-id="a0089-103">Интерфейс IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="a0089-103">IHostSecurityContext Interface</span></span>

<span data-ttu-id="a0089-104">Позволяет среде CLR поддерживать сведения о контексте безопасности, реализуемые узлом.</span><span class="sxs-lookup"><span data-stu-id="a0089-104">Allows the common language runtime (CLR) to maintain security context information implemented by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a0089-105">Методы</span><span class="sxs-lookup"><span data-stu-id="a0089-105">Methods</span></span>  
  
|<span data-ttu-id="a0089-106">Метод</span><span class="sxs-lookup"><span data-stu-id="a0089-106">Method</span></span>|<span data-ttu-id="a0089-107">Описание</span><span class="sxs-lookup"><span data-stu-id="a0089-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a0089-108">Метод Capture</span><span class="sxs-lookup"><span data-stu-id="a0089-108">Capture Method</span></span>](ihostsecuritycontext-capture-method.md)|<span data-ttu-id="a0089-109">Возвращает клон `IHostSecurityContext` экземпляра, возвращенного из вызова [IHostSecurityManager:: getsecuritycontext-](ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="a0089-109">Gets a clone of the `IHostSecurityContext` instance returned from a call to [IHostSecurityManager::GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0089-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="a0089-110">Remarks</span></span>  

 <span data-ttu-id="a0089-111">Узел может управлять доступом кода к маркерам потоков как средой CLR, так и кодом пользователя.</span><span class="sxs-lookup"><span data-stu-id="a0089-111">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="a0089-112">Он также может гарантировать, что полные сведения о контексте безопасности передаются по асинхронным операциям или кодовым точкам с ограниченным доступом к коду.</span><span class="sxs-lookup"><span data-stu-id="a0089-112">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="a0089-113">`IHostSecurityContext` инкапсулирует эти сведения о контексте безопасности, которые непрозрачны для среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="a0089-113">`IHostSecurityContext` encapsulates this security context information, which is opaque to the runtime.</span></span> <span data-ttu-id="a0089-114">Среда выполнения захватывает эти сведения с помощью `Capture` и перемещает их между отправкой рабочего элемента пула потоков, выполнением метода завершения, а также конструкторами модулей и классов.</span><span class="sxs-lookup"><span data-stu-id="a0089-114">The runtime captures this information using `Capture`, and moves it across thread pool worker item dispatch, finalizer execution, and module and class constructors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0089-115">Требования</span><span class="sxs-lookup"><span data-stu-id="a0089-115">Requirements</span></span>  

 <span data-ttu-id="a0089-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0089-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0089-117">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a0089-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a0089-118">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a0089-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a0089-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0089-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0089-120">См. также</span><span class="sxs-lookup"><span data-stu-id="a0089-120">See also</span></span>

- [<span data-ttu-id="a0089-121">Интерфейс ICLRHostProtectionManager</span><span class="sxs-lookup"><span data-stu-id="a0089-121">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="a0089-122">Интерфейс IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="a0089-122">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="a0089-123">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="a0089-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
