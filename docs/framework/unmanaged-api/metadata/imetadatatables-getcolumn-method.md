---
description: 'Дополнительные сведения о методе: IMetaDataTables:: DataColumn'
title: Метод IMetaDataTables::GetColumn
ms.date: 02/25/2019
api_name:
- IMetaDataTables.GetColumn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumn
helpviewer_keywords:
- IMetaDataTables::GetColumn method [.NET Framework metadata]
- GetColumn method [.NET Framework metadata]
ms.assetid: 1032055b-cabb-45c5-a50e-7e853201b175
topic_type:
- apiref
ms.openlocfilehash: 4c4cec7216f93783b34b594330358d1e6036ed40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688277"
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="8f5a4-103">Метод IMetaDataTables::GetColumn</span><span class="sxs-lookup"><span data-stu-id="8f5a4-103">IMetaDataTables::GetColumn Method</span></span>

<span data-ttu-id="8f5a4-104">Возвращает указатель на значение, содержащееся в ячейке указанного столбца и строки в заданной таблице.</span><span class="sxs-lookup"><span data-stu-id="8f5a4-104">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f5a4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8f5a4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetColumn (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f5a4-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8f5a4-106">Parameters</span></span>

 `ixTbl`  
 <span data-ttu-id="8f5a4-107">окне Индекс таблицы.</span><span class="sxs-lookup"><span data-stu-id="8f5a4-107">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="8f5a4-108">окне Индекс столбца в таблице.</span><span class="sxs-lookup"><span data-stu-id="8f5a4-108">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="8f5a4-109">окне Индекс строки в таблице.</span><span class="sxs-lookup"><span data-stu-id="8f5a4-109">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="8f5a4-110">заполняет Указатель на значение в ячейке.</span><span class="sxs-lookup"><span data-stu-id="8f5a4-110">[out] A pointer to the value in the cell.</span></span>  

## <a name="remarks"></a><span data-ttu-id="8f5a4-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="8f5a4-111">Remarks</span></span>

<span data-ttu-id="8f5a4-112">Интерпретация значения, возвращаемого с помощью, `pVal` зависит от типа столбца.</span><span class="sxs-lookup"><span data-stu-id="8f5a4-112">The interpretion of the value returned through `pVal` depends on the column's type.</span></span> <span data-ttu-id="8f5a4-113">Тип столбца можно определить с помощью метода [IMetaDataTables. GetColumnInfo](imetadatatables-getcolumninfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="8f5a4-113">The column type can be determined by calling [IMetaDataTables.GetColumnInfo](imetadatatables-getcolumninfo-method.md).</span></span>

- <span data-ttu-id="8f5a4-114">Метод **DataColumn** автоматически преобразует столбцы типа **RID** или **кодедтокен** в полные 32-разрядные `mdToken` значения.</span><span class="sxs-lookup"><span data-stu-id="8f5a4-114">The **GetColumn** method automatically converts columns of type **Rid** or **CodedToken** to full 32-bit `mdToken` values.</span></span>
- <span data-ttu-id="8f5a4-115">Он также автоматически преобразует 8-битные или 16-битные значения в полные 32-разрядные значения.</span><span class="sxs-lookup"><span data-stu-id="8f5a4-115">It also automatically converts 8-bit or 16-bit values to full 32-bit values.</span></span>
- <span data-ttu-id="8f5a4-116">Для столбцов типа *кучи* возвращенный *Pval* будет индексом в соответствующей куче.</span><span class="sxs-lookup"><span data-stu-id="8f5a4-116">For *heap* type columns, the returned *pVal* will be an index into the corresponding heap.</span></span>

| <span data-ttu-id="8f5a4-117">Тип столбца</span><span class="sxs-lookup"><span data-stu-id="8f5a4-117">Column type</span></span>              | <span data-ttu-id="8f5a4-118">pVal содержит</span><span class="sxs-lookup"><span data-stu-id="8f5a4-118">pVal contains</span></span> | <span data-ttu-id="8f5a4-119">Комментировать</span><span class="sxs-lookup"><span data-stu-id="8f5a4-119">Comment</span></span>                          |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="8f5a4-120">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="8f5a4-120">`0`..`iRidMax`</span></span><br><span data-ttu-id="8f5a4-121">(0.. 63)</span><span class="sxs-lookup"><span data-stu-id="8f5a4-121">(0..63)</span></span>  | <span data-ttu-id="8f5a4-122">mdToken</span><span class="sxs-lookup"><span data-stu-id="8f5a4-122">mdToken</span></span>     | <span data-ttu-id="8f5a4-123">*Pval* будет содержать полный маркер.</span><span class="sxs-lookup"><span data-stu-id="8f5a4-123">*pVal* will contain a full Token.</span></span> <span data-ttu-id="8f5a4-124">Функция автоматически преобразует RID в полный маркер.</span><span class="sxs-lookup"><span data-stu-id="8f5a4-124">The function automatically converts the Rid into a full token.</span></span> |
| <span data-ttu-id="8f5a4-125">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="8f5a4-125">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="8f5a4-126">(64.. 95)</span><span class="sxs-lookup"><span data-stu-id="8f5a4-126">(64..95)</span></span> | <span data-ttu-id="8f5a4-127">mdToken</span><span class="sxs-lookup"><span data-stu-id="8f5a4-127">mdToken</span></span> | <span data-ttu-id="8f5a4-128">После возврата *Pval* будет содержать полный маркер.</span><span class="sxs-lookup"><span data-stu-id="8f5a4-128">Upon return, *pVal* will contain a full Token.</span></span> <span data-ttu-id="8f5a4-129">Функция автоматически распаковывает Кодедтокен в полную лексему.</span><span class="sxs-lookup"><span data-stu-id="8f5a4-129">The function automatically decompresses the CodedToken into a full token.</span></span> |
| <span data-ttu-id="8f5a4-130">`iSHORT` (96)</span><span class="sxs-lookup"><span data-stu-id="8f5a4-130">`iSHORT` (96)</span></span>            | <span data-ttu-id="8f5a4-131">Int16</span><span class="sxs-lookup"><span data-stu-id="8f5a4-131">Int16</span></span>         | <span data-ttu-id="8f5a4-132">Автоматический вход в 32-разрядный.</span><span class="sxs-lookup"><span data-stu-id="8f5a4-132">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="8f5a4-133">`iUSHORT` (97)</span><span class="sxs-lookup"><span data-stu-id="8f5a4-133">`iUSHORT` (97)</span></span>           | <span data-ttu-id="8f5a4-134">UInt16</span><span class="sxs-lookup"><span data-stu-id="8f5a4-134">UInt16</span></span>        | <span data-ttu-id="8f5a4-135">Автоматический вход в 32-разрядный.</span><span class="sxs-lookup"><span data-stu-id="8f5a4-135">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="8f5a4-136">`iLONG` (98)</span><span class="sxs-lookup"><span data-stu-id="8f5a4-136">`iLONG` (98)</span></span>             | <span data-ttu-id="8f5a4-137">Int32</span><span class="sxs-lookup"><span data-stu-id="8f5a4-137">Int32</span></span>         |                                        |
| <span data-ttu-id="8f5a4-138">`iULONG` (99)</span><span class="sxs-lookup"><span data-stu-id="8f5a4-138">`iULONG` (99)</span></span>            | <span data-ttu-id="8f5a4-139">UInt32</span><span class="sxs-lookup"><span data-stu-id="8f5a4-139">UInt32</span></span>        |                                        |
| <span data-ttu-id="8f5a4-140">`iBYTE` (100)</span><span class="sxs-lookup"><span data-stu-id="8f5a4-140">`iBYTE` (100)</span></span>            | <span data-ttu-id="8f5a4-141">Byte</span><span class="sxs-lookup"><span data-stu-id="8f5a4-141">Byte</span></span>          | <span data-ttu-id="8f5a4-142">Автоматический вход в 32-разрядный.</span><span class="sxs-lookup"><span data-stu-id="8f5a4-142">Automatically sign-extended to 32-bit.</span></span>  |
| <span data-ttu-id="8f5a4-143">`iSTRING` (101)</span><span class="sxs-lookup"><span data-stu-id="8f5a4-143">`iSTRING` (101)</span></span>          | <span data-ttu-id="8f5a4-144">Индекс строковой кучи</span><span class="sxs-lookup"><span data-stu-id="8f5a4-144">String heap index</span></span> | <span data-ttu-id="8f5a4-145">*Pval* — это индекс в куче строк.</span><span class="sxs-lookup"><span data-stu-id="8f5a4-145">*pVal* is an index into the String heap.</span></span> <span data-ttu-id="8f5a4-146">Используйте [IMetadataTables:: GetString](imetadatatables-getstring-method.md) , чтобы получить фактическое строковое значение столбца.</span><span class="sxs-lookup"><span data-stu-id="8f5a4-146">Use [IMetadataTables::GetString](imetadatatables-getstring-method.md) to get the actual column String value.</span></span> |
| <span data-ttu-id="8f5a4-147">`iGUID` (102)</span><span class="sxs-lookup"><span data-stu-id="8f5a4-147">`iGUID` (102)</span></span>            | <span data-ttu-id="8f5a4-148">Индекс кучи GUID</span><span class="sxs-lookup"><span data-stu-id="8f5a4-148">Guid heap index</span></span> | <span data-ttu-id="8f5a4-149">*Pval* — это индекс в куче GUID.</span><span class="sxs-lookup"><span data-stu-id="8f5a4-149">*pVal* is an index into the Guid heap.</span></span> <span data-ttu-id="8f5a4-150">Чтобы получить действительное значение GUID столбца, используйте [IMetadataTables::](imetadatatables-getguid-method.md) DataColumn.</span><span class="sxs-lookup"><span data-stu-id="8f5a4-150">Use [IMetadataTables::GetGuid](imetadatatables-getguid-method.md) to get the actual column Guid value.</span></span> |
| <span data-ttu-id="8f5a4-151">`iBLOB` (103)</span><span class="sxs-lookup"><span data-stu-id="8f5a4-151">`iBLOB` (103)</span></span>            | <span data-ttu-id="8f5a4-152">Индекс кучи больших двоичных объектов</span><span class="sxs-lookup"><span data-stu-id="8f5a4-152">Blob heap index</span></span> | <span data-ttu-id="8f5a4-153">*Pval* — это индекс в куче больших двоичных объектов.</span><span class="sxs-lookup"><span data-stu-id="8f5a4-153">*pVal* is an index into the Blob heap.</span></span> <span data-ttu-id="8f5a4-154">Для получения действительного значения большого двоичного объекта столбца используйте [IMetadataTables::-BLOB](imetadatatables-getblob-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8f5a4-154">Use [IMetadataTables::GetBlob](imetadatatables-getblob-method.md) to get the actual column Blob value.</span></span> |
  
## <a name="requirements"></a><span data-ttu-id="8f5a4-155">Требования</span><span class="sxs-lookup"><span data-stu-id="8f5a4-155">Requirements</span></span>  

 <span data-ttu-id="8f5a4-156">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f5a4-156">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f5a4-157">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="8f5a4-157">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8f5a4-158">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8f5a4-158">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8f5a4-159">**Версии платформа .NET Framework**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f5a4-159">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f5a4-160">См. также</span><span class="sxs-lookup"><span data-stu-id="8f5a4-160">See also</span></span>

- [<span data-ttu-id="8f5a4-161">Интерфейс IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="8f5a4-161">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="8f5a4-162">Интерфейс IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="8f5a4-162">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
