---
description: 'Дополнительные сведения о методе: ICorProfilerInfo2:: GetClassLayout'
title: Метод ICorProfilerInfo2::GetClassLayout
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassLayout
helpviewer_keywords:
- ICorProfilerInfo2::GetClassLayout method [.NET Framework profiling]
- GetClassLayout method, ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: a3a36987-5666-4e2f-95b5-d0cb246502ec
topic_type:
- apiref
ms.openlocfilehash: 6b515ff84240e227914404379efcfc063c25c5a2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760496"
---
# <a name="icorprofilerinfo2getclasslayout-method"></a><span data-ttu-id="9b42e-103">Метод ICorProfilerInfo2::GetClassLayout</span><span class="sxs-lookup"><span data-stu-id="9b42e-103">ICorProfilerInfo2::GetClassLayout Method</span></span>

<span data-ttu-id="9b42e-104">Получает сведения о макете в памяти полей, определенных с помощью указанного класса.</span><span class="sxs-lookup"><span data-stu-id="9b42e-104">Gets information about the layout, in memory, of the fields defined by the specified class.</span></span> <span data-ttu-id="9b42e-105">То есть этот метод получает смещения полей класса.</span><span class="sxs-lookup"><span data-stu-id="9b42e-105">That is, this method gets the offsets of the class's fields.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b42e-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9b42e-106">Syntax</span></span>  
  
```cpp  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b42e-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="9b42e-107">Parameters</span></span>  

 `classID`  
 <span data-ttu-id="9b42e-108">[in] Идентификатор класса, для которого будет извлекаться макет.</span><span class="sxs-lookup"><span data-stu-id="9b42e-108">[in] The ID of the class for which the layout will be retrieved.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="9b42e-109">[вход, выход] Массив структур [COR_FIELD_OFFSET](../metadata/cor-field-offset-structure.md) , каждый из которых содержит токены и смещения полей класса.</span><span class="sxs-lookup"><span data-stu-id="9b42e-109">[in, out] An array of [COR_FIELD_OFFSET](../metadata/cor-field-offset-structure.md) structures, each of which contains the tokens and offsets of the class's fields.</span></span>  
  
 `cFieldOffset`  
 <span data-ttu-id="9b42e-110">[in] Размер массива `rFieldOffset`.</span><span class="sxs-lookup"><span data-stu-id="9b42e-110">[in] The size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="9b42e-111">[out] Указатель на общее число доступных элементов.</span><span class="sxs-lookup"><span data-stu-id="9b42e-111">[out] A pointer to the total number of available elements.</span></span> <span data-ttu-id="9b42e-112">Если параметр `cFieldOffset` имеет значение 0, это значение указывает число необходимых элементов.</span><span class="sxs-lookup"><span data-stu-id="9b42e-112">If `cFieldOffset` is 0, this value indicates the number of elements needed.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="9b42e-113">[out] Указатель на расположение, которое содержит размер класса в байтах.</span><span class="sxs-lookup"><span data-stu-id="9b42e-113">[out] A pointer to a location that contains the size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b42e-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="9b42e-114">Remarks</span></span>  

 <span data-ttu-id="9b42e-115">Метод `GetClassLayout` возвращает только поля, определенные самим классом.</span><span class="sxs-lookup"><span data-stu-id="9b42e-115">The `GetClassLayout` method returns only the fields defined by the class itself.</span></span> <span data-ttu-id="9b42e-116">Если в родительском классе этого класса также определены поля, профилировщик должен вызвать `GetClassLayout` в родительском классе, чтобы получить эти поля.</span><span class="sxs-lookup"><span data-stu-id="9b42e-116">If the class's parent class has defined fields as well, the profiler must call `GetClassLayout` on the parent class to obtain those fields.</span></span>  
  
 <span data-ttu-id="9b42e-117">Если вы используете метод `GetClassLayout` со строковыми классами, метод завершится с ошибкой с кодом ошибки E_INVALIDARG.</span><span class="sxs-lookup"><span data-stu-id="9b42e-117">If you use `GetClassLayout` with string classes, the method will fail with error code E_INVALIDARG.</span></span> <span data-ttu-id="9b42e-118">Чтобы получить сведения о макете строки, используйте [ICorProfilerInfo2:: GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9b42e-118">Use [ICorProfilerInfo2::GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) to get information about the layout of a string.</span></span> <span data-ttu-id="9b42e-119">Метод `GetClassLayout` также не завершится с ошибкой при его вызове с классом массива.</span><span class="sxs-lookup"><span data-stu-id="9b42e-119">`GetClassLayout` will also fail when called with an array class.</span></span>  
  
 <span data-ttu-id="9b42e-120">После возврата метода `GetClassLayout` необходимо убедиться, что буфер `rFieldOffset` был достаточно велик, чтобы вместить в себя все доступные структуры `COR_FIELD_OFFSET`.</span><span class="sxs-lookup"><span data-stu-id="9b42e-120">After `GetClassLayout` returns, you must verify that the `rFieldOffset` buffer was large enough to contain all the available `COR_FIELD_OFFSET` structures.</span></span> <span data-ttu-id="9b42e-121">Для этого нужно сравнить значение, указанное параметром `pcFieldOffset`, с размером `rFieldOffset`, деленным на размер структуры `COR_FIELD_OFFSET`.</span><span class="sxs-lookup"><span data-stu-id="9b42e-121">To do this, compare the value that `pcFieldOffset` points to with the size of `rFieldOffset` divided by the size of a `COR_FIELD_OFFSET` structure.</span></span> <span data-ttu-id="9b42e-122">Если параметр `rFieldOffset` имеет недостаточно большое значение, выделите буфер `rFieldOffset` большего размера, обновите параметр `cFieldOffset`, задав новый, больший размер, и вызовите метод `GetClassLayout` снова.</span><span class="sxs-lookup"><span data-stu-id="9b42e-122">If `rFieldOffset` is not large enough, allocate a larger `rFieldOffset` buffer, update `cFieldOffset` with the new, larger size, and call `GetClassLayout` again.</span></span>  
  
 <span data-ttu-id="9b42e-123">Кроме того, сначала можно вызвать метод `GetClassLayout` с буфером `rFieldOffset` нулевой длины для получения правильного размера буфера.</span><span class="sxs-lookup"><span data-stu-id="9b42e-123">Alternatively, you can first call `GetClassLayout` with a zero-length `rFieldOffset` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="9b42e-124">Затем можно задать размер буфера равным значению, возвращенному в параметре `pcFieldOffset`, и вызвать метод `GetClassLayout` снова.</span><span class="sxs-lookup"><span data-stu-id="9b42e-124">You can then set the buffer size to the value returned in `pcFieldOffset` and call `GetClassLayout` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b42e-125">Требования</span><span class="sxs-lookup"><span data-stu-id="9b42e-125">Requirements</span></span>  

 <span data-ttu-id="9b42e-126">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b42e-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b42e-127">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9b42e-127">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9b42e-128">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b42e-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b42e-129">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b42e-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b42e-130">См. также</span><span class="sxs-lookup"><span data-stu-id="9b42e-130">See also</span></span>

- [<span data-ttu-id="9b42e-131">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="9b42e-131">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="9b42e-132">Интерфейс ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="9b42e-132">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
- [<span data-ttu-id="9b42e-133">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="9b42e-133">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="9b42e-134">Профилирование</span><span class="sxs-lookup"><span data-stu-id="9b42e-134">Profiling</span></span>](index.md)
