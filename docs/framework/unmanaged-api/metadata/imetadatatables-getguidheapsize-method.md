---
description: 'Дополнительные сведения о методе: IMetaDataTables:: GetGuidHeapSize'
title: Метод IMetaDataTables::GetGuidHeapSize
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuidHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuidHeapSize
helpviewer_keywords:
- GetGuidHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetGuidHeapSize method [.NET Framework metadata]
ms.assetid: e875cbee-1ad9-4f1a-bf03-38cdb8ff371a
topic_type:
- apiref
ms.openlocfilehash: bbf2fd7e083c5a0a42ad69ab685b3e1aa8321d68
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688147"
---
# <a name="imetadatatablesgetguidheapsize-method"></a><span data-ttu-id="ef02c-103">Метод IMetaDataTables::GetGuidHeapSize</span><span class="sxs-lookup"><span data-stu-id="ef02c-103">IMetaDataTables::GetGuidHeapSize Method</span></span>

<span data-ttu-id="ef02c-104">Возвращает размер кучи GUID в байтах.</span><span class="sxs-lookup"><span data-stu-id="ef02c-104">Gets the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef02c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ef02c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetGuidHeapSize (  
    [out] ULONG   *pcbGuids  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef02c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ef02c-106">Parameters</span></span>  

 `pcbGuids`  
 <span data-ttu-id="ef02c-107">заполняет Указатель на размер кучи GUID в байтах.</span><span class="sxs-lookup"><span data-stu-id="ef02c-107">[out] A pointer to the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef02c-108">Требования</span><span class="sxs-lookup"><span data-stu-id="ef02c-108">Requirements</span></span>  

 <span data-ttu-id="ef02c-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef02c-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef02c-110">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="ef02c-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ef02c-111">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ef02c-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ef02c-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef02c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef02c-113">См. также</span><span class="sxs-lookup"><span data-stu-id="ef02c-113">See also</span></span>

- [<span data-ttu-id="ef02c-114">Интерфейс IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="ef02c-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="ef02c-115">Интерфейс IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="ef02c-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
