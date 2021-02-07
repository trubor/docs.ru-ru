---
description: 'Дополнительные сведения о методе: метод icordebugremote::D Ебугактивепроцессекс'
title: Метод ICorDebugRemote::DebugActiveProcessEx
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.DebugActiveProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::DebugActiveProcessEx
helpviewer_keywords:
- ICorDebugRemote::DebugActiveProcessEx method [.NET Framework debugging]
- DebugActiveProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: b0df5c5d-9a2e-47bf-894c-6f8a9fe24a1f
topic_type:
- apiref
ms.openlocfilehash: ccbde152e59146bd852a5a0a2f991d10333fa9d6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717905"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a><span data-ttu-id="e68a3-103">Метод ICorDebugRemote::DebugActiveProcessEx</span><span class="sxs-lookup"><span data-stu-id="e68a3-103">ICorDebugRemote::DebugActiveProcessEx Method</span></span>

<span data-ttu-id="e68a3-104">Запускает процесс на удаленном компьютере в отладчике.</span><span class="sxs-lookup"><span data-stu-id="e68a3-104">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e68a3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e68a3-105">Syntax</span></span>  
  
```cpp  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e68a3-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e68a3-106">Parameters</span></span>  

 `pRemoteTarget`  
 <span data-ttu-id="e68a3-107">окне Указатель на [интерфейс ICorDebugRemoteTarget](icordebugremotetarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="e68a3-107">[in] Pointer to an [ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="e68a3-108">Этот параметр используется для определения компьютера, на котором выполняется процесс.</span><span class="sxs-lookup"><span data-stu-id="e68a3-108">This parameter is used to determine the machine on which the process is running.</span></span>  
  
 `id`  
 <span data-ttu-id="e68a3-109">окне Идентификатор процесса, к которому должен быть присоединен отладчик.</span><span class="sxs-lookup"><span data-stu-id="e68a3-109">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="e68a3-110">[входные] `true` значение, если отладчик должен вести себя в качестве отладчика Win32 для процесса и передавать неуправляемые обратные вызовы; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="e68a3-110">[in] `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="e68a3-111">заполняет Указатель на адрес объекта "ICorDebugProcess", который представляет процесс, к которому присоединен отладчик.</span><span class="sxs-lookup"><span data-stu-id="e68a3-111">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e68a3-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="e68a3-112">Return Value</span></span>  

 <span data-ttu-id="e68a3-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="e68a3-113">S_OK</span></span>  
 <span data-ttu-id="e68a3-114">Успешно присоединен к процессу на удаленном компьютере.</span><span class="sxs-lookup"><span data-stu-id="e68a3-114">Successfully attached to the process on the remote machine.</span></span>  
  
 <span data-ttu-id="e68a3-115">E_FAIL (или другие коды возврата E_)</span><span class="sxs-lookup"><span data-stu-id="e68a3-115">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="e68a3-116">Не удалось присоединиться к процессу на удаленном компьютере.</span><span class="sxs-lookup"><span data-stu-id="e68a3-116">Unable to attach to the process on the remote machine.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e68a3-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="e68a3-117">Remarks</span></span>  

 <span data-ttu-id="e68a3-118">Отладка в смешанном режиме не поддерживается в Silverlight.</span><span class="sxs-lookup"><span data-stu-id="e68a3-118">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e68a3-119">Требования</span><span class="sxs-lookup"><span data-stu-id="e68a3-119">Requirements</span></span>  

 <span data-ttu-id="e68a3-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e68a3-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e68a3-121">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e68a3-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e68a3-122">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e68a3-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e68a3-123">**Платформа .NET Framework версии:** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="e68a3-123">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e68a3-124">См. также</span><span class="sxs-lookup"><span data-stu-id="e68a3-124">See also</span></span>

- [<span data-ttu-id="e68a3-125">Интерфейс ICorDebugRemote</span><span class="sxs-lookup"><span data-stu-id="e68a3-125">ICorDebugRemote Interface</span></span>](icordebugremote-interface.md)
- [<span data-ttu-id="e68a3-126">Интерфейс ICorDebug</span><span class="sxs-lookup"><span data-stu-id="e68a3-126">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="e68a3-127">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="e68a3-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
