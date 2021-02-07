---
description: 'Дополнительные сведения о методе: IGCHost:: забрать'
title: Метод IGCHost::Collect
ms.date: 03/30/2017
api_name:
- IGCHost.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Collect
helpviewer_keywords:
- Collect method, IGCHost interface [.NET Framework hosting]
- IGCHost::Collect method [.NET Framework hosting]
ms.assetid: fc7d9448-3186-494d-9f0d-ea39717e9a82
topic_type:
- apiref
ms.openlocfilehash: b4c249e07709dc443ae7dd6c6a5bfd206b7f1caa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709702"
---
# <a name="igchostcollect-method"></a><span data-ttu-id="f3fc4-103">Метод IGCHost::Collect</span><span class="sxs-lookup"><span data-stu-id="f3fc4-103">IGCHost::Collect Method</span></span>

<span data-ttu-id="f3fc4-104">Принудительно выполняет сбор данных для данного поколения независимо от состояния текущей сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="f3fc4-104">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3fc4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f3fc4-105">Syntax</span></span>  
  
```cpp  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3fc4-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f3fc4-106">Parameters</span></span>  

 `Generation`  
 <span data-ttu-id="f3fc4-107">окне Поколение, на котором выполняется сборка мусора.</span><span class="sxs-lookup"><span data-stu-id="f3fc4-107">[in] The generation on which to perform the garbage collection.</span></span> <span data-ttu-id="f3fc4-108">Значение-1 указывает, что все поколения проходят сборку мусора.</span><span class="sxs-lookup"><span data-stu-id="f3fc4-108">A value of -1 indicates that all generations will undergo a garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3fc4-109">Требования</span><span class="sxs-lookup"><span data-stu-id="f3fc4-109">Requirements</span></span>  

 <span data-ttu-id="f3fc4-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3fc4-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3fc4-111">**Заголовок:** Гчост. idl, Гчост. h</span><span class="sxs-lookup"><span data-stu-id="f3fc4-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="f3fc4-112">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f3fc4-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f3fc4-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3fc4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3fc4-114">См. также</span><span class="sxs-lookup"><span data-stu-id="f3fc4-114">See also</span></span>

- [<span data-ttu-id="f3fc4-115">Интерфейс IGCHost</span><span class="sxs-lookup"><span data-stu-id="f3fc4-115">IGCHost Interface</span></span>](igchost-interface.md)
