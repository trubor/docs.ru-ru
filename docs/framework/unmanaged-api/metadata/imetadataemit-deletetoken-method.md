---
description: 'Дополнительные сведения: IMetaDataEmit::D метод Елететокен'
title: Метод IMetaDataEmit::DeleteToken
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteToken
helpviewer_keywords:
- DeleteToken method [.NET Framework metadata]
- IMetaDataEmit::DeleteToken method [.NET Framework metadata]
ms.assetid: a4926d0a-261b-46b1-9994-82633661a64b
topic_type:
- apiref
ms.openlocfilehash: 5c28b56b06f994057409ef8fa17179cb0b0e205b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783954"
---
# <a name="imetadataemitdeletetoken-method"></a><span data-ttu-id="68e96-103">Метод IMetaDataEmit::DeleteToken</span><span class="sxs-lookup"><span data-stu-id="68e96-103">IMetaDataEmit::DeleteToken Method</span></span>

<span data-ttu-id="68e96-104">Удаляет указанный токен из текущей области метаданных.</span><span class="sxs-lookup"><span data-stu-id="68e96-104">Deletes the specified token from the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68e96-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="68e96-105">Syntax</span></span>  
  
```cpp  
HRESULT DeleteToken (
    [in]  mdToken     tkObj
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68e96-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="68e96-106">Parameters</span></span>  

 `tkObj`  
 <span data-ttu-id="68e96-107">окне Удаляемый токен.</span><span class="sxs-lookup"><span data-stu-id="68e96-107">[in] The token to be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68e96-108">Требования</span><span class="sxs-lookup"><span data-stu-id="68e96-108">Requirements</span></span>  

 <span data-ttu-id="68e96-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68e96-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68e96-110">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="68e96-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="68e96-111">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="68e96-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="68e96-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68e96-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68e96-113">См. также</span><span class="sxs-lookup"><span data-stu-id="68e96-113">See also</span></span>

- [<span data-ttu-id="68e96-114">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="68e96-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="68e96-115">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="68e96-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
