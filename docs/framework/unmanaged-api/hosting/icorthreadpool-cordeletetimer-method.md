---
description: 'Дополнительные сведения о методе: ICorThreadpool:: CorDeleteTimer'
title: Метод ICorThreadpool::CorDeleteTimer
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorDeleteTimer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorDeleteTimer
helpviewer_keywords:
- ICorThreadpool::CorDeleteTimer method [.NET Framework hosting]
- CorDeleteTimer method [.NET Framework hosting]
ms.assetid: 74847c35-7ca1-466a-b750-b25e7b03d100
topic_type:
- apiref
ms.openlocfilehash: 9096f9969702d522427640b2f881cae4aa23284d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737747"
---
# <a name="icorthreadpoolcordeletetimer-method"></a><span data-ttu-id="f2551-103">Метод ICorThreadpool::CorDeleteTimer</span><span class="sxs-lookup"><span data-stu-id="f2551-103">ICorThreadpool::CorDeleteTimer Method</span></span>

<span data-ttu-id="f2551-104">Этот метод поддерживает инфраструктуру .NET Framework и не предназначен для использования непосредственно из программного кода.</span><span class="sxs-lookup"><span data-stu-id="f2551-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2551-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f2551-105">Syntax</span></span>  
  
```cpp  
HRESULT CorDeleteTimer (  
    [in]  HANDLE Timer,  
    [in]  HANDLE CompletionEvent,  
    [out] BOOL*  result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="f2551-106">Требования</span><span class="sxs-lookup"><span data-stu-id="f2551-106">Requirements</span></span>  

 <span data-ttu-id="f2551-107">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2551-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2551-108">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f2551-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f2551-109">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f2551-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f2551-110">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2551-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2551-111">См. также</span><span class="sxs-lookup"><span data-stu-id="f2551-111">See also</span></span>

- [<span data-ttu-id="f2551-112">Интерфейс ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="f2551-112">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
