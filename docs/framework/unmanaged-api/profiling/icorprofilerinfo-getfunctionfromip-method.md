---
description: 'Дополнительные сведения о методе ICorProfilerInfo:: GetFunctionFromIP'
title: Метод ICorProfilerInfo::GetFunctionFromIP
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionFromIP
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionFromIP
helpviewer_keywords:
- GetFunctionFromIP method [.NET Framework profiling]
- ICorProfilerInfo::GetFunctionFromIP method [.NET Framework profiling]
ms.assetid: f069802a-198f-46dd-9f09-4f77adffc9ba
topic_type:
- apiref
ms.openlocfilehash: 1acea6943e74e65e4359c7da590d3888736dbd6c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647600"
---
# <a name="icorprofilerinfogetfunctionfromip-method"></a><span data-ttu-id="3f040-103">Метод ICorProfilerInfo::GetFunctionFromIP</span><span class="sxs-lookup"><span data-stu-id="3f040-103">ICorProfilerInfo::GetFunctionFromIP Method</span></span>

<span data-ttu-id="3f040-104">Сопоставляет указатель инструкции управляемого кода с `FunctionID` .</span><span class="sxs-lookup"><span data-stu-id="3f040-104">Maps a managed code instruction pointer to a `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f040-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3f040-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromIP(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f040-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="3f040-106">Parameters</span></span>

- `ip`

  <span data-ttu-id="3f040-107">\[in] указатель инструкций в управляемом коде.</span><span class="sxs-lookup"><span data-stu-id="3f040-107">\[in] The instruction pointer in managed code.</span></span>

- `pFunctionId`

  <span data-ttu-id="3f040-108">\[out] возвращаемый идентификатор функции.</span><span class="sxs-lookup"><span data-stu-id="3f040-108">\[out] The returned function ID.</span></span>

## <a name="requirements"></a><span data-ttu-id="3f040-109">Требования</span><span class="sxs-lookup"><span data-stu-id="3f040-109">Requirements</span></span>  

 <span data-ttu-id="3f040-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f040-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f040-111">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3f040-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3f040-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3f040-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f040-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f040-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f040-114">См. также</span><span class="sxs-lookup"><span data-stu-id="3f040-114">See also</span></span>

- [<span data-ttu-id="3f040-115">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="3f040-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
