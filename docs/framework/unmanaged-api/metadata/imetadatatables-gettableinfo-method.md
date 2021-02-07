---
description: 'Дополнительные сведения о методе: IMetaDataTables:: GetTableInfo'
title: Метод IMetaDataTables::GetTableInfo
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetTableInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetTableInfo
helpviewer_keywords:
- IMetaDataTables::GetTableInfo method [.NET Framework metadata]
- GetTableInfo method [.NET Framework metadata]
ms.assetid: 50cbe557-2322-41aa-8e0d-f967602eaa0f
topic_type:
- apiref
ms.openlocfilehash: 3929f91c15b5c1fc22ac3ad4b17cbaa38a08533a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687653"
---
# <a name="imetadatatablesgettableinfo-method"></a><span data-ttu-id="c76ea-103">Метод IMetaDataTables::GetTableInfo</span><span class="sxs-lookup"><span data-stu-id="c76ea-103">IMetaDataTables::GetTableInfo Method</span></span>

<span data-ttu-id="c76ea-104">Возвращает имя, размер строки, число строк, число столбцов и индекс ключевого столбца указанной таблицы.</span><span class="sxs-lookup"><span data-stu-id="c76ea-104">Gets the name, row size, number of rows, number of columns, and key column index of the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c76ea-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c76ea-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTableInfo (  
    [in]  ULONG       ixTbl,  
    [out] ULONG       *pcbRow,  
    [out] ULONG       *pcRows,  
    [out] ULONG       *pcCols,  
    [out] ULONG       *piKey,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c76ea-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c76ea-106">Parameters</span></span>  

 `ixTbl`  
 <span data-ttu-id="c76ea-107">окне Идентификатор таблицы, свойства которой должны быть возвращены.</span><span class="sxs-lookup"><span data-stu-id="c76ea-107">[in] The identifier of the table whose properties to return.</span></span>  
  
 `pcbRow`  
 <span data-ttu-id="c76ea-108">заполняет Указатель на размер строки таблицы в байтах.</span><span class="sxs-lookup"><span data-stu-id="c76ea-108">[out] A pointer to the size, in bytes, of a table row.</span></span>  
  
 `pcRows`  
 <span data-ttu-id="c76ea-109">заполняет Указатель на число строк в таблице.</span><span class="sxs-lookup"><span data-stu-id="c76ea-109">[out] A pointer to the number of rows in the table.</span></span>  
  
 `pcCols`  
 <span data-ttu-id="c76ea-110">заполняет Указатель на число столбцов в таблице.</span><span class="sxs-lookup"><span data-stu-id="c76ea-110">[out] A pointer to the number of columns in the table.</span></span>  
  
 `piKey`  
 <span data-ttu-id="c76ea-111">заполняет Указатель на индекс ключевого столбца или значение-1, если у таблицы нет ключевого столбца.</span><span class="sxs-lookup"><span data-stu-id="c76ea-111">[out] A pointer to the index of the key column, or -1 if the table has no key column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="c76ea-112">заполняет Указатель на указатель на имя таблицы.</span><span class="sxs-lookup"><span data-stu-id="c76ea-112">[out] A pointer to a pointer to the table name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c76ea-113">Требования</span><span class="sxs-lookup"><span data-stu-id="c76ea-113">Requirements</span></span>  

 <span data-ttu-id="c76ea-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c76ea-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c76ea-115">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="c76ea-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c76ea-116">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c76ea-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c76ea-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c76ea-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c76ea-118">См. также</span><span class="sxs-lookup"><span data-stu-id="c76ea-118">See also</span></span>

- [<span data-ttu-id="c76ea-119">Интерфейс IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="c76ea-119">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="c76ea-120">Интерфейс IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="c76ea-120">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
