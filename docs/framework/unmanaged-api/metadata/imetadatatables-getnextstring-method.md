---
description: 'Дополнительные сведения о методе: IMetaDataTables:: Жетнекстстринг'
title: Метод IMetaDataTables::GetNextString
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextString
helpviewer_keywords:
- IMetaDataTables::GetNextString method [.NET Framework metadata]
- GetNextString method [.NET Framework metadata]
ms.assetid: d9720428-c353-4f07-a7e8-899e106a1b37
topic_type:
- apiref
ms.openlocfilehash: b3c4f94a2659b83c89bef322517465a585b63ddc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688017"
---
# <a name="imetadatatablesgetnextstring-method"></a><span data-ttu-id="c9912-103">Метод IMetaDataTables::GetNextString</span><span class="sxs-lookup"><span data-stu-id="c9912-103">IMetaDataTables::GetNextString Method</span></span>

<span data-ttu-id="c9912-104">Возвращает индекс следующей строки в текущем столбце таблицы.</span><span class="sxs-lookup"><span data-stu-id="c9912-104">Gets the index of the next string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9912-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c9912-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNextString (
    [in]  ULONG   ixString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9912-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c9912-106">Parameters</span></span>  

 `ixString`  
 <span data-ttu-id="c9912-107">окне Значение индекса из столбца таблицы строк.</span><span class="sxs-lookup"><span data-stu-id="c9912-107">[in] The index value from a string table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="c9912-108">заполняет Указатель на индекс следующей строки в столбце.</span><span class="sxs-lookup"><span data-stu-id="c9912-108">[out] A pointer to the index of the next string in the column.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9912-109">Требования</span><span class="sxs-lookup"><span data-stu-id="c9912-109">Requirements</span></span>  

 <span data-ttu-id="c9912-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9912-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9912-111">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="c9912-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c9912-112">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c9912-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c9912-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9912-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9912-114">См. также</span><span class="sxs-lookup"><span data-stu-id="c9912-114">See also</span></span>

- [<span data-ttu-id="c9912-115">Интерфейс IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="c9912-115">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="c9912-116">Интерфейс IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="c9912-116">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
