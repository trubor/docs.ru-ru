---
description: 'Дополнительные сведения о методе: ICorDebugHeapValue3:: Жетсреадовнингмониторлокк'
title: Метод ICorDebugHeapValue3::GetThreadOwningMonitorLock
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3.GetThreadOwningMonitorLock
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetThreadOwningMonitorLock
helpviewer_keywords:
- GetThreadOwningMonitorLock method [.NET Framework debugging]
- ICorDebugHeapValue3::GetThreadOwningMonitorLock method [.NET Framework debugging]
ms.assetid: e06fc19d-2cf4-4cad-81a3-137a68af8969
topic_type:
- apiref
ms.openlocfilehash: 9bd9e251c1e04bffd749c0569e4716d4c6fa89e5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660704"
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a><span data-ttu-id="6d42c-103">Метод ICorDebugHeapValue3::GetThreadOwningMonitorLock</span><span class="sxs-lookup"><span data-stu-id="6d42c-103">ICorDebugHeapValue3::GetThreadOwningMonitorLock Method</span></span>

<span data-ttu-id="6d42c-104">Возвращает управляемый поток, которому принадлежит блокировка монитора для этого объекта.</span><span class="sxs-lookup"><span data-stu-id="6d42c-104">Returns the managed thread that owns the monitor lock on this object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d42c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6d42c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d42c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6d42c-106">Parameters</span></span>  

 `ppThread`  
 <span data-ttu-id="6d42c-107">заполняет Управляемый поток, которому принадлежит блокировка монитора для этого объекта.</span><span class="sxs-lookup"><span data-stu-id="6d42c-107">[out] The managed thread that owns the monitor lock on this object.</span></span>  
  
 `pAcquisitionCount`  
 <span data-ttu-id="6d42c-108">заполняет Количество случаев, в течение которых этот поток должен снять блокировку, прежде чем возвратить его в качестве владельца.</span><span class="sxs-lookup"><span data-stu-id="6d42c-108">[out] The number of times this thread would have to release the lock before it returns to being unowned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d42c-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="6d42c-109">Return Value</span></span>  

 <span data-ttu-id="6d42c-110">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="6d42c-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6d42c-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6d42c-111">HRESULT</span></span>|<span data-ttu-id="6d42c-112">Описание:</span><span class="sxs-lookup"><span data-stu-id="6d42c-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6d42c-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="6d42c-113">S_OK</span></span>|<span data-ttu-id="6d42c-114">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="6d42c-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="6d42c-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="6d42c-115">S_FALSE</span></span>|<span data-ttu-id="6d42c-116">Ни один управляемый поток не владеет блокировкой монитора для этого объекта.</span><span class="sxs-lookup"><span data-stu-id="6d42c-116">No managed thread owns the monitor lock on this object.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="6d42c-117">Исключения</span><span class="sxs-lookup"><span data-stu-id="6d42c-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d42c-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="6d42c-118">Remarks</span></span>  

 <span data-ttu-id="6d42c-119">Если управляемый поток владеет блокировкой монитора для этого объекта:</span><span class="sxs-lookup"><span data-stu-id="6d42c-119">If a managed thread owns the monitor lock on this object:</span></span>  
  
- <span data-ttu-id="6d42c-120">Метод возвращает S_OK.</span><span class="sxs-lookup"><span data-stu-id="6d42c-120">The method returns S_OK.</span></span>  
  
- <span data-ttu-id="6d42c-121">Объект потока действителен до тех пор, пока поток не завершит работу.</span><span class="sxs-lookup"><span data-stu-id="6d42c-121">The thread object is valid until the thread exits.</span></span>  
  
 <span data-ttu-id="6d42c-122">Если ни один управляемый поток не владеет блокировкой монитора для этого объекта `ppThread` и `pAcquisitionCount` не изменяется, а метод возвращает S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="6d42c-122">If no managed thread owns the monitor lock on this object, `ppThread` and `pAcquisitionCount` are unchanged, and the method returns S_FALSE.</span></span>  
  
 <span data-ttu-id="6d42c-123">Если `ppThread` или не `pAcquisitionCount` является допустимым указателем, результат не определен.</span><span class="sxs-lookup"><span data-stu-id="6d42c-123">If `ppThread` or `pAcquisitionCount` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="6d42c-124">Если возникает ошибка, которая не может определить, какой поток владеет блокировкой монитора для этого объекта, метод возвращает значение HRESULT, которое указывает на сбой.</span><span class="sxs-lookup"><span data-stu-id="6d42c-124">If an error occurs such that it cannot be determined which, if any, thread owns the monitor lock on this object, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d42c-125">Требования</span><span class="sxs-lookup"><span data-stu-id="6d42c-125">Requirements</span></span>  

 <span data-ttu-id="6d42c-126">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d42c-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d42c-127">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d42c-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d42c-128">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d42c-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d42c-129">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d42c-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d42c-130">См. также</span><span class="sxs-lookup"><span data-stu-id="6d42c-130">See also</span></span>

- [<span data-ttu-id="6d42c-131">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="6d42c-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="6d42c-132">Отладка</span><span class="sxs-lookup"><span data-stu-id="6d42c-132">Debugging</span></span>](index.md)
