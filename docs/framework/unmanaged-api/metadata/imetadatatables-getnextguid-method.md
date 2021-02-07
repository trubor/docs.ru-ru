---
description: 'Дополнительные сведения о методе: IMetaDataTables:: GetNextGuid'
title: Метод IMetaDataTables::GetNextGuid
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextGuid
helpviewer_keywords:
- GetNextGuid method [.NET Framework metadata]
- IMetaDataTables::GetNextGuid method [.NET Framework metadata]
ms.assetid: 68f6ea4d-9112-4d6b-93d9-e34f1e2f2496
topic_type:
- apiref
ms.openlocfilehash: 86c248bf503410a07fc0b4cf622694c4da213c34
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688108"
---
# <a name="imetadatatablesgetnextguid-method"></a><span data-ttu-id="2fa36-103">Метод IMetaDataTables::GetNextGuid</span><span class="sxs-lookup"><span data-stu-id="2fa36-103">IMetaDataTables::GetNextGuid Method</span></span>

<span data-ttu-id="2fa36-104">Возвращает индекс следующего значения GUID в текущем столбце таблицы.</span><span class="sxs-lookup"><span data-stu-id="2fa36-104">Gets the index of the next GUID value in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fa36-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2fa36-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNextGuid (  
    [in]  ULONG   ixGuid,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2fa36-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="2fa36-106">Parameters</span></span>  

 `ixGuid`  
 <span data-ttu-id="2fa36-107">окне Значение индекса из столбца таблицы GUID.</span><span class="sxs-lookup"><span data-stu-id="2fa36-107">[in] The index value from a GUID table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="2fa36-108">заполняет Указатель на индекс следующего значения GUID.</span><span class="sxs-lookup"><span data-stu-id="2fa36-108">[out] A pointer to the index of the next GUID value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2fa36-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="2fa36-109">Remarks</span></span>  

  <span data-ttu-id="2fa36-110">Мы не рекомендуем использовать этот метод, так как он не возвращает последовательные результаты.</span><span class="sxs-lookup"><span data-stu-id="2fa36-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="2fa36-111">Сведения о таблице GUID см. в документации по Common Language Infrastructure (CLI), особенно в разделе "Partition II: определение метаданных и семантика".</span><span class="sxs-lookup"><span data-stu-id="2fa36-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="2fa36-112">Документация доступна в Интернете; см. раздел [ECMA C# and Common Language Infrastructure](../../../standard/components.md#applicable-standards) Standards и [Standard ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="2fa36-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fa36-113">Требования</span><span class="sxs-lookup"><span data-stu-id="2fa36-113">Requirements</span></span>  

 <span data-ttu-id="2fa36-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fa36-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fa36-115">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="2fa36-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2fa36-116">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2fa36-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2fa36-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fa36-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fa36-118">См. также</span><span class="sxs-lookup"><span data-stu-id="2fa36-118">See also</span></span>

- [<span data-ttu-id="2fa36-119">Интерфейс IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="2fa36-119">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="2fa36-120">Интерфейс IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="2fa36-120">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
