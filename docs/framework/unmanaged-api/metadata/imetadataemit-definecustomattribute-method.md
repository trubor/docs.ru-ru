---
description: 'Дополнительные сведения: IMetaDataEmit::D метод Ефинекустоматтрибуте'
title: Метод IMetaDataEmit::DefineCustomAttribute
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineCustomAttribute
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineCustomAttribute
helpviewer_keywords:
- DefineCustomAttribute method [.NET Framework metadata]
- IMetaDataEmit::DefineCustomAttribute method [.NET Framework metadata]
ms.assetid: 7dd14854-b756-4401-b167-88ca576dc8f0
topic_type:
- apiref
ms.openlocfilehash: 5d802f590525b8b398ac270b1b7f59d122b45b73
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753488"
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="60cee-103">Метод IMetaDataEmit::DefineCustomAttribute</span><span class="sxs-lookup"><span data-stu-id="60cee-103">IMetaDataEmit::DefineCustomAttribute Method</span></span>

<span data-ttu-id="60cee-104">Создает определение для настраиваемого атрибута с указанной подписью метаданных, присоединяемого к указанному объекту и получает маркер для этого определения настраиваемого атрибута.</span><span class="sxs-lookup"><span data-stu-id="60cee-104">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60cee-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="60cee-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineCustomAttribute (
    [in]  mdToken     tkObj,
    [in]  mdToken     tkType,
    [in]  void const  *pCustomAttribute,
    [in]  ULONG       cbCustomAttribute,
    [out] mdCustomAttribute *pcv
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60cee-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="60cee-106">Parameters</span></span>  

 `tkObj`  
 <span data-ttu-id="60cee-107">окне Токен для элемента владельца.</span><span class="sxs-lookup"><span data-stu-id="60cee-107">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="60cee-108">окне Токен, определяющий настраиваемый атрибут.</span><span class="sxs-lookup"><span data-stu-id="60cee-108">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="60cee-109">окне Указатель на настраиваемый атрибут.</span><span class="sxs-lookup"><span data-stu-id="60cee-109">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="60cee-110">окне Число байтов в `pCustomAttribute` .</span><span class="sxs-lookup"><span data-stu-id="60cee-110">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="60cee-111">заполняет `mdCustomAttribute` Назначенный маркер.</span><span class="sxs-lookup"><span data-stu-id="60cee-111">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60cee-112">Требования</span><span class="sxs-lookup"><span data-stu-id="60cee-112">Requirements</span></span>  

 <span data-ttu-id="60cee-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60cee-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60cee-114">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="60cee-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="60cee-115">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="60cee-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="60cee-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60cee-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60cee-117">См. также</span><span class="sxs-lookup"><span data-stu-id="60cee-117">See also</span></span>

- [<span data-ttu-id="60cee-118">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="60cee-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="60cee-119">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="60cee-119">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
