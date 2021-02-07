---
description: 'Дополнительные сведения: метод IMetaDataImport:: Ресетенум'
title: Метод IMetaDataImport::ResetEnum
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResetEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResetEnum
helpviewer_keywords:
- ResetEnum method [.NET Framework metadata]
- IMetaDataImport::ResetEnum method [.NET Framework metadata]
ms.assetid: dda867b5-1050-49ba-b01c-fcc83b7a5617
topic_type:
- apiref
ms.openlocfilehash: 7b1572be2e2b905e6db5cf6e422643dbb76ca9be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670584"
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="5c497-103">Метод IMetaDataImport::ResetEnum</span><span class="sxs-lookup"><span data-stu-id="5c497-103">IMetaDataImport::ResetEnum Method</span></span>

<span data-ttu-id="5c497-104">Возвращает заданный перечислитель в указанную позицию.</span><span class="sxs-lookup"><span data-stu-id="5c497-104">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c497-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5c497-105">Syntax</span></span>  
  
```cpp  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,
   [in] ULONG       ulPos  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c497-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="5c497-106">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="5c497-107">окне Перечислитель для сброса.</span><span class="sxs-lookup"><span data-stu-id="5c497-107">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="5c497-108">окне Новое место для размещения перечислителя.</span><span class="sxs-lookup"><span data-stu-id="5c497-108">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c497-109">Требования</span><span class="sxs-lookup"><span data-stu-id="5c497-109">Requirements</span></span>  

 <span data-ttu-id="5c497-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c497-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c497-111">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="5c497-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5c497-112">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5c497-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5c497-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c497-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c497-114">См. также</span><span class="sxs-lookup"><span data-stu-id="5c497-114">See also</span></span>

- [<span data-ttu-id="5c497-115">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="5c497-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="5c497-116">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="5c497-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
