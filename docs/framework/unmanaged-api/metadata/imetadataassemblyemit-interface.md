---
description: 'Дополнительные сведения о: интерфейс IMetaDataAssemblyEmit'
title: Интерфейс IMetaDataAssemblyEmit
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit
helpviewer_keywords:
- IMetaDataAssemblyEmit interface [.NET Framework metadata]
ms.assetid: 34fb03cc-2285-4a45-ac48-ad993b7a921a
topic_type:
- apiref
ms.openlocfilehash: bcfca4eedc14f2292c40874d86c4984b4c1948f5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678215"
---
# <a name="imetadataassemblyemit-interface"></a><span data-ttu-id="8a24a-103">Интерфейс IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="8a24a-103">IMetaDataAssemblyEmit Interface</span></span>

<span data-ttu-id="8a24a-104">Предоставляет методы, поддерживающие модель самоописания, которая используется средой CLR для разрешения и потребления ресурсов.</span><span class="sxs-lookup"><span data-stu-id="8a24a-104">Provides methods that support the self-description model used by the common language runtime to resolve and consume resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8a24a-105">Методы</span><span class="sxs-lookup"><span data-stu-id="8a24a-105">Methods</span></span>  
  
|<span data-ttu-id="8a24a-106">Метод</span><span class="sxs-lookup"><span data-stu-id="8a24a-106">Method</span></span>|<span data-ttu-id="8a24a-107">Описание</span><span class="sxs-lookup"><span data-stu-id="8a24a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8a24a-108">Метод DefineAssembly</span><span class="sxs-lookup"><span data-stu-id="8a24a-108">DefineAssembly Method</span></span>](imetadataassemblyemit-defineassembly-method.md)|<span data-ttu-id="8a24a-109">Создает структуру данных сборки, содержащую метаданные для заданной сборки, и возвращает связанный токен метаданных.</span><span class="sxs-lookup"><span data-stu-id="8a24a-109">Creates an assembly data structure containing metadata for the specified assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="8a24a-110">Метод DefineAssemblyRef</span><span class="sxs-lookup"><span data-stu-id="8a24a-110">DefineAssemblyRef Method</span></span>](imetadataassemblyemit-defineassemblyref-method.md)|<span data-ttu-id="8a24a-111">Создает структуру `AssemblyRef`, содержащую метаданные для сборки, на которую ссылается данная сборка, и возвращает связанный токен метаданных.</span><span class="sxs-lookup"><span data-stu-id="8a24a-111">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="8a24a-112">Метод DefineExportedType</span><span class="sxs-lookup"><span data-stu-id="8a24a-112">DefineExportedType Method</span></span>](imetadataassemblyemit-defineexportedtype-method.md)|<span data-ttu-id="8a24a-113">Создает структуру `ExportedType`, содержащую метаданные для указанного экспортированного типа, и возвращает связанный токен метаданных.</span><span class="sxs-lookup"><span data-stu-id="8a24a-113">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="8a24a-114">Метод DefineFile</span><span class="sxs-lookup"><span data-stu-id="8a24a-114">DefineFile Method</span></span>](imetadataassemblyemit-definefile-method.md)|<span data-ttu-id="8a24a-115">Создает структуру метаданных `File`, содержащую метаданные для сборки, на которую ссылается данная сборка, и возвращает связанный токен метаданных.</span><span class="sxs-lookup"><span data-stu-id="8a24a-115">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="8a24a-116">Метод DefineManifestResource</span><span class="sxs-lookup"><span data-stu-id="8a24a-116">DefineManifestResource Method</span></span>](imetadataassemblyemit-definemanifestresource-method.md)|<span data-ttu-id="8a24a-117">Создает структуру `ManifestResource`, содержащую метаданные для указанного ресурса манифеста, и возвращает связанный токен метаданных.</span><span class="sxs-lookup"><span data-stu-id="8a24a-117">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="8a24a-118">Метод SetAssemblyProps</span><span class="sxs-lookup"><span data-stu-id="8a24a-118">SetAssemblyProps Method</span></span>](imetadataassemblyemit-setassemblyprops-method.md)|<span data-ttu-id="8a24a-119">Изменяет указанную структуру метаданных `Assembly`.</span><span class="sxs-lookup"><span data-stu-id="8a24a-119">Modifies the specified `Assembly` metadata structure.</span></span>|  
|[<span data-ttu-id="8a24a-120">Метод SetAssemblyRefProps</span><span class="sxs-lookup"><span data-stu-id="8a24a-120">SetAssemblyRefProps Method</span></span>](imetadataassemblyemit-setassemblyrefprops-method.md)|<span data-ttu-id="8a24a-121">Изменяет указанную структуру метаданных `AssemblyRef`.</span><span class="sxs-lookup"><span data-stu-id="8a24a-121">Modifies the specified `AssemblyRef` metadata structure.</span></span>|  
|[<span data-ttu-id="8a24a-122">Метод SetExportedTypeProps</span><span class="sxs-lookup"><span data-stu-id="8a24a-122">SetExportedTypeProps Method</span></span>](imetadataassemblyemit-setexportedtypeprops-method.md)|<span data-ttu-id="8a24a-123">Изменяет указанную структуру метаданных `ExportedType`.</span><span class="sxs-lookup"><span data-stu-id="8a24a-123">Modifies the specified `ExportedType` metadata structure.</span></span>|  
|[<span data-ttu-id="8a24a-124">Метод SetFileProps</span><span class="sxs-lookup"><span data-stu-id="8a24a-124">SetFileProps Method</span></span>](imetadataassemblyemit-setfileprops-method.md)|<span data-ttu-id="8a24a-125">Изменяет указанную структуру метаданных `File`.</span><span class="sxs-lookup"><span data-stu-id="8a24a-125">Modifies the specified `File` metadata structure.</span></span>|  
|[<span data-ttu-id="8a24a-126">Метод SetManifestResourceProps</span><span class="sxs-lookup"><span data-stu-id="8a24a-126">SetManifestResourceProps Method</span></span>](imetadataassemblyemit-setmanifestresourceprops-method.md)|<span data-ttu-id="8a24a-127">Изменяет указанную структуру метаданных `ManifestResource`.</span><span class="sxs-lookup"><span data-stu-id="8a24a-127">Modifies the specified `ManifestResource` metadata structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a24a-128">Remarks</span><span class="sxs-lookup"><span data-stu-id="8a24a-128">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a24a-129">Требования</span><span class="sxs-lookup"><span data-stu-id="8a24a-129">Requirements</span></span>  

 <span data-ttu-id="8a24a-130">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a24a-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a24a-131">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="8a24a-131">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8a24a-132">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8a24a-132">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8a24a-133">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a24a-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a24a-134">См. также</span><span class="sxs-lookup"><span data-stu-id="8a24a-134">See also</span></span>

- [<span data-ttu-id="8a24a-135">Интерфейсы метаданных</span><span class="sxs-lookup"><span data-stu-id="8a24a-135">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="8a24a-136">Интерфейс IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="8a24a-136">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
