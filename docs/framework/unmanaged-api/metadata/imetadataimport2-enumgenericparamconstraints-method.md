---
description: 'Дополнительные сведения о методе: IMetaDataImport2:: Енумженерикпарамконстраинтс'
title: Метод IMetaDataImport2::EnumGenericParamConstraints
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumGenericParamConstraints
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumGenericParamConstraints
helpviewer_keywords:
- EnumGenericParamConstraints method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParamConstraints method [.NET Framework metadata]
ms.assetid: 8a7d4e40-28fe-4e14-b801-4049880130e7
topic_type:
- apiref
ms.openlocfilehash: d7ee44059796a943411750b66f5b45034f871a0b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677552"
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="c14f6-103">Метод IMetaDataImport2::EnumGenericParamConstraints</span><span class="sxs-lookup"><span data-stu-id="c14f6-103">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>

<span data-ttu-id="c14f6-104">Возвращает перечислитель для массива ограничений универсальных параметров, связанных с универсальным параметром, представленным указанным токеном.</span><span class="sxs-lookup"><span data-stu-id="c14f6-104">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c14f6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c14f6-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c14f6-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c14f6-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="c14f6-107">[вход, выход] Указатель на перечислитель.</span><span class="sxs-lookup"><span data-stu-id="c14f6-107">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="c14f6-108">окне   Токен, представляющий универсальный параметр, ограничения которого необходимо перечислить.</span><span class="sxs-lookup"><span data-stu-id="c14f6-108">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="c14f6-109">заполняет Массив ограничений универсального параметра для перечисления.</span><span class="sxs-lookup"><span data-stu-id="c14f6-109">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c14f6-110">окне   Запрошенное максимальное число токенов для размещения в `rGenericParamConstraints` .</span><span class="sxs-lookup"><span data-stu-id="c14f6-110">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="c14f6-111">заполняет Указатель на число токенов, помещенных в `rGenericParamConstraints` .</span><span class="sxs-lookup"><span data-stu-id="c14f6-111">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c14f6-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="c14f6-112">Return Value</span></span>  
  
|<span data-ttu-id="c14f6-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c14f6-113">HRESULT</span></span>|<span data-ttu-id="c14f6-114">Описание</span><span class="sxs-lookup"><span data-stu-id="c14f6-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c14f6-115">`EnumGenericParameterConstraints` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="c14f6-115">`EnumGenericParameterConstraints` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c14f6-116">`phEnum` не содержит элементов Member.</span><span class="sxs-lookup"><span data-stu-id="c14f6-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="c14f6-117">В этом случае `pcGenericParameterConstraints` имеет значение 0 (ноль).</span><span class="sxs-lookup"><span data-stu-id="c14f6-117">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c14f6-118">Требования</span><span class="sxs-lookup"><span data-stu-id="c14f6-118">Requirements</span></span>  

 <span data-ttu-id="c14f6-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c14f6-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c14f6-120">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="c14f6-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c14f6-121">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c14f6-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c14f6-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c14f6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c14f6-123">См. также</span><span class="sxs-lookup"><span data-stu-id="c14f6-123">See also</span></span>

- [<span data-ttu-id="c14f6-124">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="c14f6-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="c14f6-125">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="c14f6-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
