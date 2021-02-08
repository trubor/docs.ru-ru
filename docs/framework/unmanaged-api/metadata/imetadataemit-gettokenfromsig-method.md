---
description: 'Дополнительные сведения: Метод IMetaDataEmit:: Жеттокенфромсиг'
title: Метод IMetaDataEmit::GetTokenFromSig
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetTokenFromSig
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetTokenFromSig
helpviewer_keywords:
- IMetaDataEmit::GetTokenFromSig method [.NET Framework metadata]
- GetTokenFromSig method [.NET Framework metadata]
ms.assetid: 50a58a83-6287-40a4-b315-47823cea0a5c
topic_type:
- apiref
ms.openlocfilehash: 3b9b38389a2bf78a65baa2cf96e3a422c54d0bcb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783928"
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="6e7df-103">Метод IMetaDataEmit::GetTokenFromSig</span><span class="sxs-lookup"><span data-stu-id="6e7df-103">IMetaDataEmit::GetTokenFromSig Method</span></span>

<span data-ttu-id="6e7df-104">Возвращает токен для указанной сигнатуры метаданных.</span><span class="sxs-lookup"><span data-stu-id="6e7df-104">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e7df-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6e7df-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromSig (
    [in]  PCCOR_SIGNATURE pvSig,
    [in]  ULONG       cbSig,
    [out] mdSignature *pmsig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e7df-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6e7df-106">Parameters</span></span>  

 `pvSig`  
 <span data-ttu-id="6e7df-107">окне Сохраняемая и хранимая сигнатура.</span><span class="sxs-lookup"><span data-stu-id="6e7df-107">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="6e7df-108">окне Число байтов в `pvSig` .</span><span class="sxs-lookup"><span data-stu-id="6e7df-108">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="6e7df-109">заполняет `mdSignature` Назначенный маркер.</span><span class="sxs-lookup"><span data-stu-id="6e7df-109">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e7df-110">Требования</span><span class="sxs-lookup"><span data-stu-id="6e7df-110">Requirements</span></span>  

 <span data-ttu-id="6e7df-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e7df-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e7df-112">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="6e7df-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6e7df-113">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6e7df-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6e7df-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e7df-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e7df-115">См. также</span><span class="sxs-lookup"><span data-stu-id="6e7df-115">See also</span></span>

- [<span data-ttu-id="6e7df-116">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="6e7df-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="6e7df-117">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="6e7df-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
