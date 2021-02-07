---
description: 'Дополнительные сведения: Метод IMetaDataEmit:: Сеттипедефпропс'
title: Метод IMetaDataEmit::SetTypeDefProps
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetTypeDefProps
helpviewer_keywords:
- SetTypeDefProps method [.NET Framework metadata]
- IMetaDataEmit::SetTypeDefProps method [.NET Framework metadata]
ms.assetid: 480d596a-759f-4d29-ac1a-3dbff8f3544d
topic_type:
- apiref
ms.openlocfilehash: 1160d20e7ceb422390f8cd725a75fdb4f42318e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706504"
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="86e09-103">Метод IMetaDataEmit::SetTypeDefProps</span><span class="sxs-lookup"><span data-stu-id="86e09-103">IMetaDataEmit::SetTypeDefProps Method</span></span>

<span data-ttu-id="86e09-104">Задает функции типа, определенного при предыдущем вызове метода [IMetaDataEmit::D ефинетипедеф](imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="86e09-104">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86e09-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="86e09-105">Syntax</span></span>  
  
```cpp  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[]
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86e09-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="86e09-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="86e09-107">окне `mdTypeDef` Маркер, полученный из исходного вызова [IMetaDataEmit::D ефинетипедеф](imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="86e09-107">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="86e09-108">[входные] `TypeDef` атрибута.</span><span class="sxs-lookup"><span data-stu-id="86e09-108">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="86e09-109">Это битовая маска `CorTypeAttr` значений.</span><span class="sxs-lookup"><span data-stu-id="86e09-109">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="86e09-110">окне `mdToken` Класс базового класса.</span><span class="sxs-lookup"><span data-stu-id="86e09-110">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="86e09-111">Получено из предыдущего вызова [IMetaDataEmit::D ефинеимпорттипе](imetadataemit-defineimporttype-method.md)или `null` .</span><span class="sxs-lookup"><span data-stu-id="86e09-111">Obtained from a previous call to [IMetaDataEmit::DefineImportType](imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="86e09-112">окне Массив токенов для интерфейсов, реализуемых этим типом.</span><span class="sxs-lookup"><span data-stu-id="86e09-112">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="86e09-113">Эти `mdTypeRef` токены получаются с помощью [IMetaDataEmit::D ефинеимпорттипе](imetadataemit-defineimporttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="86e09-113">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="86e09-114">Последним элементом массива должен быть `mdTokenNil` .</span><span class="sxs-lookup"><span data-stu-id="86e09-114">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86e09-115">Требования</span><span class="sxs-lookup"><span data-stu-id="86e09-115">Requirements</span></span>  

 <span data-ttu-id="86e09-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86e09-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86e09-117">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="86e09-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="86e09-118">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="86e09-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="86e09-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86e09-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86e09-120">См. также</span><span class="sxs-lookup"><span data-stu-id="86e09-120">See also</span></span>

- [<span data-ttu-id="86e09-121">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="86e09-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="86e09-122">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="86e09-122">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
