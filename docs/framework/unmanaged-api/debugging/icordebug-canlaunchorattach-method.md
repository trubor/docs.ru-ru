---
description: 'Дополнительные сведения: метод ICorDebug:: CanLaunchOrAttach'
title: Метод ICorDebug::CanLaunchOrAttach
ms.date: 03/30/2017
api_name:
- ICorDebug.CanLaunchOrAttach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CanLaunchOrAttach
helpviewer_keywords:
- ICorDebug::CanLaunchOrAttach method [.NET Framework debugging]
- CanLaunchOrAttach method [.NET Framework debugging]
ms.assetid: ca7723db-7c07-4cdd-bd92-fba34928b623
topic_type:
- apiref
ms.openlocfilehash: cb813c4bae968941de731d9d5b74d8f804b3c8ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723248"
---
# <a name="icordebugcanlaunchorattach-method"></a><span data-ttu-id="f820a-103">Метод ICorDebug::CanLaunchOrAttach</span><span class="sxs-lookup"><span data-stu-id="f820a-103">ICorDebug::CanLaunchOrAttach Method</span></span>

<span data-ttu-id="f820a-104">Возвращает значение HRESULT, указывающее, возможен ли запуск нового процесса или присоединение к указанному существующему процессу в контексте текущего компьютера и конфигурации среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="f820a-104">Returns an HRESULT that indicates whether launching a new process or attaching to the specified existing process is possible within the context of the current machine and runtime configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f820a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f820a-105">Syntax</span></span>  
  
```cpp  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f820a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f820a-106">Parameters</span></span>  

 `dwProcessId`  
 <span data-ttu-id="f820a-107">окне Идентификатор существующего процесса.</span><span class="sxs-lookup"><span data-stu-id="f820a-107">[in] The ID of an existing process.</span></span>  
  
 `win32DebuggingEnabled`  
 <span data-ttu-id="f820a-108">окне `true` Если вы планируете запустить отладку Win32 или присоединиться с включенной отладкой Win32, войдите в. в противном случае передайте `false` .</span><span class="sxs-lookup"><span data-stu-id="f820a-108">[in] Pass in `true` if you plan to launch with Win32 debugging enabled, or to attach with Win32 debugging enabled; otherwise, pass `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f820a-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="f820a-109">Return Value</span></span>  

 <span data-ttu-id="f820a-110">S_OK, если службы отладки определяют, что можно запустить новый процесс или присоединиться к заданному процессу, учитывая сведения о текущем компьютере и конфигурации среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="f820a-110">S_OK if the debugging services determine that launching a new process or attaching to the given process is possible, given the information about the current machine and runtime configuration.</span></span> <span data-ttu-id="f820a-111">Возможные значения HRESULT:</span><span class="sxs-lookup"><span data-stu-id="f820a-111">Possible HRESULT values are:</span></span>  
  
- <span data-ttu-id="f820a-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="f820a-112">S_OK</span></span>  
  
- <span data-ttu-id="f820a-113">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span><span class="sxs-lookup"><span data-stu-id="f820a-113">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span></span>  
  
- <span data-ttu-id="f820a-114">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span><span class="sxs-lookup"><span data-stu-id="f820a-114">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span></span>  
  
- <span data-ttu-id="f820a-115">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span><span class="sxs-lookup"><span data-stu-id="f820a-115">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f820a-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="f820a-116">Remarks</span></span>  

 <span data-ttu-id="f820a-117">Этот метод является исключительно информационным.</span><span class="sxs-lookup"><span data-stu-id="f820a-117">This method is purely informational.</span></span> <span data-ttu-id="f820a-118">Интерфейс не будет останавливаться при запуске или присоединении к процессу, независимо от значения, возвращаемого `CanLaunchOrAttach` .</span><span class="sxs-lookup"><span data-stu-id="f820a-118">The interface will not stop you from launching or attaching to a process, regardless of the value returned by `CanLaunchOrAttach`.</span></span>  
  
 <span data-ttu-id="f820a-119">Если планируется запуск с включенной отладкой Win32 или подключение с включенной отладкой Win32, передайте `true` `win32DebuggingEnabled` .</span><span class="sxs-lookup"><span data-stu-id="f820a-119">If you plan to launch with Win32 debugging enabled or attach with Win32 debugging enabled, pass `true` for `win32DebuggingEnabled`.</span></span> <span data-ttu-id="f820a-120">Значение HRESULT, возвращаемое, `CanLaunchOrAttach` может отличаться при использовании этого параметра.</span><span class="sxs-lookup"><span data-stu-id="f820a-120">The HRESULT returned by `CanLaunchOrAttach` might differ if you use this option.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f820a-121">Требования</span><span class="sxs-lookup"><span data-stu-id="f820a-121">Requirements</span></span>  

 <span data-ttu-id="f820a-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f820a-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f820a-123">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f820a-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f820a-124">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f820a-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f820a-125">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f820a-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f820a-126">См. также</span><span class="sxs-lookup"><span data-stu-id="f820a-126">See also</span></span>

- [<span data-ttu-id="f820a-127">Интерфейс ICorDebug</span><span class="sxs-lookup"><span data-stu-id="f820a-127">ICorDebug Interface</span></span>](icordebug-interface.md)
