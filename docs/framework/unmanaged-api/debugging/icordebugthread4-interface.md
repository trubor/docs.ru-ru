---
description: 'Дополнительные сведения о: интерфейс ICorDebugThread4'
title: Интерфейс ICorDebugThread4
ms.date: 03/30/2017
api_name:
- ICorDebugThread4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4
helpviewer_keywords:
- ICorDebugThread4 interface [.NET Framework debugging]
ms.assetid: a8c7719a-322b-4133-8566-4c27218dc104
topic_type:
- apiref
ms.openlocfilehash: 4ad587cee81ce635df0a8917b7a6d68e60aaf0b3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800920"
---
# <a name="icordebugthread4-interface"></a><span data-ttu-id="dd9a7-103">Интерфейс ICorDebugThread4</span><span class="sxs-lookup"><span data-stu-id="dd9a7-103">ICorDebugThread4 Interface</span></span>

<span data-ttu-id="dd9a7-104">Предоставляет сведения о блокировке потока.</span><span class="sxs-lookup"><span data-stu-id="dd9a7-104">Provides thread blocking information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dd9a7-105">Методы</span><span class="sxs-lookup"><span data-stu-id="dd9a7-105">Methods</span></span>  
  
|<span data-ttu-id="dd9a7-106">Метод</span><span class="sxs-lookup"><span data-stu-id="dd9a7-106">Method</span></span>|<span data-ttu-id="dd9a7-107">Описание</span><span class="sxs-lookup"><span data-stu-id="dd9a7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dd9a7-108">Метод GetBlockingObjects</span><span class="sxs-lookup"><span data-stu-id="dd9a7-108">GetBlockingObjects Method</span></span>](icordebugthread4-getblockingobjects-method.md)|<span data-ttu-id="dd9a7-109">Предоставляет упорядоченное перечисление структур [CorDebugBlockingObject](cordebugblockingobject-structure.md) , которые предоставляют сведения о блокировке потока.</span><span class="sxs-lookup"><span data-stu-id="dd9a7-109">Provides an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>|  
|[<span data-ttu-id="dd9a7-110">Метод HadUnhandledException</span><span class="sxs-lookup"><span data-stu-id="dd9a7-110">HadUnhandledException Method</span></span>](icordebugthread4-hadunhandledexception-method.md)|<span data-ttu-id="dd9a7-111">Указывает, имел ли когда-либо поток необработанное исключение.</span><span class="sxs-lookup"><span data-stu-id="dd9a7-111">Indicates whether the thread has ever had an unhandled exception.</span></span>|  
|[<span data-ttu-id="dd9a7-112">Метод GetCurrentCustomDebuggerNotification</span><span class="sxs-lookup"><span data-stu-id="dd9a7-112">GetCurrentCustomDebuggerNotification Method</span></span>](icordebugthread4-getcurrentcustomdebuggernotification-method.md)|<span data-ttu-id="dd9a7-113">Возвращает текущий объект [ICorDebugManagedCallback3:: CustomNotification](icordebugmanagedcallback3-customnotification-method.md) в текущем потоке.</span><span class="sxs-lookup"><span data-stu-id="dd9a7-113">Gets the current [ICorDebugManagedCallback3::CustomNotification](icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd9a7-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="dd9a7-114">Remarks</span></span>  

 <span data-ttu-id="dd9a7-115">Этот интерфейс является логическим расширением интерфейсов ICorDebugThread, ICorDebugThread2 и [ICorDebugThread3](icordebugthread3-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="dd9a7-115">This interface is a logical extension of the ICorDebugThread, ICorDebugThread2, and [ICorDebugThread3](icordebugthread3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dd9a7-116">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="dd9a7-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd9a7-117">Требования</span><span class="sxs-lookup"><span data-stu-id="dd9a7-117">Requirements</span></span>  

 <span data-ttu-id="dd9a7-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd9a7-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd9a7-119">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dd9a7-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dd9a7-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd9a7-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd9a7-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd9a7-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd9a7-122">См. также</span><span class="sxs-lookup"><span data-stu-id="dd9a7-122">See also</span></span>

- [<span data-ttu-id="dd9a7-123">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="dd9a7-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="dd9a7-124">Отладка</span><span class="sxs-lookup"><span data-stu-id="dd9a7-124">Debugging</span></span>](index.md)
