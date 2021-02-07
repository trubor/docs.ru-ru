---
description: 'Дополнительные сведения о методе: IMetaDataDispenser:: OpenScopeOnMemory'
title: Метод IMetaDataDispenser::OpenScopeOnMemory
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScopeOnMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScopeOnMemory
helpviewer_keywords:
- OpenScopeOnMemory method [.NET Framework metadata]
- IMetaDataDispenser::OpenScopeOnMemory method [.NET Framework metadata]
ms.assetid: 14218249-bdec-48ae-b5fc-9f57f7ca8501
topic_type:
- apiref
ms.openlocfilehash: 589c68ab60eec55efc43d077807789e75ae1682f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753592"
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a><span data-ttu-id="03413-103">Метод IMetaDataDispenser::OpenScopeOnMemory</span><span class="sxs-lookup"><span data-stu-id="03413-103">IMetaDataDispenser::OpenScopeOnMemory Method</span></span>

<span data-ttu-id="03413-104">Открывает область памяти, которая содержит существующие метаданные.</span><span class="sxs-lookup"><span data-stu-id="03413-104">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="03413-105">Это значит, что этот метод открывает указанную область памяти, в которой существующие данные обрабатываются как метаданные.</span><span class="sxs-lookup"><span data-stu-id="03413-105">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03413-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="03413-106">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,
    [in]  ULONG       cbData,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03413-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="03413-107">Parameters</span></span>  

 `pData`  
 <span data-ttu-id="03413-108">окне Указатель, указывающий начальный адрес области памяти.</span><span class="sxs-lookup"><span data-stu-id="03413-108">[in] A pointer that specifies the starting address of the memory area.</span></span>  
  
 `cbData`  
 <span data-ttu-id="03413-109">окне Размер области памяти в байтах.</span><span class="sxs-lookup"><span data-stu-id="03413-109">[in] The size of the memory area, in bytes.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="03413-110">окне Значение перечисления [коропенфлагс](coropenflags-enumeration.md) , определяющее режим (чтение, запись и т. д.) для открытия.</span><span class="sxs-lookup"><span data-stu-id="03413-110">[in] A value of the [CorOpenFlags](coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="03413-111">окне Идентификатор IID требуемого интерфейса метаданных, который должен быть возвращен; вызывающий объект будет использовать интерфейс для импорта (чтения) или выдачи (записи) метаданных.</span><span class="sxs-lookup"><span data-stu-id="03413-111">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="03413-112">Значение `riid` должно указывать один из интерфейсов "import" или "Emit".</span><span class="sxs-lookup"><span data-stu-id="03413-112">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="03413-113">Допустимые значения: IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 или IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="03413-113">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="03413-114">заполняет Указатель на возвращаемый интерфейс.</span><span class="sxs-lookup"><span data-stu-id="03413-114">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03413-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="03413-115">Remarks</span></span>  

 <span data-ttu-id="03413-116">Копию метаданных в памяти можно запросить с помощью методов из одного из интерфейсов "Импорт" или добавить к методам из одного из интерфейсов "выдачи".</span><span class="sxs-lookup"><span data-stu-id="03413-116">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="03413-117">`OpenScopeOnMemory`Метод аналогичен методу [IMetaDataDispenser:: OpenScope](imetadatadispenser-openscope-method.md) , за исключением того, что интересующие метаданные уже существуют в памяти, а не в файле на диске.</span><span class="sxs-lookup"><span data-stu-id="03413-117">The `OpenScopeOnMemory` method is similar to the [IMetaDataDispenser::OpenScope](imetadatadispenser-openscope-method.md) method, except that the metadata of interest already exists in memory, rather than in a file on disk.</span></span>  
  
 <span data-ttu-id="03413-118">Если целевая область памяти не содержит метаданных среды CLR, `OpenScopeOnMemory` метод завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="03413-118">If the target area of memory does not contain common language runtime (CLR) metadata, the `OpenScopeOnMemory` method will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03413-119">Требования</span><span class="sxs-lookup"><span data-stu-id="03413-119">Requirements</span></span>  

 <span data-ttu-id="03413-120">**Платформа:** См. раздел [требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03413-120">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03413-121">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="03413-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="03413-122">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="03413-122">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="03413-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03413-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03413-124">См. также</span><span class="sxs-lookup"><span data-stu-id="03413-124">See also</span></span>

- [<span data-ttu-id="03413-125">Интерфейс IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="03413-125">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="03413-126">Интерфейс IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="03413-126">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="03413-127">Интерфейс IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="03413-127">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="03413-128">Интерфейс IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="03413-128">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="03413-129">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="03413-129">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="03413-130">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="03413-130">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="03413-131">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="03413-131">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="03413-132">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="03413-132">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
