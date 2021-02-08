---
description: 'Дополнительные сведения: метод IMetaDataImport:: EnumFields'
title: Метод IMetaDataImport::EnumFields
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFields
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFields
helpviewer_keywords:
- EnumFields method [.NET Framework metadata]
- IMetaDataImport::EnumFields method [.NET Framework metadata]
ms.assetid: 1d23247e-c58c-45db-afd8-83aa89cde18e
topic_type:
- apiref
ms.openlocfilehash: 5cb9b3a47dc4c51b9eba24b9519e4b97846c1a6d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799386"
---
# <a name="imetadataimportenumfields-method"></a><span data-ttu-id="02ce3-103">Метод IMetaDataImport::EnumFields</span><span class="sxs-lookup"><span data-stu-id="02ce3-103">IMetaDataImport::EnumFields Method</span></span>

<span data-ttu-id="02ce3-104">Перечисляет токены FieldDef для типа, на который ссылается указанный токен TypeDef.</span><span class="sxs-lookup"><span data-stu-id="02ce3-104">Enumerates FieldDef tokens for the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02ce3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="02ce3-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumFields (
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   cl,
   [out]     mdFieldDef  rFields[],
   [in]      ULONG       cMax,
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02ce3-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="02ce3-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="02ce3-107">[вход, выход] Указатель на перечислитель.</span><span class="sxs-lookup"><span data-stu-id="02ce3-107">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="02ce3-108">окне Токен TypeDef класса, поля которого необходимо перечислить.</span><span class="sxs-lookup"><span data-stu-id="02ce3-108">[in] The TypeDef token of the class whose fields are to be enumerated.</span></span>  
  
 `rFields`  
 <span data-ttu-id="02ce3-109">заполняет Список токенов FieldDef.</span><span class="sxs-lookup"><span data-stu-id="02ce3-109">[out] The list of FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="02ce3-110">[in] Максимальный размер массива `rFields`.</span><span class="sxs-lookup"><span data-stu-id="02ce3-110">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="02ce3-111">заполняет Фактическое число токенов FieldDef, возвращаемых в `rFields` .</span><span class="sxs-lookup"><span data-stu-id="02ce3-111">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="02ce3-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="02ce3-112">Return Value</span></span>  
  
|<span data-ttu-id="02ce3-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="02ce3-113">HRESULT</span></span>|<span data-ttu-id="02ce3-114">Описание</span><span class="sxs-lookup"><span data-stu-id="02ce3-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="02ce3-115">`EnumFields` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="02ce3-115">`EnumFields` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="02ce3-116">Нет полей для перечисления.</span><span class="sxs-lookup"><span data-stu-id="02ce3-116">There are no fields to enumerate.</span></span> <span data-ttu-id="02ce3-117">В этом случае значение `pcTokens` равно нулю.</span><span class="sxs-lookup"><span data-stu-id="02ce3-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="02ce3-118">Требования</span><span class="sxs-lookup"><span data-stu-id="02ce3-118">Requirements</span></span>  

 <span data-ttu-id="02ce3-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02ce3-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02ce3-120">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="02ce3-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="02ce3-121">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="02ce3-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="02ce3-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02ce3-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02ce3-123">См. также</span><span class="sxs-lookup"><span data-stu-id="02ce3-123">See also</span></span>

- [<span data-ttu-id="02ce3-124">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="02ce3-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="02ce3-125">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="02ce3-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
