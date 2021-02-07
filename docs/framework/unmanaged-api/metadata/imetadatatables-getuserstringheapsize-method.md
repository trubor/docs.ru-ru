---
description: 'Дополнительные сведения о методе: IMetaDataTables:: Жетусерстрингхеапсизе'
title: Метод IMetaDataTables::GetUserStringHeapSize
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserStringHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserStringHeapSize
helpviewer_keywords:
- IMetaDataTables::GetUserStringHeapSize method [.NET Framework metadata]
- GetUserStringHeapSize method [.NET Framework metadata]
ms.assetid: cba9e4d6-9461-4420-9614-96ff7039ec9c
topic_type:
- apiref
ms.openlocfilehash: 7e6f3eed7803f52e6bde888852c4971900f0868c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687627"
---
# <a name="imetadatatablesgetuserstringheapsize-method"></a><span data-ttu-id="8feb0-103">Метод IMetaDataTables::GetUserStringHeapSize</span><span class="sxs-lookup"><span data-stu-id="8feb0-103">IMetaDataTables::GetUserStringHeapSize Method</span></span>

<span data-ttu-id="8feb0-104">Возвращает размер (в байтах) кучи пользовательской строки.</span><span class="sxs-lookup"><span data-stu-id="8feb0-104">Gets the size, in bytes, of the user string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8feb0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8feb0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetUserStringHeapSize (  
    [out] ULONG   *pcbBlobs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8feb0-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8feb0-106">Parameters</span></span>  

 `pcbBlobs`  
 <span data-ttu-id="8feb0-107">заполняет Указатель на размер (в байтах) кучи пользовательской строки.</span><span class="sxs-lookup"><span data-stu-id="8feb0-107">[out] A pointer to the size, in bytes, of the user string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8feb0-108">Требования</span><span class="sxs-lookup"><span data-stu-id="8feb0-108">Requirements</span></span>  

 <span data-ttu-id="8feb0-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8feb0-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8feb0-110">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="8feb0-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8feb0-111">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8feb0-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8feb0-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8feb0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8feb0-113">См. также</span><span class="sxs-lookup"><span data-stu-id="8feb0-113">See also</span></span>

- [<span data-ttu-id="8feb0-114">Интерфейс IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="8feb0-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="8feb0-115">Интерфейс IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="8feb0-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
