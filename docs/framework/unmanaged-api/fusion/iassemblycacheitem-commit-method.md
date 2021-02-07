---
description: 'Дополнительные сведения о методе: IAssemblyCacheItem:: Commit'
title: Метод IAssemblyCacheItem::Commit
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem.Commit
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::Commit
helpviewer_keywords:
- IAssemblyCacheItem::Commit method [.NET Framework fusion]
- Commit method, IAssemblyCacheItem interface [.NET Framework fusion]
ms.assetid: c2321f17-f46f-4815-ae41-b28678753613
topic_type:
- apiref
ms.openlocfilehash: bd73bb9099090089e52d52009cfef309b33adc53
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760862"
---
# <a name="iassemblycacheitemcommit-method"></a><span data-ttu-id="7b1f9-103">Метод IAssemblyCacheItem::Commit</span><span class="sxs-lookup"><span data-stu-id="7b1f9-103">IAssemblyCacheItem::Commit Method</span></span>

<span data-ttu-id="7b1f9-104">Фиксирует в памяти ссылку на кэшированную сборку.</span><span class="sxs-lookup"><span data-stu-id="7b1f9-104">Commits the cached assembly reference to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b1f9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7b1f9-105">Syntax</span></span>  
  
```cpp  
HRESULT Commit (  
    [in] DWORD dwFlags,
    [out, optional] ULONG *pulDisposition  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b1f9-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7b1f9-106">Parameters</span></span>  

 `dwFlags`  
 <span data-ttu-id="7b1f9-107">окне Флаги, определенные в Fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="7b1f9-107">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="7b1f9-108">[out, необязательно] Значение, указывающее результат операции.</span><span class="sxs-lookup"><span data-stu-id="7b1f9-108">[out, optional] A value that indicates the result of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b1f9-109">Требования</span><span class="sxs-lookup"><span data-stu-id="7b1f9-109">Requirements</span></span>  

 <span data-ttu-id="7b1f9-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b1f9-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b1f9-111">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="7b1f9-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="7b1f9-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b1f9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b1f9-113">См. также</span><span class="sxs-lookup"><span data-stu-id="7b1f9-113">See also</span></span>

- [<span data-ttu-id="7b1f9-114">Интерфейс IAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="7b1f9-114">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
