---
description: 'Дополнительные сведения: метод IMetaDataImport:: EnumTypeRefs'
title: Метод IMetaDataImport::EnumTypeRefs
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeRefs
helpviewer_keywords:
- EnumTypeRefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeRefs method [.NET Framework metadata]
ms.assetid: b4896b8f-8e97-469c-8089-e72a025661b5
topic_type:
- apiref
ms.openlocfilehash: 1155357e82c08660a852225f0b1a54629cbee0ca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670636"
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="6ee78-103">Метод IMetaDataImport::EnumTypeRefs</span><span class="sxs-lookup"><span data-stu-id="6ee78-103">IMetaDataImport::EnumTypeRefs Method</span></span>

<span data-ttu-id="6ee78-104">Перечисляет токены TypeRef, определенные в текущей области метаданных.</span><span class="sxs-lookup"><span data-stu-id="6ee78-104">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ee78-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6ee78-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,
   [out] ULONG           *pcTypeRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ee78-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6ee78-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="6ee78-107">[вход, выход] Указатель на перечислитель.</span><span class="sxs-lookup"><span data-stu-id="6ee78-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="6ee78-108">При первом вызове этого метода это значение должно быть равно NULL.</span><span class="sxs-lookup"><span data-stu-id="6ee78-108">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="6ee78-109">заполняет Массив, используемый для хранения токенов TypeRef.</span><span class="sxs-lookup"><span data-stu-id="6ee78-109">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="6ee78-110">[in] Максимальный размер массива `rTypeRefs`.</span><span class="sxs-lookup"><span data-stu-id="6ee78-110">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="6ee78-111">заполняет Указатель на число токенов TypeRef, возвращаемых в `rTypeRefs` .</span><span class="sxs-lookup"><span data-stu-id="6ee78-111">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ee78-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="6ee78-112">Return Value</span></span>  
  
|<span data-ttu-id="6ee78-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6ee78-113">HRESULT</span></span>|<span data-ttu-id="6ee78-114">Описание</span><span class="sxs-lookup"><span data-stu-id="6ee78-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="6ee78-115">`EnumTypeRefs` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="6ee78-115">`EnumTypeRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="6ee78-116">Нет токенов для перечисления.</span><span class="sxs-lookup"><span data-stu-id="6ee78-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="6ee78-117">В этом случае значение `pcTypeRefs` равно нулю.</span><span class="sxs-lookup"><span data-stu-id="6ee78-117">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ee78-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="6ee78-118">Remarks</span></span>  

 <span data-ttu-id="6ee78-119">Токен TypeRef представляет ссылку на тип.</span><span class="sxs-lookup"><span data-stu-id="6ee78-119">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ee78-120">Требования</span><span class="sxs-lookup"><span data-stu-id="6ee78-120">Requirements</span></span>  

 <span data-ttu-id="6ee78-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ee78-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ee78-122">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="6ee78-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6ee78-123">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6ee78-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6ee78-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ee78-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ee78-125">См. также</span><span class="sxs-lookup"><span data-stu-id="6ee78-125">See also</span></span>

- [<span data-ttu-id="6ee78-126">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="6ee78-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="6ee78-127">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="6ee78-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
