---
description: 'Дополнительные сведения о методе: IMetaDataAssemblyImport:: GetExportedTypeProps'
title: Метод IMetaDataAssemblyImport::GetExportedTypeProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetExportedTypeProps
helpviewer_keywords:
- GetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 25ca7623-5a55-4f09-b44a-36b03d142278
topic_type:
- apiref
ms.openlocfilehash: 894fb65fb6de76a218489b2a85a2d3c20c572789
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784123"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a><span data-ttu-id="80e28-103">Метод IMetaDataAssemblyImport::GetExportedTypeProps</span><span class="sxs-lookup"><span data-stu-id="80e28-103">IMetaDataAssemblyImport::GetExportedTypeProps Method</span></span>

<span data-ttu-id="80e28-104">Возвращает набор свойств экспортированного типа с указанной сигнатурой метаданных.</span><span class="sxs-lookup"><span data-stu-id="80e28-104">Gets the set of properties of the exported type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80e28-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="80e28-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExportedTypeProps (  
    [in]  mdExportedType    mdct,
    [out] LPWSTR            szName,
    [in]  ULONG             cchName,
    [out] ULONG             *pchName,
    [out] mdToken           *ptkImplementation,
    [out] mdTypeDef         *ptkTypeDef,
    [out] DWORD             *pdwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80e28-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="80e28-106">Parameters</span></span>  

 `mdct`  
 <span data-ttu-id="80e28-107">окне `mdExportedType` Токен метаданных, представляющий экспортированный тип.</span><span class="sxs-lookup"><span data-stu-id="80e28-107">[in] An `mdExportedType` metadata token that represents the exported type.</span></span>  
  
 `szName`  
 <span data-ttu-id="80e28-108">заполняет Имя экспортированного типа.</span><span class="sxs-lookup"><span data-stu-id="80e28-108">[out] The name of the exported type.</span></span>  
  
 `cchName`  
 <span data-ttu-id="80e28-109">окне Размер (в расширенных символах) `szName` .</span><span class="sxs-lookup"><span data-stu-id="80e28-109">[in] The size, in wide characters, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="80e28-110">заполняет Число расширенных символов, фактически возвращаемых в `szName`</span><span class="sxs-lookup"><span data-stu-id="80e28-110">[out] The number of wide characters actually returned in `szName`</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="80e28-111">заполняет `mdFile` `mdAssemblyRef` Маркер метаданных, или `mdExportedType` , который содержит или разрешает доступ к свойствам экспортированного типа.</span><span class="sxs-lookup"><span data-stu-id="80e28-111">[out] An `mdFile`, `mdAssemblyRef`, or `mdExportedType` metadata token that contains or allows access to the properties of the exported type.</span></span>  
  
 `ptkTypeDef`  
 <span data-ttu-id="80e28-112">заполняет Указатель на `mdTypeDef` маркер, представляющий тип в файле.</span><span class="sxs-lookup"><span data-stu-id="80e28-112">[out] A pointer to an `mdTypeDef` token that represents a type in the file.</span></span>  
  
 `pdwExportedTypeFlags`  
 <span data-ttu-id="80e28-113">заполняет Указатель на флаги, описывающие метаданные, применяемые к экспортируемому типу.</span><span class="sxs-lookup"><span data-stu-id="80e28-113">[out] A pointer to the flags that describe the metadata applied to the exported type.</span></span> <span data-ttu-id="80e28-114">Значение Flags может быть одним или несколькими [кортипеаттр](cortypeattr-enumeration.md) значениями.</span><span class="sxs-lookup"><span data-stu-id="80e28-114">The flags value can be one or more [CorTypeAttr](cortypeattr-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80e28-115">Требования</span><span class="sxs-lookup"><span data-stu-id="80e28-115">Requirements</span></span>  

 <span data-ttu-id="80e28-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80e28-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80e28-117">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="80e28-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="80e28-118">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="80e28-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="80e28-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80e28-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80e28-120">См. также</span><span class="sxs-lookup"><span data-stu-id="80e28-120">See also</span></span>

- [<span data-ttu-id="80e28-121">Интерфейс IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="80e28-121">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
