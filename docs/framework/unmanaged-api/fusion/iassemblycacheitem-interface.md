---
description: 'Дополнительные сведения о: интерфейс IAssemblyCacheItem'
title: Интерфейс IAssemblyCacheItem
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCacheItem interface [.NET Framework fusion]
ms.assetid: ccc9387a-9f44-4f4f-bf8f-0ea6d2afa21b
topic_type:
- apiref
ms.openlocfilehash: 2dcb721f6b65ecca93262f9af2ba355d94bb774d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760874"
---
# <a name="iassemblycacheitem-interface"></a><span data-ttu-id="e7d6e-103">Интерфейс IAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="e7d6e-103">IAssemblyCacheItem Interface</span></span>

<span data-ttu-id="e7d6e-104">Представляет отдельную сборку в глобальном кэше сборок.</span><span class="sxs-lookup"><span data-stu-id="e7d6e-104">Represents a single assembly in the global assembly cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e7d6e-105">Методы</span><span class="sxs-lookup"><span data-stu-id="e7d6e-105">Methods</span></span>  
  
|<span data-ttu-id="e7d6e-106">Метод</span><span class="sxs-lookup"><span data-stu-id="e7d6e-106">Method</span></span>|<span data-ttu-id="e7d6e-107">Описание</span><span class="sxs-lookup"><span data-stu-id="e7d6e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e7d6e-108">Метод AbortItem</span><span class="sxs-lookup"><span data-stu-id="e7d6e-108">AbortItem Method</span></span>](iassemblycacheitem-abortitem-method.md)|<span data-ttu-id="e7d6e-109">Позволяет сборке в глобальном кэше сборок выполнять операции очистки до ее освобождения.</span><span class="sxs-lookup"><span data-stu-id="e7d6e-109">Allows the assembly in the global assembly cache to perform cleanup operations before it is released.</span></span>|  
|[<span data-ttu-id="e7d6e-110">Метод Commit</span><span class="sxs-lookup"><span data-stu-id="e7d6e-110">Commit Method</span></span>](iassemblycacheitem-commit-method.md)|<span data-ttu-id="e7d6e-111">Фиксирует в памяти ссылку на кэшированную сборку.</span><span class="sxs-lookup"><span data-stu-id="e7d6e-111">Commits the cached assembly reference to memory.</span></span>|  
|[<span data-ttu-id="e7d6e-112">Метод CreateStream</span><span class="sxs-lookup"><span data-stu-id="e7d6e-112">CreateStream Method</span></span>](iassemblycacheitem-createstream-method.md)|<span data-ttu-id="e7d6e-113">Создает поток с указанными именем и форматом.</span><span class="sxs-lookup"><span data-stu-id="e7d6e-113">Creates a stream with the specified name and format.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e7d6e-114">Требования</span><span class="sxs-lookup"><span data-stu-id="e7d6e-114">Requirements</span></span>  

 <span data-ttu-id="e7d6e-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7d6e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7d6e-116">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="e7d6e-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e7d6e-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7d6e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7d6e-118">См. также</span><span class="sxs-lookup"><span data-stu-id="e7d6e-118">See also</span></span>

- [<span data-ttu-id="e7d6e-119">Fusion-интерфейсы</span><span class="sxs-lookup"><span data-stu-id="e7d6e-119">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="e7d6e-120">Глобальный кэш сборок</span><span class="sxs-lookup"><span data-stu-id="e7d6e-120">Global Assembly Cache</span></span>](../../app-domains/gac.md)
- [<span data-ttu-id="e7d6e-121">Интерфейс IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="e7d6e-121">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
