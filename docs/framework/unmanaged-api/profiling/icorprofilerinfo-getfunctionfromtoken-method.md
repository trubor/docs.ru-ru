---
description: 'Дополнительные сведения о методе ICorProfilerInfo:: Жетфунктионфромтокен'
title: Метод ICorProfilerInfo::GetFunctionFromToken
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionFromToken
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionFromToken method [.NET Framework profiling]
- GetFunctionFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0eed759f-cce8-405d-88dc-9ee293a38928
topic_type:
- apiref
ms.openlocfilehash: 58dea413539d6e3a625f515aa7e8d5123152c90a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647457"
---
# <a name="icorprofilerinfogetfunctionfromtoken-method"></a><span data-ttu-id="d9187-103">Метод ICorProfilerInfo::GetFunctionFromToken</span><span class="sxs-lookup"><span data-stu-id="d9187-103">ICorProfilerInfo::GetFunctionFromToken Method</span></span>

<span data-ttu-id="d9187-104">Возвращает идентификатор функции.</span><span class="sxs-lookup"><span data-stu-id="d9187-104">Gets the ID of a function.</span></span> <span data-ttu-id="d9187-105">Этот метод является устаревшим в платформа .NET Framework версии 2,0.</span><span class="sxs-lookup"><span data-stu-id="d9187-105">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="d9187-106">Используйте вместо этого метод [ICorProfilerInfo2:: жетфунктионфромтокенандтипеаргс](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d9187-106">Use the [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9187-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d9187-107">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in]  ModuleID   moduleId,  
    [in]  mdToken    token,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="remarks"></a><span data-ttu-id="d9187-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="d9187-108">Remarks</span></span>  

 <span data-ttu-id="d9187-109">`GetFunctionFromToken`Метод не будет работать для универсальных функций или функций в универсальных типах. Теперь он устарел.</span><span class="sxs-lookup"><span data-stu-id="d9187-109">The `GetFunctionFromToken` method will not work for generic functions or functions in generic types; it is now obsolete.</span></span> <span data-ttu-id="d9187-110">Используется `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` для всех функций.</span><span class="sxs-lookup"><span data-stu-id="d9187-110">Use `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` for all functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9187-111">Требования</span><span class="sxs-lookup"><span data-stu-id="d9187-111">Requirements</span></span>  

 <span data-ttu-id="d9187-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9187-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9187-113">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d9187-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d9187-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9187-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9187-115">**Платформа .NET Framework версии:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="d9187-115">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9187-116">См. также</span><span class="sxs-lookup"><span data-stu-id="d9187-116">See also</span></span>

- [<span data-ttu-id="d9187-117">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="d9187-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
