---
description: 'Дополнительные сведения: Метод IMetaDataEmit:: Саветостреам'
title: Метод IMetaDataEmit::SaveToStream
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToStream
helpviewer_keywords:
- IMetaDataEmit::SaveToStream method [.NET Framework metadata]
- SaveToStream method [.NET Framework metadata]
ms.assetid: e0290a49-3818-4a43-ad46-3014faa34f97
topic_type:
- apiref
ms.openlocfilehash: 104aa0b0dfcd0f4f9e8b87b4633880f6423f92d0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706660"
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="edbdf-103">Метод IMetaDataEmit::SaveToStream</span><span class="sxs-lookup"><span data-stu-id="edbdf-103">IMetaDataEmit::SaveToStream Method</span></span>

<span data-ttu-id="edbdf-104">Сохраняет все метаданные в текущей области в указанном `IStream` .</span><span class="sxs-lookup"><span data-stu-id="edbdf-104">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edbdf-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="edbdf-105">Syntax</span></span>  
  
```cpp  
HRESULT SaveToStream (
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="edbdf-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="edbdf-106">Parameters</span></span>  

 `pIStream`  
 <span data-ttu-id="edbdf-107">окне Доступный для записи поток для сохранения.</span><span class="sxs-lookup"><span data-stu-id="edbdf-107">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="edbdf-108">[in] Зарезервировано.</span><span class="sxs-lookup"><span data-stu-id="edbdf-108">[in] Reserved.</span></span> <span data-ttu-id="edbdf-109">Должен равняться нулю.</span><span class="sxs-lookup"><span data-stu-id="edbdf-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edbdf-110">Требования</span><span class="sxs-lookup"><span data-stu-id="edbdf-110">Requirements</span></span>  

 <span data-ttu-id="edbdf-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edbdf-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edbdf-112">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="edbdf-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="edbdf-113">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="edbdf-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="edbdf-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edbdf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edbdf-115">См. также</span><span class="sxs-lookup"><span data-stu-id="edbdf-115">See also</span></span>

- [<span data-ttu-id="edbdf-116">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="edbdf-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="edbdf-117">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="edbdf-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
