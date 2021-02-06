---
description: 'Дополнительные сведения о методе ICorProfilerInfo:: GetCodeInfo'
title: Метод ICorProfilerInfo::GetCodeInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCodeInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCodeInfo
helpviewer_keywords:
- GetCodeInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetCodeInfo method [.NET Framework profiling]
ms.assetid: 90140b0f-a926-4a7e-b6fa-23e05f703cce
topic_type:
- apiref
ms.openlocfilehash: e965e9c21b7add0367b08f152bf509ad6b6ed4cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647665"
---
# <a name="icorprofilerinfogetcodeinfo-method"></a><span data-ttu-id="5b423-103">Метод ICorProfilerInfo::GetCodeInfo</span><span class="sxs-lookup"><span data-stu-id="5b423-103">ICorProfilerInfo::GetCodeInfo Method</span></span>

<span data-ttu-id="5b423-104">Получает экстент машинного кода, связанного с указанным идентификатором функции.</span><span class="sxs-lookup"><span data-stu-id="5b423-104">Gets the extent of native code associated with the specified function ID.</span></span>  
  
 <span data-ttu-id="5b423-105">Этот метод устарел.</span><span class="sxs-lookup"><span data-stu-id="5b423-105">This method is obsolete.</span></span> <span data-ttu-id="5b423-106">Используйте вместо этого метод [ICorProfilerInfo2:: GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5b423-106">Use the [ICorProfilerInfo2::GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b423-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5b423-107">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b423-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="5b423-108">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="5b423-109">[in] Идентификатор функции, с которым связан машинный код.</span><span class="sxs-lookup"><span data-stu-id="5b423-109">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `pStart`  
 <span data-ttu-id="5b423-110">[out] Указатель на массив байтов, составляющих машинный код функции.</span><span class="sxs-lookup"><span data-stu-id="5b423-110">[out] A pointer to an array of bytes that compose the native code of the function.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="5b423-111">[out] Указатель на целое число, задающее размер машинного кода в байтах.</span><span class="sxs-lookup"><span data-stu-id="5b423-111">[out] A pointer to an integer that specifies the size, in bytes, of the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b423-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="5b423-112">Remarks</span></span>  

 <span data-ttu-id="5b423-113">Для оптимизации производительности среда выполнения в .NET Framework версии 2.0 разделяет предварительно скомпилированный машинный код функции на несколько областей.</span><span class="sxs-lookup"><span data-stu-id="5b423-113">To optimize performance, the runtime in the .NET Framework version 2.0 splits the precompiled, native code of a function into multiple regions.</span></span> <span data-ttu-id="5b423-114">Следовательно, метод `GetCodeInfo` является устаревшим в .NET Framework 2.0, так как он не может обработать экстент машинного кода функции.</span><span class="sxs-lookup"><span data-stu-id="5b423-114">Consequently, the `GetCodeInfo` method is obsolete in the .NET Framework 2.0 because it is unable to handle the extent of a function's native code.</span></span> <span data-ttu-id="5b423-115">Профилировщики следует переключить на использование более универсального метода `ICorProfilerInfo2::GetCodeInfo2`.</span><span class="sxs-lookup"><span data-stu-id="5b423-115">Profilers should switch to using the more general `ICorProfilerInfo2::GetCodeInfo2` method instead.</span></span>  
  
 <span data-ttu-id="5b423-116">Эта функция использует буферы, выделенные вызывающим объектом.</span><span class="sxs-lookup"><span data-stu-id="5b423-116">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b423-117">Требования</span><span class="sxs-lookup"><span data-stu-id="5b423-117">Requirements</span></span>  

 <span data-ttu-id="5b423-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b423-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b423-119">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5b423-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5b423-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b423-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b423-121">**Платформа .NET Framework версии:** 1,0</span><span class="sxs-lookup"><span data-stu-id="5b423-121">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b423-122">См. также</span><span class="sxs-lookup"><span data-stu-id="5b423-122">See also</span></span>

- [<span data-ttu-id="5b423-123">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="5b423-123">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="5b423-124">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="5b423-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="5b423-125">Профилирование</span><span class="sxs-lookup"><span data-stu-id="5b423-125">Profiling</span></span>](index.md)
