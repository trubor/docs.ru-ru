---
description: 'Дополнительные сведения: метод IMetaDataImport:: Енумфиелдсвиснаме'
title: Метод IMetaDataImport::EnumFieldsWithName
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFieldsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFieldsWithName
helpviewer_keywords:
- IMetaDataImport::EnumFieldsWithName method [.NET Framework metadata]
- EnumFieldsWithName method [.NET Framework metadata]
ms.assetid: 42145e8d-000f-4d0b-ae43-c08201190fa2
topic_type:
- apiref
ms.openlocfilehash: 88096b2b12a9571eb05d4550e6e26a348e28cfd2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799373"
---
# <a name="imetadataimportenumfieldswithname-method"></a><span data-ttu-id="9773d-103">Метод IMetaDataImport::EnumFieldsWithName</span><span class="sxs-lookup"><span data-stu-id="9773d-103">IMetaDataImport::EnumFieldsWithName Method</span></span>

<span data-ttu-id="9773d-104">Перечисляет токены FieldDef заданного типа с указанным именем.</span><span class="sxs-lookup"><span data-stu-id="9773d-104">Enumerates FieldDef tokens of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9773d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9773d-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumFieldsWithName (  
   [in, out] HCORENUM    *phEnum,
   [in]  mdTypeDef       cl,
   [in]  LPCWSTR         szName,
   [out] mdFieldDef      rFields[],
   [in]  ULONG           cMax,
   [out] ULONG           *pcTokens
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9773d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="9773d-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="9773d-107">[вход, выход] Указатель на перечислитель.</span><span class="sxs-lookup"><span data-stu-id="9773d-107">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="9773d-108">окне Токен типа, поля которого необходимо перечислить.</span><span class="sxs-lookup"><span data-stu-id="9773d-108">[in] The token of the type whose fields are to be enumerated.</span></span>  
  
 `szName`  
 <span data-ttu-id="9773d-109">окне Имя поля, ограничивающее область перечисления.</span><span class="sxs-lookup"><span data-stu-id="9773d-109">[in] The field name that limits the scope of the enumeration.</span></span>  
  
 `rFields`  
 <span data-ttu-id="9773d-110">заполняет Массив, используемый для хранения маркеров FieldDef.</span><span class="sxs-lookup"><span data-stu-id="9773d-110">[out] Array used to store the FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="9773d-111">[in] Максимальный размер массива `rFields`.</span><span class="sxs-lookup"><span data-stu-id="9773d-111">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="9773d-112">заполняет Фактическое число токенов FieldDef, возвращаемых в `rFields` .</span><span class="sxs-lookup"><span data-stu-id="9773d-112">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9773d-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="9773d-113">Remarks</span></span>  

 <span data-ttu-id="9773d-114">В отличие от [IMetaDataImport:: EnumFields](imetadataimport-enumfields-method.md), `EnumFieldsWithName` отменяет все маркеры полей, у которых нет указанного имени.</span><span class="sxs-lookup"><span data-stu-id="9773d-114">Unlike [IMetaDataImport::EnumFields](imetadataimport-enumfields-method.md), `EnumFieldsWithName` discards all field tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9773d-115">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="9773d-115">Return Value</span></span>  
  
|<span data-ttu-id="9773d-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9773d-116">HRESULT</span></span>|<span data-ttu-id="9773d-117">Описание</span><span class="sxs-lookup"><span data-stu-id="9773d-117">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="9773d-118">`EnumFieldsWithName` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="9773d-118">`EnumFieldsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="9773d-119">Нет полей для перечисления.</span><span class="sxs-lookup"><span data-stu-id="9773d-119">There are no fields to enumerate.</span></span> <span data-ttu-id="9773d-120">В этом случае значение `pcTokens` равно нулю.</span><span class="sxs-lookup"><span data-stu-id="9773d-120">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9773d-121">Требования</span><span class="sxs-lookup"><span data-stu-id="9773d-121">Requirements</span></span>  

 <span data-ttu-id="9773d-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9773d-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9773d-123">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="9773d-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9773d-124">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9773d-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9773d-125">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9773d-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9773d-126">См. также</span><span class="sxs-lookup"><span data-stu-id="9773d-126">See also</span></span>

- [<span data-ttu-id="9773d-127">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="9773d-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="9773d-128">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="9773d-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
