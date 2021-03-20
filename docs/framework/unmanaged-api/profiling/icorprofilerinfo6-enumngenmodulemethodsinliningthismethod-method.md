---
description: 'Дополнительные сведения о методе: ICorProfilerInfo6:: Енумнженмодулемесодсинлинингсисмесод'
title: Метод ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
ms.openlocfilehash: 236aaa820162dcc1d5c6c8ade1e8da78f5f4acb0
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759134"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a><span data-ttu-id="a570a-103">Метод ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod</span><span class="sxs-lookup"><span data-stu-id="a570a-103">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>

<span data-ttu-id="a570a-104">Возвращает перечислитель для всех методов, определенных в заданном модуле NGen, и встроенный метод.</span><span class="sxs-lookup"><span data-stu-id="a570a-104">Returns an enumerator to all the methods that are defined in a given NGen module and inline a given method.</span></span>

## <a name="syntax"></a><span data-ttu-id="a570a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a570a-105">Syntax</span></span>

```cpp
HRESULT EnumNgenModuleMethodsInliningThisMethod(
        [in] ModuleID inlinersModuleId,
        [in] ModuleID inlineeModuleId,
        [in] mdMethodDef inlineeMethodId,
        [out] BOOL *incompleteData,
        [out] ICorProfilerMethodEnum** ppEnum
);
```

## <a name="parameters"></a><span data-ttu-id="a570a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a570a-106">Parameters</span></span>

<span data-ttu-id="a570a-107">`inlinersModuleId` окне Идентификатор модуля NGen.</span><span class="sxs-lookup"><span data-stu-id="a570a-107">`inlinersModuleId` [in] The identifier of an NGen module.</span></span>

<span data-ttu-id="a570a-108">`inlineeModuleId` окне Идентификатор модуля, который определяет `inlineeMethodId` .</span><span class="sxs-lookup"><span data-stu-id="a570a-108">`inlineeModuleId` [in] The identifier of a module that defines `inlineeMethodId`.</span></span> <span data-ttu-id="a570a-109">Дополнительные сведения см. в разделе "Примечания".</span><span class="sxs-lookup"><span data-stu-id="a570a-109">See the Remarks section for more information.</span></span>

<span data-ttu-id="a570a-110">`inlineeMethodId` окне Идентификатор встроенного метода.</span><span class="sxs-lookup"><span data-stu-id="a570a-110">`inlineeMethodId` [in] The identifier of an inlined method.</span></span> <span data-ttu-id="a570a-111">Дополнительные сведения см. в разделе "Примечания".</span><span class="sxs-lookup"><span data-stu-id="a570a-111">See the Remarks section for more information.</span></span>

<span data-ttu-id="a570a-112">`incompleteData` заполняет Флаг, указывающий, `ppEnum` содержит ли все методы выравнивание данного метода.</span><span class="sxs-lookup"><span data-stu-id="a570a-112">`incompleteData` [out] A flag that indicates whether `ppEnum` contains all methods inlining a given method.</span></span>  <span data-ttu-id="a570a-113">Дополнительные сведения см. в разделе "Примечания".</span><span class="sxs-lookup"><span data-stu-id="a570a-113">See the Remarks section for more information.</span></span>

<span data-ttu-id="a570a-114">`ppEnum` заполняет Указатель на адрес перечислителя</span><span class="sxs-lookup"><span data-stu-id="a570a-114">`ppEnum` [out] A pointer to the address of an enumerator</span></span>

## <a name="remarks"></a><span data-ttu-id="a570a-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="a570a-115">Remarks</span></span>

<span data-ttu-id="a570a-116">`inlineeModuleId``inlineeMethodId`вместе образуют полный идентификатор для метода, который может быть встроенным.</span><span class="sxs-lookup"><span data-stu-id="a570a-116">`inlineeModuleId` and `inlineeMethodId` together form the full identifier for the method that might be inlined.</span></span> <span data-ttu-id="a570a-117">Например, пусть модуль `A` определяет метод `Simple.Add` :</span><span class="sxs-lookup"><span data-stu-id="a570a-117">For example, assume module `A` defines a method `Simple.Add`:</span></span>

```csharp
Simple.Add(int a, int b)
{ return a + b; }
```

<span data-ttu-id="a570a-118">а модуль B определяет `Fancy.AddTwice` :</span><span class="sxs-lookup"><span data-stu-id="a570a-118">and module B defines `Fancy.AddTwice`:</span></span>

```csharp
Fancy.AddTwice(int a, int b)
{ return Simple.Add(a,b) + Simple.Add(a,b); }
```

