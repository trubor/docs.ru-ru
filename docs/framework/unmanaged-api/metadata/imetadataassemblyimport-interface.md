---
description: 'Дополнительные сведения о: интерфейс IMetaDataAssemblyImport'
title: Интерфейс IMetaDataAssemblyImport
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport
helpviewer_keywords:
- IMetaDataAssemblyImport interface [.NET Framework metadata]
ms.assetid: 29c6fba5-4cea-417d-b484-7ed22ebff1c9
topic_type:
- apiref
ms.openlocfilehash: bb9c5163e4f5b68700e5a3836fa55edbbebac01c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753644"
---
# <a name="imetadataassemblyimport-interface"></a><span data-ttu-id="f7496-103">Интерфейс IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="f7496-103">IMetaDataAssemblyImport Interface</span></span>

<span data-ttu-id="f7496-104">Предоставляет методы для доступа и изучения содержимого манифеста сборки.</span><span class="sxs-lookup"><span data-stu-id="f7496-104">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f7496-105">Методы</span><span class="sxs-lookup"><span data-stu-id="f7496-105">Methods</span></span>  
  
|<span data-ttu-id="f7496-106">Метод</span><span class="sxs-lookup"><span data-stu-id="f7496-106">Method</span></span>|<span data-ttu-id="f7496-107">Описание</span><span class="sxs-lookup"><span data-stu-id="f7496-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f7496-108">Метод CloseEnum</span><span class="sxs-lookup"><span data-stu-id="f7496-108">CloseEnum Method</span></span>](imetadataassemblyimport-closeenum-method.md)|<span data-ttu-id="f7496-109">Освобождает дескриптор указанного перечислителя.</span><span class="sxs-lookup"><span data-stu-id="f7496-109">Releases the handle to the specified enumerator.</span></span>|  
|[<span data-ttu-id="f7496-110">Метод EnumAssemblyRefs</span><span class="sxs-lookup"><span data-stu-id="f7496-110">EnumAssemblyRefs Method</span></span>](imetadataassemblyimport-enumassemblyrefs-method.md)|<span data-ttu-id="f7496-111">Возвращает указатель интерфейса на перечислитель, содержащий `mdAssemblyRef` маркеры сборок, на которые ссылается сборка в текущей области метаданных.</span><span class="sxs-lookup"><span data-stu-id="f7496-111">Gets an interface pointer to an enumerator that contains the `mdAssemblyRef` tokens of the assemblies referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="f7496-112">Метод EnumExportedTypes</span><span class="sxs-lookup"><span data-stu-id="f7496-112">EnumExportedTypes Method</span></span>](imetadataassemblyimport-enumexportedtypes-method.md)|<span data-ttu-id="f7496-113">Возвращает указатель интерфейса на перечислитель, содержащий `mdExportedType` маркеры COM-типов, на которые ссылается сборка в текущей области метаданных.</span><span class="sxs-lookup"><span data-stu-id="f7496-113">Gets an interface pointer to an enumerator that contains the `mdExportedType` tokens of the COM types referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="f7496-114">Метод EnumFiles</span><span class="sxs-lookup"><span data-stu-id="f7496-114">EnumFiles Method</span></span>](imetadataassemblyimport-enumfiles-method.md)|<span data-ttu-id="f7496-115">Возвращает указатель интерфейса на перечислитель, содержащий `mdFile` маркеры файлов, на которые ссылается сборка в текущей области метаданных.</span><span class="sxs-lookup"><span data-stu-id="f7496-115">Gets an interface pointer to an enumerator that contains the `mdFile` tokens of the files referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="f7496-116">Метод EnumManifestResources</span><span class="sxs-lookup"><span data-stu-id="f7496-116">EnumManifestResources Method</span></span>](imetadataassemblyimport-enummanifestresources-method.md)|<span data-ttu-id="f7496-117">Возвращает указатель интерфейса на перечислитель, содержащий `mdManifestResource` маркеры ресурсов, на которые ссылается сборка в текущей области метаданных.</span><span class="sxs-lookup"><span data-stu-id="f7496-117">Gets an interface pointer to an enumerator that contains the `mdManifestResource` tokens of the resources referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="f7496-118">Метод FindAssembliesByName</span><span class="sxs-lookup"><span data-stu-id="f7496-118">FindAssembliesByName Method</span></span>](imetadataassemblyimport-findassembliesbyname-method.md)|<span data-ttu-id="f7496-119">Возвращает массив `mdAssemblyRef` токенов для сборок с указанным именем.</span><span class="sxs-lookup"><span data-stu-id="f7496-119">Gets an array of `mdAssemblyRef` tokens for the assemblies with the specified name.</span></span>|  
|[<span data-ttu-id="f7496-120">Метод FindExportedTypeByName</span><span class="sxs-lookup"><span data-stu-id="f7496-120">FindExportedTypeByName Method</span></span>](imetadataassemblyimport-findexportedtypebyname-method.md)|<span data-ttu-id="f7496-121">Возвращает `mdExportedType` токен для типа COM с указанным именем.</span><span class="sxs-lookup"><span data-stu-id="f7496-121">Gets an `mdExportedType` token for the COM type with the specified name.</span></span>|  
|[<span data-ttu-id="f7496-122">Метод FindManifestResourceByName</span><span class="sxs-lookup"><span data-stu-id="f7496-122">FindManifestResourceByName Method</span></span>](imetadataassemblyimport-findmanifestresourcebyname-method.md)|<span data-ttu-id="f7496-123">Возвращает `mdManifestResource` токен для ресурса с указанным именем.</span><span class="sxs-lookup"><span data-stu-id="f7496-123">Gets an `mdManifestResource` token for the resource with the specified name.</span></span>|  
|[<span data-ttu-id="f7496-124">Метод GetAssemblyFromScop</span><span class="sxs-lookup"><span data-stu-id="f7496-124">GetAssemblyFromScope Method</span></span>](imetadataassemblyimport-getassemblyfromscope-method.md)|<span data-ttu-id="f7496-125">Возвращает токен для сборки в текущей области метаданных.</span><span class="sxs-lookup"><span data-stu-id="f7496-125">Gets the token for the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="f7496-126">Метод GetAssemblyProps</span><span class="sxs-lookup"><span data-stu-id="f7496-126">GetAssemblyProps Method</span></span>](imetadataassemblyimport-getassemblyprops-method.md)|<span data-ttu-id="f7496-127">Возвращает параметры свойства указанной сборки.</span><span class="sxs-lookup"><span data-stu-id="f7496-127">Gets the property settings of the specified assembly.</span></span>|  
|[<span data-ttu-id="f7496-128">Метод GetAssemblyRefProps</span><span class="sxs-lookup"><span data-stu-id="f7496-128">GetAssemblyRefProps Method</span></span>](imetadataassemblyimport-getassemblyrefprops-method.md)|<span data-ttu-id="f7496-129">Возвращает параметры свойства указанного `mdAssemblyRef` токена.</span><span class="sxs-lookup"><span data-stu-id="f7496-129">Gets the property settings of the specified `mdAssemblyRef` token.</span></span>|  
|[<span data-ttu-id="f7496-130">Метод GetExportedTypeProps</span><span class="sxs-lookup"><span data-stu-id="f7496-130">GetExportedTypeProps Method</span></span>](imetadataassemblyimport-getexportedtypeprops-method.md)|<span data-ttu-id="f7496-131">Возвращает параметры свойства указанного типа COM.</span><span class="sxs-lookup"><span data-stu-id="f7496-131">Gets the property settings of the specified COM type.</span></span>|  
|[<span data-ttu-id="f7496-132">Метод GetFileProps</span><span class="sxs-lookup"><span data-stu-id="f7496-132">GetFileProps Method</span></span>](imetadataassemblyimport-getfileprops-method.md)|<span data-ttu-id="f7496-133">Возвращает настройки свойств указанного файла.</span><span class="sxs-lookup"><span data-stu-id="f7496-133">Gets the property settings of the specified file.</span></span>|  
|[<span data-ttu-id="f7496-134">Метод GetManifestResourceProps</span><span class="sxs-lookup"><span data-stu-id="f7496-134">GetManifestResourceProps Method</span></span>](imetadataassemblyimport-getmanifestresourceprops-method.md)|<span data-ttu-id="f7496-135">Возвращает параметры свойства указанного ресурса манифеста.</span><span class="sxs-lookup"><span data-stu-id="f7496-135">Gets the property settings of the specified manifest resource.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f7496-136">Требования</span><span class="sxs-lookup"><span data-stu-id="f7496-136">Requirements</span></span>  

 <span data-ttu-id="f7496-137">**Платформа:** См. раздел [требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7496-137">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7496-138">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="f7496-138">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f7496-139">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f7496-139">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f7496-140">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7496-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7496-141">См. также</span><span class="sxs-lookup"><span data-stu-id="f7496-141">See also</span></span>

- [<span data-ttu-id="f7496-142">Интерфейсы метаданных</span><span class="sxs-lookup"><span data-stu-id="f7496-142">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="f7496-143">Интерфейс IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="f7496-143">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
