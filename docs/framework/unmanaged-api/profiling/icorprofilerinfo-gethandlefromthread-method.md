---
description: 'Дополнительные сведения о методе ICorProfilerInfo:: GetHandleFromThread'
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
ms.openlocfilehash: 541a2872bc3cbbe8233e09283b9773957b0a7daf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647561"
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="2abaf-103">Метод ICorProfilerInfo::GetHandleFromThread</span><span class="sxs-lookup"><span data-stu-id="2abaf-103">ICorProfilerInfo::GetHandleFromThread Method</span></span>

<span data-ttu-id="2abaf-104">Сопоставляет идентификатор потока с обработчиком потока Win32.</span><span class="sxs-lookup"><span data-stu-id="2abaf-104">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2abaf-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2abaf-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2abaf-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="2abaf-106">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="2abaf-107">окне Идентификатор потока для сопоставления.</span><span class="sxs-lookup"><span data-stu-id="2abaf-107">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="2abaf-108">заполняет Указатель на обработчик потока Win32.</span><span class="sxs-lookup"><span data-stu-id="2abaf-108">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2abaf-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="2abaf-109">Remarks</span></span>  

 <span data-ttu-id="2abaf-110">Профилировщик должен вызвать `DuplicateHandle` функцию Win32 для этого маркера перед его использованием.</span><span class="sxs-lookup"><span data-stu-id="2abaf-110">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  

 <span data-ttu-id="2abaf-111">Маркер, возвращаемый этим методом, принадлежит среде выполнения, и профилировщик никогда не должен его закрывать.</span><span class="sxs-lookup"><span data-stu-id="2abaf-111">The handle returned from this method is owned by the runtime and the profiler should never close it.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="2abaf-112">Требования</span><span class="sxs-lookup"><span data-stu-id="2abaf-112">Requirements</span></span>  

 <span data-ttu-id="2abaf-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2abaf-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2abaf-114">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2abaf-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2abaf-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2abaf-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2abaf-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2abaf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2abaf-117">См. также</span><span class="sxs-lookup"><span data-stu-id="2abaf-117">See also</span></span>

- [<span data-ttu-id="2abaf-118">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="2abaf-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
