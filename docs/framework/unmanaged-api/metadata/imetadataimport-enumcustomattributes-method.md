---
description: 'Дополнительные сведения: метод IMetaDataImport:: EnumCustomAttributes'
title: Метод IMetaDataImport::EnumCustomAttributes
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumCustomAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method [.NET Framework metadata]
- IMetaDataImport::EnumCustomAttributes method [.NET Framework metadata]
ms.assetid: 798513a0-68b1-4d04-bc5b-782a4445ea68
topic_type:
- apiref
ms.openlocfilehash: 1c55ea4b72483e5dc30425172b95be7f77e8a62a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677591"
---
# <a name="imetadataimportenumcustomattributes-method"></a><span data-ttu-id="c3db3-103">Метод IMetaDataImport::EnumCustomAttributes</span><span class="sxs-lookup"><span data-stu-id="c3db3-103">IMetaDataImport::EnumCustomAttributes Method</span></span>

<span data-ttu-id="c3db3-104">Перечисляет токены определения пользовательских атрибутов, связанные с указанным типом или членом.</span><span class="sxs-lookup"><span data-stu-id="c3db3-104">Enumerates custom attribute-definition tokens associated with the specified type or member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3db3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c3db3-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes (
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,
   [in]  mdToken            tkType,
   [out] mdCustomAttribute  rCustomAttributes[],
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3db3-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c3db3-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="c3db3-107">[вход, выход] Указатель на возвращаемый перечислитель.</span><span class="sxs-lookup"><span data-stu-id="c3db3-107">[in, out] A pointer to the returned enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="c3db3-108">окне Токен для области перечисления или ноль для всех настраиваемых атрибутов.</span><span class="sxs-lookup"><span data-stu-id="c3db3-108">[in] A token for the scope of the enumeration, or zero for all custom attributes.</span></span>  
  
 `tkType`  
 <span data-ttu-id="c3db3-109">окне Токен для конструктора типа атрибутов для перечисления или `null` для всех типов.</span><span class="sxs-lookup"><span data-stu-id="c3db3-109">[in] A token for the constructor of the type of the attributes to be enumerated, or `null` for all types.</span></span>  
  
 `rCustomAttributes`  
 <span data-ttu-id="c3db3-110">заполняет Массив токенов настраиваемых атрибутов.</span><span class="sxs-lookup"><span data-stu-id="c3db3-110">[out] An array of custom attribute tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c3db3-111">[in] Максимальный размер массива `rCustomAttributes`.</span><span class="sxs-lookup"><span data-stu-id="c3db3-111">[in] The maximum size of the `rCustomAttributes` array.</span></span>  
  
 `pcCustomAttributes`  
 <span data-ttu-id="c3db3-112">[out, необязательно] Фактическое число значений токена, возвращаемых в `rCustomAttributes` .</span><span class="sxs-lookup"><span data-stu-id="c3db3-112">[out, optional] The actual number of token values returned in `rCustomAttributes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3db3-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="c3db3-113">Return Value</span></span>  
  
|<span data-ttu-id="c3db3-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c3db3-114">HRESULT</span></span>|<span data-ttu-id="c3db3-115">Описание</span><span class="sxs-lookup"><span data-stu-id="c3db3-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c3db3-116">`EnumCustomAttributes` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="c3db3-116">`EnumCustomAttributes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c3db3-117">Нет настраиваемых атрибутов для перечисления.</span><span class="sxs-lookup"><span data-stu-id="c3db3-117">There are no custom attributes to enumerate.</span></span> <span data-ttu-id="c3db3-118">В этом случае значение `pcCustomAttributes` равно нулю.</span><span class="sxs-lookup"><span data-stu-id="c3db3-118">In that case, `pcCustomAttributes` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c3db3-119">Требования</span><span class="sxs-lookup"><span data-stu-id="c3db3-119">Requirements</span></span>  

 <span data-ttu-id="c3db3-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3db3-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3db3-121">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="c3db3-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c3db3-122">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c3db3-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c3db3-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3db3-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3db3-124">См. также</span><span class="sxs-lookup"><span data-stu-id="c3db3-124">See also</span></span>

- [<span data-ttu-id="c3db3-125">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="c3db3-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="c3db3-126">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="c3db3-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
