---
description: 'Дополнительные сведения: IMetaDataEmit::D метод Ефиненестедтипе'
title: Метод IMetaDataEmit::DefineNestedType
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineNestedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineNestedType
helpviewer_keywords:
- IMetaDataEmit::DefineNestedType method [.NET Framework metadata]
- DefineNestedType method [.NET Framework metadata]
ms.assetid: 1e994de6-4628-459c-b967-b34be1e9fe4f
topic_type:
- apiref
ms.openlocfilehash: 1b0c5c8d1bffa425b2019a4434042c84a0069907
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753384"
---
# <a name="imetadataemitdefinenestedtype-method"></a><span data-ttu-id="0d83f-103">Метод IMetaDataEmit::DefineNestedType</span><span class="sxs-lookup"><span data-stu-id="0d83f-103">IMetaDataEmit::DefineNestedType Method</span></span>

<span data-ttu-id="0d83f-104">Создает сигнатуру метаданных определения типа, возвращает `mdTypeDef` маркер для этого типа и указывает, что определенный тип является членом типа, на который ссылается `tdEncloser` параметр.</span><span class="sxs-lookup"><span data-stu-id="0d83f-104">Creates the metadata signature of a type definition, returns an `mdTypeDef` token for that type, and specifies that the defined type is a member of the type referenced by the `tdEncloser` parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d83f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0d83f-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineNestedType (
    [in]  LPCWSTR     szTypeDef,  
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [in]  mdTypeDef   tdEncloser,
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d83f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0d83f-106">Parameters</span></span>  

 `szTypeDef`  
 <span data-ttu-id="0d83f-107">окне Имя типа в Юникоде.</span><span class="sxs-lookup"><span data-stu-id="0d83f-107">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="0d83f-108">[входные] `TypeDef` атрибута.</span><span class="sxs-lookup"><span data-stu-id="0d83f-108">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="0d83f-109">Это битовая маска `CorTypeAttr` значений.</span><span class="sxs-lookup"><span data-stu-id="0d83f-109">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="0d83f-110">окне Маркер базового класса.</span><span class="sxs-lookup"><span data-stu-id="0d83f-110">[in] The token of the base class.</span></span> <span data-ttu-id="0d83f-111">Это либо маркер, либо `mdTypeDef` `mdTypeRef` .</span><span class="sxs-lookup"><span data-stu-id="0d83f-111">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 <span data-ttu-id="0d83f-112">`rtkImplements`[]</span><span class="sxs-lookup"><span data-stu-id="0d83f-112">`rtkImplements`[]</span></span>  
 <span data-ttu-id="0d83f-113">окне Массив токенов, задающих интерфейсы, реализуемые этим классом или интерфейсом.</span><span class="sxs-lookup"><span data-stu-id="0d83f-113">[in] An array of tokens that specify the interfaces that this class or interface implements.</span></span>  
  
 `tdEncloser`  
 <span data-ttu-id="0d83f-114">окне Токен включающего типа.</span><span class="sxs-lookup"><span data-stu-id="0d83f-114">[in] The token of the enclosing type.</span></span> <span data-ttu-id="0d83f-115">Последний элемент массива должен быть `mdTokenNil` .</span><span class="sxs-lookup"><span data-stu-id="0d83f-115">The last element of the array must be `mdTokenNil`.</span></span>  
  
 `ptd`  
 <span data-ttu-id="0d83f-116">заполняет `mdTypeDef` Назначенный маркер.</span><span class="sxs-lookup"><span data-stu-id="0d83f-116">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d83f-117">Требования</span><span class="sxs-lookup"><span data-stu-id="0d83f-117">Requirements</span></span>  

 <span data-ttu-id="0d83f-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d83f-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d83f-119">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="0d83f-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0d83f-120">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0d83f-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0d83f-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d83f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d83f-122">См. также</span><span class="sxs-lookup"><span data-stu-id="0d83f-122">See also</span></span>

- [<span data-ttu-id="0d83f-123">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="0d83f-123">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="0d83f-124">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="0d83f-124">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
