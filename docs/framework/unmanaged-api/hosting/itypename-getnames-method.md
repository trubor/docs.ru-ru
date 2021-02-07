---
description: 'Дополнительные сведения о методе: ITypeName:: Names'
title: Метод ITypeName::GetNames
ms.date: 03/30/2017
api_name:
- ITypeName.GetNames
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetNames
helpviewer_keywords:
- ITypeName::GetNames method [.NET Framework hosting]
- GetNames method [.NET Framework hosting]
ms.assetid: e2a3637b-d1e9-4d93-9e9b-0555fbff793d
topic_type:
- apiref
ms.openlocfilehash: 958e24947adc02713d48f16b916c3ed669080b8e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753696"
---
# <a name="itypenamegetnames-method"></a><span data-ttu-id="314cd-103">Метод ITypeName::GetNames</span><span class="sxs-lookup"><span data-stu-id="314cd-103">ITypeName::GetNames Method</span></span>

<span data-ttu-id="314cd-104">Этот метод поддерживает инфраструктуру .NET Framework и не предназначен для использования непосредственно из программного кода.</span><span class="sxs-lookup"><span data-stu-id="314cd-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="314cd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="314cd-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNames (  
    [in] DWORD           count,  
    [out] BSTR*          rgbszNames,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="314cd-106">Требования</span><span class="sxs-lookup"><span data-stu-id="314cd-106">Requirements</span></span>  

 <span data-ttu-id="314cd-107">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="314cd-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="314cd-108">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="314cd-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="314cd-109">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="314cd-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="314cd-110">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="314cd-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="314cd-111">См. также</span><span class="sxs-lookup"><span data-stu-id="314cd-111">See also</span></span>

- [<span data-ttu-id="314cd-112">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="314cd-112">Hosting Interfaces</span></span>](hosting-interfaces.md)
