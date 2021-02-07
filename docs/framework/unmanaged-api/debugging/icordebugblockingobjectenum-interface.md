---
description: 'Дополнительные сведения о: интерфейс Икордебугблоккингобжектенум'
title: Интерфейс ICorDebugBlockingObjectEnum
ms.date: 03/30/2017
api_name:
- ICorDebugBlockingObjectEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBlockingObjectEnum
helpviewer_keywords:
- ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
ms.assetid: 208e5c2d-3f3f-404e-8b3c-7cccc14ddb16
topic_type:
- apiref
ms.openlocfilehash: 4f28039cb8a9bdcb376a9acf22572d29e41a2adf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754073"
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="da14c-103">Интерфейс ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="da14c-103">ICorDebugBlockingObjectEnum Interface</span></span>

<span data-ttu-id="da14c-104">Предоставляет перечислитель для списка структур [CorDebugBlockingObject](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="da14c-104">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="da14c-105">Этот интерфейс является подклассом интерфейса ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="da14c-105">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="da14c-106">Методы</span><span class="sxs-lookup"><span data-stu-id="da14c-106">Methods</span></span>  
  
|<span data-ttu-id="da14c-107">Метод</span><span class="sxs-lookup"><span data-stu-id="da14c-107">Method</span></span>|<span data-ttu-id="da14c-108">Описание</span><span class="sxs-lookup"><span data-stu-id="da14c-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="da14c-109">Следующий метод</span><span class="sxs-lookup"><span data-stu-id="da14c-109">Next Method</span></span>](icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="da14c-110">Перечисляет по списку структур [CorDebugBlockingObject](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="da14c-110">Enumerates through a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da14c-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="da14c-111">Remarks</span></span>  

 <span data-ttu-id="da14c-112">Каждая структура `CorDebugBlockingObject` представляет объект, блокирующий поток.</span><span class="sxs-lookup"><span data-stu-id="da14c-112">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="da14c-113">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="da14c-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da14c-114">Требования</span><span class="sxs-lookup"><span data-stu-id="da14c-114">Requirements</span></span>  

 <span data-ttu-id="da14c-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da14c-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da14c-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="da14c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da14c-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da14c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da14c-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da14c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da14c-119">См. также</span><span class="sxs-lookup"><span data-stu-id="da14c-119">See also</span></span>

- [<span data-ttu-id="da14c-120">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="da14c-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="da14c-121">Отладка</span><span class="sxs-lookup"><span data-stu-id="da14c-121">Debugging</span></span>](index.md)
