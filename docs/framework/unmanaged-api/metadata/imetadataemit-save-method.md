---
description: 'Дополнительные сведения: Метод IMetaDataEmit:: Save'
title: Метод IMetaDataEmit::Save
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Save
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Save
helpviewer_keywords:
- Save method, IMetaDataEmit interface [.NET Framework metadata]
- IMetaDataEmit::Save method [.NET Framework metadata]
ms.assetid: c1de8400-adfe-4a71-b828-a1d0cc1ea505
topic_type:
- apiref
ms.openlocfilehash: bf8675540ae2c851d2b6ed14883c9b75e9631903
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745870"
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="fe42b-103">Метод IMetaDataEmit::Save</span><span class="sxs-lookup"><span data-stu-id="fe42b-103">IMetaDataEmit::Save Method</span></span>

<span data-ttu-id="fe42b-104">Сохраняет все метаданные в текущей области в файле по указанному адресу.</span><span class="sxs-lookup"><span data-stu-id="fe42b-104">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe42b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fe42b-105">Syntax</span></span>  
  
```cpp  
HRESULT Save (
    [in]  LPCWSTR     szFile,
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe42b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="fe42b-106">Parameters</span></span>  

 `wzFile`  
 <span data-ttu-id="fe42b-107">окне Имя файла, в который необходимо выполнить сохранение.</span><span class="sxs-lookup"><span data-stu-id="fe42b-107">[in] The name of the file to save to.</span></span> <span data-ttu-id="fe42b-108">Если это значение равно null, копия в памяти будет сохранена в последнем используемом расположении.</span><span class="sxs-lookup"><span data-stu-id="fe42b-108">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="fe42b-109">[in] Зарезервировано.</span><span class="sxs-lookup"><span data-stu-id="fe42b-109">[in] Reserved.</span></span> <span data-ttu-id="fe42b-110">Должен равняться нулю.</span><span class="sxs-lookup"><span data-stu-id="fe42b-110">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe42b-111">Требования</span><span class="sxs-lookup"><span data-stu-id="fe42b-111">Requirements</span></span>  

 <span data-ttu-id="fe42b-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe42b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe42b-113">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="fe42b-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fe42b-114">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fe42b-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fe42b-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe42b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe42b-116">См. также</span><span class="sxs-lookup"><span data-stu-id="fe42b-116">See also</span></span>

- [<span data-ttu-id="fe42b-117">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="fe42b-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="fe42b-118">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="fe42b-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
