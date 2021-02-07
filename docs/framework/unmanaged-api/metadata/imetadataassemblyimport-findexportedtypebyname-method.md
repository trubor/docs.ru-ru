---
description: 'Дополнительные сведения о методе: IMetaDataAssemblyImport:: Финдекспортедтипебинаме'
title: Метод IMetaDataAssemblyImport::FindExportedTypeByName
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindExportedTypeByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindExportedTypeByName
helpviewer_keywords:
- FindExportedTypeByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindExportedTypeByName method [.NET Framework metadata]
ms.assetid: 46264b2c-574d-4dde-aafc-77187a104fdd
topic_type:
- apiref
ms.openlocfilehash: 4a2dc2b65b7f7fe6d5f2e120c635214d457991bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677994"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="a0c3d-103">Метод IMetaDataAssemblyImport::FindExportedTypeByName</span><span class="sxs-lookup"><span data-stu-id="a0c3d-103">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>

<span data-ttu-id="a0c3d-104">Возвращает указатель на экспортированный тип по заданному имени и включающему его типу.</span><span class="sxs-lookup"><span data-stu-id="a0c3d-104">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0c3d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a0c3d-105">Syntax</span></span>  
  
```cpp  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,
    [in]  mdToken           mdtExportedType,
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0c3d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a0c3d-106">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="a0c3d-107">окне Имя экспортированного типа.</span><span class="sxs-lookup"><span data-stu-id="a0c3d-107">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="a0c3d-108">окне Токен метаданных для включающего класса экспортируемого типа.</span><span class="sxs-lookup"><span data-stu-id="a0c3d-108">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="a0c3d-109">Это значение равно, `mdExportedTypeNil` Если запрошенный экспортированный тип не является вложенным типом.</span><span class="sxs-lookup"><span data-stu-id="a0c3d-109">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="a0c3d-110">заполняет Указатель на `mdExportedType` маркер, представляющий экспортированный тип.</span><span class="sxs-lookup"><span data-stu-id="a0c3d-110">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0c3d-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="a0c3d-111">Remarks</span></span>  

 <span data-ttu-id="a0c3d-112">`FindExportedTypeByName`Метод использует стандартные правила, используемые средой CLR для разрешения ссылок.</span><span class="sxs-lookup"><span data-stu-id="a0c3d-112">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0c3d-113">Требования</span><span class="sxs-lookup"><span data-stu-id="a0c3d-113">Requirements</span></span>  

 <span data-ttu-id="a0c3d-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0c3d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0c3d-115">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="a0c3d-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a0c3d-116">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a0c3d-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a0c3d-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0c3d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0c3d-118">См. также</span><span class="sxs-lookup"><span data-stu-id="a0c3d-118">See also</span></span>

- [<span data-ttu-id="a0c3d-119">Интерфейс IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="a0c3d-119">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="a0c3d-120">Обнаружение сборок в среде выполнения</span><span class="sxs-lookup"><span data-stu-id="a0c3d-120">How the Runtime Locates Assemblies</span></span>](../../deployment/how-the-runtime-locates-assemblies.md)
