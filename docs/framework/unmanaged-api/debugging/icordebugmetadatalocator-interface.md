---
description: 'Дополнительные сведения о: интерфейс Икордебугметадаталокатор'
title: Интерфейс ICorDebugMetaDataLocator
ms.date: 03/30/2017
api_name:
- ICorDebugMetaDataLocator
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMetaDataLocator
helpviewer_keywords:
- ICorDebugMetaDataLocator interface [.NET Framework debugging]
ms.assetid: 287f5ecd-863f-4090-a615-077859f0257b
topic_type:
- apiref
ms.openlocfilehash: 7b87527d4d0b98fc97631fb47184665daaf39edb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790832"
---
# <a name="icordebugmetadatalocator-interface"></a><span data-ttu-id="69771-103">Интерфейс ICorDebugMetaDataLocator</span><span class="sxs-lookup"><span data-stu-id="69771-103">ICorDebugMetaDataLocator Interface</span></span>

<span data-ttu-id="69771-104">Предоставляет сведения о метаданных для отладчика.</span><span class="sxs-lookup"><span data-stu-id="69771-104">Provides metadata information to the debugger.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="69771-105">Методы</span><span class="sxs-lookup"><span data-stu-id="69771-105">Methods</span></span>  
  
|<span data-ttu-id="69771-106">Метод</span><span class="sxs-lookup"><span data-stu-id="69771-106">Method</span></span>|<span data-ttu-id="69771-107">Описание</span><span class="sxs-lookup"><span data-stu-id="69771-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="69771-108">Метод GetMetaData</span><span class="sxs-lookup"><span data-stu-id="69771-108">GetMetaData Method</span></span>](icordebugmetadatalocator-getmetadata-method.md)|<span data-ttu-id="69771-109">Запрашивает у отладчика возврат полного пути к модулю, метаданные которого необходимы для завершения запрошенной отладчиком операции.</span><span class="sxs-lookup"><span data-stu-id="69771-109">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69771-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="69771-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="69771-111">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="69771-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69771-112">Требования</span><span class="sxs-lookup"><span data-stu-id="69771-112">Requirements</span></span>  

 <span data-ttu-id="69771-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69771-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69771-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69771-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69771-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69771-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69771-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69771-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69771-117">См. также</span><span class="sxs-lookup"><span data-stu-id="69771-117">See also</span></span>

- [<span data-ttu-id="69771-118">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="69771-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="69771-119">Отладка</span><span class="sxs-lookup"><span data-stu-id="69771-119">Debugging</span></span>](index.md)
