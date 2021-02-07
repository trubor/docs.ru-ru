---
description: 'Дополнительные сведения о методе: IMetaDataDispenser:: OpenScope'
title: Метод IMetaDataDispenser::OpenScope
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScope
helpviewer_keywords:
- IMetaDataDispenser::OpenScope method [.NET Framework metadata]
- OpenScope method, IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 65063ad5-e0d9-4c01-8f8b-9a5950109fa6
topic_type:
- apiref
ms.openlocfilehash: a1fa9a955bfc38ee4b2f23efbe8e492877a3d0c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753620"
---
# <a name="imetadatadispenseropenscope-method"></a><span data-ttu-id="05ea4-103">Метод IMetaDataDispenser::OpenScope</span><span class="sxs-lookup"><span data-stu-id="05ea4-103">IMetaDataDispenser::OpenScope Method</span></span>

<span data-ttu-id="05ea4-104">Открывает существующий файл на диске и сопоставляет его метаданные с памятью.</span><span class="sxs-lookup"><span data-stu-id="05ea4-104">Opens an existing, on-disk file and maps its metadata into memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05ea4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="05ea4-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05ea4-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="05ea4-106">Parameters</span></span>  

 `szScope`  
 <span data-ttu-id="05ea4-107">окне Имя открываемого файла.</span><span class="sxs-lookup"><span data-stu-id="05ea4-107">[in] The name of the file to be opened.</span></span> <span data-ttu-id="05ea4-108">Файл должен содержать метаданные среды CLR.</span><span class="sxs-lookup"><span data-stu-id="05ea4-108">The file must contain common language runtime (CLR) metadata.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="05ea4-109">окне Значение перечисления [коропенфлагс](coropenflags-enumeration.md) , определяющее режим (чтение, запись и т. д.) для открытия.</span><span class="sxs-lookup"><span data-stu-id="05ea4-109">[in] A value of the [CorOpenFlags](coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="05ea4-110">окне Идентификатор IID требуемого интерфейса метаданных, который должен быть возвращен; вызывающий объект будет использовать интерфейс для импорта (чтения) или выдачи (записи) метаданных.</span><span class="sxs-lookup"><span data-stu-id="05ea4-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="05ea4-111">Значение `riid` должно указывать один из интерфейсов "import" или "Emit".</span><span class="sxs-lookup"><span data-stu-id="05ea4-111">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="05ea4-112">Допустимые значения: IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 или IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="05ea4-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="05ea4-113">заполняет Указатель на возвращаемый интерфейс.</span><span class="sxs-lookup"><span data-stu-id="05ea4-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05ea4-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="05ea4-114">Remarks</span></span>  

 <span data-ttu-id="05ea4-115">Копию метаданных в памяти можно запросить с помощью методов из одного из интерфейсов "Импорт" или добавить к методам из одного из интерфейсов "выдачи".</span><span class="sxs-lookup"><span data-stu-id="05ea4-115">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="05ea4-116">Если целевой файл не содержит метаданные CLR, `OpenScope` метод завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="05ea4-116">If the target file does not contain CLR metadata, the `OpenScope` method will fail.</span></span>  
  
 <span data-ttu-id="05ea4-117">В платформа .NET Framework версии 1,0 и 1,1, если область открыта с параметром `dwOpenFlags` офреад, она может предоставлять общий доступ.</span><span class="sxs-lookup"><span data-stu-id="05ea4-117">In the .NET Framework version 1.0 and version 1.1, if a scope is opened with `dwOpenFlags` set to ofRead, it is eligible for sharing.</span></span> <span data-ttu-id="05ea4-118">То есть, если последующие вызовы `OpenScope` передают имя ранее открытого файла, существующая область используется повторно, а новый набор структур данных не создается.</span><span class="sxs-lookup"><span data-stu-id="05ea4-118">That is, if subsequent calls to `OpenScope` pass in the name of a file that was previously opened, the existing scope is reused and a new set of data structures is not created.</span></span> <span data-ttu-id="05ea4-119">Тем не менее проблемы могут возникать из-за этого общего доступа.</span><span class="sxs-lookup"><span data-stu-id="05ea4-119">However, problems can arise due to this sharing.</span></span>  
  
 <span data-ttu-id="05ea4-120">В платформа .NET Framework версии 2,0 области, открытые с параметром `dwOpenFlags` офреад, больше не являются общими.</span><span class="sxs-lookup"><span data-stu-id="05ea4-120">In the .NET Framework version 2.0, scopes opened with `dwOpenFlags` set to ofRead are no longer shared.</span></span> <span data-ttu-id="05ea4-121">Используйте значение Офреадонли, чтобы разрешить общий доступ к области.</span><span class="sxs-lookup"><span data-stu-id="05ea4-121">Use the ofReadOnly value to allow the scope to be shared.</span></span> <span data-ttu-id="05ea4-122">При совместном использовании области запросы, использующие интерфейсы метаданных для чтения и записи, завершатся ошибкой.</span><span class="sxs-lookup"><span data-stu-id="05ea4-122">When a scope is shared, queries that use "read/write" metadata interfaces will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05ea4-123">Требования</span><span class="sxs-lookup"><span data-stu-id="05ea4-123">Requirements</span></span>  

 <span data-ttu-id="05ea4-124">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05ea4-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05ea4-125">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="05ea4-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="05ea4-126">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="05ea4-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="05ea4-127">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05ea4-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05ea4-128">См. также</span><span class="sxs-lookup"><span data-stu-id="05ea4-128">See also</span></span>

- [<span data-ttu-id="05ea4-129">Интерфейс IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="05ea4-129">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="05ea4-130">Интерфейс IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="05ea4-130">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="05ea4-131">Интерфейс IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="05ea4-131">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="05ea4-132">Интерфейс IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="05ea4-132">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="05ea4-133">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="05ea4-133">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="05ea4-134">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="05ea4-134">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="05ea4-135">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="05ea4-135">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="05ea4-136">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="05ea4-136">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
