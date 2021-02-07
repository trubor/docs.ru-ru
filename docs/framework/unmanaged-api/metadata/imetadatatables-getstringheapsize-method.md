---
description: 'Дополнительные сведения о методе: IMetaDataTables:: Жетстрингхеапсизе'
title: Метод IMetaDataTables::GetStringHeapSize
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetStringHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetStringHeapSize
helpviewer_keywords:
- IMetaDataTables::GetStringHeapSize method [.NET Framework metadata]
- GetStringHeapSize method [.NET Framework metadata]
ms.assetid: ed8f6335-81f5-4c09-81a9-2a909fc530c9
topic_type:
- apiref
ms.openlocfilehash: 0ec9f4e2768cc78163db67bc9099fc9cafae8c8c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687783"
---
# <a name="imetadatatablesgetstringheapsize-method"></a><span data-ttu-id="5cb41-103">Метод IMetaDataTables::GetStringHeapSize</span><span class="sxs-lookup"><span data-stu-id="5cb41-103">IMetaDataTables::GetStringHeapSize Method</span></span>

<span data-ttu-id="5cb41-104">Возвращает размер кучи строк (в байтах).</span><span class="sxs-lookup"><span data-stu-id="5cb41-104">Gets the size, in bytes, of the string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cb41-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5cb41-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringHeapSize (  
    [out] ULONG   *pcbStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5cb41-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="5cb41-106">Parameters</span></span>  

 `pcbStrings`  
 <span data-ttu-id="5cb41-107">заполняет Указатель на размер (в байтах) кучи строк.</span><span class="sxs-lookup"><span data-stu-id="5cb41-107">[out] A pointer to the size, in bytes, of the string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cb41-108">Требования</span><span class="sxs-lookup"><span data-stu-id="5cb41-108">Requirements</span></span>  

 <span data-ttu-id="5cb41-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cb41-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cb41-110">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="5cb41-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5cb41-111">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5cb41-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5cb41-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cb41-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cb41-113">См. также</span><span class="sxs-lookup"><span data-stu-id="5cb41-113">See also</span></span>

- [<span data-ttu-id="5cb41-114">Интерфейс IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="5cb41-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="5cb41-115">Интерфейс IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="5cb41-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
