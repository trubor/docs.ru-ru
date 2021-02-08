---
description: 'Дополнительные сведения: IMetaDataEmit::D метод Елетепинвокемап'
title: Метод IMetaDataEmit::DeletePinvokeMap
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeletePinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeletePinvokeMap
helpviewer_keywords:
- IMetaDataEmit::DeletePinvokeMap method [.NET Framework metadata]
- DeletePinvokeMap method [.NET Framework metadata]
ms.assetid: 3c4f6b54-5ce7-4a2a-83e1-6dec16441f50
topic_type:
- apiref
ms.openlocfilehash: 977fd600600cdfba0fd9fd5d383648ffbf63229f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783980"
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="50513-103">Метод IMetaDataEmit::DeletePinvokeMap</span><span class="sxs-lookup"><span data-stu-id="50513-103">IMetaDataEmit::DeletePinvokeMap Method</span></span>

<span data-ttu-id="50513-104">Уничтожает метаданные сопоставления PInvoke для объекта, на который ссылается указанный токен.</span><span class="sxs-lookup"><span data-stu-id="50513-104">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50513-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="50513-105">Syntax</span></span>  
  
```cpp  
HRESULT DeletePinvokeMap (
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50513-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="50513-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="50513-107">окне `mdFieldDef` Токен или `mdMethodDef` , представляющий объект, для которого необходимо удалить метаданные сопоставления PInvoke.</span><span class="sxs-lookup"><span data-stu-id="50513-107">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50513-108">Требования</span><span class="sxs-lookup"><span data-stu-id="50513-108">Requirements</span></span>  

 <span data-ttu-id="50513-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50513-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50513-110">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="50513-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="50513-111">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="50513-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50513-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50513-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50513-113">См. также</span><span class="sxs-lookup"><span data-stu-id="50513-113">See also</span></span>

- [<span data-ttu-id="50513-114">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="50513-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="50513-115">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="50513-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
