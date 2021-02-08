---
description: 'Дополнительные сведения о: интерфейс IMetaDataTables'
title: Интерфейс IMetaDataTables
ms.date: 03/30/2017
api_name:
- IMetaDataTables
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables
helpviewer_keywords:
- IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 31272cce-506a-4f18-bcbf-01ee45e36356
topic_type:
- apiref
ms.openlocfilehash: c3edf504586bad1252c36d6e8254193eaf9cc26d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799276"
---
# <a name="imetadatatables-interface"></a><span data-ttu-id="08a05-103">Интерфейс IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="08a05-103">IMetaDataTables Interface</span></span>

<span data-ttu-id="08a05-104">Предоставляет методы для хранения и извлечения сведений о метаданных в таблицах.</span><span class="sxs-lookup"><span data-stu-id="08a05-104">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="08a05-105">Методы</span><span class="sxs-lookup"><span data-stu-id="08a05-105">Methods</span></span>  
  
|<span data-ttu-id="08a05-106">Метод</span><span class="sxs-lookup"><span data-stu-id="08a05-106">Method</span></span>|<span data-ttu-id="08a05-107">Описание</span><span class="sxs-lookup"><span data-stu-id="08a05-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="08a05-108">Метод GetBlob</span><span class="sxs-lookup"><span data-stu-id="08a05-108">GetBlob Method</span></span>](imetadatatables-getblob-method.md)|<span data-ttu-id="08a05-109">Возвращает указатель на большой двоичный объект (BLOB) по указанному индексу столбца.</span><span class="sxs-lookup"><span data-stu-id="08a05-109">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>|  
|[<span data-ttu-id="08a05-110">Метод GetBlobHeapSize</span><span class="sxs-lookup"><span data-stu-id="08a05-110">GetBlobHeapSize Method</span></span>](imetadatatables-getblobheapsize-method.md)|<span data-ttu-id="08a05-111">Возвращает размер кучи больших двоичных объектов в байтах.</span><span class="sxs-lookup"><span data-stu-id="08a05-111">Gets the size, in bytes, of the BLOB heap.</span></span>|  
|[<span data-ttu-id="08a05-112">Метод GetCodedTokenInfo</span><span class="sxs-lookup"><span data-stu-id="08a05-112">GetCodedTokenInfo Method</span></span>](imetadatatables-getcodedtokeninfo-method.md)|<span data-ttu-id="08a05-113">Возвращает указатель на массив токенов, связанных с указанным индексом строки.</span><span class="sxs-lookup"><span data-stu-id="08a05-113">Gets a pointer to an array of tokens associated with the specified row index.</span></span>|  
|[<span data-ttu-id="08a05-114">Метод GetColumn</span><span class="sxs-lookup"><span data-stu-id="08a05-114">GetColumn Method</span></span>](imetadatatables-getcolumn-method.md)|<span data-ttu-id="08a05-115">Возвращает указатель на значения, содержащиеся в столбце по указанному индексу столбца в таблице по указанному индексу таблицы.</span><span class="sxs-lookup"><span data-stu-id="08a05-115">Gets a pointer to the values contained in the column at the specified column index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="08a05-116">Метод GetColumnInfo</span><span class="sxs-lookup"><span data-stu-id="08a05-116">GetColumnInfo Method</span></span>](imetadatatables-getcolumninfo-method.md)|<span data-ttu-id="08a05-117">Получает данные о указанном столбце в указанной таблице.</span><span class="sxs-lookup"><span data-stu-id="08a05-117">Gets data about the specified column in the specified table.</span></span>|  
|[<span data-ttu-id="08a05-118">Метод GetGuid</span><span class="sxs-lookup"><span data-stu-id="08a05-118">GetGuid Method</span></span>](imetadatatables-getguid-method.md)|<span data-ttu-id="08a05-119">Возвращает идентификатор GUID из строки по указанному индексу.</span><span class="sxs-lookup"><span data-stu-id="08a05-119">Gets a GUID from the row at the specified index.</span></span>|  
|[<span data-ttu-id="08a05-120">Метод GetGuidHeapSize</span><span class="sxs-lookup"><span data-stu-id="08a05-120">GetGuidHeapSize Method</span></span>](imetadatatables-getguidheapsize-method.md)|<span data-ttu-id="08a05-121">Возвращает размер кучи GUID в байтах.</span><span class="sxs-lookup"><span data-stu-id="08a05-121">Gets the size, in bytes, of the GUID heap.</span></span>|  
|[<span data-ttu-id="08a05-122">Метод GetNextBlob</span><span class="sxs-lookup"><span data-stu-id="08a05-122">GetNextBlob Method</span></span>](imetadatatables-getnextblob-method.md)|<span data-ttu-id="08a05-123">Возвращает индекс следующего большого двоичного объекта в таблице.</span><span class="sxs-lookup"><span data-stu-id="08a05-123">Gets the index of the next BLOB in the table.</span></span>|  
|[<span data-ttu-id="08a05-124">Метод GetNextGuid</span><span class="sxs-lookup"><span data-stu-id="08a05-124">GetNextGuid Method</span></span>](imetadatatables-getnextguid-method.md)|<span data-ttu-id="08a05-125">Возвращает индекс следующего значения GUID в текущем столбце таблицы.</span><span class="sxs-lookup"><span data-stu-id="08a05-125">Gets the index of the next GUID value in the current table column.</span></span>|  
|[<span data-ttu-id="08a05-126">Метод GetNextString</span><span class="sxs-lookup"><span data-stu-id="08a05-126">GetNextString Method</span></span>](imetadatatables-getnextstring-method.md)|<span data-ttu-id="08a05-127">Возвращает индекс следующей строки в текущем столбце таблицы.</span><span class="sxs-lookup"><span data-stu-id="08a05-127">Gets the index of the next string in the current table column.</span></span>|  
|[<span data-ttu-id="08a05-128">Метод GetNextUserString</span><span class="sxs-lookup"><span data-stu-id="08a05-128">GetNextUserString Method</span></span>](imetadatatables-getnextuserstring-method.md)|<span data-ttu-id="08a05-129">Возвращает индекс строки, содержащей следующую жестко заданную строку в текущем столбце таблицы.</span><span class="sxs-lookup"><span data-stu-id="08a05-129">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>|  
|[<span data-ttu-id="08a05-130">Метод GetNumTables</span><span class="sxs-lookup"><span data-stu-id="08a05-130">GetNumTables Method</span></span>](imetadatatables-getnumtables-method.md)|<span data-ttu-id="08a05-131">Возвращает количество таблиц в области текущего `IMetaDataTables` экземпляра.</span><span class="sxs-lookup"><span data-stu-id="08a05-131">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>|  
|[<span data-ttu-id="08a05-132">Метод GetRow</span><span class="sxs-lookup"><span data-stu-id="08a05-132">GetRow Method</span></span>](imetadatatables-getrow-method.md)|<span data-ttu-id="08a05-133">Возвращает строку по указанному индексу строки в таблице по указанному индексу таблицы.</span><span class="sxs-lookup"><span data-stu-id="08a05-133">Gets the row at the specified row index, in the table at the specified table index.</span></span>|  
|[<span data-ttu-id="08a05-134">Метод GetString</span><span class="sxs-lookup"><span data-stu-id="08a05-134">GetString Method</span></span>](imetadatatables-getstring-method.md)|<span data-ttu-id="08a05-135">Возвращает строку по указанному индексу из столбца таблицы в области текущей ссылки.</span><span class="sxs-lookup"><span data-stu-id="08a05-135">Gets the string at the specified index from the table column in the current reference scope.</span></span>|  
|[<span data-ttu-id="08a05-136">Метод GetStringHeapSize</span><span class="sxs-lookup"><span data-stu-id="08a05-136">GetStringHeapSize Method</span></span>](imetadatatables-getstringheapsize-method.md)|<span data-ttu-id="08a05-137">Возвращает размер кучи строк (в байтах).</span><span class="sxs-lookup"><span data-stu-id="08a05-137">Gets the size, in bytes, of the string heap.</span></span>|  
|[<span data-ttu-id="08a05-138">Метод GetTableIndex</span><span class="sxs-lookup"><span data-stu-id="08a05-138">GetTableIndex Method</span></span>](imetadatatables-gettableindex-method.md)|<span data-ttu-id="08a05-139">Возвращает индекс для таблицы, на которую ссылается указанный токен.</span><span class="sxs-lookup"><span data-stu-id="08a05-139">Gets the index for the table referenced by the specified token.</span></span>|  
|[<span data-ttu-id="08a05-140">Метод GetTableInfo</span><span class="sxs-lookup"><span data-stu-id="08a05-140">GetTableInfo Method</span></span>](imetadatatables-gettableinfo-method.md)|<span data-ttu-id="08a05-141">Возвращает имя, размер строки, число строк, число столбцов и индекс ключевого столбца таблицы по указанному индексу таблицы.</span><span class="sxs-lookup"><span data-stu-id="08a05-141">Gets the name, row size, number of rows, number of columns, and key column index of the table at the specified table index.</span></span>|  
|[<span data-ttu-id="08a05-142">Метод GetUserString</span><span class="sxs-lookup"><span data-stu-id="08a05-142">GetUserString Method</span></span>](imetadatatables-getuserstring-method.md)|<span data-ttu-id="08a05-143">Получает жестко заданную строку по указанному индексу в строковом столбце текущей области.</span><span class="sxs-lookup"><span data-stu-id="08a05-143">Gets the hard-coded string at the specified index in the string column in the current scope.</span></span>|  
|[<span data-ttu-id="08a05-144">Метод GetUserStringHeapSize</span><span class="sxs-lookup"><span data-stu-id="08a05-144">GetUserStringHeapSize Method</span></span>](imetadatatables-getuserstringheapsize-method.md)|<span data-ttu-id="08a05-145">Возвращает размер (в байтах) кучи пользовательской строки.</span><span class="sxs-lookup"><span data-stu-id="08a05-145">Gets the size, in bytes, of the user string heap.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="08a05-146">Требования</span><span class="sxs-lookup"><span data-stu-id="08a05-146">Requirements</span></span>  

 <span data-ttu-id="08a05-147">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08a05-147">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08a05-148">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="08a05-148">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="08a05-149">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="08a05-149">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="08a05-150">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08a05-150">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08a05-151">См. также</span><span class="sxs-lookup"><span data-stu-id="08a05-151">See also</span></span>

- [<span data-ttu-id="08a05-152">Интерфейсы метаданных</span><span class="sxs-lookup"><span data-stu-id="08a05-152">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="08a05-153">Интерфейс IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="08a05-153">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
