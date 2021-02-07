---
description: 'Дополнительные сведения о методе IAssemblyName:: Clone'
title: Метод IAssemblyName::Clone
ms.date: 03/30/2017
api_name:
- IAssemblyName.Clone
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::Clone
helpviewer_keywords:
- Clone method, IAssemblyName interface [.NET Framework fusion]
- IAssemblyName::Clone method [.NET Framework fusion]
ms.assetid: 7b345e08-5e16-4e3d-a044-4e19d0892943
topic_type:
- apiref
ms.openlocfilehash: b1d8ba2aec73565e9f6acaa44a5ef3731baa3af9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760788"
---
# <a name="iassemblynameclone-method"></a><span data-ttu-id="90464-103">Метод IAssemblyName::Clone</span><span class="sxs-lookup"><span data-stu-id="90464-103">IAssemblyName::Clone Method</span></span>

<span data-ttu-id="90464-104">Создает неполную копию этого объекта [IAssemblyName](iassemblyname-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="90464-104">Creates a shallow copy of this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90464-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="90464-105">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] IAssemblyName **pName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90464-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="90464-106">Parameters</span></span>  

 `pName`  
 <span data-ttu-id="90464-107">заполняет Возвращенная копия этого `IAssemblyName` объекта.</span><span class="sxs-lookup"><span data-stu-id="90464-107">[out] The returned copy of this `IAssemblyName` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90464-108">Требования</span><span class="sxs-lookup"><span data-stu-id="90464-108">Requirements</span></span>  

 <span data-ttu-id="90464-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90464-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90464-110">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="90464-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="90464-111">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90464-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90464-112">См. также</span><span class="sxs-lookup"><span data-stu-id="90464-112">See also</span></span>

- [<span data-ttu-id="90464-113">Интерфейс IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="90464-113">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
