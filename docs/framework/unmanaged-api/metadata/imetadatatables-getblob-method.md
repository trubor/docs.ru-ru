---
description: 'Дополнительные сведения о методе: IMetaDataTables:: BLOB'
title: Метод IMetaDataTables::GetBlob
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetBlob
helpviewer_keywords:
- GetBlob method [.NET Framework metadata]
- IMetaDataTables::GetBlob method [.NET Framework metadata]
ms.assetid: 94667c1c-6d58-4aa7-b74e-530b11e2a276
topic_type:
- apiref
ms.openlocfilehash: 733f94c280283e00b644fe7811d450efbc7e1e7c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688394"
---
# <a name="imetadatatablesgetblob-method"></a><span data-ttu-id="7308c-103">Метод IMetaDataTables::GetBlob</span><span class="sxs-lookup"><span data-stu-id="7308c-103">IMetaDataTables::GetBlob Method</span></span>

<span data-ttu-id="7308c-104">Возвращает указатель на большой двоичный объект (BLOB) по указанному индексу столбца.</span><span class="sxs-lookup"><span data-stu-id="7308c-104">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7308c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7308c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetBlob (  
    [in]  ULONG          ixBlob,  
    [out] ULONG          *pcbData,  
    [out] const void     **ppData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7308c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7308c-106">Parameters</span></span>  

 `ixBlob`  
 <span data-ttu-id="7308c-107">окне Адрес памяти, из которого будет получено значение `ppData` .</span><span class="sxs-lookup"><span data-stu-id="7308c-107">[in] The memory address from which to get `ppData`.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="7308c-108">заполняет Указатель на размер в байтах `ppData` .</span><span class="sxs-lookup"><span data-stu-id="7308c-108">[out] A pointer to the size, in bytes, of `ppData`.</span></span>  
  
 `ppData`  
 <span data-ttu-id="7308c-109">заполняет Указатель на указатель на извлекаемые двоичные данные.</span><span class="sxs-lookup"><span data-stu-id="7308c-109">[out] A pointer to a pointer to the binary data retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7308c-110">Требования</span><span class="sxs-lookup"><span data-stu-id="7308c-110">Requirements</span></span>  

 <span data-ttu-id="7308c-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7308c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7308c-112">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="7308c-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7308c-113">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7308c-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7308c-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7308c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7308c-115">См. также</span><span class="sxs-lookup"><span data-stu-id="7308c-115">See also</span></span>

- [<span data-ttu-id="7308c-116">Интерфейс IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="7308c-116">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="7308c-117">Интерфейс IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="7308c-117">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
