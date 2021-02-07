---
description: 'Дополнительные сведения о: интерфейс IGCHost2'
title: Интерфейс IGCHost2
ms.date: 03/30/2017
api_name:
- IGCHost2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2
helpviewer_keywords:
- IGCHost2 interface [.NET Framework hosting]
ms.assetid: e5323fa4-18ac-424d-859d-a65a550d08d9
topic_type:
- apiref
ms.openlocfilehash: e32a4894fcff3600c9385f0f559443e23b2bc307
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709325"
---
# <a name="igchost2-interface"></a><span data-ttu-id="395bd-103">Интерфейс IGCHost2</span><span class="sxs-lookup"><span data-stu-id="395bd-103">IGCHost2 Interface</span></span>

<span data-ttu-id="395bd-104">Предоставляет методы для получения сведений о системе сборки мусора и для управления некоторыми аспектами сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="395bd-104">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="395bd-105">Для новой разработки рекомендуется вместо этого использовать интерфейс [ICLRGCManager2](iclrgcmanager2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="395bd-105">For new development, we recommend that you use the [ICLRGCManager2](iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="395bd-106">Методы</span><span class="sxs-lookup"><span data-stu-id="395bd-106">Methods</span></span>  
  
|<span data-ttu-id="395bd-107">Метод</span><span class="sxs-lookup"><span data-stu-id="395bd-107">Method</span></span>|<span data-ttu-id="395bd-108">Описание</span><span class="sxs-lookup"><span data-stu-id="395bd-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="395bd-109">Метод SetGCStartupLimitsEx</span><span class="sxs-lookup"><span data-stu-id="395bd-109">SetGCStartupLimitsEx Method</span></span>](igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="395bd-110">Задает размер сегмента и максимальный размер для поколения 0.</span><span class="sxs-lookup"><span data-stu-id="395bd-110">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="395bd-111">Включает поколение 0 и размеры сегментов, превышающие `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="395bd-111">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="395bd-112">Требования</span><span class="sxs-lookup"><span data-stu-id="395bd-112">Requirements</span></span>  

 <span data-ttu-id="395bd-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="395bd-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="395bd-114">**Заголовок:** Гчост. idl, Гчост. h</span><span class="sxs-lookup"><span data-stu-id="395bd-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="395bd-115">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="395bd-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="395bd-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="395bd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="395bd-117">См. также</span><span class="sxs-lookup"><span data-stu-id="395bd-117">See also</span></span>

- [<span data-ttu-id="395bd-118">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="395bd-118">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="395bd-119">Интерфейсы размещения CLR</span><span class="sxs-lookup"><span data-stu-id="395bd-119">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="395bd-120">Компонентный класс CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="395bd-120">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
