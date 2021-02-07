---
description: 'Дополнительные сведения о методе: ITypeNameFactory::P Арсетипенаме'
title: Метод ITypeNameFactory::ParseTypeName
ms.date: 03/30/2017
api_name:
- ITypeNameFactory.ParseTypeName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ParseTypeName
helpviewer_keywords:
- ITypeNameFactory::ParseTypeName method [.NET Framework hosting]
- ParseTypeName method [.NET Framework hosting]
ms.assetid: 13c9f063-371c-4911-a5e7-e1e0b88ae382
topic_type:
- apiref
ms.openlocfilehash: e0ff068dd0d095c3eed1c7a697d0c72919306996
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680204"
---
# <a name="itypenamefactoryparsetypename-method"></a><span data-ttu-id="26980-103">Метод ITypeNameFactory::ParseTypeName</span><span class="sxs-lookup"><span data-stu-id="26980-103">ITypeNameFactory::ParseTypeName Method</span></span>

<span data-ttu-id="26980-104">Этот метод поддерживает инфраструктуру .NET Framework и не предназначен для использования непосредственно из программного кода.</span><span class="sxs-lookup"><span data-stu-id="26980-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26980-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="26980-105">Syntax</span></span>  
  
```cpp  
HRESULT ParseTypeName (  
    [in]  LPCWSTR             szName,  
    [out] DWORD*              pError,  
    [out, retval] ITypeName** ppTypeName  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="26980-106">Требования</span><span class="sxs-lookup"><span data-stu-id="26980-106">Requirements</span></span>  

 <span data-ttu-id="26980-107">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26980-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26980-108">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="26980-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="26980-109">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="26980-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="26980-110">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26980-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26980-111">См. также</span><span class="sxs-lookup"><span data-stu-id="26980-111">See also</span></span>

- [<span data-ttu-id="26980-112">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="26980-112">Hosting Interfaces</span></span>](hosting-interfaces.md)
