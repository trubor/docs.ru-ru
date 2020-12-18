---
title: Метод ICorProfilerInfo::GetHandleFromThread
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetHandleFromThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetHandleFromThread
helpviewer_keywords:
- GetHandleFromThread method [.NET Framework profiling]
- ICorProfilerInfo::GetHandleFromThread method [.NET Framework profiling]
ms.assetid: 36cdc9f5-7579-4cd2-aa36-fc05c741584c
topic_type:
- apiref
ms.openlocfilehash: 94c2c6e01e4188f1fa13c3b6a9f638d4b79a502f
ms.sourcegitcommit: 4b79862c5b41fbd86cf38f926f6a49516059f6f2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/18/2020
ms.locfileid: "97678184"
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="9a16d-102">Метод ICorProfilerInfo::GetHandleFromThread</span><span class="sxs-lookup"><span data-stu-id="9a16d-102">ICorProfilerInfo::GetHandleFromThread Method</span></span>

<span data-ttu-id="9a16d-103">Сопоставляет идентификатор потока с обработчиком потока Win32.</span><span class="sxs-lookup"><span data-stu-id="9a16d-103">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a16d-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9a16d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a16d-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="9a16d-105">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="9a16d-106">окне Идентификатор потока для сопоставления.</span><span class="sxs-lookup"><span data-stu-id="9a16d-106">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="9a16d-107">заполняет Указатель на обработчик потока Win32.</span><span class="sxs-lookup"><span data-stu-id="9a16d-107">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a16d-108">Комментарии</span><span class="sxs-lookup"><span data-stu-id="9a16d-108">Remarks</span></span>  

 <span data-ttu-id="9a16d-109">Профилировщик должен вызвать `DuplicateHandle` функцию Win32 для этого маркера перед его использованием.</span><span class="sxs-lookup"><span data-stu-id="9a16d-109">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  

 <span data-ttu-id="9a16d-110">Маркер, возвращаемый этим методом, принадлежит среде выполнения, и профилировщик никогда не должен его закрывать.</span><span class="sxs-lookup"><span data-stu-id="9a16d-110">The handle returned from this method is owned by the runtime and the profiler should never close it.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="9a16d-111">Требования</span><span class="sxs-lookup"><span data-stu-id="9a16d-111">Requirements</span></span>  

 <span data-ttu-id="9a16d-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a16d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a16d-113">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9a16d-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9a16d-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a16d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a16d-115">**.NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a16d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a16d-116">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="9a16d-116">See also</span></span>

- [<span data-ttu-id="9a16d-117">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="9a16d-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
