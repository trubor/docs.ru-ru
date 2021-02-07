---
description: 'Дополнительные сведения о методе: IMetaDataAssemblyEmit::D Ефиникспортедтипе'
title: Метод IMetaDataAssemblyEmit::DefineExportedType
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineExportedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type:
- apiref
ms.openlocfilehash: 0da1b1eb0880b0ba9df0ba9ad70b460163dffc39
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671117"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a><span data-ttu-id="4c9d9-103">Метод IMetaDataAssemblyEmit::DefineExportedType</span><span class="sxs-lookup"><span data-stu-id="4c9d9-103">IMetaDataAssemblyEmit::DefineExportedType Method</span></span>

<span data-ttu-id="4c9d9-104">Создает структуру `ExportedType`, содержащую метаданные для указанного экспортированного типа, и возвращает связанный токен метаданных.</span><span class="sxs-lookup"><span data-stu-id="4c9d9-104">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c9d9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4c9d9-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c9d9-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="4c9d9-106">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="4c9d9-107">окне Имя экспортируемого типа.</span><span class="sxs-lookup"><span data-stu-id="4c9d9-107">[in] The name of type to be exported.</span></span> <span data-ttu-id="4c9d9-108">Для версии 1,1 среды CLR имя экспортируемого типа должно точно совпадать с именем, заданным в `TypeDef` для типа.</span><span class="sxs-lookup"><span data-stu-id="4c9d9-108">For version 1.1 of the common language runtime, the name of the exported type must exactly match the name given in the `TypeDef` for the type.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="4c9d9-109">окне Токен, указывающий, где реализуется экспортируемый тип.</span><span class="sxs-lookup"><span data-stu-id="4c9d9-109">[in] A token specifying where the exported type is implemented.</span></span> <span data-ttu-id="4c9d9-110">Допустимые значения и их связанное с ними значение:</span><span class="sxs-lookup"><span data-stu-id="4c9d9-110">The valid values and their associated meanings are:</span></span>  
  
- <span data-ttu-id="4c9d9-111">`mdFile` Тип реализуется в другом файле в этой сборке.</span><span class="sxs-lookup"><span data-stu-id="4c9d9-111">`mdFile` The type is implemented in a different file within this assembly.</span></span>  
  
- <span data-ttu-id="4c9d9-112">`mdAssemblyRef` Тип реализован в другой сборке.</span><span class="sxs-lookup"><span data-stu-id="4c9d9-112">`mdAssemblyRef` The type is implemented in a different assembly.</span></span>  
  
- <span data-ttu-id="4c9d9-113">`mdExportedTYpe` Тип вложен в другой тип.</span><span class="sxs-lookup"><span data-stu-id="4c9d9-113">`mdExportedTYpe` The type is nested within some other type.</span></span>  
  
- <span data-ttu-id="4c9d9-114">`mdFileNil` Тип находится в том же файле, что и манифест, и не является вложенным типом.</span><span class="sxs-lookup"><span data-stu-id="4c9d9-114">`mdFileNil` The type is in the same file as the manifest and is not a nested type.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="4c9d9-115">окне Токен метаданных, указывающий тип для экспорта.</span><span class="sxs-lookup"><span data-stu-id="4c9d9-115">[in] A token to the metadata that specifies the type to be exported.</span></span> <span data-ttu-id="4c9d9-116">Это значение вводится в `TypeDef` таблицу в файле, который реализует тип, и имеет смысл только в том случае, если этот файл находится в этой сборке.</span><span class="sxs-lookup"><span data-stu-id="4c9d9-116">This value is entered in the `TypeDef` table in the file that implements the type and is relevant only if that file is in this assembly.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="4c9d9-117">окне Побитовое сочетание значений перечисления [кортипеаттр](cortypeattr-enumeration.md) , определяющих настройки свойств для экспортируемого типа.</span><span class="sxs-lookup"><span data-stu-id="4c9d9-117">[in] A bitwise combination of [CorTypeAttr](cortypeattr-enumeration.md) enumeration values that define the property settings for the exported type.</span></span>  
  
 `pmdct`  
 <span data-ttu-id="4c9d9-118">заполняет Указатель на возвращаемый маркер метаданных, указывающий на экспортируемый тип.</span><span class="sxs-lookup"><span data-stu-id="4c9d9-118">[out] A pointer to the returned metadata token that indicates the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c9d9-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="4c9d9-119">Remarks</span></span>  

 <span data-ttu-id="4c9d9-120">`ExportedType`Структура метаданных должна быть определена для каждого типа, предоставляемого этой сборкой и реализованного в модуле, отличном от того, который содержит манифест.</span><span class="sxs-lookup"><span data-stu-id="4c9d9-120">An `ExportedType` metadata structure must be defined for each type that is exposed by this assembly and that is implemented in a module other than the one containing the manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c9d9-121">Требования</span><span class="sxs-lookup"><span data-stu-id="4c9d9-121">Requirements</span></span>  

 <span data-ttu-id="4c9d9-122">**Платформа:** См. раздел [требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c9d9-122">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c9d9-123">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="4c9d9-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4c9d9-124">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4c9d9-124">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4c9d9-125">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c9d9-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c9d9-126">См. также</span><span class="sxs-lookup"><span data-stu-id="4c9d9-126">See also</span></span>

- [<span data-ttu-id="4c9d9-127">Интерфейс IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="4c9d9-127">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
