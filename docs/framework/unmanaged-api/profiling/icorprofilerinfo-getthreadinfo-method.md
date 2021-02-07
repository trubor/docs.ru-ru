---
description: 'Дополнительные сведения о методе ICorProfilerInfo:: GetThreadInfo'
title: Метод ICorProfilerInfo::GetThreadInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetThreadInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetThreadInfo
helpviewer_keywords:
- ICorProfilerInfo::GetThreadInfo method [.NET Framework profiling]
- GetThreadInfo method [.NET Framework profiling]
ms.assetid: fc994fef-65c9-432a-84cb-66c8141147e7
topic_type:
- apiref
ms.openlocfilehash: 5514b1c4860067a07bf922e9d9a8bfab8c05e218
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760554"
---
# <a name="icorprofilerinfogetthreadinfo-method"></a><span data-ttu-id="13666-103">Метод ICorProfilerInfo::GetThreadInfo</span><span class="sxs-lookup"><span data-stu-id="13666-103">ICorProfilerInfo::GetThreadInfo Method</span></span>

<span data-ttu-id="13666-104">Возвращает текущее удостоверение потока Win32 для указанного потока.</span><span class="sxs-lookup"><span data-stu-id="13666-104">Gets the current Win32 thread identity for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13666-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="13666-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadInfo(  
    [in]  ThreadID threadId,  
    [out] DWORD    *pdwWin32ThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13666-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="13666-106">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="13666-107">окне Идентификатор потока, для которого необходимо получить текущий идентификатор Win32.</span><span class="sxs-lookup"><span data-stu-id="13666-107">[in] The ID of the thread for which to get the current Win32 ID.</span></span>  
  
 `pdwWin32ThreadId`  
 <span data-ttu-id="13666-108">заполняет Указатель на текущий идентификатор потока Win32 указанного потока.</span><span class="sxs-lookup"><span data-stu-id="13666-108">[out] A pointer to the specified thread's current Win32 thread ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13666-109">Требования</span><span class="sxs-lookup"><span data-stu-id="13666-109">Requirements</span></span>  

 <span data-ttu-id="13666-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13666-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13666-111">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="13666-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="13666-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13666-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13666-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13666-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13666-114">См. также</span><span class="sxs-lookup"><span data-stu-id="13666-114">See also</span></span>

- [<span data-ttu-id="13666-115">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="13666-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
