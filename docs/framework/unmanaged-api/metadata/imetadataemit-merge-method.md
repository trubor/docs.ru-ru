---
description: 'Дополнительные сведения: Метод IMetaDataEmit:: Merge'
title: Метод IMetaDataEmit::Merge
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Merge
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Merge
helpviewer_keywords:
- IMetaDataEmit::Merge method [.NET Framework metadata]
- Merge method [.NET Framework metadata]
ms.assetid: 7596220c-f699-4b6c-8ae7-c83220610650
topic_type:
- apiref
ms.openlocfilehash: 6b78dd20555acf1eaf610ed05d8a37ab6cdeee5c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745948"
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="b8c22-103">Метод IMetaDataEmit::Merge</span><span class="sxs-lookup"><span data-stu-id="b8c22-103">IMetaDataEmit::Merge Method</span></span>

<span data-ttu-id="b8c22-104">Добавляет указанную импортированную область в список объединяемых областей.</span><span class="sxs-lookup"><span data-stu-id="b8c22-104">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8c22-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b8c22-105">Syntax</span></span>  
  
```cpp  
HRESULT Merge (
    [in]  IMetaDataImport  *pImport,
    [in]  IMapToken        *pHostMapToken,
    [in]  IUnknown         *pHandler
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8c22-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b8c22-106">Parameters</span></span>  

 `pImport`  
 <span data-ttu-id="b8c22-107">окне Указатель на объект [IMetaDataImport](imetadataimport-interface.md) , определяющий импортируемую область для слияния.</span><span class="sxs-lookup"><span data-stu-id="b8c22-107">[in] A pointer to an [IMetaDataImport](imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="b8c22-108">окне Указатель на объект [IMapToken](imaptoken-interface.md) , указывающий повторное отображение токена.</span><span class="sxs-lookup"><span data-stu-id="b8c22-108">[in] A pointer to an [IMapToken](imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandler`  
 <span data-ttu-id="b8c22-109">окне Указатель на объект [IUnknown](/cpp/atl/iunknown) , указывающий ошибки.</span><span class="sxs-lookup"><span data-stu-id="b8c22-109">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8c22-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="b8c22-110">Remarks</span></span>  

 <span data-ttu-id="b8c22-111">Вызовите метод [IMetaDataEmit:: мержеенд](imetadataemit-mergeend-method.md) , чтобы активировать слияние метаданных в одну область.</span><span class="sxs-lookup"><span data-stu-id="b8c22-111">Call [IMetaDataEmit::MergeEnd](imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8c22-112">Требования</span><span class="sxs-lookup"><span data-stu-id="b8c22-112">Requirements</span></span>  

 <span data-ttu-id="b8c22-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8c22-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8c22-114">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="b8c22-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b8c22-115">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b8c22-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b8c22-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8c22-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8c22-117">См. также</span><span class="sxs-lookup"><span data-stu-id="b8c22-117">See also</span></span>

- [<span data-ttu-id="b8c22-118">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="b8c22-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="b8c22-119">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="b8c22-119">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
