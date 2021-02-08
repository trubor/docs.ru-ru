---
description: 'Дополнительные сведения о методе: IMetaDataAssemblyImport:: Финдманифестресаурцебинаме'
title: Метод IMetaDataAssemblyImport::FindManifestResourceByName
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindManifestResourceByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindManifestResourceByName
helpviewer_keywords:
- FindManifestResourceByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindManifestResourceByName method [.NET Framework metadata]
ms.assetid: 7b72fa11-3866-402b-bdea-2b966b77cfe0
topic_type:
- apiref
ms.openlocfilehash: 1d1312277675a1f2bf213221ab8d9d2a584733a4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784175"
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="e3e78-103">Метод IMetaDataAssemblyImport::FindManifestResourceByName</span><span class="sxs-lookup"><span data-stu-id="e3e78-103">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>

<span data-ttu-id="e3e78-104">Возвращает указатель на ресурс манифеста с указанным именем.</span><span class="sxs-lookup"><span data-stu-id="e3e78-104">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3e78-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e3e78-105">Syntax</span></span>  
  
```cpp
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,
    [out] mdManifestResource     *ptkManifestResource  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="e3e78-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e3e78-106">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="e3e78-107">[in] Имя ресурса.</span><span class="sxs-lookup"><span data-stu-id="e3e78-107">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="e3e78-108">заполняет Массив, используемый для хранения `mdManifestResource` маркеров метаданных, каждый из которых представляет ресурс манифеста.</span><span class="sxs-lookup"><span data-stu-id="e3e78-108">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3e78-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="e3e78-109">Remarks</span></span>  

 <span data-ttu-id="e3e78-110">`FindManifestResourceByName`Метод использует стандартные правила, используемые средой CLR для разрешения ссылок.</span><span class="sxs-lookup"><span data-stu-id="e3e78-110">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3e78-111">Требования</span><span class="sxs-lookup"><span data-stu-id="e3e78-111">Requirements</span></span>  

 <span data-ttu-id="e3e78-112">**Платформа:** См. раздел [требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3e78-112">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3e78-113">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="e3e78-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e3e78-114">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e3e78-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e3e78-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3e78-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3e78-116">См. также</span><span class="sxs-lookup"><span data-stu-id="e3e78-116">See also</span></span>

- [<span data-ttu-id="e3e78-117">Интерфейс IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="e3e78-117">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="e3e78-118">Обнаружение сборок в среде выполнения</span><span class="sxs-lookup"><span data-stu-id="e3e78-118">How the Runtime Locates Assemblies</span></span>](../../deployment/how-the-runtime-locates-assemblies.md)
