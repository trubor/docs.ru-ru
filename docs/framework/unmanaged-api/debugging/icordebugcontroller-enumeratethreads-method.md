---
description: 'Дополнительные сведения о методе: ICorDebugController:: Енумератесреадс'
title: Метод ICorDebugController::EnumerateThreads
ms.date: 03/30/2017
api_name:
- ICorDebugController.EnumerateThreads
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::EnumerateThreads
helpviewer_keywords:
- ICorDebugController::EnumerateThreads method [.NET Framework debugging]
- EnumerateThreads method [.NET Framework debugging]
ms.assetid: 73f536f6-4668-4a4a-b3e4-ac7df862d5be
topic_type:
- apiref
ms.openlocfilehash: b53425de36be5a435ef0dac538c5165f41db63f2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710781"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a><span data-ttu-id="b9041-103">Метод ICorDebugController::EnumerateThreads</span><span class="sxs-lookup"><span data-stu-id="b9041-103">ICorDebugController::EnumerateThreads Method</span></span>

<span data-ttu-id="b9041-104">Возвращает перечислитель для активных управляемых потоков в процессе.</span><span class="sxs-lookup"><span data-stu-id="b9041-104">Gets an enumerator for the active managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9041-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b9041-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9041-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b9041-106">Parameters</span></span>  

 `ppThreads`  
 <span data-ttu-id="b9041-107">заполняет Указатель на адрес объекта "Икордебугсреаденум", который представляет перечислитель для всех управляемых потоков, активных в процессе.</span><span class="sxs-lookup"><span data-stu-id="b9041-107">[out] A pointer to the address of an "ICorDebugThreadEnum" object that represents an enumerator for all managed threads that are active in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9041-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="b9041-108">Remarks</span></span>  

 <span data-ttu-id="b9041-109">Поток считается активным после отправки обратного вызова [ICorDebugManagedCallback:: CreateThread](icordebugmanagedcallback-createthread-method.md) и перед отправкой обратного вызова [ICorDebugManagedCallback:: ExitThread](icordebugmanagedcallback-exitthread-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b9041-109">A thread is considered active after the [ICorDebugManagedCallback::CreateThread](icordebugmanagedcallback-createthread-method.md) callback has been dispatched and before the [ICorDebugManagedCallback::ExitThread](icordebugmanagedcallback-exitthread-method.md) callback has been dispatched.</span></span> <span data-ttu-id="b9041-110">Управляемый поток может не обязательно содержать управляемые фреймы в своем стеке.</span><span class="sxs-lookup"><span data-stu-id="b9041-110">A managed thread may not necessarily have any managed frames on its stack.</span></span> <span data-ttu-id="b9041-111">Потоки можно перечислить даже перед обратным вызовом [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b9041-111">Threads can be enumerated even before the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="b9041-112">Перечисление естественным образом будет пустым.</span><span class="sxs-lookup"><span data-stu-id="b9041-112">The enumeration will naturally be empty.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9041-113">Требования</span><span class="sxs-lookup"><span data-stu-id="b9041-113">Requirements</span></span>  

 <span data-ttu-id="b9041-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9041-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9041-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b9041-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9041-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9041-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9041-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9041-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9041-118">См. также</span><span class="sxs-lookup"><span data-stu-id="b9041-118">See also</span></span>
