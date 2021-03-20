---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Класслоадстартед'
title: Метод ICorProfilerCallback::ClassLoadStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::ClassLoadStarted method [.NET Framework profiling]
- ClassLoadStarted method [.NET Framework profiling]
ms.assetid: 9f728de8-45c2-45a5-ac4a-45660bd36ecf
topic_type:
- apiref
ms.openlocfilehash: 4950f1d806efb304a860fa6fce18f8655bdc0976
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759261"
---
# <a name="icorprofilercallbackclassloadstarted-method"></a><span data-ttu-id="47507-103">Метод ICorProfilerCallback::ClassLoadStarted</span><span class="sxs-lookup"><span data-stu-id="47507-103">ICorProfilerCallback::ClassLoadStarted Method</span></span>

<span data-ttu-id="47507-104">Уведомляет профилировщик о том, что класс загружается.</span><span class="sxs-lookup"><span data-stu-id="47507-104">Notifies the profiler that a class is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47507-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="47507-105">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47507-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="47507-106">Parameters</span></span>

<span data-ttu-id="47507-107">`classId` окне Определяет загружаемый класс.</span><span class="sxs-lookup"><span data-stu-id="47507-107">`classId` [in] Identifies the class that is being loaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="47507-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="47507-108">Remarks</span></span>  

 <span data-ttu-id="47507-109">Значение недопустимо `classId` для информационного запроса, пока не будет вызван метод [ICorProfilerCallback:: класслоадфинишед](icorprofilercallback-classloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="47507-109">The value of `classId` is not valid for an information request until the [ICorProfilerCallback::ClassLoadFinished](icorprofilercallback-classloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47507-110">Требования</span><span class="sxs-lookup"><span data-stu-id="47507-110">Requirements</span></span>  

 <span data-ttu-id="47507-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47507-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47507-112">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="47507-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="47507-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47507-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47507-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47507-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47507-115">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="47507-115">See also</span></span>

- [<span data-ttu-id="47507-116">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="47507-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
