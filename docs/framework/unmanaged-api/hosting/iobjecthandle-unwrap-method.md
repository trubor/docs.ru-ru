---
description: 'Дополнительные сведения о методе: Иобжександле:: Unwrap'
title: Метод IObjectHandle::Unwrap
ms.date: 03/30/2017
api_name:
- IObjectHandle.Unwrap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Unwrap
helpviewer_keywords:
- Unwrap method [.NET Framework hosting]
- IObjectHandle::Unwrap method [.NET Framework hosting]
ms.assetid: 794c6f8e-ed58-416b-b756-e864f2c958f7
topic_type:
- apiref
ms.openlocfilehash: 3f791eaf52abd045d495fe15e868423e464fd27e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728331"
---
# <a name="iobjecthandleunwrap-method"></a><span data-ttu-id="1b4cb-103">Метод IObjectHandle::Unwrap</span><span class="sxs-lookup"><span data-stu-id="1b4cb-103">IObjectHandle::Unwrap Method</span></span>

<span data-ttu-id="1b4cb-104">Распаковывает объект по значению из косвенного обращения.</span><span class="sxs-lookup"><span data-stu-id="1b4cb-104">Unwraps a marshal-by-value object from indirection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b4cb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1b4cb-105">Syntax</span></span>  
  
```cpp  
HRESULT Unwrap (  
    [out, retval] VARIANT *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b4cb-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1b4cb-106">Parameters</span></span>  

 `ppv`  
 <span data-ttu-id="1b4cb-107">заполняет Указатель на объект, который необходимо распаковать.</span><span class="sxs-lookup"><span data-stu-id="1b4cb-107">[out] A pointer to the object to be unwrapped.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b4cb-108">Требования</span><span class="sxs-lookup"><span data-stu-id="1b4cb-108">Requirements</span></span>  

 <span data-ttu-id="1b4cb-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b4cb-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b4cb-110">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1b4cb-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1b4cb-111">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1b4cb-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1b4cb-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b4cb-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
