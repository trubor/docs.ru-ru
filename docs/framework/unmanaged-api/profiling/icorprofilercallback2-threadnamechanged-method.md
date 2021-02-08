---
description: 'Дополнительные сведения о методе: ICorProfilerCallback2:: ThreadNameChanged'
title: Метод ICorProfilerCallback2::ThreadNameChanged
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.ThreadNameChanged
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::ThreadNameChanged
helpviewer_keywords:
- ThreadNameChanged method [.NET Framework profiling]
- ICorProfilerCallback2::ThreadNameChanged method [.NET Framework profiling]
ms.assetid: c8bbd76d-a9ff-44f2-87a6-be052819da36
topic_type:
- apiref
ms.openlocfilehash: 161247f9692d1307d063e244b200eb0d8f739e9a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799048"
---
# <a name="icorprofilercallback2threadnamechanged-method"></a><span data-ttu-id="6b004-103">Метод ICorProfilerCallback2::ThreadNameChanged</span><span class="sxs-lookup"><span data-stu-id="6b004-103">ICorProfilerCallback2::ThreadNameChanged Method</span></span>

<span data-ttu-id="6b004-104">Уведомляет профилировщик кода о том, что имя потока изменилось.</span><span class="sxs-lookup"><span data-stu-id="6b004-104">Notifies the code profiler that the name of a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b004-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6b004-105">Syntax</span></span>  
  
```cpp  
HRESULT ThreadNameChanged(  
    [in] ThreadID threadId,  
    [in] ULONG cchName,  
    [in] WCHAR name[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b004-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6b004-106">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="6b004-107">окне Идентификатор потока.</span><span class="sxs-lookup"><span data-stu-id="6b004-107">[in] The ID of the thread.</span></span>  
  
 `cchName`  
 <span data-ttu-id="6b004-108">окне Длина нового имени потока.</span><span class="sxs-lookup"><span data-stu-id="6b004-108">[in] The length of the new name of the thread.</span></span>  
  
 `name`  
 <span data-ttu-id="6b004-109">окне Новое имя потока.</span><span class="sxs-lookup"><span data-stu-id="6b004-109">[in] The new name of the thread.</span></span> <span data-ttu-id="6b004-110">Имя не завершается нулем.</span><span class="sxs-lookup"><span data-stu-id="6b004-110">The name is not null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b004-111">Требования</span><span class="sxs-lookup"><span data-stu-id="6b004-111">Requirements</span></span>  

 <span data-ttu-id="6b004-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b004-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b004-113">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6b004-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6b004-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b004-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b004-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b004-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b004-116">См. также</span><span class="sxs-lookup"><span data-stu-id="6b004-116">See also</span></span>

- [<span data-ttu-id="6b004-117">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="6b004-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="6b004-118">Интерфейс ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="6b004-118">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