<span data-ttu-id="a570a-119">Также можно предположить, что `Fancy.AddTwice` встроенный вызов `SimpleAdd` .</span><span class="sxs-lookup"><span data-stu-id="a570a-119">Lets also assume that `Fancy.AddTwice` inlines the call to `SimpleAdd`.</span></span> <span data-ttu-id="a570a-120">Профилировщик может использовать этот перечислитель для поиска всех методов, определенных в модуле B, которые являются встроенными `Simple.Add` , и результат будет перечисляться `AddTwice` .</span><span class="sxs-lookup"><span data-stu-id="a570a-120">A profiler could use this enumerator to find all methods defined in module B which inline `Simple.Add`, and the result would enumerate `AddTwice`.</span></span>  <span data-ttu-id="a570a-121">`inlineeModuleId` Идентификатор модуля `A` , а `inlineeMethodId` — идентификатор `Simple.Add(int a, int b)` .</span><span class="sxs-lookup"><span data-stu-id="a570a-121">`inlineeModuleId` is the identifier of module `A`, and `inlineeMethodId` is the identifier of `Simple.Add(int a, int b)`.</span></span>

<span data-ttu-id="a570a-122">Если `incompleteData` параметр имеет значение true после возвращения функции, перечислитель не содержит всех методов, выставляемых в данном методе.</span><span class="sxs-lookup"><span data-stu-id="a570a-122">If `incompleteData` is true after the function returns, the enumerator does not contain all methods inlining a given method.</span></span> <span data-ttu-id="a570a-123">Это может произойти, если одна или несколько непосредственных или косвенных зависимостей модуля "вкладыши" еще не загружены.</span><span class="sxs-lookup"><span data-stu-id="a570a-123">This can happen when one or more direct or indirect dependencies of inliners module haven't been loaded yet.</span></span> <span data-ttu-id="a570a-124">Если профилировщику требуются точные данные, необходимо повторить попытку позже, когда загрузится больше модулей, лучше при каждой загрузке модуля.</span><span class="sxs-lookup"><span data-stu-id="a570a-124">If a profiler needs accurate data, it should retry later when more modules are loaded, preferably on each module load.</span></span>

<span data-ttu-id="a570a-125">`EnumNgenModuleMethodsInliningThisMethod`Метод можно использовать для обхода ограничений встраивания для ReJIT.</span><span class="sxs-lookup"><span data-stu-id="a570a-125">The `EnumNgenModuleMethodsInliningThisMethod` method can be used to work around limitations on inlining for ReJIT.</span></span> <span data-ttu-id="a570a-126">ReJIT позволяет профилировщику изменить реализацию метода, а затем создать новый код для него в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="a570a-126">ReJIT lets a profiler change the implementation of a method and then create new code for it on the fly.</span></span> <span data-ttu-id="a570a-127">Например, можно изменить следующим образом `Simple.Add` :</span><span class="sxs-lookup"><span data-stu-id="a570a-127">For example, we could change `Simple.Add` as follows:</span></span>

```csharp
Simple.Add(int a, int b)
{ return 42; }
```

<span data-ttu-id="a570a-128">Тем не менее `Fancy.AddTwice` , поскольку уже встроено `Simple.Add` , он по-разному будет иметь такое же поведение, как и раньше.</span><span class="sxs-lookup"><span data-stu-id="a570a-128">However because `Fancy.AddTwice` has already inlined `Simple.Add`, it continues to have the same behavior as before.</span></span> <span data-ttu-id="a570a-129">Чтобы обойти это ограничение, вызывающий должен найти все методы во всех модулях, которые встроены `Simple.Add` и используются `ICorProfilerInfo5::RequestRejit` в каждом из этих методов.</span><span class="sxs-lookup"><span data-stu-id="a570a-129">To work around that limitation, the caller has to search for all methods in all modules that inline `Simple.Add` and use `ICorProfilerInfo5::RequestRejit` on each of those methods.</span></span> <span data-ttu-id="a570a-130">При повторной компиляции методов они будут иметь новое поведение, `Simple.Add` а не старое поведение.</span><span class="sxs-lookup"><span data-stu-id="a570a-130">When the methods are re-compiled, they will have the new behavior of `Simple.Add` instead of the old behavior.</span></span>

## <a name="requirements"></a><span data-ttu-id="a570a-131">Требования</span><span class="sxs-lookup"><span data-stu-id="a570a-131">Requirements</span></span>

<span data-ttu-id="a570a-132">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a570a-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="a570a-133">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a570a-133">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="a570a-134">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a570a-134">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="a570a-135">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a570a-135">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a570a-136">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a570a-136">See also</span></span>

- [<span data-ttu-id="a570a-137">Интерфейс ICorProfilerInfo6</span><span class="sxs-lookup"><span data-stu-id="a570a-137">ICorProfilerInfo6 Interface</span></span>](icorprofilerinfo6-interface.md)
