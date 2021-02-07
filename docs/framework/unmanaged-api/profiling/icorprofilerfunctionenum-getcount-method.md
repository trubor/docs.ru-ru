---
description: 'Дополнительные сведения о методе: ICorProfilerFunctionEnum:: NOCOUNT'
title: Метод ICorProfilerFunctionEnum::GetCount
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.GetCount Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::GetCount
helpviewer_keywords:
- ICorProfilerFunctionEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 62ec65e3-3e9d-400b-ae61-d24b8963995b
topic_type:
- apiref
ms.openlocfilehash: a3eccfa31676636aff7379b4080bcb85a268df6c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737627"
---
# <a name="icorprofilerfunctionenumgetcount-method"></a><span data-ttu-id="04f48-103">Метод ICorProfilerFunctionEnum::GetCount</span><span class="sxs-lookup"><span data-stu-id="04f48-103">ICorProfilerFunctionEnum::GetCount Method</span></span>

<span data-ttu-id="04f48-104">Возвращает количество функций, загруженных приложением или принудительно загруженных профилировщиком.</span><span class="sxs-lookup"><span data-stu-id="04f48-104">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04f48-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="04f48-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04f48-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="04f48-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="04f48-107">заполняет Число загруженных функций.</span><span class="sxs-lookup"><span data-stu-id="04f48-107">[out] The number of functions that were loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04f48-108">Требования</span><span class="sxs-lookup"><span data-stu-id="04f48-108">Requirements</span></span>  

 <span data-ttu-id="04f48-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04f48-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04f48-110">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="04f48-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="04f48-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04f48-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04f48-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04f48-112">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04f48-113">См. также</span><span class="sxs-lookup"><span data-stu-id="04f48-113">See also</span></span>

- [<span data-ttu-id="04f48-114">Интерфейс ICorProfilerFunctionEnum</span><span class="sxs-lookup"><span data-stu-id="04f48-114">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="04f48-115">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="04f48-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
