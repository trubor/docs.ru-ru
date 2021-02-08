---
description: 'Дополнительные сведения о методе: ICorDebugThread4:: HadUnhandledException'
title: Метод ICorDebugThread4::HadUnhandledException
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.HadUnhandledException Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::HadUnhandledException
helpviewer_keywords:
- ICorDebugThread4::HadUnhandledException method [.NET Framework debugging]
- HadUnhandledException method [.NET Framework debugging]
ms.assetid: 05558daa-39e2-4c38-aeaf-e2aec4a09468
topic_type:
- apiref
ms.openlocfilehash: cd0ccdbdd68c37b5fbdbd705da7136e5d36baa60
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800933"
---
# <a name="icordebugthread4hadunhandledexception-method"></a><span data-ttu-id="74ed8-103">Метод ICorDebugThread4::HadUnhandledException</span><span class="sxs-lookup"><span data-stu-id="74ed8-103">ICorDebugThread4::HadUnhandledException Method</span></span>

<span data-ttu-id="74ed8-104">Указывает, имел ли когда-либо поток необработанное исключение.</span><span class="sxs-lookup"><span data-stu-id="74ed8-104">Indicates whether the thread has ever had an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74ed8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="74ed8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="74ed8-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="74ed8-106">Parameters</span></span>  

 `ppBlockingObjectEnum`  
 <span data-ttu-id="74ed8-107">заполняет Указатель на адрес упорядоченного перечисления структур [CorDebugBlockingObject](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="74ed8-107">[out] A pointer to the address of an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74ed8-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="74ed8-108">Return Value</span></span>  

 <span data-ttu-id="74ed8-109">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="74ed8-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="74ed8-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="74ed8-110">HRESULT</span></span>|<span data-ttu-id="74ed8-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="74ed8-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="74ed8-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="74ed8-112">S_OK</span></span>|<span data-ttu-id="74ed8-113">В потоке возникло необработанное исключение с момента его создания.</span><span class="sxs-lookup"><span data-stu-id="74ed8-113">The thread has had an unhandled exception since its creation.</span></span>|  
|<span data-ttu-id="74ed8-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="74ed8-114">S_FALSE</span></span>|<span data-ttu-id="74ed8-115">В потоке никогда не было необработанного исключения.</span><span class="sxs-lookup"><span data-stu-id="74ed8-115">The thread has never had an unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74ed8-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="74ed8-116">Remarks</span></span>  

 <span data-ttu-id="74ed8-117">Этот метод указывает, имел ли у потока когда-либо необработанное исключение.</span><span class="sxs-lookup"><span data-stu-id="74ed8-117">This method indicates whether the thread has ever had an unhandled exception.</span></span> <span data-ttu-id="74ed8-118">К моменту запуска обратного вызова необработанного исключения или инициализации собственного JIT-присоединения этот метод гарантированно возвращает S_OK.</span><span class="sxs-lookup"><span data-stu-id="74ed8-118">By the time the unhandled exception callback is triggered or native JIT-attach is initiated, this method is guaranteed to return S_OK.</span></span> <span data-ttu-id="74ed8-119">Нет никакой гарантии, что метод [ICorDebugThread. жеткуррентексцептион](icordebugthread-getcurrentexception-method.md) будет возвращать необработанное исключение; Тем не менее, если процесс еще не был продолжен после получения обратного вызова необработанного исключения или собственного JIT-присоединения.</span><span class="sxs-lookup"><span data-stu-id="74ed8-119">There is no guarantee that the [ICorDebugThread.GetCurrentException](icordebugthread-getcurrentexception-method.md) method will return the unhandled exception; however, it will if the process has not yet been continued after getting the unhandled exception callback or upon native JIT-attach.</span></span> <span data-ttu-id="74ed8-120">Кроме того, во время выполнения собственного JIT-присоединения можно (хотя маловероятно) иметь более одного потока с необработанным исключением.</span><span class="sxs-lookup"><span data-stu-id="74ed8-120">Furthermore, it is possible (although unlikely) to have more than one thread with an unhandled exception at the time native JIT-attach is triggered.</span></span> <span data-ttu-id="74ed8-121">В этом случае нет способа определить, какое исключение активировало JIT-присоединение.</span><span class="sxs-lookup"><span data-stu-id="74ed8-121">In such a case there is no way to determine which exception triggered the JIT-attach.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74ed8-122">Требования</span><span class="sxs-lookup"><span data-stu-id="74ed8-122">Requirements</span></span>  

 <span data-ttu-id="74ed8-123">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74ed8-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74ed8-124">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="74ed8-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74ed8-125">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74ed8-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74ed8-126">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74ed8-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74ed8-127">См. также</span><span class="sxs-lookup"><span data-stu-id="74ed8-127">See also</span></span>

- [<span data-ttu-id="74ed8-128">Интерфейс ICorDebugThread4</span><span class="sxs-lookup"><span data-stu-id="74ed8-128">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="74ed8-129">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="74ed8-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="74ed8-130">Отладка</span><span class="sxs-lookup"><span data-stu-id="74ed8-130">Debugging</span></span>](index.md)
