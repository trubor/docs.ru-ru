---
description: 'Дополнительные сведения о методе: IMetaDataTables:: GetNextUserString'
title: Метод IMetaDataTables::GetNextUserString
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextUserString
helpviewer_keywords:
- GetNextUserString method [.NET Framework metadata]
- IMetaDataTables::GetNextUserString method [.NET Framework metadata]
ms.assetid: b7cb40ee-67b7-4f4e-8dcc-ee7ac8bc986b
topic_type:
- apiref
ms.openlocfilehash: cba1fad18b4f697a5e48ad3b0676bf93f9c66e4e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687965"
---
# <a name="imetadatatablesgetnextuserstring-method"></a><span data-ttu-id="4197e-103">Метод IMetaDataTables::GetNextUserString</span><span class="sxs-lookup"><span data-stu-id="4197e-103">IMetaDataTables::GetNextUserString Method</span></span>

<span data-ttu-id="4197e-104">Возвращает индекс строки, содержащей следующую жестко заданную строку в текущем столбце таблицы.</span><span class="sxs-lookup"><span data-stu-id="4197e-104">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4197e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4197e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNextUserString (  
    [in]  ULONG   ixUserString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4197e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="4197e-106">Parameters</span></span>  

 `ixUserString`  
 <span data-ttu-id="4197e-107">окне Значение индекса из текущего строкового столбца.</span><span class="sxs-lookup"><span data-stu-id="4197e-107">[in] An index value from the current string column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="4197e-108">заполняет Указатель на индекс строки следующей строки в столбце.</span><span class="sxs-lookup"><span data-stu-id="4197e-108">[out] A pointer to the row index of the next string in the column.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4197e-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="4197e-109">Remarks</span></span>  

 <span data-ttu-id="4197e-110">Мы не рекомендуем использовать этот метод, так как он не возвращает последовательные результаты.</span><span class="sxs-lookup"><span data-stu-id="4197e-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="4197e-111">Сведения о таблице GUID см. в документации по Common Language Infrastructure (CLI), особенно в разделе "Partition II: определение метаданных и семантика".</span><span class="sxs-lookup"><span data-stu-id="4197e-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="4197e-112">Документация доступна в Интернете; см. раздел [ECMA C# and Common Language Infrastructure](../../../standard/components.md#applicable-standards) Standards и [Standard ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="4197e-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4197e-113">Требования</span><span class="sxs-lookup"><span data-stu-id="4197e-113">Requirements</span></span>  

 <span data-ttu-id="4197e-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4197e-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4197e-115">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="4197e-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4197e-116">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4197e-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4197e-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4197e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4197e-118">См. также</span><span class="sxs-lookup"><span data-stu-id="4197e-118">See also</span></span>

- [<span data-ttu-id="4197e-119">Интерфейс IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="4197e-119">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="4197e-120">Интерфейс IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="4197e-120">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
