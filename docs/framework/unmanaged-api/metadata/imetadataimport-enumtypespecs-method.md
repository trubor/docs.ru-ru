---
description: 'Дополнительные сведения: метод IMetaDataImport:: Енумтипеспекс'
title: Метод IMetaDataImport::EnumTypeSpecs
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeSpecs
helpviewer_keywords:
- EnumTypeSpecs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeSpecs method [.NET Framework metadata]
ms.assetid: 75331c7b-988b-436c-9eb9-a270d37b4f06
topic_type:
- apiref
ms.openlocfilehash: 7446bbf3296ffb6cfa3a20f594b4a7da22acff5c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799347"
---
# <a name="imetadataimportenumtypespecs-method"></a><span data-ttu-id="eee87-103">Метод IMetaDataImport::EnumTypeSpecs</span><span class="sxs-lookup"><span data-stu-id="eee87-103">IMetaDataImport::EnumTypeSpecs Method</span></span>

<span data-ttu-id="eee87-104">Перечисляет токены TypeSpec, определенные в текущей области метаданных.</span><span class="sxs-lookup"><span data-stu-id="eee87-104">Enumerates TypeSpec tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eee87-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="eee87-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eee87-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="eee87-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="eee87-107">[вход, выход] Указатель на перечислитель.</span><span class="sxs-lookup"><span data-stu-id="eee87-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="eee87-108">При первом вызове этого метода это значение должно быть равно NULL.</span><span class="sxs-lookup"><span data-stu-id="eee87-108">This value must be NULL for the first call of this method.</span></span>  
  
 `rTypeSpecs`  
 <span data-ttu-id="eee87-109">заполняет Массив, используемый для хранения токенов TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="eee87-109">[out] The array used to store the TypeSpec tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="eee87-110">[in] Максимальный размер массива `rTypeSpecs`.</span><span class="sxs-lookup"><span data-stu-id="eee87-110">[in] The maximum size of the `rTypeSpecs` array.</span></span>  
  
 `pcTypeSpecs`  
 <span data-ttu-id="eee87-111">заполняет Число токенов TypeSpec, возвращаемых в `rTypeSpecs` .</span><span class="sxs-lookup"><span data-stu-id="eee87-111">[out] The number of TypeSpec tokens returned in `rTypeSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eee87-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="eee87-112">Return Value</span></span>  
  
|<span data-ttu-id="eee87-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eee87-113">HRESULT</span></span>|<span data-ttu-id="eee87-114">Описание</span><span class="sxs-lookup"><span data-stu-id="eee87-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="eee87-115">`EnumTypeSpecs` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="eee87-115">`EnumTypeSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="eee87-116">Нет токенов для перечисления.</span><span class="sxs-lookup"><span data-stu-id="eee87-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="eee87-117">В этом случае значение `pcTypeSpecs` равно нулю.</span><span class="sxs-lookup"><span data-stu-id="eee87-117">In that case, `pcTypeSpecs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eee87-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="eee87-118">Remarks</span></span>  

 <span data-ttu-id="eee87-119">Токены TypeSpec создаются методом [IMetaDataEmit:: жеттокенфромтипеспек](imetadataemit-gettokenfromtypespec-method.md) .</span><span class="sxs-lookup"><span data-stu-id="eee87-119">The TypeSpec tokens are created by the [IMetaDataEmit::GetTokenFromTypeSpec](imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eee87-120">Требования</span><span class="sxs-lookup"><span data-stu-id="eee87-120">Requirements</span></span>  

 <span data-ttu-id="eee87-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eee87-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eee87-122">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="eee87-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="eee87-123">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="eee87-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="eee87-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eee87-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eee87-125">См. также</span><span class="sxs-lookup"><span data-stu-id="eee87-125">See also</span></span>

- [<span data-ttu-id="eee87-126">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="eee87-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="eee87-127">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="eee87-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
