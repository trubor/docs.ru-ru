---
description: 'Дополнительные сведения о методе: IMetaDataEmit2:: Саведелтатостреам'
title: Метод IMetaDataEmit2::SaveDeltaToStream
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDeltaToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDeltaToStream
helpviewer_keywords:
- IMetaDataEmit2::SaveDeltaToStream method [.NET Framework metadata]
- SaveDeltaToStream method [.NET Framework metadata]
ms.assetid: ecd786e8-f9a4-4190-a6ef-af18e8c6d654
topic_type:
- apiref
ms.openlocfilehash: ce2e7822a5220a8ab1264a6e18337ba0f7828e3b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771708"
---
# <a name="imetadataemit2savedeltatostream-method"></a><span data-ttu-id="b362c-103">Метод IMetaDataEmit2::SaveDeltaToStream</span><span class="sxs-lookup"><span data-stu-id="b362c-103">IMetaDataEmit2::SaveDeltaToStream Method</span></span>

<span data-ttu-id="b362c-104">Сохраняет изменения из текущего сеанса "изменить и продолжить" в указанный поток.</span><span class="sxs-lookup"><span data-stu-id="b362c-104">Saves changes from the current edit-and-continue session to the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b362c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b362c-105">Syntax</span></span>  
  
```cpp  
HRESULT SaveDeltaToStream (  
    [in] IStream     *pIStream,
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b362c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b362c-106">Parameters</span></span>  

 `pIStream`  
 <span data-ttu-id="b362c-107">окне Указатель интерфейса на поток, доступный для записи, в который необходимо сохранить изменения.</span><span class="sxs-lookup"><span data-stu-id="b362c-107">[in] An interface pointer to the writable stream to which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="b362c-108">[in] Зарезервировано.</span><span class="sxs-lookup"><span data-stu-id="b362c-108">[in] Reserved.</span></span> <span data-ttu-id="b362c-109">Это значение должно быть равно нулю.</span><span class="sxs-lookup"><span data-stu-id="b362c-109">This value must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b362c-110">Требования</span><span class="sxs-lookup"><span data-stu-id="b362c-110">Requirements</span></span>  

 <span data-ttu-id="b362c-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b362c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b362c-112">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="b362c-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b362c-113">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b362c-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b362c-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b362c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b362c-115">См. также</span><span class="sxs-lookup"><span data-stu-id="b362c-115">See also</span></span>

- [<span data-ttu-id="b362c-116">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="b362c-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="b362c-117">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="b362c-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
