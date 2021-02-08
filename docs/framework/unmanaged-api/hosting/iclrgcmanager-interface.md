---
description: 'Дополнительные сведения о: интерфейс Иклргкманажер'
title: Интерфейс ICLRGCManager
ms.date: 03/30/2017
api_name:
- ICLRGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager
helpviewer_keywords:
- ICLRGCManager interface [.NET Framework hosting]
ms.assetid: fb511c9b-3fe4-41b0-822a-6ba4a079d1f5
topic_type:
- apiref
ms.openlocfilehash: 648b2b131e28da8aabc7028b6d745351cae772fe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790000"
---
# <a name="iclrgcmanager-interface"></a><span data-ttu-id="21a23-103">Интерфейс ICLRGCManager</span><span class="sxs-lookup"><span data-stu-id="21a23-103">ICLRGCManager Interface</span></span>

<span data-ttu-id="21a23-104">Предоставляет методы, позволяющие узлу взаимодействовать с системой сборки мусора среды CLR.</span><span class="sxs-lookup"><span data-stu-id="21a23-104">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="21a23-105">Начиная с платформа .NET Framework 4,5, можно использовать метод [ICLRGCManager2:: SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) , чтобы задать размер сегмента сборки мусора и максимальный размер поколения 0 системы сборки мусора до значений, превышающих `DWORD` предельное значение, накладываемое методом [сетгкстартуплимитс](iclrgcmanager-setgcstartuplimits-method.md) .</span><span class="sxs-lookup"><span data-stu-id="21a23-105">Starting with the .NET Framework 4.5, you can use the [ICLRGCManager2::SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](iclrgcmanager-setgcstartuplimits-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="21a23-106">Методы</span><span class="sxs-lookup"><span data-stu-id="21a23-106">Methods</span></span>  
  
|<span data-ttu-id="21a23-107">Метод</span><span class="sxs-lookup"><span data-stu-id="21a23-107">Method</span></span>|<span data-ttu-id="21a23-108">Описание</span><span class="sxs-lookup"><span data-stu-id="21a23-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="21a23-109">Метод Collect</span><span class="sxs-lookup"><span data-stu-id="21a23-109">Collect Method</span></span>](iclrgcmanager-collect-method.md)|<span data-ttu-id="21a23-110">Вызывает принудительную сборку мусора для указанного поколения.</span><span class="sxs-lookup"><span data-stu-id="21a23-110">Forces a garbage collection for the specified generation.</span></span>|  
|[<span data-ttu-id="21a23-111">Метод GetStats</span><span class="sxs-lookup"><span data-stu-id="21a23-111">GetStats Method</span></span>](iclrgcmanager-getstats-method.md)|<span data-ttu-id="21a23-112">Возвращает набор текущих статистических данных о системе сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="21a23-112">Gets a set of current statistics about the garbage collection system.</span></span>|  
|[<span data-ttu-id="21a23-113">Метод SetGCStartupLimits</span><span class="sxs-lookup"><span data-stu-id="21a23-113">SetGCStartupLimits Method</span></span>](iclrgcmanager-setgcstartuplimits-method.md)|<span data-ttu-id="21a23-114">Задает размер сегмента сборки мусора и максимальный размер поколения 0 для системы сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="21a23-114">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21a23-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="21a23-115">Remarks</span></span>  

 <span data-ttu-id="21a23-116">Среда CLR реализует механизм сборки мусора для управляемого <xref:System.GC> типа.</span><span class="sxs-lookup"><span data-stu-id="21a23-116">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="21a23-117">Дополнительные сведения о системе сборки мусора см. в разделе [сборка мусора](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="21a23-117">For more information about the garbage collection system, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21a23-118">Требования</span><span class="sxs-lookup"><span data-stu-id="21a23-118">Requirements</span></span>  

 <span data-ttu-id="21a23-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21a23-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21a23-120">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="21a23-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="21a23-121">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="21a23-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21a23-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21a23-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21a23-123">См. также</span><span class="sxs-lookup"><span data-stu-id="21a23-123">See also</span></span>

- [<span data-ttu-id="21a23-124">Автоматическое управление памятью</span><span class="sxs-lookup"><span data-stu-id="21a23-124">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="21a23-125">Структура COR_GC_STATS</span><span class="sxs-lookup"><span data-stu-id="21a23-125">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="21a23-126">Интерфейс ICLRControl</span><span class="sxs-lookup"><span data-stu-id="21a23-126">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="21a23-127">Интерфейсы размещения CLR</span><span class="sxs-lookup"><span data-stu-id="21a23-127">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="21a23-128">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="21a23-128">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="21a23-129">Размещение</span><span class="sxs-lookup"><span data-stu-id="21a23-129">Hosting</span></span>](index.md)
