---
description: 'Дополнительные сведения о методе: IMetaDataTables:: Жетнекстблоб'
title: Метод IMetaDataTables::GetNextBlob
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextBlob
helpviewer_keywords:
- IMetaDataTables::GetNextBlob method [.NET Framework metadata]
- GetNextBlob method [.NET Framework metadata]
ms.assetid: 017c8ab4-4c09-4754-9935-5b0b49cabecb
topic_type:
- apiref
ms.openlocfilehash: 99126ab5c3891ee09346bb54096a4fce3ca44bc5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688134"
---
# <a name="imetadatatablesgetnextblob-method"></a><span data-ttu-id="6fb49-103">Метод IMetaDataTables::GetNextBlob</span><span class="sxs-lookup"><span data-stu-id="6fb49-103">IMetaDataTables::GetNextBlob Method</span></span>

<span data-ttu-id="6fb49-104">Возвращает индекс следующего большого двоичного объекта (BLOB) в таблице.</span><span class="sxs-lookup"><span data-stu-id="6fb49-104">Gets the index of the next binary large object (BLOB) in the table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fb49-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6fb49-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNextBlob (  
    [in]  ULONG   ixBlob,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6fb49-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6fb49-106">Parameters</span></span>  

 `ixBlob`  
 <span data-ttu-id="6fb49-107">окне Индекс, возвращенный из столбца больших двоичных объектов.</span><span class="sxs-lookup"><span data-stu-id="6fb49-107">[in] The index, as returned from a column of BLOBs.</span></span>  
  
 `pNext`  
 <span data-ttu-id="6fb49-108">заполняет Указатель на индекс следующего большого двоичного объекта.</span><span class="sxs-lookup"><span data-stu-id="6fb49-108">[out] A pointer to the index of the next BLOB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fb49-109">Требования</span><span class="sxs-lookup"><span data-stu-id="6fb49-109">Requirements</span></span>  

 <span data-ttu-id="6fb49-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fb49-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fb49-111">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="6fb49-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6fb49-112">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6fb49-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6fb49-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fb49-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fb49-114">См. также</span><span class="sxs-lookup"><span data-stu-id="6fb49-114">See also</span></span>

- [<span data-ttu-id="6fb49-115">Интерфейс IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="6fb49-115">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="6fb49-116">Интерфейс IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="6fb49-116">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
