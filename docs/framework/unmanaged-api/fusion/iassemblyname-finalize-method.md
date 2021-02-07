---
description: 'Дополнительные сведения о методе IAssemblyName:: Finalize'
title: Метод IAssemblyName::Finalize
ms.date: 03/30/2017
api_name:
- IAssemblyName.Finalize
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::Finalize
helpviewer_keywords:
- Finalize method [.NET Framework fusion]
- IAssemblyName::Finalize method [.NET Framework fusion]
ms.assetid: 610e792d-98ef-411f-90b0-5b9a3813f547
topic_type:
- apiref
ms.openlocfilehash: d6277fdbc15f6f907d5e758dac4a3670570d585d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760775"
---
# <a name="iassemblynamefinalize-method"></a><span data-ttu-id="78c1d-103">Метод IAssemblyName::Finalize</span><span class="sxs-lookup"><span data-stu-id="78c1d-103">IAssemblyName::Finalize Method</span></span>

<span data-ttu-id="78c1d-104">Позволяет этому объекту [IAssemblyName](iassemblyname-interface.md) освобождать ресурсы и выполнять другие операции очистки перед вызовом деструктора.</span><span class="sxs-lookup"><span data-stu-id="78c1d-104">Allows this [IAssemblyName](iassemblyname-interface.md) object to release resources and perform other cleanup operations before its destructor is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78c1d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="78c1d-105">Syntax</span></span>  
  
```cpp  
HRESULT Finalize ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="78c1d-106">Требования</span><span class="sxs-lookup"><span data-stu-id="78c1d-106">Requirements</span></span>  

 <span data-ttu-id="78c1d-107">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78c1d-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78c1d-108">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="78c1d-108">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="78c1d-109">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78c1d-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78c1d-110">См. также</span><span class="sxs-lookup"><span data-stu-id="78c1d-110">See also</span></span>

- [<span data-ttu-id="78c1d-111">Интерфейс IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="78c1d-111">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
