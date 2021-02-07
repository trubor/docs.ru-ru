---
description: 'Дополнительные сведения о методе ICorProfilerCallback:: Модулеаттачедтоассембли'
title: Метод ICorProfilerCallback::ModuleAttachedToAssembly
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleAttachedToAssembly
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly
helpviewer_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly method [.NET Framework profiling]
- ModuleAttachedToAssembly method [.NET Framework profiling]
ms.assetid: b595798a-5d40-4cac-ab4f-911c61d2c5d2
topic_type:
- apiref
ms.openlocfilehash: cc6a83188a8bdc4826232aa6ff6e416cbb8ae893
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705601"
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a><span data-ttu-id="8d73e-103">Метод ICorProfilerCallback::ModuleAttachedToAssembly</span><span class="sxs-lookup"><span data-stu-id="8d73e-103">ICorProfilerCallback::ModuleAttachedToAssembly Method</span></span>

<span data-ttu-id="8d73e-104">Уведомляет профилировщик о том, что модуль присоединен к своей родительской сборке.</span><span class="sxs-lookup"><span data-stu-id="8d73e-104">Notifies the profiler that a module is being attached to its parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d73e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8d73e-105">Syntax</span></span>  
  
```cpp  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d73e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8d73e-106">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="8d73e-107">окне Идентификатор присоединяемого модуля.</span><span class="sxs-lookup"><span data-stu-id="8d73e-107">[in] The ID of the module that is being attached.</span></span>  
  
 `AssemblyId`  
 <span data-ttu-id="8d73e-108">окне ИДЕНТИФИКАТОР родительской сборки, к которой присоединен модуль.</span><span class="sxs-lookup"><span data-stu-id="8d73e-108">[in] The ID of the parent assembly to which the module is attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d73e-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="8d73e-109">Remarks</span></span>  

 <span data-ttu-id="8d73e-110">Модуль можно загрузить через таблицу адресов импорта (IAT), через вызов `LoadLibrary` или через ссылку на метаданные.</span><span class="sxs-lookup"><span data-stu-id="8d73e-110">A module can be loaded through an import address table (IAT), through a call to `LoadLibrary`, or through a metadata reference.</span></span> <span data-ttu-id="8d73e-111">В результате загрузчик среды CLR имеет несколько путей кода для определения сборки, в которой находится модуль.</span><span class="sxs-lookup"><span data-stu-id="8d73e-111">As a result, the common language runtime (CLR) loader has multiple code paths for determining the assembly in which a module lives.</span></span> <span data-ttu-id="8d73e-112">Таким образом, после вызова метода [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) модуль не знает, в какой сборке он находится, и получение идентификатора родительской сборки невозможно.</span><span class="sxs-lookup"><span data-stu-id="8d73e-112">Therefore, it is possible that after [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) is called, the module does not know what assembly it is in and getting the parent assembly ID is not possible.</span></span> <span data-ttu-id="8d73e-113">`ModuleAttachedToAssembly`Метод вызывается, когда модуль присоединяется к своей родительской сборке и может быть ПОЛУЧЕН идентификатор его родительской сборки.</span><span class="sxs-lookup"><span data-stu-id="8d73e-113">The `ModuleAttachedToAssembly` method is called when the module is attached to its parent assembly and its parent assembly ID can be obtained.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d73e-114">Требования</span><span class="sxs-lookup"><span data-stu-id="8d73e-114">Requirements</span></span>  

 <span data-ttu-id="8d73e-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d73e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d73e-116">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8d73e-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8d73e-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d73e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d73e-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d73e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d73e-119">См. также</span><span class="sxs-lookup"><span data-stu-id="8d73e-119">See also</span></span>

- [<span data-ttu-id="8d73e-120">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="8d73e-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
