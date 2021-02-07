---
description: 'Дополнительные сведения о методе: IMetaDataTables:: Жеттаблеиндекс'
title: Метод IMetaDataTables::GetTableIndex
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetTableIndex
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetTableIndex
helpviewer_keywords:
- GetTableIndex method [.NET Framework metadata]
- IMetaDataTables::GetTableIndex method [.NET Framework metadata]
ms.assetid: c6ec3800-e0d9-4387-afb8-ddc0b818114c
topic_type:
- apiref
ms.openlocfilehash: d42a42a1a19a67fada17bbe1016f7e324cd1c287
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687731"
---
# <a name="imetadatatablesgettableindex-method"></a><span data-ttu-id="07ac5-103">Метод IMetaDataTables::GetTableIndex</span><span class="sxs-lookup"><span data-stu-id="07ac5-103">IMetaDataTables::GetTableIndex Method</span></span>

<span data-ttu-id="07ac5-104">Возвращает индекс для таблицы, на которую ссылается указанный токен.</span><span class="sxs-lookup"><span data-stu-id="07ac5-104">Gets the index for the table referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07ac5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="07ac5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTableIndex (  
    [in]  ULONG   token,  
    [out] ULONG   *pixTbl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07ac5-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="07ac5-106">Parameters</span></span>  

 `token`  
 <span data-ttu-id="07ac5-107">окне Токен, ссылающийся на таблицу.</span><span class="sxs-lookup"><span data-stu-id="07ac5-107">[in] The token that references the table.</span></span>  
  
 `pixTbl`  
 <span data-ttu-id="07ac5-108">заполняет Указатель на возвращаемый индекс для упоминаемой таблицы.</span><span class="sxs-lookup"><span data-stu-id="07ac5-108">[out] A pointer to the returned index for the referenced table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07ac5-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="07ac5-109">Remarks</span></span>  

 <span data-ttu-id="07ac5-110">Мы не рекомендуем использовать этот метод, так как он не возвращает последовательные результаты.</span><span class="sxs-lookup"><span data-stu-id="07ac5-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="07ac5-111">Сведения о таблице GUID см. в документации по Common Language Infrastructure (CLI), особенно в разделе "Partition II: определение метаданных и семантика".</span><span class="sxs-lookup"><span data-stu-id="07ac5-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="07ac5-112">Документация доступна в Интернете; см. раздел [ECMA C# and Common Language Infrastructure](../../../standard/components.md#applicable-standards) Standards и [Standard ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="07ac5-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07ac5-113">Требования</span><span class="sxs-lookup"><span data-stu-id="07ac5-113">Requirements</span></span>  

 <span data-ttu-id="07ac5-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07ac5-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07ac5-115">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="07ac5-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="07ac5-116">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="07ac5-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="07ac5-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07ac5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07ac5-118">См. также</span><span class="sxs-lookup"><span data-stu-id="07ac5-118">See also</span></span>

- [<span data-ttu-id="07ac5-119">Интерфейс IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="07ac5-119">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="07ac5-120">Интерфейс IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="07ac5-120">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
