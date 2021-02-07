---
description: 'Дополнительные сведения о методе: IMetaDataTables:: GetString'
title: Метод IMetaDataTables::GetString
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetString
helpviewer_keywords:
- IMetaDataTables::GetString method [.NET Framework metadata]
- GetString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 895c35cf-b95d-4e3b-93b5-cfc1cf9044fc
topic_type:
- apiref
ms.openlocfilehash: 2104e30657a152d1b9a2ace743da9b126fb15d60
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687796"
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="4fc26-103">Метод IMetaDataTables::GetString</span><span class="sxs-lookup"><span data-stu-id="4fc26-103">IMetaDataTables::GetString Method</span></span>

<span data-ttu-id="4fc26-104">Возвращает строку по указанному индексу из столбца таблицы в области текущей ссылки.</span><span class="sxs-lookup"><span data-stu-id="4fc26-104">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fc26-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4fc26-105">Syntax</span></span>  
  
```cpp  
HRESULT GetString (
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4fc26-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="4fc26-106">Parameters</span></span>  

 `ixString`  
 <span data-ttu-id="4fc26-107">окне Индекс, с которого начинается поиск следующего значения.</span><span class="sxs-lookup"><span data-stu-id="4fc26-107">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="4fc26-108">заполняет Указатель на указатель на возвращаемое строковое значение.</span><span class="sxs-lookup"><span data-stu-id="4fc26-108">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fc26-109">Требования</span><span class="sxs-lookup"><span data-stu-id="4fc26-109">Requirements</span></span>  

 <span data-ttu-id="4fc26-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fc26-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fc26-111">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="4fc26-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4fc26-112">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4fc26-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4fc26-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fc26-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fc26-114">См. также</span><span class="sxs-lookup"><span data-stu-id="4fc26-114">See also</span></span>

- [<span data-ttu-id="4fc26-115">Интерфейс IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="4fc26-115">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="4fc26-116">Интерфейс IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="4fc26-116">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
