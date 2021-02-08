---
description: 'Дополнительные сведения о методе: IMetaDataEmit2:: Саведелта'
title: Метод IMetaDataEmit2::SaveDelta
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDelta
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDelta
helpviewer_keywords:
- IMetaDataEmit2::SaveDelta method [.NET Framework metadata]
- SaveDelta method [.NET Framework metadata]
ms.assetid: b95739fe-d2fa-4776-ae0d-31d9707ef799
topic_type:
- apiref
ms.openlocfilehash: 6e7a7527125869fea041f407da056db3eea88cbe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771773"
---
# <a name="imetadataemit2savedelta-method"></a><span data-ttu-id="002e5-103">Метод IMetaDataEmit2::SaveDelta</span><span class="sxs-lookup"><span data-stu-id="002e5-103">IMetaDataEmit2::SaveDelta Method</span></span>

<span data-ttu-id="002e5-104">Сохраняет изменения из текущего сеанса "изменить и продолжить" в указанный файл.</span><span class="sxs-lookup"><span data-stu-id="002e5-104">Saves changes from the current edit-and-continue session to the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="002e5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="002e5-105">Syntax</span></span>  
  
```cpp  
HRESULT SaveDelta (  
    [in] LPCWSTR     szFile,
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="002e5-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="002e5-106">Parameters</span></span>  

 `szFile`  
 <span data-ttu-id="002e5-107">окне Имя файла, в котором необходимо сохранить изменения.</span><span class="sxs-lookup"><span data-stu-id="002e5-107">[in] The file name under which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="002e5-108">[in] Зарезервировано.</span><span class="sxs-lookup"><span data-stu-id="002e5-108">[in] Reserved.</span></span> <span data-ttu-id="002e5-109">Должен равняться нулю.</span><span class="sxs-lookup"><span data-stu-id="002e5-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="002e5-110">Требования</span><span class="sxs-lookup"><span data-stu-id="002e5-110">Requirements</span></span>  

 <span data-ttu-id="002e5-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="002e5-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="002e5-112">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="002e5-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="002e5-113">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="002e5-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="002e5-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="002e5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="002e5-115">См. также</span><span class="sxs-lookup"><span data-stu-id="002e5-115">See also</span></span>

- [<span data-ttu-id="002e5-116">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="002e5-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="002e5-117">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="002e5-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
