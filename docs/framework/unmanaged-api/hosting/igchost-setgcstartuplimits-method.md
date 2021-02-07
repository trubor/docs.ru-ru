---
description: 'Дополнительные сведения о методе: IGCHost:: Сетгкстартуплимитс'
title: Метод IGCHost::SetGCStartupLimits
ms.date: 03/30/2017
api_name:
- IGCHost.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, IGCHost interface [.NET Framework hosting]
- IGCHost::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: cae53926-82ac-4d1d-b297-0bde0bd1bebb
topic_type:
- apiref
ms.openlocfilehash: 91c74d54189bbfb7e9f208e507fe6e75b7023e00
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709507"
---
# <a name="igchostsetgcstartuplimits-method"></a><span data-ttu-id="8bf75-103">Метод IGCHost::SetGCStartupLimits</span><span class="sxs-lookup"><span data-stu-id="8bf75-103">IGCHost::SetGCStartupLimits Method</span></span>

<span data-ttu-id="8bf75-104">Задает размер сегмента и максимальный размер для поколения 0.</span><span class="sxs-lookup"><span data-stu-id="8bf75-104">Sets the segment size and the maximum size for generation 0.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8bf75-105">Начиная с платформа .NET Framework 4,5 можно задать размер сегмента и максимальный размер поколения 0 в значениях, превышающих `DWORD` использование метода [IGCHost2:: SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8bf75-105">Starting with the .NET Framework 4.5, you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [IGCHost2::SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bf75-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8bf75-106">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8bf75-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="8bf75-107">Parameters</span></span>  

 `SegmentSize`  
 <span data-ttu-id="8bf75-108">окне Размер сегмента, используемого системой сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="8bf75-108">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="8bf75-109">окне Максимальный размер для поколения 0.</span><span class="sxs-lookup"><span data-stu-id="8bf75-109">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8bf75-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="8bf75-110">Remarks</span></span>  

 <span data-ttu-id="8bf75-111">`SetGCStartupLimits`Метод может быть вызван только один раз.</span><span class="sxs-lookup"><span data-stu-id="8bf75-111">The `SetGCStartupLimits` method may be called only once.</span></span> <span data-ttu-id="8bf75-112">Эти значения нельзя изменить позже.</span><span class="sxs-lookup"><span data-stu-id="8bf75-112">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bf75-113">Требования</span><span class="sxs-lookup"><span data-stu-id="8bf75-113">Requirements</span></span>  

 <span data-ttu-id="8bf75-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bf75-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bf75-115">**Заголовок:** Гчост. idl, Гчост. h</span><span class="sxs-lookup"><span data-stu-id="8bf75-115">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="8bf75-116">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8bf75-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8bf75-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bf75-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bf75-118">См. также</span><span class="sxs-lookup"><span data-stu-id="8bf75-118">See also</span></span>

- [<span data-ttu-id="8bf75-119">Интерфейс IGCHost</span><span class="sxs-lookup"><span data-stu-id="8bf75-119">IGCHost Interface</span></span>](igchost-interface.md)
