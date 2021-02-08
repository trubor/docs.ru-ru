---
description: 'Дополнительные сведения о: интерфейс ICLRGCManager2'
title: Интерфейс ICLRGCManager2
ms.date: 03/30/2017
api_name:
- ICLRGCManager2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2
helpviewer_keywords:
- ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 4b5ffd7b-9ad7-41cd-9bba-34030ae3da7e
topic_type:
- apiref
ms.openlocfilehash: 455b3a99d10fa43bf325e9f7075d255dd55ae38b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789961"
---
# <a name="iclrgcmanager2-interface"></a><span data-ttu-id="6f787-103">Интерфейс ICLRGCManager2</span><span class="sxs-lookup"><span data-stu-id="6f787-103">ICLRGCManager2 Interface</span></span>

<span data-ttu-id="6f787-104">Предоставляет методы, позволяющие узлу взаимодействовать с системой сборки мусора среды CLR.</span><span class="sxs-lookup"><span data-stu-id="6f787-104">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6f787-105">Методы</span><span class="sxs-lookup"><span data-stu-id="6f787-105">Methods</span></span>  
  
|<span data-ttu-id="6f787-106">Метод</span><span class="sxs-lookup"><span data-stu-id="6f787-106">Method</span></span>|<span data-ttu-id="6f787-107">Описание</span><span class="sxs-lookup"><span data-stu-id="6f787-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6f787-108">Метод SetGCStartupLimitsEx</span><span class="sxs-lookup"><span data-stu-id="6f787-108">SetGCStartupLimitsEx Method</span></span>](iclrgcmanager2-setgcstartuplimitsex-method.md)|<span data-ttu-id="6f787-109">Задает размер сегмента сборки мусора и максимальный размер поколения 0 для системы сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="6f787-109">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span> <span data-ttu-id="6f787-110">Включает поколение 0 и размеры сегментов, превышающие `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="6f787-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f787-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="6f787-111">Remarks</span></span>  

 <span data-ttu-id="6f787-112">Этот интерфейс наследуется от [интерфейса иклргкманажер](iclrgcmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="6f787-112">This interface inherits from the [ICLRGCManager Interface](iclrgcmanager-interface.md).</span></span>  
  
 <span data-ttu-id="6f787-113">Среда CLR реализует механизм сборки мусора для управляемого <xref:System.GC> типа.</span><span class="sxs-lookup"><span data-stu-id="6f787-113">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="6f787-114">Дополнительные сведения о системе сборки мусора см. в разделе [сборка мусора](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="6f787-114">For more information about the garbage collection system, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f787-115">Требования</span><span class="sxs-lookup"><span data-stu-id="6f787-115">Requirements</span></span>  

 <span data-ttu-id="6f787-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f787-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f787-117">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6f787-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6f787-118">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6f787-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6f787-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f787-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f787-120">См. также</span><span class="sxs-lookup"><span data-stu-id="6f787-120">See also</span></span>

- [<span data-ttu-id="6f787-121">Автоматическое управление памятью</span><span class="sxs-lookup"><span data-stu-id="6f787-121">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="6f787-122">Структура COR_GC_STATS</span><span class="sxs-lookup"><span data-stu-id="6f787-122">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="6f787-123">Интерфейс ICLRControl</span><span class="sxs-lookup"><span data-stu-id="6f787-123">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="6f787-124">Интерфейсы размещения CLR, добавленные в версиях .NET Framework 4 и 4.5</span><span class="sxs-lookup"><span data-stu-id="6f787-124">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="6f787-125">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="6f787-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="6f787-126">Размещение</span><span class="sxs-lookup"><span data-stu-id="6f787-126">Hosting</span></span>](index.md)
