---
description: 'Дополнительные сведения о методе: IMethodMalloc:: Alloc'
title: Метод IMethodMalloc::Alloc
ms.date: 03/30/2017
api_name:
- IMethodMalloc.Alloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc::Alloc
helpviewer_keywords:
- IMethodMalloc::Alloc method [.NET Framework profiling]
- Alloc method, IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8653bd4c-2290-43d2-a3e1-cbbd50033f4f
topic_type:
- apiref
ms.openlocfilehash: f8a41530e0e1a126fafa1816e6fed58d10df6587
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736958"
---
# <a name="imethodmallocalloc-method"></a><span data-ttu-id="e759a-103">Метод IMethodMalloc::Alloc</span><span class="sxs-lookup"><span data-stu-id="e759a-103">IMethodMalloc::Alloc Method</span></span>

<span data-ttu-id="e759a-104">Пытается выделить указанный объем памяти для нового текста функции MSIL.</span><span class="sxs-lookup"><span data-stu-id="e759a-104">Attempts to allocate a specified amount of memory for a new Microsoft intermediate language (MSIL) function body.</span></span>

## <a name="syntax"></a><span data-ttu-id="e759a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e759a-105">Syntax</span></span>

```cpp
PVOID Alloc (
    [in] ULONG   cb
);
```

## <a name="parameters"></a><span data-ttu-id="e759a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e759a-106">Parameters</span></span>

`cb`\
<span data-ttu-id="e759a-107">окне Число байтов, которое необходимо выделить для тела метода.</span><span class="sxs-lookup"><span data-stu-id="e759a-107">[in] The number of bytes to allocate for the method body.</span></span>

## <a name="remarks"></a><span data-ttu-id="e759a-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="e759a-108">Remarks</span></span>

 <span data-ttu-id="e759a-109">Выделенная память будет начинаться с адреса, превышающего базовый адрес модуля, связанного с этим распределителем.</span><span class="sxs-lookup"><span data-stu-id="e759a-109">The allocated memory will begin at an address greater than the base address of the module that is associated with this allocator.</span></span> <span data-ttu-id="e759a-110">Иными словами, каждый распределитель создается для конкретного модуля и пытается выделить память с положительным смещением от его базового адреса.</span><span class="sxs-lookup"><span data-stu-id="e759a-110">In other words, each allocator is created for a particular module, and will attempt to allocate memory at a positive offset from its base address.</span></span> <span data-ttu-id="e759a-111">Если `Alloc` не удается выделить запрошенное число байтов по адресу, превышающему базовый адрес модуля, он возвращает E_OUTOFMEMORY, независимо от фактического объема доступной памяти.</span><span class="sxs-lookup"><span data-stu-id="e759a-111">If `Alloc` fails to allocate the requested number of bytes at an address greater than the base address of the module, it returns E_OUTOFMEMORY, regardless of the actual amount of memory space available.</span></span>

 <span data-ttu-id="e759a-112">`Alloc`Метод следует использовать в сочетании с методом [ICorProfilerInfo:: SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e759a-112">The `Alloc` method should be used in conjunction with the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e759a-113">Требования</span><span class="sxs-lookup"><span data-stu-id="e759a-113">Requirements</span></span>

 <span data-ttu-id="e759a-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e759a-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="e759a-115">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e759a-115">**Header:** CorProf.idl, CorProf.h</span></span>

 <span data-ttu-id="e759a-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e759a-116">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="e759a-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e759a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e759a-118">См. также</span><span class="sxs-lookup"><span data-stu-id="e759a-118">See also</span></span>

- [<span data-ttu-id="e759a-119">Интерфейс IMethodMalloc</span><span class="sxs-lookup"><span data-stu-id="e759a-119">IMethodMalloc Interface</span></span>](imethodmalloc-interface.md)
