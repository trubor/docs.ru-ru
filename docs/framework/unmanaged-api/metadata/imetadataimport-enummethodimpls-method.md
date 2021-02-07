---
description: 'Дополнительные сведения: метод IMetaDataImport:: Енуммесодимплс'
title: Метод IMetaDataImport::EnumMethodImpls
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodImpls
helpviewer_keywords:
- EnumMethodImpls method [.NET Framework metadata]
- IMetaDataImport::EnumMethodImpls method [.NET Framework metadata]
ms.assetid: 4e0f865d-88b5-44bd-be35-492622e5e08e
topic_type:
- apiref
ms.openlocfilehash: 3ae5795bdde36ad07c447370553e24e1ceacf493
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670701"
---
# <a name="imetadataimportenummethodimpls-method"></a><span data-ttu-id="9679f-103">Метод IMetaDataImport::EnumMethodImpls</span><span class="sxs-lookup"><span data-stu-id="9679f-103">IMetaDataImport::EnumMethodImpls Method</span></span>

<span data-ttu-id="9679f-104">Перечисляет токены MethodBody и MethodDeclaration, представляющие методы указанного типа.</span><span class="sxs-lookup"><span data-stu-id="9679f-104">Enumerates MethodBody and MethodDeclaration tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9679f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9679f-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodImpls (  
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   td,
   [out]     mdToken     rMethodBody[],
   [out]     mdToken     rMethodDecl[],
   [in]      ULONG       cMax,
   [in]      ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9679f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="9679f-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="9679f-107">[вход, выход] Указатель на перечислитель.</span><span class="sxs-lookup"><span data-stu-id="9679f-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="9679f-108">При первом вызове этого метода это значение должно быть равно NULL.</span><span class="sxs-lookup"><span data-stu-id="9679f-108">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="9679f-109">окне Токен TypeDef для типа, реализации методов которого требуется перечислить.</span><span class="sxs-lookup"><span data-stu-id="9679f-109">[in] A TypeDef token for the type whose method implementations to enumerate.</span></span>  
  
 `rMethodBody`  
 <span data-ttu-id="9679f-110">заполняет Массив для хранения токенов Месодбоди.</span><span class="sxs-lookup"><span data-stu-id="9679f-110">[out] The array to store the MethodBody tokens.</span></span>  
  
 `rMethodDecl`  
 <span data-ttu-id="9679f-111">заполняет Массив для хранения токенов MethodDeclaration.</span><span class="sxs-lookup"><span data-stu-id="9679f-111">[out] The array to store the MethodDeclaration tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="9679f-112">окне Максимальный размер `rMethodBody` `rMethodDecl` массивов и.</span><span class="sxs-lookup"><span data-stu-id="9679f-112">[in] The maximum size of the `rMethodBody` and `rMethodDecl` arrays.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="9679f-113">окне Фактическое число методов, возвращаемых в `rMethodBody` и `rMethodDecl` .</span><span class="sxs-lookup"><span data-stu-id="9679f-113">[in] The actual number of methods returned in `rMethodBody` and `rMethodDecl`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9679f-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="9679f-114">Return Value</span></span>  
  
|<span data-ttu-id="9679f-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9679f-115">HRESULT</span></span>|<span data-ttu-id="9679f-116">Описание</span><span class="sxs-lookup"><span data-stu-id="9679f-116">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="9679f-117">`EnumMethodImpls` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="9679f-117">`EnumMethodImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="9679f-118">Нет токенов метода для перечисления.</span><span class="sxs-lookup"><span data-stu-id="9679f-118">There are no method tokens to enumerate.</span></span> <span data-ttu-id="9679f-119">В этом случае значение `pcTokens` равно нулю.</span><span class="sxs-lookup"><span data-stu-id="9679f-119">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9679f-120">Требования</span><span class="sxs-lookup"><span data-stu-id="9679f-120">Requirements</span></span>  

 <span data-ttu-id="9679f-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9679f-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9679f-122">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="9679f-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9679f-123">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9679f-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9679f-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9679f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9679f-125">См. также</span><span class="sxs-lookup"><span data-stu-id="9679f-125">See also</span></span>

- [<span data-ttu-id="9679f-126">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="9679f-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="9679f-127">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="9679f-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
