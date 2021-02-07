---
description: 'Дополнительные сведения о методе: ICorProfilerInfo6:: Енумнженмодулемесодсинлинингсисмесод'
title: Метод ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
ms.openlocfilehash: bd43dcecabe9a75f7ce3a94996727b192574e321
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737172"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a><span data-ttu-id="5ba66-103">Метод ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod</span><span class="sxs-lookup"><span data-stu-id="5ba66-103">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>

<span data-ttu-id="5ba66-104">Возвращает перечислитель для всех методов, определенных в заданном модуле NGen, и встроенный метод.</span><span class="sxs-lookup"><span data-stu-id="5ba66-104">Returns an enumerator to all the methods that are defined in a given NGen module and inline a given method.</span></span>

## <a name="syntax"></a><span data-ttu-id="5ba66-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5ba66-105">Syntax</span></span>

```cpp
HRESULT EnumNgenModuleMethodsInliningThisMethod(
        [in] ModuleID inlinersModuleId,
        [in] ModuleID inlineeModuleId,
        [in] mdMethodDef inlineeMethodId,
        [out] BOOL *incompleteData,
        [out] ICorProfilerMethodEnum** ppEnum
);
```

## <a name="parameters"></a><span data-ttu-id="5ba66-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="5ba66-106">Parameters</span></span>

`inlinersModuleId`\
<span data-ttu-id="5ba66-107">окне Идентификатор модуля NGen.</span><span class="sxs-lookup"><span data-stu-id="5ba66-107">[in] The identifier of an NGen module.</span></span>

`inlineeModuleId`\
<span data-ttu-id="5ba66-108">окне Идентификатор модуля, который определяет `inlineeMethodId` .</span><span class="sxs-lookup"><span data-stu-id="5ba66-108">[in] The identifier of a module that defines `inlineeMethodId`.</span></span> <span data-ttu-id="5ba66-109">Дополнительные сведения см. в разделе "Примечания".</span><span class="sxs-lookup"><span data-stu-id="5ba66-109">See the Remarks section for more information.</span></span>

`inlineeMethodId`\
<span data-ttu-id="5ba66-110">окне Идентификатор встроенного метода.</span><span class="sxs-lookup"><span data-stu-id="5ba66-110">[in] The identifier of an inlined method.</span></span> <span data-ttu-id="5ba66-111">Дополнительные сведения см. в разделе "Примечания".</span><span class="sxs-lookup"><span data-stu-id="5ba66-111">See the Remarks section for more information.</span></span>

`incompleteData`\
<span data-ttu-id="5ba66-112">заполняет Флаг, указывающий, `ppEnum` содержит ли все методы выравнивание данного метода.</span><span class="sxs-lookup"><span data-stu-id="5ba66-112">[out] A flag that indicates whether `ppEnum` contains all methods inlining a given method.</span></span>  <span data-ttu-id="5ba66-113">Дополнительные сведения см. в разделе "Примечания".</span><span class="sxs-lookup"><span data-stu-id="5ba66-113">See the Remarks section for more information.</span></span>

`ppEnum`\
<span data-ttu-id="5ba66-114">заполняет Указатель на адрес перечислителя</span><span class="sxs-lookup"><span data-stu-id="5ba66-114">[out] A pointer to the address of an enumerator</span></span>

## <a name="remarks"></a><span data-ttu-id="5ba66-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="5ba66-115">Remarks</span></span>

<span data-ttu-id="5ba66-116">`inlineeModuleId``inlineeMethodId`вместе образуют полный идентификатор для метода, который может быть встроенным.</span><span class="sxs-lookup"><span data-stu-id="5ba66-116">`inlineeModuleId` and `inlineeMethodId` together form the full identifier for the method that might be inlined.</span></span> <span data-ttu-id="5ba66-117">Например, пусть модуль `A` определяет метод `Simple.Add` :</span><span class="sxs-lookup"><span data-stu-id="5ba66-117">For example, assume module `A` defines a method `Simple.Add`:</span></span>

```csharp
Simple.Add(int a, int b)
{ return a + b; }
```

<span data-ttu-id="5ba66-118">а модуль B определяет `Fancy.AddTwice` :</span><span class="sxs-lookup"><span data-stu-id="5ba66-118">and module B defines `Fancy.AddTwice`:</span></span>

```csharp
Fancy.AddTwice(int a, int b)
{ return Simple.Add(a,b) + Simple.Add(a,b); }
```

