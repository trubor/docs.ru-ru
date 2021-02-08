---
description: 'Дополнительные сведения о: интерфейс метод iclrdatatarget3'
title: Интерфейс ICLRDataTarget3
ms.date: 03/30/2017
api_name:
- ICLRDataTarget3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: d2711bdf-64b3-404c-a0c3-01ba4907f703
topic_type:
- apiref
ms.openlocfilehash: deea609298563e60897f9bedab9fb1e175dc7b73
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794793"
---
# <a name="iclrdatatarget3-interface"></a><span data-ttu-id="7376a-103">Интерфейс ICLRDataTarget3</span><span class="sxs-lookup"><span data-stu-id="7376a-103">ICLRDataTarget3 Interface</span></span>

<span data-ttu-id="7376a-104">Подкласс [ICLRDataTarget2](iclrdatatarget2-interface.md) , предоставляющий доступ к сведениям об исключениях.</span><span class="sxs-lookup"><span data-stu-id="7376a-104">A subclass of [ICLRDataTarget2](iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7376a-105">Методы</span><span class="sxs-lookup"><span data-stu-id="7376a-105">Methods</span></span>  
  
|<span data-ttu-id="7376a-106">Метод</span><span class="sxs-lookup"><span data-stu-id="7376a-106">Method</span></span>|<span data-ttu-id="7376a-107">Описание</span><span class="sxs-lookup"><span data-stu-id="7376a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7376a-108">Метод GetExceptionRecord</span><span class="sxs-lookup"><span data-stu-id="7376a-108">GetExceptionRecord Method</span></span>](iclrdatatarget3-getexceptionrecord-method.md)|<span data-ttu-id="7376a-109">Вызывается службами доступа к данным среды CLR для извлечения записи исключения, связанной с целевым процессом.</span><span class="sxs-lookup"><span data-stu-id="7376a-109">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span>|  
|[<span data-ttu-id="7376a-110">Метод GetExceptionContextRecord</span><span class="sxs-lookup"><span data-stu-id="7376a-110">GetExceptionContextRecord Method</span></span>](iclrdatatarget3-getexceptioncontextrecord-method.md)|<span data-ttu-id="7376a-111">Вызывается службами доступа к данным среды CLR для извлечения записи контекста, связанной с целевым процессом.</span><span class="sxs-lookup"><span data-stu-id="7376a-111">Called by the CLR data access services to retrieve the context record associated with the target process.</span></span>|  
|[<span data-ttu-id="7376a-112">Метод GetExceptionThreadID</span><span class="sxs-lookup"><span data-stu-id="7376a-112">GetExceptionThreadID Method</span></span>](iclrdatatarget3-getexceptionthreadid-method.md)|<span data-ttu-id="7376a-113">Вызывается службами доступа к данным среды CLR для получения идентификатора потока, вызвавшего исключение.</span><span class="sxs-lookup"><span data-stu-id="7376a-113">Called by the CLR data access services to get the ID of the thread that threw the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7376a-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="7376a-114">Remarks</span></span>  

 <span data-ttu-id="7376a-115">Клиент API (то есть отладчик) должен реализовывать этот интерфейс для определенного целевого процесса по мере необходимости.</span><span class="sxs-lookup"><span data-stu-id="7376a-115">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="7376a-116">Например, реализация активного процесса будет отличаться от реализации дампа памяти.</span><span class="sxs-lookup"><span data-stu-id="7376a-116">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="7376a-117">Целевой объект может не поддерживать изменение областей его памяти.</span><span class="sxs-lookup"><span data-stu-id="7376a-117">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7376a-118">Требования</span><span class="sxs-lookup"><span data-stu-id="7376a-118">Requirements</span></span>  

 <span data-ttu-id="7376a-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7376a-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7376a-120">**Заголовок:** Клрдата. idl, Клрдата. h</span><span class="sxs-lookup"><span data-stu-id="7376a-120">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="7376a-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7376a-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7376a-122">**Платформа .NET Framework версии:**[!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7376a-122">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7376a-123">См. также</span><span class="sxs-lookup"><span data-stu-id="7376a-123">See also</span></span>

- [<span data-ttu-id="7376a-124">Интерфейс ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="7376a-124">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
- [<span data-ttu-id="7376a-125">Интерфейс ICLRDataTarget2</span><span class="sxs-lookup"><span data-stu-id="7376a-125">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="7376a-126">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="7376a-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
