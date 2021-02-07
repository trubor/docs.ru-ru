---
description: 'Дополнительные сведения о методе: ITypeName:: Modifiers'
title: Метод ITypeName::GetModifiers
ms.date: 03/30/2017
api_name:
- ITypeName.GetModifiers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetModifiers
helpviewer_keywords:
- ITypeName::GetModifiers method [.NET Framework hosting]
- GetModifiers method [.NET Framework hosting]
ms.assetid: 75508c55-3e09-4135-80da-cc811003fa82
topic_type:
- apiref
ms.openlocfilehash: 3c44d569255656f95ccceec0462d09044b46679b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753722"
---
# <a name="itypenamegetmodifiers-method"></a><span data-ttu-id="9a5a8-103">Метод ITypeName::GetModifiers</span><span class="sxs-lookup"><span data-stu-id="9a5a8-103">ITypeName::GetModifiers Method</span></span>

<span data-ttu-id="9a5a8-104">Этот метод поддерживает инфраструктуру .NET Framework и не предназначен для использования непосредственно из программного кода.</span><span class="sxs-lookup"><span data-stu-id="9a5a8-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a5a8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9a5a8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetModifiers (  
    [in] DWORD           count,  
    [out] DWORD*         rgModifiers,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="9a5a8-106">Требования</span><span class="sxs-lookup"><span data-stu-id="9a5a8-106">Requirements</span></span>  

 <span data-ttu-id="9a5a8-107">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a5a8-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a5a8-108">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9a5a8-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9a5a8-109">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9a5a8-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a5a8-110">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a5a8-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a5a8-111">См. также</span><span class="sxs-lookup"><span data-stu-id="9a5a8-111">See also</span></span>

- [<span data-ttu-id="9a5a8-112">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="9a5a8-112">Hosting Interfaces</span></span>](hosting-interfaces.md)
