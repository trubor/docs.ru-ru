---
description: 'Дополнительные сведения о методе: IHostFilter:: Марктокен'
title: Метод IHostFilter::MarkToken
ms.date: 03/30/2017
api_name:
- IHostFilter.MarkToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostFilter::MarkToken
helpviewer_keywords:
- MarkToken method, IHostFilter interface [.NET Framework metadata]
- IHostFilter::MarkToken method [.NET Framework metadata]
ms.assetid: d7061343-d0a3-4fd5-b312-61974f98bd62
topic_type:
- apiref
ms.openlocfilehash: c8f5ecdef56b77e1b0031a93d6d8f7de79de4c3b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784188"
---
# <a name="ihostfiltermarktoken-method"></a><span data-ttu-id="6a67b-103">Метод IHostFilter::MarkToken</span><span class="sxs-lookup"><span data-stu-id="6a67b-103">IHostFilter::MarkToken Method</span></span>

<span data-ttu-id="6a67b-104">Указывает, что заданный маркер метаданных будет обработан.</span><span class="sxs-lookup"><span data-stu-id="6a67b-104">Indicates that the specified metadata token will be processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a67b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6a67b-105">Syntax</span></span>  
  
```cpp  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a67b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a67b-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="6a67b-107">окне Токен метаданных для обработки.</span><span class="sxs-lookup"><span data-stu-id="6a67b-107">[in] The metadata token to be processed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a67b-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="6a67b-108">Remarks</span></span>  

 <span data-ttu-id="6a67b-109">Как правило, требуется обработка маркера, если он находится в области действия метаданных.</span><span class="sxs-lookup"><span data-stu-id="6a67b-109">Typically, you want a token to be processed if it is in the metadata scope.</span></span> <span data-ttu-id="6a67b-110">`MarkToken`Метод передается в обработчик метаданных с помощью метода [IMetaDataEmit:: сесандлер](imetadataemit-sethandler-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6a67b-110">The `MarkToken` method is passed to the metadata engine via the [IMetaDataEmit::SetHandler](imetadataemit-sethandler-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a67b-111">Требования</span><span class="sxs-lookup"><span data-stu-id="6a67b-111">Requirements</span></span>  

 <span data-ttu-id="6a67b-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a67b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a67b-113">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="6a67b-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6a67b-114">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6a67b-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6a67b-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a67b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a67b-116">См. также</span><span class="sxs-lookup"><span data-stu-id="6a67b-116">See also</span></span>

- [<span data-ttu-id="6a67b-117">Интерфейсы метаданных</span><span class="sxs-lookup"><span data-stu-id="6a67b-117">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="6a67b-118">Интерфейс IHostFilter</span><span class="sxs-lookup"><span data-stu-id="6a67b-118">IHostFilter Interface</span></span>](ihostfilter-interface.md)
