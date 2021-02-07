---
description: 'Дополнительные сведения о методе: ICorThreadpool:: Корчанжетимер'
title: Метод ICorThreadpool::CorChangeTimer
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorChangeTimer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorChangeTimer
helpviewer_keywords:
- CorChangeTimer method [.NET Framework hosting]
- ICorThreadpool::CorChangeTimer method [.NET Framework hosting]
ms.assetid: 82b03a59-5a87-43ed-9b75-e04b256e1a46
topic_type:
- apiref
ms.openlocfilehash: 259974d7c04f0bf0b4cc6b93234b35ab2c96e2ae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672001"
---
# <a name="icorthreadpoolcorchangetimer-method"></a><span data-ttu-id="7596f-103">Метод ICorThreadpool::CorChangeTimer</span><span class="sxs-lookup"><span data-stu-id="7596f-103">ICorThreadpool::CorChangeTimer Method</span></span>

<span data-ttu-id="7596f-104">Этот метод поддерживает инфраструктуру .NET Framework и не предназначен для использования непосредственно из программного кода.</span><span class="sxs-lookup"><span data-stu-id="7596f-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7596f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7596f-105">Syntax</span></span>  
  
```cpp  
HRESULT CorChangeTimer (  
    [in]  HANDLE Timer,
    [in]  ULONG  DueTime,
    [in]  ULONG  Period,  
    [out] BOOL*  result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="7596f-106">Требования</span><span class="sxs-lookup"><span data-stu-id="7596f-106">Requirements</span></span>  

 <span data-ttu-id="7596f-107">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7596f-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7596f-108">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7596f-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7596f-109">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7596f-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7596f-110">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7596f-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7596f-111">См. также</span><span class="sxs-lookup"><span data-stu-id="7596f-111">See also</span></span>

- [<span data-ttu-id="7596f-112">Интерфейс ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="7596f-112">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
