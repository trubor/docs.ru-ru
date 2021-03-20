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
ms.openlocfilehash: b21b8ad10c76b2e9eaad773315122c3635845a78
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760253"
---
# <a name="icorprofilerinfogetfunctionfromip-method"></a><span data-ttu-id="0116a-103">Метод ICorProfilerInfo::GetFunctionFromIP</span><span class="sxs-lookup"><span data-stu-id="0116a-103">ICorProfilerInfo::GetFunctionFromIP Method</span></span>

<span data-ttu-id="0116a-104">Сопоставляет указатель инструкции управляемого кода с `FunctionID` .</span><span class="sxs-lookup"><span data-stu-id="0116a-104">Maps a managed code instruction pointer to a `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0116a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0116a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromIP(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0116a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0116a-106">Parameters</span></span>

<span data-ttu-id="0116a-107">`ip` окне Указатель инструкции в управляемом коде.</span><span class="sxs-lookup"><span data-stu-id="0116a-107">`ip` [in] The instruction pointer in managed code.</span></span>

<span data-ttu-id="0116a-108">`pFunctionId` заполняет Возвращаемый идентификатор функции.</span><span class="sxs-lookup"><span data-stu-id="0116a-108">`pFunctionId` [out] The returned function ID.</span></span>

## <a name="requirements"></a><span data-ttu-id="0116a-109">Требования</span><span class="sxs-lookup"><span data-stu-id="0116a-109">Requirements</span></span>  

 <span data-ttu-id="0116a-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0116a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0116a-111">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0116a-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0116a-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0116a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0116a-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0116a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0116a-114">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="0116a-114">See also</span></span>

- [<span data-ttu-id="0116a-115">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="0116a-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
