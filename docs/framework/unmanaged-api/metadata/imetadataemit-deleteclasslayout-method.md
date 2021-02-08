---
description: 'Дополнительные сведения: IMetaDataEmit::D метод Елетекласслайаут'
title: Метод IMetaDataEmit::DeleteClassLayout
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteClassLayout
helpviewer_keywords:
- DeleteClassLayout method [.NET Framework metadata]
- IMetaDataEmit::DeleteClassLayout method [.NET Framework metadata]
ms.assetid: 65a4ad49-fa49-4b36-8ed1-76dd6a185ab4
topic_type:
- apiref
ms.openlocfilehash: 44be89f415087a1457a83bb1167e1017d26ed5ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783993"
---
# <a name="imetadataemitdeleteclasslayout-method"></a><span data-ttu-id="33dda-103">Метод IMetaDataEmit::DeleteClassLayout</span><span class="sxs-lookup"><span data-stu-id="33dda-103">IMetaDataEmit::DeleteClassLayout Method</span></span>

<span data-ttu-id="33dda-104">Уничтожает сигнатуру метаданных макета класса для типа, представленного указанным токеном.</span><span class="sxs-lookup"><span data-stu-id="33dda-104">Destroys the class layout metadata signature for the type represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33dda-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="33dda-105">Syntax</span></span>  
  
```cpp  
HRESULT DeleteClassLayout (  
    [in]  mdTypeDef   td  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33dda-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="33dda-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="33dda-107">окне `mdTypeDef` Токен метаданных, представляющий тип, для которого будет удален макет класса.</span><span class="sxs-lookup"><span data-stu-id="33dda-107">[in] An `mdTypeDef` metadata token that represents the type for which the class layout will be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33dda-108">Требования</span><span class="sxs-lookup"><span data-stu-id="33dda-108">Requirements</span></span>  

 <span data-ttu-id="33dda-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33dda-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33dda-110">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="33dda-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="33dda-111">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="33dda-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="33dda-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33dda-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33dda-113">См. также</span><span class="sxs-lookup"><span data-stu-id="33dda-113">See also</span></span>

- [<span data-ttu-id="33dda-114">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="33dda-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="33dda-115">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="33dda-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
