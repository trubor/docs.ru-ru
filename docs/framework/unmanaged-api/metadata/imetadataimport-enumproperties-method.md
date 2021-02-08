---
description: 'Дополнительные сведения: метод IMetaDataImport:: Енумпропертиес'
title: Метод IMetaDataImport::EnumProperties
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumProperties
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumProperties
helpviewer_keywords:
- IMetaDataImport::EnumProperties method [.NET Framework metadata]
- EnumProperties method [.NET Framework metadata]
ms.assetid: 60573ad7-8821-4721-a068-3f7a6d25926a
topic_type:
- apiref
ms.openlocfilehash: 7503dd14668e8ea4ccf8939e67b91a41db187105
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799360"
---
# <a name="imetadataimportenumproperties-method"></a><span data-ttu-id="a424b-103">Метод IMetaDataImport::EnumProperties</span><span class="sxs-lookup"><span data-stu-id="a424b-103">IMetaDataImport::EnumProperties Method</span></span>

<span data-ttu-id="a424b-104">Перечисляет токены PropertyDef, представляющие свойства типа, на который ссылается указанный токен TypeDef.</span><span class="sxs-lookup"><span data-stu-id="a424b-104">Enumerates PropertyDef tokens representing the properties of the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a424b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a424b-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumProperties (  
   [in, out] HCORENUM    *phEnum,  
   [in]      mdTypeDef   td,  
   [out]     mdProperty  rProperties[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcProperties  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a424b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a424b-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="a424b-107">[вход, выход] Указатель на перечислитель.</span><span class="sxs-lookup"><span data-stu-id="a424b-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="a424b-108">При первом вызове этого метода это значение должно быть равно NULL.</span><span class="sxs-lookup"><span data-stu-id="a424b-108">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="a424b-109">окне Токен TypeDef, представляющий тип со свойствами для перечисления.</span><span class="sxs-lookup"><span data-stu-id="a424b-109">[in] A TypeDef token representing the type with properties to enumerate.</span></span>  
  
 `rProperties`  
 <span data-ttu-id="a424b-110">заполняет Массив, используемый для хранения маркеров Пропертидеф.</span><span class="sxs-lookup"><span data-stu-id="a424b-110">[out] The array used to store the PropertyDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a424b-111">[in] Максимальный размер массива `rProperties`.</span><span class="sxs-lookup"><span data-stu-id="a424b-111">[in] The maximum size of the `rProperties` array.</span></span>  
  
 `pcProperties`  
 <span data-ttu-id="a424b-112">заполняет Число токенов Пропертидеф, возвращаемых в `rProperties` .</span><span class="sxs-lookup"><span data-stu-id="a424b-112">[out] The number of PropertyDef tokens returned in `rProperties`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a424b-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="a424b-113">Return Value</span></span>  
  
|<span data-ttu-id="a424b-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a424b-114">HRESULT</span></span>|<span data-ttu-id="a424b-115">Описание</span><span class="sxs-lookup"><span data-stu-id="a424b-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a424b-116">`EnumProperties` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="a424b-116">`EnumProperties` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a424b-117">Нет токенов для перечисления.</span><span class="sxs-lookup"><span data-stu-id="a424b-117">There are no tokens to enumerate.</span></span> <span data-ttu-id="a424b-118">В этом случае значение `pcProperties` равно нулю.</span><span class="sxs-lookup"><span data-stu-id="a424b-118">In that case, `pcProperties` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a424b-119">Требования</span><span class="sxs-lookup"><span data-stu-id="a424b-119">Requirements</span></span>  

 <span data-ttu-id="a424b-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a424b-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a424b-121">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="a424b-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a424b-122">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a424b-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a424b-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a424b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a424b-124">См. также</span><span class="sxs-lookup"><span data-stu-id="a424b-124">See also</span></span>

- [<span data-ttu-id="a424b-125">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="a424b-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="a424b-126">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="a424b-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
