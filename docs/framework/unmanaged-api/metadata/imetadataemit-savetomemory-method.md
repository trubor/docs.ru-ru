---
description: 'Дополнительные сведения: Метод IMetaDataEmit:: Саветомемори'
title: Метод IMetaDataEmit::SaveToMemory
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToMemory
helpviewer_keywords:
- IMetaDataEmit::SaveToMemory method [.NET Framework metadata]
- SaveToMemory method [.NET Framework metadata]
ms.assetid: d5237628-2675-45ed-a39e-65c0731b6a56
topic_type:
- apiref
ms.openlocfilehash: b5fbca2c3ce06398de72bf2690108077545fef9c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745805"
---
# <a name="imetadataemitsavetomemory-method"></a><span data-ttu-id="8942d-103">Метод IMetaDataEmit::SaveToMemory</span><span class="sxs-lookup"><span data-stu-id="8942d-103">IMetaDataEmit::SaveToMemory Method</span></span>

<span data-ttu-id="8942d-104">Сохраняет все метаданные в текущей области в указанную область памяти.</span><span class="sxs-lookup"><span data-stu-id="8942d-104">Saves all metadata in the current scope to the specified area of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8942d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8942d-105">Syntax</span></span>  
  
```cpp  
HRESULT SaveToMemory (
    [out]  void        *pbData,
    [in]   ULONG       cbData
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8942d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8942d-106">Parameters</span></span>  

 `pbData`  
 <span data-ttu-id="8942d-107">заполняет Адрес, с которого начинается запись метаданных.</span><span class="sxs-lookup"><span data-stu-id="8942d-107">[out] The address at which to begin writing metadata.</span></span>  
  
 `cbData`  
 <span data-ttu-id="8942d-108">окне Размер выделенной памяти в байтах.</span><span class="sxs-lookup"><span data-stu-id="8942d-108">[in] The size, in bytes, of the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8942d-109">Требования</span><span class="sxs-lookup"><span data-stu-id="8942d-109">Requirements</span></span>  

 <span data-ttu-id="8942d-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8942d-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8942d-111">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="8942d-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8942d-112">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8942d-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8942d-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8942d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8942d-114">См. также</span><span class="sxs-lookup"><span data-stu-id="8942d-114">See also</span></span>

- [<span data-ttu-id="8942d-115">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="8942d-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="8942d-116">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="8942d-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
