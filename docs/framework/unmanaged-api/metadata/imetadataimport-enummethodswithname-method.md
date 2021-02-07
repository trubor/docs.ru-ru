---
description: 'Дополнительные сведения: метод IMetaDataImport:: Енуммесодсвиснаме'
title: Метод IMetaDataImport::EnumMethodsWithName
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodsWithName
helpviewer_keywords:
- IMetaDataImport::EnumMethodsWithName method [.NET Framework metadata]
- EnumMethodsWithName method [.NET Framework metadata]
ms.assetid: a8624913-2e23-46ad-a0c1-bb8eccbbf20f
topic_type:
- apiref
ms.openlocfilehash: b77fc15bd7752b5b6b2b95d66a6bf04518616884
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745610"
---
# <a name="imetadataimportenummethodswithname-method"></a><span data-ttu-id="65f8c-103">Метод IMetaDataImport::EnumMethodsWithName</span><span class="sxs-lookup"><span data-stu-id="65f8c-103">IMetaDataImport::EnumMethodsWithName Method</span></span>

<span data-ttu-id="65f8c-104">Перечисляет методы с заданным именем, определяемые по типу, на который ссылается указанный токен TypeDef.</span><span class="sxs-lookup"><span data-stu-id="65f8c-104">Enumerates methods that have the specified name and that are defined by the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65f8c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="65f8c-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodsWithName (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdTypeDef       cl,  
   [in]  LPCWSTR         szName,  
   [out] mdMethodDef     rMethods[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65f8c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="65f8c-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="65f8c-107">[вход, выход] Указатель на перечислитель.</span><span class="sxs-lookup"><span data-stu-id="65f8c-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="65f8c-108">При первом вызове этого метода это значение должно быть равно NULL.</span><span class="sxs-lookup"><span data-stu-id="65f8c-108">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="65f8c-109">окне Токен TypeDef, представляющий тип, методы которого необходимо перечислить.</span><span class="sxs-lookup"><span data-stu-id="65f8c-109">[in] A TypeDef token representing the type whose methods to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="65f8c-110">окне Имя, ограничивающее область перечисления.</span><span class="sxs-lookup"><span data-stu-id="65f8c-110">[in] The name that limits the scope of the enumeration.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="65f8c-111">заполняет Массив, используемый для хранения маркеров MethodDef.</span><span class="sxs-lookup"><span data-stu-id="65f8c-111">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="65f8c-112">[in] Максимальный размер массива `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="65f8c-112">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="65f8c-113">заполняет Число токенов MethodDef, возвращаемых в `rMethods` .</span><span class="sxs-lookup"><span data-stu-id="65f8c-113">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65f8c-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="65f8c-114">Remarks</span></span>  

 <span data-ttu-id="65f8c-115">Этот метод перечисляет поля и методы, но не свойства или события.</span><span class="sxs-lookup"><span data-stu-id="65f8c-115">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="65f8c-116">В отличие от метода [IMetaDataImport:: enummethods-](imetadataimport-enummethods-method.md), `EnumMethodsWithName` отменяет все маркеры методов, у которых нет указанного имени.</span><span class="sxs-lookup"><span data-stu-id="65f8c-116">Unlike [IMetaDataImport::EnumMethods](imetadataimport-enummethods-method.md), `EnumMethodsWithName` discards all method tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="65f8c-117">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="65f8c-117">Return Value</span></span>  
  
|<span data-ttu-id="65f8c-118">HRESULT</span><span class="sxs-lookup"><span data-stu-id="65f8c-118">HRESULT</span></span>|<span data-ttu-id="65f8c-119">Описание</span><span class="sxs-lookup"><span data-stu-id="65f8c-119">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="65f8c-120">`EnumMethodsWithName` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="65f8c-120">`EnumMethodsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="65f8c-121">Нет токенов для перечисления.</span><span class="sxs-lookup"><span data-stu-id="65f8c-121">There are no tokens to enumerate.</span></span> <span data-ttu-id="65f8c-122">В этом случае значение `pcTokens` равно нулю.</span><span class="sxs-lookup"><span data-stu-id="65f8c-122">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="65f8c-123">Требования</span><span class="sxs-lookup"><span data-stu-id="65f8c-123">Requirements</span></span>  

 <span data-ttu-id="65f8c-124">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65f8c-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65f8c-125">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="65f8c-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="65f8c-126">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="65f8c-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="65f8c-127">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65f8c-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65f8c-128">См. также</span><span class="sxs-lookup"><span data-stu-id="65f8c-128">See also</span></span>

- [<span data-ttu-id="65f8c-129">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="65f8c-129">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="65f8c-130">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="65f8c-130">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
