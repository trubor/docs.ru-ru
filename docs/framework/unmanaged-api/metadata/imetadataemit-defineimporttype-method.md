---
description: 'Дополнительные сведения: IMetaDataEmit::D метод Ефинеимпорттипе'
title: Метод IMetaDataEmit::DefineImportType
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportType
helpviewer_keywords:
- DefineImportType method [.NET Framework metadata]
- IMetaDataEmit::DefineImportType method [.NET Framework metadata]
ms.assetid: 37fd27af-8062-4904-ace4-51bb78ec600a
topic_type:
- apiref
ms.openlocfilehash: 7afe0fe400e4eb6e177a06e00b2d69202820804c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753436"
---
# <a name="imetadataemitdefineimporttype-method"></a><span data-ttu-id="f91ad-103">Метод IMetaDataEmit::DefineImportType</span><span class="sxs-lookup"><span data-stu-id="f91ad-103">IMetaDataEmit::DefineImportType Method</span></span>

<span data-ttu-id="f91ad-104">Создает ссылку на указанный тип, определенный вне текущей области, и определяет маркер для этой ссылки.</span><span class="sxs-lookup"><span data-stu-id="f91ad-104">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f91ad-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f91ad-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineImportType (
    [in]  IMetaDataAssemblyImport  *pAssemImport,
    [in]  const void               *pbHashValue,
    [in]  ULONG                    cbHashValue,
    [in]  IMetaDataImport          *pImport,
    [in]  mdTypeDef                tdImport,
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,
    [out] mdTypeRef                *ptr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f91ad-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f91ad-106">Parameters</span></span>  

 `pAssemImport`  
 <span data-ttu-id="f91ad-107">окне Интерфейс [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) , представляющий сборку, из которой импортируется целевой тип.</span><span class="sxs-lookup"><span data-stu-id="f91ad-107">[in] An [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="f91ad-108">окне Массив, содержащий хэш для сборки, заданной параметром `pAssemImport` .</span><span class="sxs-lookup"><span data-stu-id="f91ad-108">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="f91ad-109">[in] Число байтов в массиве `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="f91ad-109">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="f91ad-110">окне Интерфейс [IMetaDataImport](imetadataimport-interface.md) , представляющий область метаданных, из которой импортируется целевой тип.</span><span class="sxs-lookup"><span data-stu-id="f91ad-110">[in] An [IMetaDataImport](imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span></span>  
  
 `tdImport`  
 <span data-ttu-id="f91ad-111">окне `mdTypeDef` Токен, указывающий тип целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="f91ad-111">[in] An `mdTypeDef` token that specifies the target type.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="f91ad-112">окне Интерфейс [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) , представляющий сборку, в которую импортируется целевой тип.</span><span class="sxs-lookup"><span data-stu-id="f91ad-112">[in] An [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span></span>  
  
 `ptr`  
 <span data-ttu-id="f91ad-113">заполняет `mdTypeRef` Токен, определенный в текущей области для ссылки на тип.</span><span class="sxs-lookup"><span data-stu-id="f91ad-113">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f91ad-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="f91ad-114">Remarks</span></span>  

 <span data-ttu-id="f91ad-115">Перед вызовом метода [IMetaDataEmit::D ефинеимпортмембер](imetadataemit-defineimportmember-method.md) можно использовать `DefineImportType` метод для создания ссылки на тип в текущей области для родительского класса члена или родительского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="f91ad-115">Prior to calling the [IMetaDataEmit::DefineImportMember](imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f91ad-116">Требования</span><span class="sxs-lookup"><span data-stu-id="f91ad-116">Requirements</span></span>  

 <span data-ttu-id="f91ad-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f91ad-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f91ad-118">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="f91ad-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f91ad-119">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f91ad-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f91ad-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f91ad-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f91ad-121">См. также</span><span class="sxs-lookup"><span data-stu-id="f91ad-121">See also</span></span>

- [<span data-ttu-id="f91ad-122">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="f91ad-122">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="f91ad-123">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="f91ad-123">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
