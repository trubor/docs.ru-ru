---
description: 'Дополнительные сведения о методе: IMetaDataImport2:: EnumGenericParams'
title: Метод IMetaDataImport2::EnumGenericParams
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumGenericParams
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumGenericParams
helpviewer_keywords:
- EnumGenericParams method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParams method [.NET Framework metadata]
ms.assetid: b50488a5-3cf0-483c-82dc-2892a3ec61ac
topic_type:
- apiref
ms.openlocfilehash: 9d4e9d163da07ec4a3af1aa628b8b6ec4b2338fe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720947"
---
# <a name="imetadataimport2enumgenericparams-method"></a><span data-ttu-id="0c996-103">Метод IMetaDataImport2::EnumGenericParams</span><span class="sxs-lookup"><span data-stu-id="0c996-103">IMetaDataImport2::EnumGenericParams Method</span></span>

<span data-ttu-id="0c996-104">Возвращает перечислитель для массива маркеров универсальных параметров, связанных с указанным маркером TypeDef или MethodDef.</span><span class="sxs-lookup"><span data-stu-id="0c996-104">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c996-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0c996-105">Syntax</span></span>  
  
```cpp
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],
   [in]  ULONG            cMax,
   [out] ULONG            *pcGenericParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c996-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0c996-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="0c996-107">[вход, выход] Указатель на перечислитель.</span><span class="sxs-lookup"><span data-stu-id="0c996-107">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="0c996-108">окне Маркер TypeDef или MethodDef, универсальные параметры которого необходимо перечислить.</span><span class="sxs-lookup"><span data-stu-id="0c996-108">[in] The TypeDef or MethodDef token whose generic parameters are to be enumerated.</span></span>  
  
 `rGenericParams`  
 <span data-ttu-id="0c996-109">заполняет Массив универсальных параметров для перечисления.</span><span class="sxs-lookup"><span data-stu-id="0c996-109">[out] The array of generic parameters to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="0c996-110">окне Запрошенное максимальное число токенов для размещения в `rGenericParams` .</span><span class="sxs-lookup"><span data-stu-id="0c996-110">[in] The requested maximum number of tokens to place in `rGenericParams`.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="0c996-111">заполняет Возвращенное число токенов, помещенных в `rGenericParams` .</span><span class="sxs-lookup"><span data-stu-id="0c996-111">[out] The returned number of tokens placed in `rGenericParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0c996-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="0c996-112">Return Value</span></span>  
  
|<span data-ttu-id="0c996-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0c996-113">HRESULT</span></span>|<span data-ttu-id="0c996-114">Описание</span><span class="sxs-lookup"><span data-stu-id="0c996-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="0c996-115">`EnumGenericParams` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="0c996-115">`EnumGenericParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="0c996-116">`phEnum` не содержит элементов Member.</span><span class="sxs-lookup"><span data-stu-id="0c996-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="0c996-117">В этом случае `pcGenericParams` имеет значение 0 (ноль).</span><span class="sxs-lookup"><span data-stu-id="0c996-117">In this case, `pcGenericParams` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0c996-118">Требования</span><span class="sxs-lookup"><span data-stu-id="0c996-118">Requirements</span></span>  

 <span data-ttu-id="0c996-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c996-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c996-120">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="0c996-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0c996-121">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0c996-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0c996-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c996-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c996-123">См. также</span><span class="sxs-lookup"><span data-stu-id="0c996-123">See also</span></span>

- [<span data-ttu-id="0c996-124">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="0c996-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="0c996-125">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="0c996-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
