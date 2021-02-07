---
description: 'Дополнительные сведения: метод IMetaDataImport:: Енумпарамс'
title: Метод IMetaDataImport::EnumParams
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumParams
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumParams
helpviewer_keywords:
- IMetaDataImport::EnumParams method [.NET Framework metadata]
- EnumParams method [.NET Framework metadata]
ms.assetid: 52118dc9-fe6e-4b39-aa48-c3cc3ea4214d
topic_type:
- apiref
ms.openlocfilehash: 3402e0277631cb54232269ad96194583cc466c4d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688804"
---
# <a name="imetadataimportenumparams-method"></a><span data-ttu-id="b46ab-103">Метод IMetaDataImport::EnumParams</span><span class="sxs-lookup"><span data-stu-id="b46ab-103">IMetaDataImport::EnumParams Method</span></span>

<span data-ttu-id="b46ab-104">Перечисляет токены ParamDef, представляющие параметры метода, на который ссылается указанный токен MethodDef.</span><span class="sxs-lookup"><span data-stu-id="b46ab-104">Enumerates ParamDef tokens representing the parameters of the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b46ab-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b46ab-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumParams (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,  
   [out] mdParamDef      rParams[],  
   [in]  ULONG           cMax,  
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b46ab-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b46ab-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="b46ab-107">[вход, выход] Указатель на перечислитель.</span><span class="sxs-lookup"><span data-stu-id="b46ab-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="b46ab-108">При первом вызове этого метода это значение должно быть равно NULL.</span><span class="sxs-lookup"><span data-stu-id="b46ab-108">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="b46ab-109">окне Токен MethodDef, представляющий метод с параметрами для перечисления.</span><span class="sxs-lookup"><span data-stu-id="b46ab-109">[in] A MethodDef token representing the method with the parameters to enumerate.</span></span>  
  
 `rParams`  
 <span data-ttu-id="b46ab-110">заполняет Массив, используемый для хранения маркеров Парамдеф.</span><span class="sxs-lookup"><span data-stu-id="b46ab-110">[out] The array used to store the ParamDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b46ab-111">[in] Максимальный размер массива `rParams`.</span><span class="sxs-lookup"><span data-stu-id="b46ab-111">[in] The maximum size of the `rParams` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="b46ab-112">заполняет Число токенов Парамдеф, возвращаемых в `rParams` .</span><span class="sxs-lookup"><span data-stu-id="b46ab-112">[out] The number of ParamDef tokens returned in `rParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b46ab-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="b46ab-113">Return Value</span></span>  
  
|<span data-ttu-id="b46ab-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b46ab-114">HRESULT</span></span>|<span data-ttu-id="b46ab-115">Описание</span><span class="sxs-lookup"><span data-stu-id="b46ab-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b46ab-116">`EnumParams` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="b46ab-116">`EnumParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b46ab-117">Нет токенов для перечисления.</span><span class="sxs-lookup"><span data-stu-id="b46ab-117">There are no tokens to enumerate.</span></span> <span data-ttu-id="b46ab-118">В этом случае значение `pcTokens` равно нулю.</span><span class="sxs-lookup"><span data-stu-id="b46ab-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b46ab-119">Требования</span><span class="sxs-lookup"><span data-stu-id="b46ab-119">Requirements</span></span>  

 <span data-ttu-id="b46ab-120">**Платформа:** См. раздел [требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b46ab-120">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b46ab-121">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="b46ab-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b46ab-122">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b46ab-122">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b46ab-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b46ab-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b46ab-124">См. также</span><span class="sxs-lookup"><span data-stu-id="b46ab-124">See also</span></span>

- [<span data-ttu-id="b46ab-125">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="b46ab-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="b46ab-126">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="b46ab-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
