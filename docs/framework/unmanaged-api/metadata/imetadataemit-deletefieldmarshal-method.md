---
description: 'Дополнительные сведения: IMetaDataEmit::D метод Елетефиелдмаршал'
title: Метод IMetaDataEmit::DeleteFieldMarshal
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteFieldMarshal
helpviewer_keywords:
- IMetaDataEmit::DeleteFieldMarshal method [.NET Framework metadata]
- DeleteFieldMarshal method [.NET Framework metadata]
ms.assetid: 7c75aef9-c742-4b33-a14b-56ff94b0f725
topic_type:
- apiref
ms.openlocfilehash: 966f2ae20ad9ff4b9c1c9eec32974bc89aa76d13
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783967"
---
# <a name="imetadataemitdeletefieldmarshal-method"></a><span data-ttu-id="941c6-103">Метод IMetaDataEmit::DeleteFieldMarshal</span><span class="sxs-lookup"><span data-stu-id="941c6-103">IMetaDataEmit::DeleteFieldMarshal Method</span></span>

<span data-ttu-id="941c6-104">Уничтожает сигнатуру метаданных упаковки PInvoke для объекта, на который ссылается указанный токен.</span><span class="sxs-lookup"><span data-stu-id="941c6-104">Destroys the PInvoke marshaling metadata signature for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="941c6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="941c6-105">Syntax</span></span>  
  
```cpp  
HRESULT DeleteFieldMarshal (  
    [in]  mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="941c6-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="941c6-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="941c6-107">окне `mdFieldDef` Токен или `mdParamDef` , представляющий поле или параметр, для которого необходимо удалить подпись метаданных упаковки.</span><span class="sxs-lookup"><span data-stu-id="941c6-107">[in] An `mdFieldDef` or `mdParamDef` token that represents the field or parameter for which to delete the marshaling metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="941c6-108">Требования</span><span class="sxs-lookup"><span data-stu-id="941c6-108">Requirements</span></span>  

 <span data-ttu-id="941c6-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="941c6-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="941c6-110">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="941c6-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="941c6-111">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="941c6-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="941c6-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="941c6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="941c6-113">См. также</span><span class="sxs-lookup"><span data-stu-id="941c6-113">See also</span></span>

- [<span data-ttu-id="941c6-114">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="941c6-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="941c6-115">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="941c6-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
