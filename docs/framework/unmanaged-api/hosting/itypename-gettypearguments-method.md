---
description: 'Дополнительные сведения о методе: ITypeName:: GetTypeArguments'
title: Метод ITypeName::GetTypeArguments
ms.date: 03/30/2017
api_name:
- ITypeName.GetTypeArguments
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetTypeArguments
helpviewer_keywords:
- ITypeName::GetTypeArguments method [.NET Framework hosting]
- GetTypeArguments method [.NET Framework hosting]
ms.assetid: 638d77df-ff9c-40d9-88ee-930f5f87ada1
topic_type:
- apiref
ms.openlocfilehash: b88ffcfb856905bf891ebeafa1e6dbeda2563aaf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753667"
---
# <a name="itypenamegettypearguments-method"></a><span data-ttu-id="91433-103">Метод ITypeName::GetTypeArguments</span><span class="sxs-lookup"><span data-stu-id="91433-103">ITypeName::GetTypeArguments Method</span></span>

<span data-ttu-id="91433-104">Этот метод поддерживает инфраструктуру .NET Framework и не предназначен для использования непосредственно из программного кода.</span><span class="sxs-lookup"><span data-stu-id="91433-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91433-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="91433-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeArguments (  
    [in] DWORD           count,  
    [out] ITypeName**    rgpArguments,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="91433-106">Требования</span><span class="sxs-lookup"><span data-stu-id="91433-106">Requirements</span></span>  

 <span data-ttu-id="91433-107">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91433-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91433-108">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="91433-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="91433-109">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="91433-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="91433-110">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91433-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91433-111">См. также</span><span class="sxs-lookup"><span data-stu-id="91433-111">See also</span></span>

- [<span data-ttu-id="91433-112">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="91433-112">Hosting Interfaces</span></span>](hosting-interfaces.md)
