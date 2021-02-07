---
description: 'Дополнительные сведения о методе: IGCHost2:: SetGCStartupLimitsEx'
title: Метод IGCHost2::SetGCStartupLimitsEx
ms.date: 03/30/2017
api_name:
- IGCHost2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2::SetGCStartupLimitsEx
helpviewer_keywords:
- IGCHost2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, IGCHost2 interface [.NET Framework hosting]
ms.assetid: bba941c2-1c57-46d3-bbf5-5fb92700c490
topic_type:
- apiref
ms.openlocfilehash: 32d3bcbb467a1a418c7123779c881c46e983edef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709312"
---
# <a name="igchost2setgcstartuplimitsex-method"></a><span data-ttu-id="ebd4c-103">Метод IGCHost2::SetGCStartupLimitsEx</span><span class="sxs-lookup"><span data-stu-id="ebd4c-103">IGCHost2::SetGCStartupLimitsEx Method</span></span>

<span data-ttu-id="ebd4c-104">Задает размер сегмента и максимальный размер для поколения 0.</span><span class="sxs-lookup"><span data-stu-id="ebd4c-104">Sets the segment size and the maximum size for generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebd4c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ebd4c-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,  
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ebd4c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ebd4c-106">Parameters</span></span>  

 `SegmentSize`  
 <span data-ttu-id="ebd4c-107">окне Размер сегмента, используемого системой сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="ebd4c-107">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="ebd4c-108">окне Максимальный размер для поколения 0.</span><span class="sxs-lookup"><span data-stu-id="ebd4c-108">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ebd4c-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="ebd4c-109">Remarks</span></span>  

 <span data-ttu-id="ebd4c-110">Значения, которые `SetGCStartupLimitsEx` задаются, можно указать только перед запуском узла.</span><span class="sxs-lookup"><span data-stu-id="ebd4c-110">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="ebd4c-111">Эти значения нельзя изменить позже.</span><span class="sxs-lookup"><span data-stu-id="ebd4c-111">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebd4c-112">Требования</span><span class="sxs-lookup"><span data-stu-id="ebd4c-112">Requirements</span></span>  

 <span data-ttu-id="ebd4c-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebd4c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebd4c-114">**Заголовок:** Гчост. idl, Гчост. h</span><span class="sxs-lookup"><span data-stu-id="ebd4c-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="ebd4c-115">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ebd4c-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ebd4c-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebd4c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebd4c-117">См. также</span><span class="sxs-lookup"><span data-stu-id="ebd4c-117">See also</span></span>

- [<span data-ttu-id="ebd4c-118">Интерфейс IGCHost2</span><span class="sxs-lookup"><span data-stu-id="ebd4c-118">IGCHost2 Interface</span></span>](igchost2-interface.md)
