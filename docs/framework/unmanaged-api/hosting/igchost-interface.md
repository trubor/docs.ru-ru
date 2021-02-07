---
description: 'Дополнительные сведения о: интерфейс IGCHost'
title: Интерфейс IGCHost
ms.date: 03/30/2017
api_name:
- IGCHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost
helpviewer_keywords:
- IGCHost interface [.NET Framework hosting]
ms.assetid: 9ad70ffd-6963-4ab2-8c84-3d86c3fb8deb
topic_type:
- apiref
ms.openlocfilehash: 73b1125eb66a38373da85769ab80ddcaf0b955c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709598"
---
# <a name="igchost-interface"></a><span data-ttu-id="68dc0-103">Интерфейс IGCHost</span><span class="sxs-lookup"><span data-stu-id="68dc0-103">IGCHost Interface</span></span>

<span data-ttu-id="68dc0-104">Предоставляет методы для получения сведений о системе сборки мусора и для управления некоторыми аспектами сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="68dc0-104">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="68dc0-105">Начиная с платформа .NET Framework 4,5, можно использовать метод [IGCHost2:: SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) , чтобы задать размер сегмента сборки мусора и максимальный размер поколения 0 системы сборки мусора до значений, превышающих `DWORD` предельное значение, накладываемое методом [сетгкстартуплимитс](igchost-setgcstartuplimits-method.md) .</span><span class="sxs-lookup"><span data-stu-id="68dc0-105">Starting with the .NET Framework 4.5, you can use the [IGCHost2::SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](igchost-setgcstartuplimits-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="68dc0-106">Этот интерфейс предназначен только для экспертного использования.</span><span class="sxs-lookup"><span data-stu-id="68dc0-106">This interface is for expert usage only.</span></span> <span data-ttu-id="68dc0-107">Это может повлиять на производительность приложения при неправильном использовании.</span><span class="sxs-lookup"><span data-stu-id="68dc0-107">It can affect the performance of an application if used improperly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="68dc0-108">Методы</span><span class="sxs-lookup"><span data-stu-id="68dc0-108">Methods</span></span>  
  
|<span data-ttu-id="68dc0-109">Метод</span><span class="sxs-lookup"><span data-stu-id="68dc0-109">Method</span></span>|<span data-ttu-id="68dc0-110">Описание</span><span class="sxs-lookup"><span data-stu-id="68dc0-110">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="68dc0-111">Метод Collect</span><span class="sxs-lookup"><span data-stu-id="68dc0-111">Collect Method</span></span>](igchost-collect-method.md)|<span data-ttu-id="68dc0-112">Принудительно выполняет сбор данных для данного поколения независимо от состояния текущей сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="68dc0-112">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>|  
|[<span data-ttu-id="68dc0-113">Метод GetStats</span><span class="sxs-lookup"><span data-stu-id="68dc0-113">GetStats Method</span></span>](igchost-getstats-method.md)|<span data-ttu-id="68dc0-114">Возвращает статистику текущего состояния системы сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="68dc0-114">Gets the statistics for the current state of the garbage collection system.</span></span>|  
|[<span data-ttu-id="68dc0-115">Метод GetThreadStats</span><span class="sxs-lookup"><span data-stu-id="68dc0-115">GetThreadStats Method</span></span>](igchost-getthreadstats-method.md)|<span data-ttu-id="68dc0-116">Возвращает статистику по потокам для сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="68dc0-116">Gets the per-thread statistics for garbage collection.</span></span>|  
|[<span data-ttu-id="68dc0-117">Метод SetGCStartupLimits</span><span class="sxs-lookup"><span data-stu-id="68dc0-117">SetGCStartupLimits Method</span></span>](igchost-setgcstartuplimits-method.md)|<span data-ttu-id="68dc0-118">Задает размер сегмента и максимальный размер для поколения 0.</span><span class="sxs-lookup"><span data-stu-id="68dc0-118">Sets the segment size and the maximum size for generation 0.</span></span>|  
|[<span data-ttu-id="68dc0-119">Метод SetVirtualMemLimit</span><span class="sxs-lookup"><span data-stu-id="68dc0-119">SetVirtualMemLimit Method</span></span>](igchost-setvirtualmemlimit-method.md)|<span data-ttu-id="68dc0-120">Задает максимальный размер виртуальной памяти среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="68dc0-120">Sets the maximum size of the runtime's virtual memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="68dc0-121">Требования</span><span class="sxs-lookup"><span data-stu-id="68dc0-121">Requirements</span></span>  

 <span data-ttu-id="68dc0-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68dc0-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68dc0-123">**Заголовок:** Гчост. idl, Гчост. h</span><span class="sxs-lookup"><span data-stu-id="68dc0-123">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="68dc0-124">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="68dc0-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="68dc0-125">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68dc0-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68dc0-126">См. также</span><span class="sxs-lookup"><span data-stu-id="68dc0-126">See also</span></span>

- [<span data-ttu-id="68dc0-127">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="68dc0-127">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="68dc0-128">Компонентный класс CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="68dc0-128">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
