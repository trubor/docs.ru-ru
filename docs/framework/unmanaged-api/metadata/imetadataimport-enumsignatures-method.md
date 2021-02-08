---
description: 'Дополнительные сведения: метод IMetaDataImport:: Енумсигнатурес'
title: Метод IMetaDataImport::EnumSignatures
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumSignatures
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumSignatures
helpviewer_keywords:
- EnumSignatures method [.NET Framework metadata]
- IMetaDataImport::EnumSignatures method [.NET Framework metadata]
ms.assetid: d0d65060-6f90-42a2-95cf-6ffb04352996
topic_type:
- apiref
ms.openlocfilehash: ed41dd42151791e3d27950f30b10d91217ad7e7a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771630"
---
# <a name="imetadataimportenumsignatures-method"></a><span data-ttu-id="5983d-103">Метод IMetaDataImport::EnumSignatures</span><span class="sxs-lookup"><span data-stu-id="5983d-103">IMetaDataImport::EnumSignatures Method</span></span>

<span data-ttu-id="5983d-104">Перечисляет токены Signature, представляющие отдельные подписи в текущей области.</span><span class="sxs-lookup"><span data-stu-id="5983d-104">Enumerates Signature tokens representing stand-alone signatures in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5983d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5983d-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumSignatures (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdSignature  rSignatures[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcSignatures  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5983d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="5983d-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="5983d-107">[вход, выход] Указатель на перечислитель.</span><span class="sxs-lookup"><span data-stu-id="5983d-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="5983d-108">При первом вызове этого метода это значение должно быть равно NULL.</span><span class="sxs-lookup"><span data-stu-id="5983d-108">This must be NULL for the first call of this method.</span></span>  
  
 `rSignatures`  
 <span data-ttu-id="5983d-109">заполняет Массив, используемый для хранения маркеров подписи.</span><span class="sxs-lookup"><span data-stu-id="5983d-109">[out] The array used to store the Signature tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="5983d-110">[in] Максимальный размер массива `rSignatures`.</span><span class="sxs-lookup"><span data-stu-id="5983d-110">[in] The maximum size of the `rSignatures` array.</span></span>  
  
 `pcSignatures`  
 <span data-ttu-id="5983d-111">заполняет Число маркеров подписи, возвращаемых в `rSignatures` .</span><span class="sxs-lookup"><span data-stu-id="5983d-111">[out] The number of Signature tokens returned in `rSignatures`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5983d-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="5983d-112">Return Value</span></span>  
  
|<span data-ttu-id="5983d-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5983d-113">HRESULT</span></span>|<span data-ttu-id="5983d-114">Описание</span><span class="sxs-lookup"><span data-stu-id="5983d-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="5983d-115">`EnumSignatures` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="5983d-115">`EnumSignatures` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="5983d-116">Нет токенов для перечисления.</span><span class="sxs-lookup"><span data-stu-id="5983d-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="5983d-117">В этом случае значение `pcSignatures` равно нулю.</span><span class="sxs-lookup"><span data-stu-id="5983d-117">In that case, `pcSignatures` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5983d-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="5983d-118">Remarks</span></span>  

 <span data-ttu-id="5983d-119">Маркеры подписи создаются методом [IMetaDataEmit:: жеттокенфромсиг](imetadataemit-gettokenfromsig-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5983d-119">The Signature tokens are created by the [IMetaDataEmit::GetTokenFromSig](imetadataemit-gettokenfromsig-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5983d-120">Требования</span><span class="sxs-lookup"><span data-stu-id="5983d-120">Requirements</span></span>  

 <span data-ttu-id="5983d-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5983d-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5983d-122">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="5983d-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5983d-123">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5983d-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5983d-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5983d-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5983d-125">См. также</span><span class="sxs-lookup"><span data-stu-id="5983d-125">See also</span></span>

- [<span data-ttu-id="5983d-126">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="5983d-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="5983d-127">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="5983d-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
