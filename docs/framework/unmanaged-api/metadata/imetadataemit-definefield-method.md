---
description: 'Дополнительные сведения: IMetaDataEmit::D метод Ефинефиелд'
title: Метод IMetaDataEmit::DefineField
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type:
- apiref
ms.openlocfilehash: 7636b1521de721cc183305e8a0763ff0a61f331b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753450"
---
# <a name="imetadataemitdefinefield-method"></a><span data-ttu-id="3e88b-103">Метод IMetaDataEmit::DefineField</span><span class="sxs-lookup"><span data-stu-id="3e88b-103">IMetaDataEmit::DefineField Method</span></span>

<span data-ttu-id="3e88b-104">Создает определение для поля с указанной сигнатурой метаданных и получает маркер для этого определения поля.</span><span class="sxs-lookup"><span data-stu-id="3e88b-104">Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e88b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3e88b-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineField (
    [in]  mdTypeDef   td,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwFieldFlags,
    [in]  PCCOR_SIGNATURE pvSigBlob,
    [in]  ULONG       cbSigBlob,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue,
    [out] mdFieldDef  *pmd
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e88b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="3e88b-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="3e88b-107">окне `mdTypeDef` Токен для включающего класса или интерфейса.</span><span class="sxs-lookup"><span data-stu-id="3e88b-107">[in] The `mdTypeDef` token for the enclosing class or interface.</span></span>  
  
 `szName`  
 <span data-ttu-id="3e88b-108">окне Имя поля в Юникоде.</span><span class="sxs-lookup"><span data-stu-id="3e88b-108">[in] The field name in Unicode.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="3e88b-109">окне Атрибуты поля.</span><span class="sxs-lookup"><span data-stu-id="3e88b-109">[in] The field attributes.</span></span> <span data-ttu-id="3e88b-110">Это битовая маска `CorFieldAttr` значений.</span><span class="sxs-lookup"><span data-stu-id="3e88b-110">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="3e88b-111">окне Подпись поля в виде большого двоичного объекта.</span><span class="sxs-lookup"><span data-stu-id="3e88b-111">[in] The field signature as a BLOB.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="3e88b-112">окне Число байтов в `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="3e88b-112">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="3e88b-113">окне `ELEMENT_TYPE_` *\** Значение для постоянного значения.</span><span class="sxs-lookup"><span data-stu-id="3e88b-113">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="3e88b-114">Это `CorElementType` значение.</span><span class="sxs-lookup"><span data-stu-id="3e88b-114">This is a `CorElementType` value.</span></span> <span data-ttu-id="3e88b-115">Если для поля не определено постоянное значение, используйте `ELEMENT_TYPE_END` .</span><span class="sxs-lookup"><span data-stu-id="3e88b-115">If not defining a constant value for the field, use `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="3e88b-116">окне Постоянное значение для поля.</span><span class="sxs-lookup"><span data-stu-id="3e88b-116">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="3e88b-117">окне Размер символов (в Юникоде) `pValue` .</span><span class="sxs-lookup"><span data-stu-id="3e88b-117">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
 `pmd`  
 <span data-ttu-id="3e88b-118">заполняет `mdFieldDef` Назначенный маркер.</span><span class="sxs-lookup"><span data-stu-id="3e88b-118">[out] The `mdFieldDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e88b-119">Требования</span><span class="sxs-lookup"><span data-stu-id="3e88b-119">Requirements</span></span>  

 <span data-ttu-id="3e88b-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e88b-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e88b-121">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="3e88b-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3e88b-122">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3e88b-122">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3e88b-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e88b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e88b-124">См. также</span><span class="sxs-lookup"><span data-stu-id="3e88b-124">See also</span></span>

- [<span data-ttu-id="3e88b-125">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="3e88b-125">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="3e88b-126">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="3e88b-126">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
