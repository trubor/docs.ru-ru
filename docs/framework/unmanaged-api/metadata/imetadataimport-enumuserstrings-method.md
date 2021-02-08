---
description: 'Дополнительные сведения: метод IMetaDataImport:: Енумусерстрингс'
title: Метод IMetaDataImport::EnumUserStrings
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUserStrings
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUserStrings
helpviewer_keywords:
- IMetaDataImport::EnumUserStrings method [.NET Framework metadata]
- EnumUserStrings method [.NET Framework metadata]
ms.assetid: 2b1f1418-4be8-4cdb-b418-b3abccc527a7
topic_type:
- apiref
ms.openlocfilehash: a4ead696f3d924fef9ebfed5c4f1eb97eb13e14e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799321"
---
# <a name="imetadataimportenumuserstrings-method"></a><span data-ttu-id="44ce8-103">Метод IMetaDataImport::EnumUserStrings</span><span class="sxs-lookup"><span data-stu-id="44ce8-103">IMetaDataImport::EnumUserStrings Method</span></span>

<span data-ttu-id="44ce8-104">Перечисляет токены String, представляющие жестко заданные строки в текущей области метаданных.</span><span class="sxs-lookup"><span data-stu-id="44ce8-104">Enumerates String tokens representing hard-coded strings in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44ce8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="44ce8-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumUserStrings (  
   [in, out]  HCORENUM    *phEnum,  
   [out]  mdString        rStrings[],  
   [in]   ULONG           cMax,  
   [out]  ULONG           *pcStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44ce8-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="44ce8-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="44ce8-107">[вход, выход] Указатель на перечислитель.</span><span class="sxs-lookup"><span data-stu-id="44ce8-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="44ce8-108">При первом вызове этого метода это значение должно быть равно NULL.</span><span class="sxs-lookup"><span data-stu-id="44ce8-108">This must be NULL for the first call of this method.</span></span>  
  
 `rStrings`  
 <span data-ttu-id="44ce8-109">заполняет Массив, используемый для хранения токенов строк.</span><span class="sxs-lookup"><span data-stu-id="44ce8-109">[out] The array used to store the String tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="44ce8-110">[in] Максимальный размер массива `rStrings`.</span><span class="sxs-lookup"><span data-stu-id="44ce8-110">[in] The maximum size of the `rStrings` array.</span></span>  
  
 `pcStrings`  
 <span data-ttu-id="44ce8-111">заполняет Число токенов строк, возвращаемых в `rStrings` .</span><span class="sxs-lookup"><span data-stu-id="44ce8-111">[out] The number of String tokens returned in `rStrings`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44ce8-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="44ce8-112">Return Value</span></span>  
  
|<span data-ttu-id="44ce8-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="44ce8-113">HRESULT</span></span>|<span data-ttu-id="44ce8-114">Описание</span><span class="sxs-lookup"><span data-stu-id="44ce8-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="44ce8-115">`EnumUserStrings` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="44ce8-115">`EnumUserStrings` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="44ce8-116">Нет токенов для перечисления.</span><span class="sxs-lookup"><span data-stu-id="44ce8-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="44ce8-117">В этом случае значение `pcStrings` равно нулю.</span><span class="sxs-lookup"><span data-stu-id="44ce8-117">In that case, `pcStrings` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44ce8-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="44ce8-118">Remarks</span></span>  

 <span data-ttu-id="44ce8-119">Строковые токены создаются методом [IMetaDataEmit::D ефинеусерстринг](imetadataemit-defineuserstring-method.md) .</span><span class="sxs-lookup"><span data-stu-id="44ce8-119">The String tokens are created by the [IMetaDataEmit::DefineUserString](imetadataemit-defineuserstring-method.md) method.</span></span> <span data-ttu-id="44ce8-120">Этот метод предназначен для использования обозревателем метаданных, а не компилятором.</span><span class="sxs-lookup"><span data-stu-id="44ce8-120">This method is designed to be used by a metadata browser rather than by a compiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44ce8-121">Требования</span><span class="sxs-lookup"><span data-stu-id="44ce8-121">Requirements</span></span>  

 <span data-ttu-id="44ce8-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44ce8-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44ce8-123">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="44ce8-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="44ce8-124">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="44ce8-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="44ce8-125">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44ce8-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44ce8-126">См. также</span><span class="sxs-lookup"><span data-stu-id="44ce8-126">See also</span></span>

- [<span data-ttu-id="44ce8-127">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="44ce8-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="44ce8-128">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="44ce8-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