<span data-ttu-id="5ba66-119">Также можно предположить, что `Fancy.AddTwice` встроенный вызов `SimpleAdd` .</span><span class="sxs-lookup"><span data-stu-id="5ba66-119">Lets also assume that `Fancy.AddTwice` inlines the call to `SimpleAdd`.</span></span> <span data-ttu-id="5ba66-120">Профилировщик может использовать этот перечислитель для поиска всех методов, определенных в модуле B, которые являются встроенными `Simple.Add` , и результат будет перечисляться `AddTwice` .</span><span class="sxs-lookup"><span data-stu-id="5ba66-120">A profiler could use this enumerator to find all methods defined in module B which inline `Simple.Add`, and the result would enumerate `AddTwice`.</span></span>  <span data-ttu-id="5ba66-121">`inlineeModuleId` Идентификатор модуля `A` , а `inlineeMethodId` — идентификатор `Simple.Add(int a, int b)` .</span><span class="sxs-lookup"><span data-stu-id="5ba66-121">`inlineeModuleId` is the identifier of module `A`, and `inlineeMethodId` is the identifier of `Simple.Add(int a, int b)`.</span></span>

<span data-ttu-id="5ba66-122">Если `incompleteData` параметр имеет значение true после возвращения функции, перечислитель не содержит всех методов, выставляемых в данном методе.</span><span class="sxs-lookup"><span data-stu-id="5ba66-122">If `incompleteData` is true after the function returns, the enumerator does not contain all methods inlining a given method.</span></span> <span data-ttu-id="5ba66-123">Это может произойти, если одна или несколько непосредственных или косвенных зависимостей модуля "вкладыши" еще не загружены.</span><span class="sxs-lookup"><span data-stu-id="5ba66-123">This can happen when one or more direct or indirect dependencies of inliners module haven't been loaded yet.</span></span> <span data-ttu-id="5ba66-124">Если профилировщику требуются точные данные, необходимо повторить попытку позже, когда загрузится больше модулей, лучше при каждой загрузке модуля.</span><span class="sxs-lookup"><span data-stu-id="5ba66-124">If a profiler needs accurate data, it should retry later when more modules are loaded, preferably on each module load.</span></span>

<span data-ttu-id="5ba66-125">`EnumNgenModuleMethodsInliningThisMethod`Метод можно использовать для обхода ограничений встраивания для ReJIT.</span><span class="sxs-lookup"><span data-stu-id="5ba66-125">The `EnumNgenModuleMethodsInliningThisMethod` method can be used to work around limitations on inlining for ReJIT.</span></span> <span data-ttu-id="5ba66-126">ReJIT позволяет профилировщику изменить реализацию метода, а затем создать новый код для него в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="5ba66-126">ReJIT lets a profiler change the implementation of a method and then create new code for it on the fly.</span></span> <span data-ttu-id="5ba66-127">Например, можно изменить следующим образом `Simple.Add` :</span><span class="sxs-lookup"><span data-stu-id="5ba66-127">For example, we could change `Simple.Add` as follows:</span></span>

```csharp
Simple.Add(int a, int b)
{ return 42; }
```

<span data-ttu-id="5ba66-128">Тем не менее `Fancy.AddTwice` , поскольку уже встроено `Simple.Add` , он по-разному будет иметь такое же поведение, как и раньше.</span><span class="sxs-lookup"><span data-stu-id="5ba66-128">However because `Fancy.AddTwice` has already inlined `Simple.Add`, it continues to have the same behavior as before.</span></span> <span data-ttu-id="5ba66-129">Чтобы обойти это ограничение, вызывающий должен найти все методы во всех модулях, которые встроены `Simple.Add` и используются `ICorProfilerInfo5::RequestRejit` в каждом из этих методов.</span><span class="sxs-lookup"><span data-stu-id="5ba66-129">To work around that limitation, the caller has to search for all methods in all modules that inline `Simple.Add` and use `ICorProfilerInfo5::RequestRejit` on each of those methods.</span></span> <span data-ttu-id="5ba66-130">При повторной компиляции методов они будут иметь новое поведение, `Simple.Add` а не старое поведение.</span><span class="sxs-lookup"><span data-stu-id="5ba66-130">When the methods are re-compiled, they will have the new behavior of `Simple.Add` instead of the old behavior.</span></span>

## <a name="requirements"></a><span data-ttu-id="5ba66-131">Требования</span><span class="sxs-lookup"><span data-stu-id="5ba66-131">Requirements</span></span>

<span data-ttu-id="5ba66-132">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ba66-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="5ba66-133">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5ba66-133">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="5ba66-134">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ba66-134">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="5ba66-135">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ba66-135">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5ba66-136">См. также</span><span class="sxs-lookup"><span data-stu-id="5ba66-136">See also</span></span>

- [<span data-ttu-id="5ba66-137">Интерфейс ICorProfilerInfo6</span><span class="sxs-lookup"><span data-stu-id="5ba66-137">ICorProfilerInfo6 Interface</span></span>](icorprofilerinfo6-interface.md)
