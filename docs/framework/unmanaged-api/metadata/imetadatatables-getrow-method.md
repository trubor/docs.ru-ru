---
description: 'Дополнительные сведения о методе: IMetaDataTables:: GetRow'
title: Метод IMetaDataTables::GetRow
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetRow
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetRow
helpviewer_keywords:
- IMetaDataTables::GetRow method [.NET Framework metadata]
- GetRow method [.NET Framework metadata]
ms.assetid: a7408d51-0bce-45a2-b58f-da4660bbc039
topic_type:
- apiref
ms.openlocfilehash: f3888bbb53339dc60eb0c2d36f2d7383e5f8c228
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687822"
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="fffc8-103">Метод IMetaDataTables::GetRow</span><span class="sxs-lookup"><span data-stu-id="fffc8-103">IMetaDataTables::GetRow Method</span></span>

<span data-ttu-id="fffc8-104">Возвращает строку по указанному индексу строки в таблице по указанному индексу таблицы.</span><span class="sxs-lookup"><span data-stu-id="fffc8-104">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fffc8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fffc8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRow (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fffc8-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="fffc8-106">Parameters</span></span>  

 `ixTbl`  
 <span data-ttu-id="fffc8-107">окне Индекс таблицы, из которой будет извлечена строка.</span><span class="sxs-lookup"><span data-stu-id="fffc8-107">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="fffc8-108">окне Индекс получаемой строки.</span><span class="sxs-lookup"><span data-stu-id="fffc8-108">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="fffc8-109">заполняет Указатель на указатель на строку.</span><span class="sxs-lookup"><span data-stu-id="fffc8-109">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fffc8-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="fffc8-110">Remarks</span></span>  

  <span data-ttu-id="fffc8-111">Мы не рекомендуем использовать этот метод, так как он не возвращает последовательные результаты.</span><span class="sxs-lookup"><span data-stu-id="fffc8-111">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="fffc8-112">Сведения о таблице GUID см. в документации по Common Language Infrastructure (CLI), особенно в разделе "Partition II: определение метаданных и семантика".</span><span class="sxs-lookup"><span data-stu-id="fffc8-112">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="fffc8-113">Документация доступна в Интернете; см. раздел [ECMA C# and Common Language Infrastructure](../../../standard/components.md#applicable-standards) Standards и [Standard ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="fffc8-113">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fffc8-114">Требования</span><span class="sxs-lookup"><span data-stu-id="fffc8-114">Requirements</span></span>  

 <span data-ttu-id="fffc8-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fffc8-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fffc8-116">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="fffc8-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fffc8-117">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fffc8-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fffc8-118">**Версии платформа .NET Framework**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fffc8-118">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fffc8-119">См. также</span><span class="sxs-lookup"><span data-stu-id="fffc8-119">See also</span></span>

- [<span data-ttu-id="fffc8-120">Интерфейс IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="fffc8-120">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="fffc8-121">Интерфейс IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="fffc8-121">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
