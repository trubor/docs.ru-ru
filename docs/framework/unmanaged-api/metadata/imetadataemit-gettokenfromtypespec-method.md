---
description: 'Дополнительные сведения: Метод IMetaDataEmit:: Жеттокенфромтипеспек'
title: Метод IMetaDataEmit::GetTokenFromTypeSpec
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetTokenFromTypeSpec
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetTokenFromTypeSpec
helpviewer_keywords:
- GetTokenFromTypeSpec method [.NET Framework metadata]
- IMetaDataEmit::GetTokenFromTypeSpec method [.NET Framework metadata]
ms.assetid: 7de6447a-a751-49d8-87e2-951cee77b536
topic_type:
- apiref
ms.openlocfilehash: 09f7133af9b9d912b03cdc1c93744ee260c69169
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728240"
---
# <a name="imetadataemitgettokenfromtypespec-method"></a><span data-ttu-id="01f6b-103">Метод IMetaDataEmit::GetTokenFromTypeSpec</span><span class="sxs-lookup"><span data-stu-id="01f6b-103">IMetaDataEmit::GetTokenFromTypeSpec Method</span></span>

<span data-ttu-id="01f6b-104">Возвращает токен метаданных для типа с указанной сигнатурой метаданных.</span><span class="sxs-lookup"><span data-stu-id="01f6b-104">Gets a metadata token for the type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01f6b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="01f6b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromTypeSpec (
    [in]  PCCOR_SIGNATURE       pvSig,
    [in]  ULONG                 cbSig,
    [out] mdTypeSpec            *ptypespec
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01f6b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="01f6b-106">Parameters</span></span>  

 `pvSig`  
 <span data-ttu-id="01f6b-107">окне Определяемая сигнатура.</span><span class="sxs-lookup"><span data-stu-id="01f6b-107">[in] The signature being defined.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="01f6b-108">окне Число байтов в `pvSig` .</span><span class="sxs-lookup"><span data-stu-id="01f6b-108">[in] The count of bytes in `pvSig`.</span></span>  
  
 `ptypespec`  
 <span data-ttu-id="01f6b-109">заполняет `mdTypeSpec` Назначенный маркер.</span><span class="sxs-lookup"><span data-stu-id="01f6b-109">[out] The `mdTypeSpec` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01f6b-110">Требования</span><span class="sxs-lookup"><span data-stu-id="01f6b-110">Requirements</span></span>  

 <span data-ttu-id="01f6b-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01f6b-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01f6b-112">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="01f6b-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="01f6b-113">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="01f6b-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="01f6b-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01f6b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01f6b-115">См. также</span><span class="sxs-lookup"><span data-stu-id="01f6b-115">See also</span></span>

- [<span data-ttu-id="01f6b-116">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="01f6b-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="01f6b-117">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="01f6b-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
