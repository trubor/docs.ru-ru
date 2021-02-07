---
description: 'Дополнительные сведения о: интерфейс ICoreClrDebugTarget'
title: Интерфейс ICoreClrDebugTarget
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget interface
- Silverlight, remote debugging
ms.assetid: 7cfaee76-e284-4a66-a431-8e33f0f60038
topic_type:
- apiref
ms.openlocfilehash: f0ed4dd75cd1daca6e83617433b29bbaecb1dd36
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728760"
---
# <a name="icoreclrdebugtarget-interface"></a><span data-ttu-id="a7616-103">Интерфейс ICoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="a7616-103">ICoreClrDebugTarget Interface</span></span>

<span data-ttu-id="a7616-104">Предоставляет методы, управляющие счетчиком ссылок, перечисление процессов и освобождение памяти, связанной с отладчиком, который подключен к удаленному целевому объекту Macintosh Silverlight.</span><span class="sxs-lookup"><span data-stu-id="a7616-104">Provides methods that control reference counts, enumerate processes, and free the memory associated with a debugger that is attached to a remote Macintosh Silverlight target.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7616-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a7616-105">Syntax</span></span>  
  
```cpp  
class ICoreClrDebugTarget {  
      HRESULT EnumProcesses (  
          [out] DWORD*                    pcProcs,  
          [out] CoreClrDebugProcInfo**    ppProcs  
      );  
  
      HRESULT EnumRuntimes (  
      [in]  DWORD                      dwInternalProcessID,  
      [out] DWORD*                     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**  ppRuntimes  
      );  
  
      void FreeMemory (  
      [in] void*      pMemory  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a7616-106">Методы</span><span class="sxs-lookup"><span data-stu-id="a7616-106">Methods</span></span>  
  
|<span data-ttu-id="a7616-107">Метод</span><span class="sxs-lookup"><span data-stu-id="a7616-107">Method</span></span>|<span data-ttu-id="a7616-108">Описание</span><span class="sxs-lookup"><span data-stu-id="a7616-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a7616-109">Метод ICoreClrDebugTarget::EnumProcesses</span><span class="sxs-lookup"><span data-stu-id="a7616-109">ICoreClrDebugTarget::EnumProcesses Method</span></span>](icoreclrdebugtarget-enumprocesses-method.md)|<span data-ttu-id="a7616-110">Перечисляет процессы, работающие на удаленном компьютере.</span><span class="sxs-lookup"><span data-stu-id="a7616-110">Enumerates the processes that are running on a remote computer.</span></span>|  
|[<span data-ttu-id="a7616-111">Метод ICoreClrDebugTarget::EnumRuntimes</span><span class="sxs-lookup"><span data-stu-id="a7616-111">ICoreClrDebugTarget::EnumRuntimes Method</span></span>](icoreclrdebugtarget-enumruntimes-method.md)|<span data-ttu-id="a7616-112">Перечисляет общеязыковые среды выполнения (CLR) в указанном процессе на удаленном компьютере.</span><span class="sxs-lookup"><span data-stu-id="a7616-112">Enumerates the common language runtimes (CLRs) in the specified process on a remote computer.</span></span>|  
|[<span data-ttu-id="a7616-113">Метод ICoreClrDebugTarget::FreeMemory</span><span class="sxs-lookup"><span data-stu-id="a7616-113">ICoreClrDebugTarget::FreeMemory Method</span></span>](icoreclrdebugtarget-freememory-method.md)|<span data-ttu-id="a7616-114">Освобождает память, выделенную методами перечисления в этом классе.</span><span class="sxs-lookup"><span data-stu-id="a7616-114">Frees the memory that is allocated by the enumeration methods in this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7616-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="a7616-115">Remarks</span></span>  

 <span data-ttu-id="a7616-116">В настоящее время эта функция поддерживается только для отладки целевого объекта приложения на основе Silverlight, который выполняется на удаленном компьютере Macintosh.</span><span class="sxs-lookup"><span data-stu-id="a7616-116">Currently, this functionality is supported only for debugging a Silverlight-based application target that is running on a remote Macintosh computer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7616-117">Требования</span><span class="sxs-lookup"><span data-stu-id="a7616-117">Requirements</span></span>  

 <span data-ttu-id="a7616-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7616-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7616-119">**Заголовок:** Кореклрремотедебуггингинтерфацес. h</span><span class="sxs-lookup"><span data-stu-id="a7616-119">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="a7616-120">**Библиотека:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="a7616-120">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="a7616-121">**Платформа .NET Framework версии:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="a7616-121">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7616-122">См. также</span><span class="sxs-lookup"><span data-stu-id="a7616-122">See also</span></span>

- [<span data-ttu-id="a7616-123">Интерфейс ICorDebugRemoteTarget</span><span class="sxs-lookup"><span data-stu-id="a7616-123">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="a7616-124">Интерфейс ICorDebug</span><span class="sxs-lookup"><span data-stu-id="a7616-124">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="a7616-125">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="a7616-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
