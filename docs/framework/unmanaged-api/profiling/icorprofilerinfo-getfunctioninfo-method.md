---
description: 'Дополнительные сведения о методе ICorProfilerInfo:: GetFunctionInfo'
title: Метод ICorProfilerInfo::GetFunctionInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionInfo
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionInfo method [.NET Framework profiling]
- GetFunctionInfo method [.NET Framework profiling]
ms.assetid: c42b5891-019d-46b3-b551-4606295b75b8
topic_type:
- apiref
ms.openlocfilehash: e6ad1112f0e6938fc6de549d3a1d2f0901150025
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647557"
---
# <a name="icorprofilerinfogetfunctioninfo-method"></a><span data-ttu-id="91871-103">Метод ICorProfilerInfo::GetFunctionInfo</span><span class="sxs-lookup"><span data-stu-id="91871-103">ICorProfilerInfo::GetFunctionInfo Method</span></span>

<span data-ttu-id="91871-104">Возвращает родительский класс и токен метаданных для указанной функции.</span><span class="sxs-lookup"><span data-stu-id="91871-104">Gets the parent class and metadata token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91871-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="91871-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionInfo(  
    [in]  FunctionID functionId,  
    [out] ClassID    *pClassId,  
    [out] ModuleID   *pModuleId,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91871-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="91871-106">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="91871-107">окне Идентификатор функции, для которой необходимо получить родительский класс и маркер метаданных.</span><span class="sxs-lookup"><span data-stu-id="91871-107">[in] The ID of the function for which to get the parent class and metadata token.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="91871-108">[выходной] Указатель на родительский класс функции.</span><span class="sxs-lookup"><span data-stu-id="91871-108">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="91871-109">[выходной] Указатель на модуль, в котором определен родительский класс функции.</span><span class="sxs-lookup"><span data-stu-id="91871-109">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="91871-110">[выходной] Указатель на токен метаданных функции.</span><span class="sxs-lookup"><span data-stu-id="91871-110">[out] A pointer to the metadata token for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91871-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="91871-111">Remarks</span></span>  

 <span data-ttu-id="91871-112">Чтобы получить интерфейс метаданных для заданного модуля, код профилировщика может вызвать метод [ICorProfilerInfo:: жетмодулеметадата](icorprofilerinfo-getmodulemetadata-method.md) .</span><span class="sxs-lookup"><span data-stu-id="91871-112">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="91871-113">Токен метаданных, возвращенный в расположение, на которое ссылается `pToken`, можно впоследствии использовать для доступа к метаданным функции.</span><span class="sxs-lookup"><span data-stu-id="91871-113">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="91871-114">`ClassID`Функция в универсальном классе может быть недоступна без более контекстной информации об использовании функции.</span><span class="sxs-lookup"><span data-stu-id="91871-114">The `ClassID` of a function on a generic class might not be obtainable without more contextual information about the use of the function.</span></span> <span data-ttu-id="91871-115">В этом случае `pClassId` будет иметь значение 0.</span><span class="sxs-lookup"><span data-stu-id="91871-115">In this case, `pClassId` will be 0.</span></span> <span data-ttu-id="91871-116">Для предоставления большего контекста в коде профилировщика следует использовать [ICorProfilerInfo2:: GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) со значением COR_PRF_FRAME_INFO.</span><span class="sxs-lookup"><span data-stu-id="91871-116">Profiler code should use [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) with a COR_PRF_FRAME_INFO value to provide more context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91871-117">Требования</span><span class="sxs-lookup"><span data-stu-id="91871-117">Requirements</span></span>  

 <span data-ttu-id="91871-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91871-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91871-119">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="91871-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="91871-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91871-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91871-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91871-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91871-122">См. также</span><span class="sxs-lookup"><span data-stu-id="91871-122">See also</span></span>

- [<span data-ttu-id="91871-123">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="91871-123">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
