---
description: 'Дополнительные сведения: метод IMetaDataImport:: EnumEvents'
title: Метод IMetaDataImport::EnumEvents
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumEvents
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumEvents
helpviewer_keywords:
- IMetaDataImport::EnumEvents method [.NET Framework metadata]
- EnumEvents method [.NET Framework metadata]
ms.assetid: e1efedcb-3dd7-42ae-a399-21c24728aec5
topic_type:
- apiref
ms.openlocfilehash: e944c15a19314b315e01493836ce078fccc917eb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799412"
---
# <a name="imetadataimportenumevents-method"></a><span data-ttu-id="57397-103">Метод IMetaDataImport::EnumEvents</span><span class="sxs-lookup"><span data-stu-id="57397-103">IMetaDataImport::EnumEvents Method</span></span>

<span data-ttu-id="57397-104">Перечисляет токены определений событий для указанного токена TypeDef.</span><span class="sxs-lookup"><span data-stu-id="57397-104">Enumerates event definition tokens for the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57397-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="57397-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumEvents (
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   td,
   [out]     mdEvent     rEvents[],
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57397-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="57397-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="57397-107">[вход, выход] Указатель на перечислитель.</span><span class="sxs-lookup"><span data-stu-id="57397-107">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="57397-108">окне Токен TypeDef, определения событий которого должны быть перечислены.</span><span class="sxs-lookup"><span data-stu-id="57397-108">[in] The TypeDef token whose event definitions are to be enumerated.</span></span>  
  
 `rEvents`  
 <span data-ttu-id="57397-109">заполняет Массив возвращаемых событий.</span><span class="sxs-lookup"><span data-stu-id="57397-109">[out] The array of returned events.</span></span>  
  
 `cMax`  
 <span data-ttu-id="57397-110">[in] Максимальный размер массива `rEvents`.</span><span class="sxs-lookup"><span data-stu-id="57397-110">[in] The maximum size of the `rEvents` array.</span></span>  
  
 `pcEvents`  
 <span data-ttu-id="57397-111">заполняет Фактическое число событий, возвращаемых в `rEvents` .</span><span class="sxs-lookup"><span data-stu-id="57397-111">[out] The actual number of events returned in `rEvents`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57397-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="57397-112">Return Value</span></span>  
  
|<span data-ttu-id="57397-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="57397-113">HRESULT</span></span>|<span data-ttu-id="57397-114">Описание</span><span class="sxs-lookup"><span data-stu-id="57397-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="57397-115">`EnumEvents` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="57397-115">`EnumEvents` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="57397-116">Нет событий для перечисления.</span><span class="sxs-lookup"><span data-stu-id="57397-116">There are no events to enumerate.</span></span> <span data-ttu-id="57397-117">В этом случае значение `pcEvents` равно нулю.</span><span class="sxs-lookup"><span data-stu-id="57397-117">In that case, `pcEvents` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="57397-118">Требования</span><span class="sxs-lookup"><span data-stu-id="57397-118">Requirements</span></span>  

 <span data-ttu-id="57397-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57397-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57397-120">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="57397-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="57397-121">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="57397-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="57397-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57397-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57397-123">См. также</span><span class="sxs-lookup"><span data-stu-id="57397-123">See also</span></span>

- [<span data-ttu-id="57397-124">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="57397-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="57397-125">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="57397-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
