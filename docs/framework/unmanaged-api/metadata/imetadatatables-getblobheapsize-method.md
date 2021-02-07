---
description: 'Дополнительные сведения о методе: IMetaDataTables:: Жетблобхеапсизе'
title: Метод IMetaDataTables::GetBlobHeapSize
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetBlobHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetBlobHeapSize
helpviewer_keywords:
- GetBlobHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetBlobHeapSize method [.NET Framework metadata]
ms.assetid: 6330a9ee-8cd5-4299-86f1-b4de2c701a0d
topic_type:
- apiref
ms.openlocfilehash: f6d5c7aeb5e1cc1f307d53d8f3e3cc99daa72311
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688316"
---
# <a name="imetadatatablesgetblobheapsize-method"></a><span data-ttu-id="b063f-103">Метод IMetaDataTables::GetBlobHeapSize</span><span class="sxs-lookup"><span data-stu-id="b063f-103">IMetaDataTables::GetBlobHeapSize Method</span></span>

<span data-ttu-id="b063f-104">Возвращает размер кучи большого двоичного объекта (в байтах).</span><span class="sxs-lookup"><span data-stu-id="b063f-104">Gets the size, in bytes, of the binary large object (BLOB) heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b063f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b063f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetBlobHeapSize (  
    [out] ULONG     *pcbBlobs  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="b063f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b063f-106">Parameters</span></span>  

 `pcbBlobs`  
 <span data-ttu-id="b063f-107">заполняет Указатель на размер кучи больших двоичных объектов (в байтах).</span><span class="sxs-lookup"><span data-stu-id="b063f-107">[out] A pointer to the size, in bytes, of the BLOB heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b063f-108">Требования</span><span class="sxs-lookup"><span data-stu-id="b063f-108">Requirements</span></span>  

 <span data-ttu-id="b063f-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b063f-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b063f-110">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="b063f-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b063f-111">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b063f-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b063f-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b063f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b063f-113">См. также</span><span class="sxs-lookup"><span data-stu-id="b063f-113">See also</span></span>

- [<span data-ttu-id="b063f-114">Интерфейс IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="b063f-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="b063f-115">Интерфейс IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="b063f-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
