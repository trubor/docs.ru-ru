---
description: 'Дополнительные сведения о: интерфейс Иапартменткаллбакк'
title: Интерфейс IApartmentCallback
ms.date: 03/30/2017
api_name:
- IApartmentCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IApartmentCallback
helpviewer_keywords:
- IApartmentCallback interface [.NET Framework hosting]
ms.assetid: 57c33c58-bf0b-4533-b569-e6a682d02cba
topic_type:
- apiref
ms.openlocfilehash: ddf99b1d926bd2d9765b936143785a975ea378a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785144"
---
# <a name="iapartmentcallback-interface"></a><span data-ttu-id="1dd6e-103">Интерфейс IApartmentCallback</span><span class="sxs-lookup"><span data-stu-id="1dd6e-103">IApartmentCallback Interface</span></span>

<span data-ttu-id="1dd6e-104">Предоставляет методы для выполнения обратных вызовов в апартаменте.</span><span class="sxs-lookup"><span data-stu-id="1dd6e-104">Provides methods for making callbacks within an apartment.</span></span> <span data-ttu-id="1dd6e-105">*Апартамент* — это логический контейнер в рамках процесса для объектов, имеющих одинаковые требования доступа к потокам.</span><span class="sxs-lookup"><span data-stu-id="1dd6e-105">An *apartment* is a logical container within a process for objects that share the same thread access requirements.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1dd6e-106">Методы</span><span class="sxs-lookup"><span data-stu-id="1dd6e-106">Methods</span></span>  
  
|<span data-ttu-id="1dd6e-107">Метод</span><span class="sxs-lookup"><span data-stu-id="1dd6e-107">Method</span></span>|<span data-ttu-id="1dd6e-108">Описание</span><span class="sxs-lookup"><span data-stu-id="1dd6e-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1dd6e-109">Метод DoCallback</span><span class="sxs-lookup"><span data-stu-id="1dd6e-109">DoCallback Method</span></span>](iapartmentcallback-docallback-method.md)|<span data-ttu-id="1dd6e-110">Выполняет указанную функцию в апартаменте.</span><span class="sxs-lookup"><span data-stu-id="1dd6e-110">Executes the specified function within an apartment.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1dd6e-111">Требования</span><span class="sxs-lookup"><span data-stu-id="1dd6e-111">Requirements</span></span>  

 <span data-ttu-id="1dd6e-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1dd6e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dd6e-113">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1dd6e-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1dd6e-114">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1dd6e-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1dd6e-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dd6e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dd6e-116">См. также</span><span class="sxs-lookup"><span data-stu-id="1dd6e-116">See also</span></span>

- [<span data-ttu-id="1dd6e-117">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="1dd6e-117">Hosting Interfaces</span></span>](hosting-interfaces.md)
