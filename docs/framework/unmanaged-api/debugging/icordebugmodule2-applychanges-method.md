---
description: 'Дополнительные сведения о методе: ICorDebugModule2:: ApplyChanges'
title: Метод ICorDebugModule2::ApplyChanges
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ApplyChanges
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ApplyChanges
helpviewer_keywords:
- ApplyChanges method [.NET Framework debugging]
- ICorDebugModule2::ApplyChanges method [.NET Framework debugging]
ms.assetid: 96fa3406-6a6f-41a1-88c6-d9bc5d1a16d1
topic_type:
- apiref
ms.openlocfilehash: 09cbc395c8d656d1dc27de86305432b26308c885
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660080"
---
# <a name="icordebugmodule2applychanges-method"></a><span data-ttu-id="e3075-103">Метод ICorDebugModule2::ApplyChanges</span><span class="sxs-lookup"><span data-stu-id="e3075-103">ICorDebugModule2::ApplyChanges Method</span></span>

<span data-ttu-id="e3075-104">Применяет изменения в метаданных и изменения в коде промежуточного языка MSIL к выполняющемуся процессу.</span><span class="sxs-lookup"><span data-stu-id="e3075-104">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3075-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e3075-105">Syntax</span></span>  
  
```cpp  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3075-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e3075-106">Parameters</span></span>  

 `cbMetadata`  
 <span data-ttu-id="e3075-107">окне Размер (в байтах) разностных метаданных.</span><span class="sxs-lookup"><span data-stu-id="e3075-107">[in] Size, in bytes, of the delta metadata.</span></span>  
  
 `pbMetadata`  
 <span data-ttu-id="e3075-108">окне Буфер, содержащий разностные метаданные.</span><span class="sxs-lookup"><span data-stu-id="e3075-108">[in] Buffer that contains the delta metadata.</span></span> <span data-ttu-id="e3075-109">Адрес буфера возвращается методом [IMetaDataEmit2:: саведелтатомемори](../metadata/imetadataemit2-savedeltatomemory-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e3075-109">The address of the buffer is returned from the [IMetaDataEmit2::SaveDeltaToMemory](../metadata/imetadataemit2-savedeltatomemory-method.md) method.</span></span>  
  
 <span data-ttu-id="e3075-110">Относительные виртуальные адреса (RVA) в метаданных должны относиться к началу кода MSIL.</span><span class="sxs-lookup"><span data-stu-id="e3075-110">The relative virtual addresses (RVAs) in the metadata should be relative to the start of the MSIL code.</span></span>  
  
 `cbIL`  
 <span data-ttu-id="e3075-111">окне Размер (в байтах) разностного кода MSIL.</span><span class="sxs-lookup"><span data-stu-id="e3075-111">[in] Size, in bytes, of the delta MSIL code.</span></span>  
  
 `pbIL`  
 <span data-ttu-id="e3075-112">окне Буфер, содержащий обновленный код MSIL.</span><span class="sxs-lookup"><span data-stu-id="e3075-112">[in] Buffer that contains the updated MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3075-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="e3075-113">Remarks</span></span>  

 <span data-ttu-id="e3075-114">`pbMetadata`Параметр находится в особом формате разностных метаданных (в виде выходных данных [IMetaDataEmit2:: саведелтатомемори](../metadata/imetadataemit2-savedeltatomemory-method.md)).</span><span class="sxs-lookup"><span data-stu-id="e3075-114">The `pbMetadata` parameter is in a special delta metadata format (as output by [IMetaDataEmit2::SaveDeltaToMemory](../metadata/imetadataemit2-savedeltatomemory-method.md)).</span></span> <span data-ttu-id="e3075-115">`pbMetadata` принимает предыдущие метаданные в качестве основы и описывает отдельные изменения, которые необходимо применить к этой базе.</span><span class="sxs-lookup"><span data-stu-id="e3075-115">`pbMetadata` takes previous metadata as a base and describes individual changes to apply to that base.</span></span>  
  
 <span data-ttu-id="e3075-116">В отличие от этого, `pbIL[` параметр] содержит новый код MSIL для обновленного метода и предназначен для полной замены предыдущего MSIL для этого метода.</span><span class="sxs-lookup"><span data-stu-id="e3075-116">In contrast, the `pbIL[`] parameter contains the new MSIL for the updated method, and is meant to completely replace the previous MSIL for that method</span></span>  
  
 <span data-ttu-id="e3075-117">Если разностный код MSIL и метаданные были созданы в памяти отладчика, отладчик вызывает метод `ApplyChanges` , чтобы отправить изменения в среду CLR.</span><span class="sxs-lookup"><span data-stu-id="e3075-117">When the delta MSIL and the metadata have been created in the debugger’s memory, the debugger calls `ApplyChanges` to send the changes into the common language runtime (CLR).</span></span> <span data-ttu-id="e3075-118">Среда выполнения обновляет свои таблицы метаданных, помещает новый код MSIL в процесс и настраивает JIT-компиляцию нового MSIL.</span><span class="sxs-lookup"><span data-stu-id="e3075-118">The runtime updates its metadata tables, places the new MSIL into the process, and sets up a just-in-time (JIT) compilation of the new MSIL.</span></span> <span data-ttu-id="e3075-119">После применения изменений отладчик должен вызвать [IMetaDataEmit2:: ресетенклог](../metadata/imetadataemit2-resetenclog-method.md) , чтобы подготовиться к следующему сеансу редактирования.</span><span class="sxs-lookup"><span data-stu-id="e3075-119">When the changes have been applied, the debugger should call [IMetaDataEmit2::ResetENCLog](../metadata/imetadataemit2-resetenclog-method.md) to prepare for the next editing session.</span></span> <span data-ttu-id="e3075-120">Затем отладчик может продолжить процесс.</span><span class="sxs-lookup"><span data-stu-id="e3075-120">The debugger may then continue the process.</span></span>  
  
 <span data-ttu-id="e3075-121">Всякий раз, когда отладчик вызывает `ApplyChanges` модуль с разностными метаданными, он должен также вызвать метод [IMetaDataEmit:: ApplyEditAndContinue](../metadata/imetadataemit-applyeditandcontinue-method.md) с теми же разностными метаданными для всех его копий метаданных этого модуля, за исключением копирования, используемой для отправки изменений.</span><span class="sxs-lookup"><span data-stu-id="e3075-121">Whenever the debugger calls `ApplyChanges` on a module that has delta metadata, it should also call [IMetaDataEmit::ApplyEditAndContinue](../metadata/imetadataemit-applyeditandcontinue-method.md) with the same delta metadata on all of its copies of that module’s metadata except for the copy used to emit the changes.</span></span> <span data-ttu-id="e3075-122">Если копия метаданных по каким-либо причинам не синхронизирована с фактическими метаданными, то отладчик всегда может создать копию и получить новую копию.</span><span class="sxs-lookup"><span data-stu-id="e3075-122">If a copy of the metadata somehow becomes out-of-sync with the actual metadata, the debugger can always throw away that copy and obtain a new copy.</span></span>  
  
 <span data-ttu-id="e3075-123">В случае `ApplyChanges` сбоя метода сеанс отладки находится в недопустимом состоянии и должен быть перезапущен.</span><span class="sxs-lookup"><span data-stu-id="e3075-123">If the `ApplyChanges` method fails, the debug session is in an invalid state and must be restarted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3075-124">Требования</span><span class="sxs-lookup"><span data-stu-id="e3075-124">Requirements</span></span>  

 <span data-ttu-id="e3075-125">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3075-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3075-126">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3075-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3075-127">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3075-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3075-128">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3075-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
