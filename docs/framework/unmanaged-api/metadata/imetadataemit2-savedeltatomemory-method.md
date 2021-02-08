---
description: 'Дополнительные сведения о методе: IMetaDataEmit2:: Саведелтатомемори'
title: Метод IMetaDataEmit2::SaveDeltaToMemory
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDeltaToMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDeltaToMemory
helpviewer_keywords:
- SaveDeltaToMemory method [.NET Framework metadata]
- IMetaDataEmit2::SaveDeltaToMemory method [.NET Framework metadata]
ms.assetid: e2146726-0084-4c9e-a2d2-e8d461b13b21
topic_type:
- apiref
ms.openlocfilehash: 3ef01889df6dede85947508ca08635c95d655666
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771760"
---
# <a name="imetadataemit2savedeltatomemory-method"></a><span data-ttu-id="1b110-103">Метод IMetaDataEmit2::SaveDeltaToMemory</span><span class="sxs-lookup"><span data-stu-id="1b110-103">IMetaDataEmit2::SaveDeltaToMemory Method</span></span>

<span data-ttu-id="1b110-104">Сохраняет изменения из текущего сеанса "изменить и продолжить" в память.</span><span class="sxs-lookup"><span data-stu-id="1b110-104">Saves changes from the current edit-and-continue session to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b110-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1b110-105">Syntax</span></span>  
  
```cpp  
HRESULT SaveDeltaToMemory (  
    [out] void        *pbData,
    [in]  ULONG       cbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b110-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1b110-106">Parameters</span></span>  

 `pbData`  
 <span data-ttu-id="1b110-107">заполняет Адрес, с которого начинается запись разностных метаданных.</span><span class="sxs-lookup"><span data-stu-id="1b110-107">[out] The address at which to begin writing the metadata delta.</span></span>  
  
 `cbData`  
 <span data-ttu-id="1b110-108">окне Размер изменений.</span><span class="sxs-lookup"><span data-stu-id="1b110-108">[in] The size of the changes.</span></span> <span data-ttu-id="1b110-109">Чтобы определить размер, используйте [IMetaDataEmit2:: жетделтасавесизе](imetadataemit2-getdeltasavesize-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1b110-109">Use [IMetaDataEmit2::GetDeltaSaveSize](imetadataemit2-getdeltasavesize-method.md) to determine the size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b110-110">Требования</span><span class="sxs-lookup"><span data-stu-id="1b110-110">Requirements</span></span>  

 <span data-ttu-id="1b110-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b110-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b110-112">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="1b110-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1b110-113">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1b110-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1b110-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b110-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b110-115">См. также</span><span class="sxs-lookup"><span data-stu-id="1b110-115">See also</span></span>

- [<span data-ttu-id="1b110-116">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="1b110-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="1b110-117">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="1b110-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
