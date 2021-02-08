---
description: 'Дополнительные сведения о методе: ICorProfilerInfo2:: Жетфунктионфромтокенандтипеаргс'
title: Метод ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetFunctionFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs
helpviewer_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
- GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: ce8f6aa6-4ebf-4a86-b429-4bbc8af41a8f
topic_type:
- apiref
ms.openlocfilehash: 4b4bb8631a5f33c939666af68226b19d2e4d666d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799041"
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a><span data-ttu-id="f1245-103">Метод ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs</span><span class="sxs-lookup"><span data-stu-id="f1245-103">ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs Method</span></span>

<span data-ttu-id="f1245-104">Возвращает объект `FunctionID` функции с помощью указанного маркера метаданных, содержащего класс, и `ClassID` значений любых аргументов типа.</span><span class="sxs-lookup"><span data-stu-id="f1245-104">Gets the `FunctionID` of a function by using the specified metadata token, containing class, and `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1245-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f1245-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdMethodDef funcDef,  
    [in] ClassID classId,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] FunctionID* pFunctionID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1245-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f1245-106">Parameters</span></span>  

 `moduleID`  
 <span data-ttu-id="f1245-107">окне Идентификатор модуля, в котором находится функция.</span><span class="sxs-lookup"><span data-stu-id="f1245-107">[in] The ID of the module in which the function resides.</span></span>  
  
 `funcDef`  
 <span data-ttu-id="f1245-108">окне `mdMethodDef` Токен метаданных, ссылающийся на функцию.</span><span class="sxs-lookup"><span data-stu-id="f1245-108">[in] An `mdMethodDef` metadata token that references the function.</span></span>  
  
 `classId`  
 <span data-ttu-id="f1245-109">окне Идентификатор содержащего класса функции.</span><span class="sxs-lookup"><span data-stu-id="f1245-109">[in] The ID of the function's containing class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="f1245-110">окне Число параметров типа для данной функции.</span><span class="sxs-lookup"><span data-stu-id="f1245-110">[in] The number of type parameters for the given function.</span></span> <span data-ttu-id="f1245-111">Для неуниверсальных функций это значение должно быть равно нулю.</span><span class="sxs-lookup"><span data-stu-id="f1245-111">This value must be zero for non-generic functions.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="f1245-112">окне Массив `ClassID` значений, каждый из которых является аргументом функции.</span><span class="sxs-lookup"><span data-stu-id="f1245-112">[in] An array of `ClassID` values, each of which is an argument of the function.</span></span> <span data-ttu-id="f1245-113">Значение `typeArgs` может быть равно null, если `cTypeArgs` имеет значение 0.</span><span class="sxs-lookup"><span data-stu-id="f1245-113">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pFunctionID`  
 <span data-ttu-id="f1245-114">заполняет Указатель на объект `FunctionID` указанной функции.</span><span class="sxs-lookup"><span data-stu-id="f1245-114">[out] A pointer to the `FunctionID` of the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1245-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="f1245-115">Remarks</span></span>  

 <span data-ttu-id="f1245-116">Вызов `GetFunctionFromTokenAndTypeArgs` метода с `mdMethodRef` метаданными вместо `mdMethodDef` токена метаданных может иметь непредсказуемые результаты.</span><span class="sxs-lookup"><span data-stu-id="f1245-116">Calling the `GetFunctionFromTokenAndTypeArgs` method with an `mdMethodRef` metadata instead of an `mdMethodDef` metadata token can have unpredictable results.</span></span> <span data-ttu-id="f1245-117">Вызывающие объекты должны разрешить объект `mdMethodRef` в `mdMethodDef` при передаче.</span><span class="sxs-lookup"><span data-stu-id="f1245-117">Callers should resolve the `mdMethodRef` to an `mdMethodDef` when passing it.</span></span>  
  
 <span data-ttu-id="f1245-118">Если функция еще не загружена, вызов `GetFunctionFromTokenAndTypeArgs` приведет к возникновению загрузки, что является опасной операцией во многих контекстах.</span><span class="sxs-lookup"><span data-stu-id="f1245-118">If the function is not already loaded, calling `GetFunctionFromTokenAndTypeArgs` will cause loading to occur, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="f1245-119">Например, вызов этого метода во время загрузки модулей или типов может привести к бесконечному циклу, так как среда выполнения пытается циклически загружать вещи.</span><span class="sxs-lookup"><span data-stu-id="f1245-119">For example, calling this method during loading of modules or types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="f1245-120">Как правило, использование параметра `GetFunctionFromTokenAndTypeArgs` не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="f1245-120">In general, use of `GetFunctionFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="f1245-121">Если профилировщики заинтересованы в событиях для определенной функции, они должны хранить и для `ModuleID` `mdMethodDef` этой функции, а также использовать [ICorProfilerInfo2:: GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) для проверки того, является ли заданная `FunctionID` функция требуемой.</span><span class="sxs-lookup"><span data-stu-id="f1245-121">If profilers are interested in events for a particular function, they should store the `ModuleID` and `mdMethodDef` of that function, and use [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) to check whether a given `FunctionID` is that of the desired function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1245-122">Требования</span><span class="sxs-lookup"><span data-stu-id="f1245-122">Requirements</span></span>  

 <span data-ttu-id="f1245-123">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1245-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1245-124">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f1245-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f1245-125">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1245-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1245-126">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1245-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1245-127">См. также</span><span class="sxs-lookup"><span data-stu-id="f1245-127">See also</span></span>

- [<span data-ttu-id="f1245-128">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="f1245-128">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="f1245-129">Интерфейс ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="f1245-129">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
