---
description: 'Дополнительные сведения о: интерфейс ICLRDataTarget2'
title: Интерфейс ICLRDataTarget2
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2
helpviewer_keywords:
- ICLRDataTarget2 interface [.NET Framework debugging]
ms.assetid: 94249397-861b-4294-a538-cf01466a66d3
topic_type:
- apiref
ms.openlocfilehash: 9ba6d11ea043d3b6ba85544b47e063f585854af8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794849"
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="92297-103">Интерфейс ICLRDataTarget2</span><span class="sxs-lookup"><span data-stu-id="92297-103">ICLRDataTarget2 Interface</span></span>

<span data-ttu-id="92297-104">Подкласс [ICLRDataTarget](iclrdatatarget-interface.md) , используемый уровнем служб доступа к данным для управления областями виртуальной памяти в целевом процессе.</span><span class="sxs-lookup"><span data-stu-id="92297-104">A subclass of [ICLRDataTarget](iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="92297-105">Методы</span><span class="sxs-lookup"><span data-stu-id="92297-105">Methods</span></span>  
  
|<span data-ttu-id="92297-106">Метод</span><span class="sxs-lookup"><span data-stu-id="92297-106">Method</span></span>|<span data-ttu-id="92297-107">Описание</span><span class="sxs-lookup"><span data-stu-id="92297-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="92297-108">Метод AllocVirtual</span><span class="sxs-lookup"><span data-stu-id="92297-108">AllocVirtual Method</span></span>](iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="92297-109">Выделяет память в адресном пространстве целевого процесса.</span><span class="sxs-lookup"><span data-stu-id="92297-109">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="92297-110">Метод FreeVirtual</span><span class="sxs-lookup"><span data-stu-id="92297-110">FreeVirtual Method</span></span>](iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="92297-111">Освобождает память, которая была ранее выделена в адресном пространстве целевого процесса.</span><span class="sxs-lookup"><span data-stu-id="92297-111">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92297-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="92297-112">Remarks</span></span>  

 <span data-ttu-id="92297-113">Клиент API (то есть отладчик) должен реализовывать этот интерфейс для определенного целевого процесса по мере необходимости.</span><span class="sxs-lookup"><span data-stu-id="92297-113">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="92297-114">Например, реализация активного процесса будет отличаться от реализации дампа памяти.</span><span class="sxs-lookup"><span data-stu-id="92297-114">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="92297-115">Целевой объект может не поддерживать изменение областей его памяти.</span><span class="sxs-lookup"><span data-stu-id="92297-115">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92297-116">Требования</span><span class="sxs-lookup"><span data-stu-id="92297-116">Requirements</span></span>  

 <span data-ttu-id="92297-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92297-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92297-118">**Заголовок:** Клрдата. idl, Клрдата. h</span><span class="sxs-lookup"><span data-stu-id="92297-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="92297-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92297-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92297-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92297-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92297-121">См. также</span><span class="sxs-lookup"><span data-stu-id="92297-121">See also</span></span>

- [<span data-ttu-id="92297-122">Интерфейс ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="92297-122">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
- [<span data-ttu-id="92297-123">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="92297-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
