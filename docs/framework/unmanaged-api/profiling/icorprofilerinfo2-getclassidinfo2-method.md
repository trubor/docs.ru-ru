---
description: 'Дополнительные сведения о методе: ICorProfilerInfo2:: GetClassIDInfo2'
title: Метод ICorProfilerInfo2::GetClassIDInfo2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassIDInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassIDInfo2
helpviewer_keywords:
- GetClassIDInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassIDInfo2 method [.NET Framework profiling]
ms.assetid: 0141d582-d066-4d49-8d1f-ae82129a1960
topic_type:
- apiref
ms.openlocfilehash: 44ef38b5f50da0f0aea045bd755614e00dae8c22
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760524"
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a><span data-ttu-id="24ca8-103">Метод ICorProfilerInfo2::GetClassIDInfo2</span><span class="sxs-lookup"><span data-stu-id="24ca8-103">ICorProfilerInfo2::GetClassIDInfo2 Method</span></span>

<span data-ttu-id="24ca8-104">Возвращает родительский модуль и маркер метаданных для открытого универсального определения указанного класса, `ClassID` родительского класса и `ClassID` для каждого аргумента типа, если он имеется, класса.</span><span class="sxs-lookup"><span data-stu-id="24ca8-104">Gets the parent module and metadata token for the open generic definition of the specified class, the `ClassID` of its parent class, and the `ClassID` for each type argument, if present, of the class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24ca8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="24ca8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetClassIDInfo2(  
    [in]  ClassID classId,  
    [out] ModuleID *pModuleId,  
    [out] mdTypeDef *pTypeDefToken,  
    [out] ClassID *pParentClassId,  
    [in]  ULONG32 cNumTypeArgs,  
    [out] ULONG32 *pcNumTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24ca8-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="24ca8-106">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="24ca8-107">[in] Идентификатор класса, для которого будут извлекаться сведения.</span><span class="sxs-lookup"><span data-stu-id="24ca8-107">[in] The ID of the class for which information will be retrieved.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="24ca8-108">заполняет Указатель на идентификатор родительского модуля для открытого универсального определения указанного класса.</span><span class="sxs-lookup"><span data-stu-id="24ca8-108">[out] Pointer to the ID of the parent module for the open generic definition of the specified class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="24ca8-109">заполняет Указатель на маркер метаданных для открытого универсального определения указанного класса.</span><span class="sxs-lookup"><span data-stu-id="24ca8-109">[out] Pointer to the metadata token for the open generic definition of the specified class.</span></span>  
  
 `pParentClassId`  
 <span data-ttu-id="24ca8-110">[out] Указатель на идентификатор родительского класса.</span><span class="sxs-lookup"><span data-stu-id="24ca8-110">[out] Pointer to the ID of the parent class.</span></span>  
  
 `cNumTypeArgs`  
 <span data-ttu-id="24ca8-111">[in] Размер массива `typeArgs`.</span><span class="sxs-lookup"><span data-stu-id="24ca8-111">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcNumTypeArgs`  
 <span data-ttu-id="24ca8-112">[out] Указатель на общее число доступных элементов.</span><span class="sxs-lookup"><span data-stu-id="24ca8-112">[out] Pointer to the total number of available elements.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="24ca8-113">[out] Массив значений `ClassID`, каждое из которых представляет идентификатор аргумента типа класса.</span><span class="sxs-lookup"><span data-stu-id="24ca8-113">[out] An array of `ClassID` values, each of which represents the ID of a type argument of the class.</span></span> <span data-ttu-id="24ca8-114">При возврате метода в массиве `typeArgs` будут содержаться все или некоторые доступные значения `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="24ca8-114">When the method returns, `typeArgs` will contain some or all the available `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24ca8-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="24ca8-115">Remarks</span></span>  

 <span data-ttu-id="24ca8-116">`GetClassIDInfo2`Метод аналогичен методу [ICorProfilerInfo:: жетклассидинфо](icorprofilerinfo-getclassidinfo-method.md) , но `GetClassIDInfo2` получает дополнительные сведения о универсальном типе.</span><span class="sxs-lookup"><span data-stu-id="24ca8-116">The `GetClassIDInfo2` method is similar to the [ICorProfilerInfo::GetClassIDInfo](icorprofilerinfo-getclassidinfo-method.md) method, but `GetClassIDInfo2` obtains additional information about a generic type.</span></span>  
  
 <span data-ttu-id="24ca8-117">Чтобы получить интерфейс [метаданных](../metadata/index.md) для заданного модуля, код профилировщика может вызвать метод [ICorProfilerInfo:: жетмодулеметадата](icorprofilerinfo-getmodulemetadata-method.md) .</span><span class="sxs-lookup"><span data-stu-id="24ca8-117">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="24ca8-118">Токен метаданных, возвращенный в расположение, на которое ссылается `pTypeDefToken`, можно впоследствии использовать для доступа к метаданным класса.</span><span class="sxs-lookup"><span data-stu-id="24ca8-118">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="24ca8-119">После возврата метода `GetClassIDInfo2` необходимо убедиться, что буфер `typeArgs` был достаточно велик, чтобы вместить в себя все значения `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="24ca8-119">After `GetClassIDInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="24ca8-120">Для этого сравните значение, на которое указывает параметр `pcNumTypeArgs`, со значением параметра `cNumTypeArgs`.</span><span class="sxs-lookup"><span data-stu-id="24ca8-120">To do this, compare the value that `pcNumTypeArgs` points to with the value of the `cNumTypeArgs` parameter.</span></span> <span data-ttu-id="24ca8-121">Если параметр `pcNumTypeArgs` указывает на значение, превышающее значение `cNumTypeArgs`, выделите буфер `typeArgs` большего размера, обновите параметр `cNumTypeArgs`, задав новый, больший размер, и вызовите метод `GetClassIDInfo2` снова.</span><span class="sxs-lookup"><span data-stu-id="24ca8-121">If `pcNumTypeArgs` points to a value that is larger than `cNumTypeArgs`, allocate a larger `typeArgs` buffer, update `cNumTypeArgs` with the new, larger size, and call `GetClassIDInfo2` again.</span></span>  
  
 <span data-ttu-id="24ca8-122">Кроме того, сначала можно вызвать метод `GetClassIDInfo2` с буфером `typeArgs` нулевой длины для получения правильного размера буфера.</span><span class="sxs-lookup"><span data-stu-id="24ca8-122">Alternatively, you can first call `GetClassIDInfo2` with a zero-length `typeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="24ca8-123">Затем можно задать размер буфера `typeArgs` равным значению, возвращенному в параметре `pcNumTypeArgs`, и вызвать метод `GetClassIDInfo2` снова.</span><span class="sxs-lookup"><span data-stu-id="24ca8-123">You can then set the `typeArgs` buffer size to the value returned in `pcNumTypeArgs` and call `GetClassIDInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24ca8-124">Требования</span><span class="sxs-lookup"><span data-stu-id="24ca8-124">Requirements</span></span>  

 <span data-ttu-id="24ca8-125">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24ca8-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24ca8-126">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="24ca8-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="24ca8-127">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24ca8-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24ca8-128">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24ca8-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24ca8-129">См. также</span><span class="sxs-lookup"><span data-stu-id="24ca8-129">See also</span></span>

- [<span data-ttu-id="24ca8-130">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="24ca8-130">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="24ca8-131">Интерфейс ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="24ca8-131">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
- [<span data-ttu-id="24ca8-132">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="24ca8-132">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="24ca8-133">Профилирование</span><span class="sxs-lookup"><span data-stu-id="24ca8-133">Profiling</span></span>](index.md)
