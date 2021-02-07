---
description: 'Дополнительные сведения о методе: IMetaDataFilter:: Марктокен'
title: Метод IMetaDataFilter::MarkToken
ms.date: 03/30/2017
api_name:
- IMetaDataFilter.MarkToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter::MarkToken
helpviewer_keywords:
- IMetaDataFilter::MarkToken method [.NET Framework metadata]
- MarkToken method, IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: bd492834-6529-4d39-b93d-f8cdbd3e297f
topic_type:
- apiref
ms.openlocfilehash: 97191533ae7d2bdc951521f1929a4c001c521b9d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677799"
---
# <a name="imetadatafiltermarktoken-method"></a><span data-ttu-id="31d6d-103">Метод IMetaDataFilter::MarkToken</span><span class="sxs-lookup"><span data-stu-id="31d6d-103">IMetaDataFilter::MarkToken Method</span></span>

<span data-ttu-id="31d6d-104">Задает значение, указывающее, что указанный токен метаданных был обработан.</span><span class="sxs-lookup"><span data-stu-id="31d6d-104">Sets a value indicating that the specified metadata token has been processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31d6d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="31d6d-105">Syntax</span></span>  
  
```cpp  
HRESULT MarkToken (  
    [in] mdToken   tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31d6d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="31d6d-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="31d6d-107">окне Маркер, помечающий как обработанный.</span><span class="sxs-lookup"><span data-stu-id="31d6d-107">[in] The token to mark as processed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31d6d-108">Требования</span><span class="sxs-lookup"><span data-stu-id="31d6d-108">Requirements</span></span>  

 <span data-ttu-id="31d6d-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31d6d-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31d6d-110">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="31d6d-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="31d6d-111">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="31d6d-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="31d6d-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31d6d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31d6d-113">См. также</span><span class="sxs-lookup"><span data-stu-id="31d6d-113">See also</span></span>

- [<span data-ttu-id="31d6d-114">Интерфейс IMetaDataFilter</span><span class="sxs-lookup"><span data-stu-id="31d6d-114">IMetaDataFilter Interface</span></span>](imetadatafilter-interface.md)
