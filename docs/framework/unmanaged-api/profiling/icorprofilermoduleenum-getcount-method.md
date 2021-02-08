---
description: 'Дополнительные сведения о методе: ICorProfilerModuleEnum:: NOCOUNT'
title: Метод ICorProfilerModuleEnum::GetCount
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.GetCount Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::GetCount
helpviewer_keywords:
- ICorProfilerModuleEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: f0a4a5e0-4689-474b-b0f4-37ca0639c918
topic_type:
- apiref
ms.openlocfilehash: efdd812795002c25aaeb7634e7a4f4e4287553e8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781393"
---
# <a name="icorprofilermoduleenumgetcount-method"></a><span data-ttu-id="8aff9-103">Метод ICorProfilerModuleEnum::GetCount</span><span class="sxs-lookup"><span data-stu-id="8aff9-103">ICorProfilerModuleEnum::GetCount Method</span></span>

<span data-ttu-id="8aff9-104">Возвращает число управляемых модулей, загруженных в приложение.</span><span class="sxs-lookup"><span data-stu-id="8aff9-104">Gets the number of managed modules that were loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8aff9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8aff9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8aff9-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8aff9-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="8aff9-107">заполняет Количество модулей среды выполнения в коллекции.</span><span class="sxs-lookup"><span data-stu-id="8aff9-107">[out] The number of runtime modules in the collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8aff9-108">Требования</span><span class="sxs-lookup"><span data-stu-id="8aff9-108">Requirements</span></span>  

 <span data-ttu-id="8aff9-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8aff9-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8aff9-110">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8aff9-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8aff9-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8aff9-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8aff9-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8aff9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aff9-113">См. также</span><span class="sxs-lookup"><span data-stu-id="8aff9-113">See also</span></span>

- [<span data-ttu-id="8aff9-114">Интерфейс ICorProfilerModuleEnum</span><span class="sxs-lookup"><span data-stu-id="8aff9-114">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="8aff9-115">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="8aff9-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
