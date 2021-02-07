---
description: 'Дополнительные сведения о: интерфейс Икордебугобжектенум'
title: Интерфейс ICorDebugObjectEnum
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum
helpviewer_keywords:
- ICorDebugObjectEnum interface [.NET Framework debugging]
ms.assetid: 9ffb4498-7719-49d3-8890-df2c22248a0c
topic_type:
- apiref
ms.openlocfilehash: d5cd8580bfa81af7d644c2fb11524a43a9062ddf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722247"
---
# <a name="icordebugobjectenum-interface"></a><span data-ttu-id="3f77c-103">Интерфейс ICorDebugObjectEnum</span><span class="sxs-lookup"><span data-stu-id="3f77c-103">ICorDebugObjectEnum Interface</span></span>

<span data-ttu-id="3f77c-104">Реализует методы ICorDebugEnum и перечисляет массивы объектов по их относительным виртуальным адресам (RVA).</span><span class="sxs-lookup"><span data-stu-id="3f77c-104">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3f77c-105">Методы</span><span class="sxs-lookup"><span data-stu-id="3f77c-105">Methods</span></span>  
  
|<span data-ttu-id="3f77c-106">Метод</span><span class="sxs-lookup"><span data-stu-id="3f77c-106">Method</span></span>|<span data-ttu-id="3f77c-107">Описание</span><span class="sxs-lookup"><span data-stu-id="3f77c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3f77c-108">Следующий метод</span><span class="sxs-lookup"><span data-stu-id="3f77c-108">Next Method</span></span>](icordebugobjectenum-next-method.md)|<span data-ttu-id="3f77c-109">Возвращает RVA указанного числа объектов из перечисления, начиная с текущей позиции.</span><span class="sxs-lookup"><span data-stu-id="3f77c-109">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f77c-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="3f77c-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3f77c-111">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="3f77c-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f77c-112">Требования</span><span class="sxs-lookup"><span data-stu-id="3f77c-112">Requirements</span></span>  

 <span data-ttu-id="3f77c-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f77c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f77c-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3f77c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3f77c-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3f77c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f77c-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f77c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f77c-117">См. также</span><span class="sxs-lookup"><span data-stu-id="3f77c-117">See also</span></span>

- [<span data-ttu-id="3f77c-118">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="3f77c-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
