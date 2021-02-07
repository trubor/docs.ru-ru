---
description: 'Дополнительные сведения: метод IMetaDataImport:: EnumMembersWithName'
title: Метод IMetaDataImport::EnumMembersWithName
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembersWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembersWithName
helpviewer_keywords:
- IMetaDataImport::EnumMembersWithName method [.NET Framework metadata]
- EnumMembersWithName method [.NET Framework metadata]
ms.assetid: 7c9e9120-3104-42f0-86ce-19a025f20dcc
topic_type:
- apiref
ms.openlocfilehash: bb6d8f0769029dccaf1f52dd211c67d47bf32a73
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670766"
---
# <a name="imetadataimportenummemberswithname-method"></a><span data-ttu-id="04148-103">Метод IMetaDataImport::EnumMembersWithName</span><span class="sxs-lookup"><span data-stu-id="04148-103">IMetaDataImport::EnumMembersWithName Method</span></span>

<span data-ttu-id="04148-104">Перечисляет токены MemberDef, представляющие члены указанного типа с заданным именем.</span><span class="sxs-lookup"><span data-stu-id="04148-104">Enumerates MemberDef tokens representing members of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04148-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="04148-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumMembersWithName (  
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   cl,
   [in]      LPCWSTR     szName,
   [out]     mdToken     rMembers[],
   [in]      ULONG       cMax,
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04148-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="04148-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="04148-107">[вход, выход] Указатель на перечислитель.</span><span class="sxs-lookup"><span data-stu-id="04148-107">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="04148-108">окне Токен TypeDef, представляющий тип с элементами для перечисления.</span><span class="sxs-lookup"><span data-stu-id="04148-108">[in] A TypeDef token representing the type with members to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="04148-109">окне Имя элемента, ограничивающее область действия перечислителя.</span><span class="sxs-lookup"><span data-stu-id="04148-109">[in] The member name that limits the scope of the enumerator.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="04148-110">заполняет Массив, используемый для хранения маркеров Мембердеф.</span><span class="sxs-lookup"><span data-stu-id="04148-110">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="04148-111">[in] Максимальный размер массива `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="04148-111">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="04148-112">заполняет Фактическое число токенов Мембердеф, возвращаемых в `rMembers` .</span><span class="sxs-lookup"><span data-stu-id="04148-112">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04148-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="04148-113">Remarks</span></span>  

 <span data-ttu-id="04148-114">Этот метод перечисляет поля и методы, но не свойства или события.</span><span class="sxs-lookup"><span data-stu-id="04148-114">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="04148-115">В отличие от [IMetaDataImport:: EnumMembers](imetadataimport-enummembers-method.md), `EnumMembersWithName` отменяет все маркеры полей и элементов, у которых нет указанного имени.</span><span class="sxs-lookup"><span data-stu-id="04148-115">Unlike [IMetaDataImport::EnumMembers](imetadataimport-enummembers-method.md), `EnumMembersWithName` discards all field and member tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04148-116">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="04148-116">Return Value</span></span>  
  
|<span data-ttu-id="04148-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="04148-117">HRESULT</span></span>|<span data-ttu-id="04148-118">Описание</span><span class="sxs-lookup"><span data-stu-id="04148-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="04148-119">`EnumTypeDefs` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="04148-119">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="04148-120">Нет токенов Мембердеф для перечисления.</span><span class="sxs-lookup"><span data-stu-id="04148-120">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="04148-121">В этом случае значение `pcTokens` равно нулю.</span><span class="sxs-lookup"><span data-stu-id="04148-121">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="04148-122">Требования</span><span class="sxs-lookup"><span data-stu-id="04148-122">Requirements</span></span>  

 <span data-ttu-id="04148-123">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04148-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04148-124">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="04148-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="04148-125">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="04148-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="04148-126">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04148-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04148-127">См. также</span><span class="sxs-lookup"><span data-stu-id="04148-127">See also</span></span>

- [<span data-ttu-id="04148-128">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="04148-128">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="04148-129">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="04148-129">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
