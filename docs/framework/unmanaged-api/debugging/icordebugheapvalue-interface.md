---
description: 'Дополнительные сведения о: интерфейс ICorDebugHeapValue'
title: Интерфейс ICorDebugHeapValue
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue
helpviewer_keywords:
- ICorDebugHeapValue interface [.NET Framework debugging]
ms.assetid: 1bca66db-0359-4ae8-846e-e35f7e547e8b
topic_type:
- apiref
ms.openlocfilehash: 7c65cbce530f0d1f00d8610031fb604a0118ee29
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803689"
---
# <a name="icordebugheapvalue-interface"></a><span data-ttu-id="cf150-103">Интерфейс ICorDebugHeapValue</span><span class="sxs-lookup"><span data-stu-id="cf150-103">ICorDebugHeapValue Interface</span></span>

<span data-ttu-id="cf150-104">Подкласс "ICorDebugValue", представляющий объект, собранный сборщиком мусора среды CLR.</span><span class="sxs-lookup"><span data-stu-id="cf150-104">A subclass of "ICorDebugValue" that represents an object that has been collected by the common language runtime (CLR) garbage collector.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cf150-105">Методы</span><span class="sxs-lookup"><span data-stu-id="cf150-105">Methods</span></span>  
  
|<span data-ttu-id="cf150-106">Метод</span><span class="sxs-lookup"><span data-stu-id="cf150-106">Method</span></span>|<span data-ttu-id="cf150-107">Описание</span><span class="sxs-lookup"><span data-stu-id="cf150-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cf150-108">Метод CreateRelocBreakpoint</span><span class="sxs-lookup"><span data-stu-id="cf150-108">CreateRelocBreakpoint Method</span></span>](icordebugheapvalue-createrelocbreakpoint-method.md)|<span data-ttu-id="cf150-109">Не реализован.</span><span class="sxs-lookup"><span data-stu-id="cf150-109">Not implemented.</span></span>|  
|[<span data-ttu-id="cf150-110">Метод IsValid</span><span class="sxs-lookup"><span data-stu-id="cf150-110">IsValid Method</span></span>](icordebugheapvalue-isvalid-method.md)|<span data-ttu-id="cf150-111">Возвращает значение, указывающее, является ли объект, представленный этим объектом `ICorDebugHeapValue` , допустимым или освобожденным сборщиком мусора.</span><span class="sxs-lookup"><span data-stu-id="cf150-111">Gets a value that indicates whether the object represented by this `ICorDebugHeapValue` is valid, or has been reclaimed by the garbage collector.</span></span> <span data-ttu-id="cf150-112">Этот метод не рекомендуется к использованию в платформа .NET Framework версии 2,0.</span><span class="sxs-lookup"><span data-stu-id="cf150-112">This method has been deprecated in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf150-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="cf150-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf150-114">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="cf150-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf150-115">Требования</span><span class="sxs-lookup"><span data-stu-id="cf150-115">Requirements</span></span>  

 <span data-ttu-id="cf150-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf150-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf150-117">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cf150-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf150-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf150-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf150-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf150-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf150-120">См. также</span><span class="sxs-lookup"><span data-stu-id="cf150-120">See also</span></span>

- [<span data-ttu-id="cf150-121">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="cf150-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
