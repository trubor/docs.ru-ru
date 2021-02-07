---
description: 'Дополнительные сведения о методе: ICorProfilerInfo7:: ApplyMetaData'
title: 'Метод ICorProfilerInfo7:: ApplyMetaData'
ms.date: 02/15/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo7.ApplyMetaData
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: a1bfb649-4584-4d35-b3e6-8fe59b53992a
ms.openlocfilehash: 3a4554357ede85d936e8bf9c87c6b9c096dab188
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737133"
---
# <a name="icorprofilerinfo7applymetadata-method"></a><span data-ttu-id="c66b6-103">Метод ICorProfilerInfo7:: ApplyMetaData</span><span class="sxs-lookup"><span data-stu-id="c66b6-103">ICorProfilerInfo7::ApplyMetaData Method</span></span>

<span data-ttu-id="c66b6-104">[Поддерживается в .NET Framework 4.6.1 и более поздних версиях.]</span><span class="sxs-lookup"><span data-stu-id="c66b6-104">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="c66b6-105">Применяет метаданные, которые были недавно определены `IMetadataEmit::Define*` методами, к указанному модулю.</span><span class="sxs-lookup"><span data-stu-id="c66b6-105">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c66b6-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c66b6-106">Syntax</span></span>  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c66b6-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="c66b6-107">Parameters</span></span>  

 `moduleID`  
 <span data-ttu-id="c66b6-108">окне Идентификатор модуля, метаданные которого были изменены.</span><span class="sxs-lookup"><span data-stu-id="c66b6-108">[in] The identifier of the module whose metadata was changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c66b6-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="c66b6-109">Remarks</span></span>  

 <span data-ttu-id="c66b6-110">Если изменения метаданных вносятся после обратного вызова [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) , необходимо вызвать этот метод перед использованием новых метаданных.</span><span class="sxs-lookup"><span data-stu-id="c66b6-110">If metadata changes are made after the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback, you must call this method before using the new metadata.</span></span>  
  
 <span data-ttu-id="c66b6-111">`ApplyMetaData` поддерживает добавление только следующих типов метаданных:</span><span class="sxs-lookup"><span data-stu-id="c66b6-111">`ApplyMetaData` only supports adding the following types of metadata:</span></span>  
  
- <span data-ttu-id="c66b6-112">`AssemblyRef` записи, которые создаются путем вызова метода [IMetaDataAssemblyEmit::D ефинеассемблиреф](../metadata/imetadataassemblyemit-defineassemblyref-method.md).</span><span class="sxs-lookup"><span data-stu-id="c66b6-112">`AssemblyRef` records, which you create by calling the [IMetaDataAssemblyEmit::DefineAssemblyRef](../metadata/imetadataassemblyemit-defineassemblyref-method.md).</span></span> <span data-ttu-id="c66b6-113">метод.</span><span class="sxs-lookup"><span data-stu-id="c66b6-113">method.</span></span>  
  
- <span data-ttu-id="c66b6-114">`TypeRef` записи, которые создаются путем вызова метода [IMetaDataEmit::D ефинетиперефбинаме](../metadata/imetadataemit-definetyperefbyname-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c66b6-114">`TypeRef` records, which you create by calling the [IMetaDataEmit::DefineTypeRefByName](../metadata/imetadataemit-definetyperefbyname-method.md) method.</span></span>  
  
- <span data-ttu-id="c66b6-115">`TypeSpec` записи, которые создаются путем вызова метода [IMetaDataEmit:: жеттокенфромтипеспек](../metadata/imetadataemit-gettokenfromtypespec-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c66b6-115">`TypeSpec` records, which you create by calling the [IMetaDataEmit::GetTokenFromTypeSpec](../metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
- <span data-ttu-id="c66b6-116">`MemberRef` записи, которые создаются путем вызова метода [IMetaDataEmit::D ефинемемберреф](../metadata/imetadataemit-definememberref-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c66b6-116">`MemberRef` records, which you create by calling the [IMetaDataEmit::DefineMemberRef](../metadata/imetadataemit-definememberref-method.md) method.</span></span>  
  
- <span data-ttu-id="c66b6-117">`MemberSpec` записи, которые создаются путем вызова метода [IMetaDataEmit2::D ефинемесодспек](../metadata/imetadataemit2-definemethodspec-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c66b6-117">`MemberSpec` records, which you create by calling the [IMetaDataEmit2::DefineMethodSpec](../metadata/imetadataemit2-definemethodspec-method.md) method.</span></span>  
  
- <span data-ttu-id="c66b6-118">`UserString` записи, которые создаются путем вызова метода [IMetaDataEmit::D ефинеусерстринг](../metadata/imetadataemit-defineuserstring-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c66b6-118">`UserString` records, which you create by calling the [IMetaDataEmit::DefineUserString](../metadata/imetadataemit-defineuserstring-method.md) method.</span></span>  

<span data-ttu-id="c66b6-119">Начиная с .NET Core 3,0, `ApplyMetaData` также поддерживает следующие типы:</span><span class="sxs-lookup"><span data-stu-id="c66b6-119">Starting with .NET Core 3.0, `ApplyMetaData` also supports the following types:</span></span>

- <span data-ttu-id="c66b6-120">`TypeDef` записи, которые создаются путем вызова метода [IMetaDataEmit::D ефинетипедеф](../metadata/imetadataemit-definetypedef-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c66b6-120">`TypeDef` records, which you create by calling the [IMetaDataEmit::DefineTypeDef](../metadata/imetadataemit-definetypedef-method.md) method.</span></span>

- <span data-ttu-id="c66b6-121">`MethodDef` записи, которые создаются путем вызова метода [IMetaDataEmit::D ефинемесод](../metadata/imetadataemit-definemethod-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c66b6-121">`MethodDef` records, which you create by calling the [IMetaDataEmit::DefineMethod](../metadata/imetadataemit-definemethod-method.md) method.</span></span> <span data-ttu-id="c66b6-122">Однако добавление виртуальных методов в существующий тип не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="c66b6-122">However, adding virtual methods to an existing type is not supported.</span></span> <span data-ttu-id="c66b6-123">Виртуальные методы должны быть добавлены перед обратным вызовом [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c66b6-123">Virtual methods must be added before the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="c66b6-124">Требования</span><span class="sxs-lookup"><span data-stu-id="c66b6-124">Requirements</span></span>  

 <span data-ttu-id="c66b6-125">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c66b6-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c66b6-126">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c66b6-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c66b6-127">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c66b6-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c66b6-128">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c66b6-128">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c66b6-129">См. также</span><span class="sxs-lookup"><span data-stu-id="c66b6-129">See also</span></span>

- [<span data-ttu-id="c66b6-130">Интерфейс ICorProfilerInfo7</span><span class="sxs-lookup"><span data-stu-id="c66b6-130">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
