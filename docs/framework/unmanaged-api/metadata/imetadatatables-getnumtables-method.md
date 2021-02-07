---
description: 'Дополнительные сведения о методе: IMetaDataTables:: GetNumTables'
title: Метод IMetaDataTables::GetNumTables
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNumTables
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNumTables
helpviewer_keywords:
- GetNumTables method [.NET Framework metadata]
- IMetaDataTables::GetNumTables method [.NET Framework metadata]
ms.assetid: 8196f2a3-bbf2-45d3-a6cd-74502c356644
topic_type:
- apiref
ms.openlocfilehash: 1d1e386b1f1eb0f73fbd0df8ddff9cebc5817692
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687848"
---
# <a name="imetadatatablesgetnumtables-method"></a><span data-ttu-id="41308-103">Метод IMetaDataTables::GetNumTables</span><span class="sxs-lookup"><span data-stu-id="41308-103">IMetaDataTables::GetNumTables Method</span></span>

<span data-ttu-id="41308-104">Возвращает количество таблиц в области текущего `IMetaDataTables` экземпляра.</span><span class="sxs-lookup"><span data-stu-id="41308-104">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41308-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="41308-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNumTables (  
    [out]  ULONG   *pcTables  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41308-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="41308-106">Parameters</span></span>  

 `pcTables`  
 <span data-ttu-id="41308-107">заполняет Указатель на число таблиц в области текущего экземпляра.</span><span class="sxs-lookup"><span data-stu-id="41308-107">[out] A pointer to the number of tables in the current instance scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41308-108">Требования</span><span class="sxs-lookup"><span data-stu-id="41308-108">Requirements</span></span>  

 <span data-ttu-id="41308-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41308-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41308-110">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="41308-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="41308-111">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="41308-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="41308-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41308-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41308-113">См. также</span><span class="sxs-lookup"><span data-stu-id="41308-113">See also</span></span>

- [<span data-ttu-id="41308-114">Интерфейс IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="41308-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="41308-115">Интерфейс IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="41308-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
