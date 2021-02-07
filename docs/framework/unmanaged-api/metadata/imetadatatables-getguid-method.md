---
description: 'Дополнительные сведения о методе: IMetaDataTables:: с идентификатором GUID'
title: Метод IMetaDataTables::GetGuid
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuid
helpviewer_keywords:
- GetGuid method [.NET Framework metadata]
- IMetaDataTables::GetGuid method [.NET Framework metadata]
ms.assetid: a3546316-e24d-417f-9909-e45d42c9d471
topic_type:
- apiref
ms.openlocfilehash: 9c3b8b11bb2f6a1abc3c55d953e1cbfbd7ee8622
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688173"
---
# <a name="imetadatatablesgetguid-method"></a><span data-ttu-id="dab33-103">Метод IMetaDataTables::GetGuid</span><span class="sxs-lookup"><span data-stu-id="dab33-103">IMetaDataTables::GetGuid Method</span></span>

<span data-ttu-id="dab33-104">Возвращает идентификатор GUID из строки по указанному индексу.</span><span class="sxs-lookup"><span data-stu-id="dab33-104">Gets a GUID from the row at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dab33-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dab33-105">Syntax</span></span>  
  
```cpp  
HRESULT GetGuid (
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dab33-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="dab33-106">Parameters</span></span>  

 `ixGuid`  
 <span data-ttu-id="dab33-107">окне Индекс строки, из которой необходимо получить идентификатор GUID.</span><span class="sxs-lookup"><span data-stu-id="dab33-107">[in] The index of the row from which to get the GUID.</span></span>  
  
 `ppGuid`  
 <span data-ttu-id="dab33-108">заполняет Указатель на указатель на идентификатор GUID.</span><span class="sxs-lookup"><span data-stu-id="dab33-108">[out] A pointer to a pointer to the GUID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dab33-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="dab33-109">Remarks</span></span>  

  <span data-ttu-id="dab33-110">Мы не рекомендуем использовать этот метод, так как он не возвращает последовательные результаты.</span><span class="sxs-lookup"><span data-stu-id="dab33-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="dab33-111">Сведения о таблице GUID см. в документации по Common Language Infrastructure (CLI), особенно в разделе "Partition II: определение метаданных и семантика".</span><span class="sxs-lookup"><span data-stu-id="dab33-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="dab33-112">Документация доступна в Интернете; см. раздел [ECMA C# and Common Language Infrastructure](../../../standard/components.md#applicable-standards) Standards и [Standard ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="dab33-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dab33-113">Требования</span><span class="sxs-lookup"><span data-stu-id="dab33-113">Requirements</span></span>  

 <span data-ttu-id="dab33-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dab33-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dab33-115">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="dab33-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dab33-116">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dab33-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dab33-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dab33-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dab33-118">См. также</span><span class="sxs-lookup"><span data-stu-id="dab33-118">See also</span></span>

- [<span data-ttu-id="dab33-119">Интерфейс IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="dab33-119">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="dab33-120">Интерфейс IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="dab33-120">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
