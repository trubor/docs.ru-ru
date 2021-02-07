---
description: 'Дополнительные сведения о методе: IMetaDataFilter:: Истокенмаркед'
title: Метод IMetaDataFilter::IsTokenMarked
ms.date: 03/30/2017
api_name:
- IMetaDataFilter.IsTokenMarked
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter::IsTokenMarked
helpviewer_keywords:
- IMetaDataFilter::IsTokenMarked method [.NET Framework metadata]
- IsTokenMarked method [.NET Framework metadata]
ms.assetid: 7d90dcee-0206-4540-807b-06982fe65f1a
topic_type:
- apiref
ms.openlocfilehash: dddb0aa9040a2f5ef3ec972bb37a9e8778ddffe8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677792"
---
# <a name="imetadatafilteristokenmarked-method"></a><span data-ttu-id="3a832-103">Метод IMetaDataFilter::IsTokenMarked</span><span class="sxs-lookup"><span data-stu-id="3a832-103">IMetaDataFilter::IsTokenMarked Method</span></span>

<span data-ttu-id="3a832-104">Возвращает значение, указывающее, помечен ли заданный маркер метаданных как обработанный.</span><span class="sxs-lookup"><span data-stu-id="3a832-104">Gets a value indicating whether the specified metadata token has been marked as processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a832-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3a832-105">Syntax</span></span>  
  
```cpp  
HRESULT IsTokenMarked (  
    [in]  mdToken  tk,
    [out] BOOL     *pIsMarked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a832-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="3a832-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="3a832-107">окне Токен для проверки на наличие метки обработки.</span><span class="sxs-lookup"><span data-stu-id="3a832-107">[in] The token to examine for a processing mark.</span></span>  
  
 `pIsMarked`  
 <span data-ttu-id="3a832-108">заполняет Значение, равное, если объект был `true` `tk` обработан; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="3a832-108">[out] A value that is `true` if `tk` has been processed; otherwise `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a832-109">Требования</span><span class="sxs-lookup"><span data-stu-id="3a832-109">Requirements</span></span>  

 <span data-ttu-id="3a832-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a832-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a832-111">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="3a832-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3a832-112">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3a832-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3a832-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a832-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a832-114">См. также</span><span class="sxs-lookup"><span data-stu-id="3a832-114">See also</span></span>

- [<span data-ttu-id="3a832-115">Интерфейс IMetaDataFilter</span><span class="sxs-lookup"><span data-stu-id="3a832-115">IMetaDataFilter Interface</span></span>](imetadatafilter-interface.md)
