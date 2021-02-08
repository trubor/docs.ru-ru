---
description: 'Дополнительные сведения о: интерфейс метод icordebugremote'
title: Интерфейс ICorDebugRemote
ms.date: 03/30/2017
api_name:
- ICorDebugRemote
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemote
helpviewer_keywords:
- ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: 53d073c6-fa02-40d2-82e1-b9452bb6abaa
topic_type:
- apiref
ms.openlocfilehash: 4c9d92800c68155216a077180ea0b613c67423dd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790676"
---
# <a name="icordebugremote-interface"></a><span data-ttu-id="7ae89-103">Интерфейс ICorDebugRemote</span><span class="sxs-lookup"><span data-stu-id="7ae89-103">ICorDebugRemote Interface</span></span>

<span data-ttu-id="7ae89-104">Позволяет запускать или подключать управляемый отладчик к удаленному целевому процессу.</span><span class="sxs-lookup"><span data-stu-id="7ae89-104">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ae89-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7ae89-105">Syntax</span></span>  
  
```cpp  
interface ICorDebugRemote : IUnknown  
{  
    HRESULT CreateProcessEx  
      (  
      [in] ICorDebugRemoteTarget *     pRemoteTarget,  
      [in] LPCWSTR                     lpApplicationName,  
      [in] LPWSTR                      lpCommandLine,  
      [in] LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
      [in] LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
      [in] BOOL                        bInheritHandles,  
      [in] DWORD                       dwCreationFlags,  
      [in] PVOID                       lpEnvironment,  
      [in] LPCWSTR                     lpCurrentDirectory,  
      [in] LPSTARTUPINFOW              lpStartupInfo,  
      [in] LPPROCESS_INFORMATION       lpProcessInformation,  
      [in] CorDebugCreateProcessFlags  debuggingFlags,  
      [out] ICorDebugProcess **        ppProcess  
      );  
  
    HRESULT DebugActiveProcessEx  
      (  
      [in] ICorDebugRemoteTarget *   pRemoteTarget,  
      [in] DWORD                     dwProcessId,  
      [in] BOOL                      fWin32Attach,  
      [out] ICorDebugProcess **      ppProcess  
      );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7ae89-106">Методы</span><span class="sxs-lookup"><span data-stu-id="7ae89-106">Methods</span></span>  
  
|<span data-ttu-id="7ae89-107">Метод</span><span class="sxs-lookup"><span data-stu-id="7ae89-107">Method</span></span>|<span data-ttu-id="7ae89-108">Описание</span><span class="sxs-lookup"><span data-stu-id="7ae89-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7ae89-109">Метод ICorDebugRemote::CreateProcessEx</span><span class="sxs-lookup"><span data-stu-id="7ae89-109">ICorDebugRemote::CreateProcessEx Method</span></span>](icordebugremote-createprocessex-method.md)|<span data-ttu-id="7ae89-110">Создает процесс на удаленном компьютере для управляемой отладки.</span><span class="sxs-lookup"><span data-stu-id="7ae89-110">Creates a process on a remote machine for managed debugging.</span></span>|  
|[<span data-ttu-id="7ae89-111">Метод ICorDebugRemote::DebugActiveProcessEx</span><span class="sxs-lookup"><span data-stu-id="7ae89-111">ICorDebugRemote::DebugActiveProcessEx Method</span></span>](icordebugremote-debugactiveprocessex-method.md)|<span data-ttu-id="7ae89-112">Запускает процесс на удаленном компьютере в отладчике.</span><span class="sxs-lookup"><span data-stu-id="7ae89-112">Launches a process on a remote machine under the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ae89-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="7ae89-113">Remarks</span></span>  

 <span data-ttu-id="7ae89-114">В настоящее время эта функция поддерживается только для отладки целевого объекта приложения на основе Silverlight, который выполняется на удаленном компьютере Macintosh.</span><span class="sxs-lookup"><span data-stu-id="7ae89-114">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh machine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ae89-115">Требования</span><span class="sxs-lookup"><span data-stu-id="7ae89-115">Requirements</span></span>  

 <span data-ttu-id="7ae89-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ae89-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ae89-117">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7ae89-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7ae89-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ae89-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ae89-119">**Платформа .NET Framework версии:** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="7ae89-119">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ae89-120">См. также</span><span class="sxs-lookup"><span data-stu-id="7ae89-120">See also</span></span>

- [<span data-ttu-id="7ae89-121">Интерфейс ICorDebugRemoteTarget</span><span class="sxs-lookup"><span data-stu-id="7ae89-121">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="7ae89-122">Интерфейс ICorDebug</span><span class="sxs-lookup"><span data-stu-id="7ae89-122">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="7ae89-123">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="7ae89-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
