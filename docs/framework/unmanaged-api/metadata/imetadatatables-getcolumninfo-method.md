---
description: 'Дополнительные сведения о методе: IMetaDataTables:: GetColumnInfo'
title: Метод IMetaDataTables::GetColumnInfo
ms.date: 10/10/2019
api_name:
- IMetaDataTables.GetColumnInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumnInfo
helpviewer_keywords:
- IMetaDataTables::GetColumnInfo method [.NET Framework metadata]
- GetColumnInfo method [.NET Framework metadata]
ms.assetid: 68c160ea-ae7d-4750-985d-a038b2c8e7d9
topic_type:
- apiref
ms.openlocfilehash: 21980567c5f9b364362f7e3ff02ee3a5e60b01ee
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688238"
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="98d86-103">Метод IMetaDataTables::GetColumnInfo</span><span class="sxs-lookup"><span data-stu-id="98d86-103">IMetaDataTables::GetColumnInfo Method</span></span>

<span data-ttu-id="98d86-104">Получает данные о указанном столбце в указанной таблице.</span><span class="sxs-lookup"><span data-stu-id="98d86-104">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98d86-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="98d86-105">Syntax</span></span>  
  
```cpp  
HRESULT GetColumnInfo (
    [in]  ULONG        ixTbl,  
    [in]  ULONG        ixCol,  
    [out] ULONG        *poCol,  
    [out] ULONG        *pcbCol,  
    [out] ULONG        *pType,  
    [out] const char   **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98d86-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="98d86-106">Parameters</span></span>

=======

 `ixTbl`  
 <span data-ttu-id="98d86-107">окне Индекс требуемой таблицы.</span><span class="sxs-lookup"><span data-stu-id="98d86-107">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="98d86-108">окне Индекс нужного столбца.</span><span class="sxs-lookup"><span data-stu-id="98d86-108">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="98d86-109">заполняет Указатель на смещение столбца в строке.</span><span class="sxs-lookup"><span data-stu-id="98d86-109">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="98d86-110">заполняет Указатель на размер столбца в байтах.</span><span class="sxs-lookup"><span data-stu-id="98d86-110">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="98d86-111">заполняет Указатель на тип значений в столбце.</span><span class="sxs-lookup"><span data-stu-id="98d86-111">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="98d86-112">заполняет Указатель на указатель на имя столбца.</span><span class="sxs-lookup"><span data-stu-id="98d86-112">[out] A pointer to a pointer to the column name.</span></span>  

## <a name="remarks"></a><span data-ttu-id="98d86-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="98d86-113">Remarks</span></span>

<span data-ttu-id="98d86-114">Возвращаемый тип столбца попадает в диапазон значений:</span><span class="sxs-lookup"><span data-stu-id="98d86-114">The returned column type falls within a range of values:</span></span>

| <span data-ttu-id="98d86-115">птипе</span><span class="sxs-lookup"><span data-stu-id="98d86-115">pType</span></span>                    | <span data-ttu-id="98d86-116">Описание</span><span class="sxs-lookup"><span data-stu-id="98d86-116">Description</span></span>   | <span data-ttu-id="98d86-117">Вспомогательная функция</span><span class="sxs-lookup"><span data-stu-id="98d86-117">Helper function</span></span>                   |
|--------------------------|---------------|-----------------------------------|
| <span data-ttu-id="98d86-118">`0`..`iRidMax`</span><span class="sxs-lookup"><span data-stu-id="98d86-118">`0`..`iRidMax`</span></span><br><span data-ttu-id="98d86-119">(0.. 63)</span><span class="sxs-lookup"><span data-stu-id="98d86-119">(0..63)</span></span>   | <span data-ttu-id="98d86-120">Избежать</span><span class="sxs-lookup"><span data-stu-id="98d86-120">Rid</span></span>           | <span data-ttu-id="98d86-121">**исридтипе**</span><span class="sxs-lookup"><span data-stu-id="98d86-121">**IsRidType**</span></span><br><span data-ttu-id="98d86-122">**исридортокен**</span><span class="sxs-lookup"><span data-stu-id="98d86-122">**IsRidOrToken**</span></span> |
| <span data-ttu-id="98d86-123">`iCodedToken`..`iCodedTokenMax`</span><span class="sxs-lookup"><span data-stu-id="98d86-123">`iCodedToken`..`iCodedTokenMax`</span></span><br><span data-ttu-id="98d86-124">(64.. 95)</span><span class="sxs-lookup"><span data-stu-id="98d86-124">(64..95)</span></span> | <span data-ttu-id="98d86-125">Закодированный маркер</span><span class="sxs-lookup"><span data-stu-id="98d86-125">Coded token</span></span> | <span data-ttu-id="98d86-126">**искодедтокентипе**</span><span class="sxs-lookup"><span data-stu-id="98d86-126">**IsCodedTokenType**</span></span> <br><span data-ttu-id="98d86-127">**исридортокен**</span><span class="sxs-lookup"><span data-stu-id="98d86-127">**IsRidOrToken**</span></span> |
| <span data-ttu-id="98d86-128">`iSHORT` (96)</span><span class="sxs-lookup"><span data-stu-id="98d86-128">`iSHORT` (96)</span></span>            | <span data-ttu-id="98d86-129">Int16</span><span class="sxs-lookup"><span data-stu-id="98d86-129">Int16</span></span>         | <span data-ttu-id="98d86-130">**исфикседтипе**</span><span class="sxs-lookup"><span data-stu-id="98d86-130">**IsFixedType**</span></span>                   |
| <span data-ttu-id="98d86-131">`iUSHORT` (97)</span><span class="sxs-lookup"><span data-stu-id="98d86-131">`iUSHORT` (97)</span></span>           | <span data-ttu-id="98d86-132">UInt16</span><span class="sxs-lookup"><span data-stu-id="98d86-132">UInt16</span></span>        | <span data-ttu-id="98d86-133">**исфикседтипе**</span><span class="sxs-lookup"><span data-stu-id="98d86-133">**IsFixedType**</span></span>                   |
| <span data-ttu-id="98d86-134">`iLONG` (98)</span><span class="sxs-lookup"><span data-stu-id="98d86-134">`iLONG` (98)</span></span>             | <span data-ttu-id="98d86-135">Int32</span><span class="sxs-lookup"><span data-stu-id="98d86-135">Int32</span></span>         | <span data-ttu-id="98d86-136">**исфикседтипе**</span><span class="sxs-lookup"><span data-stu-id="98d86-136">**IsFixedType**</span></span>                   |
| <span data-ttu-id="98d86-137">`iULONG` (99)</span><span class="sxs-lookup"><span data-stu-id="98d86-137">`iULONG` (99)</span></span>            | <span data-ttu-id="98d86-138">UInt32</span><span class="sxs-lookup"><span data-stu-id="98d86-138">UInt32</span></span>        | <span data-ttu-id="98d86-139">**исфикседтипе**</span><span class="sxs-lookup"><span data-stu-id="98d86-139">**IsFixedType**</span></span>                   |
| <span data-ttu-id="98d86-140">`iBYTE` (100)</span><span class="sxs-lookup"><span data-stu-id="98d86-140">`iBYTE` (100)</span></span>            | <span data-ttu-id="98d86-141">Byte</span><span class="sxs-lookup"><span data-stu-id="98d86-141">Byte</span></span>          | <span data-ttu-id="98d86-142">**исфикседтипе**</span><span class="sxs-lookup"><span data-stu-id="98d86-142">**IsFixedType**</span></span>                   |
| <span data-ttu-id="98d86-143">`iSTRING` (101)</span><span class="sxs-lookup"><span data-stu-id="98d86-143">`iSTRING` (101)</span></span>          | <span data-ttu-id="98d86-144">Строка</span><span class="sxs-lookup"><span data-stu-id="98d86-144">String</span></span>        | <span data-ttu-id="98d86-145">**ишеаптипе**</span><span class="sxs-lookup"><span data-stu-id="98d86-145">**IsHeapType**</span></span>                    |
| <span data-ttu-id="98d86-146">`iGUID` (102)</span><span class="sxs-lookup"><span data-stu-id="98d86-146">`iGUID` (102)</span></span>            | <span data-ttu-id="98d86-147">Guid</span><span class="sxs-lookup"><span data-stu-id="98d86-147">Guid</span></span>          | <span data-ttu-id="98d86-148">**ишеаптипе**</span><span class="sxs-lookup"><span data-stu-id="98d86-148">**IsHeapType**</span></span>                    |
| <span data-ttu-id="98d86-149">`iBLOB` (103)</span><span class="sxs-lookup"><span data-stu-id="98d86-149">`iBLOB` (103)</span></span>            | <span data-ttu-id="98d86-150">BLOB-объект</span><span class="sxs-lookup"><span data-stu-id="98d86-150">Blob</span></span>          | <span data-ttu-id="98d86-151">**ишеаптипе**</span><span class="sxs-lookup"><span data-stu-id="98d86-151">**IsHeapType**</span></span>                    |

<span data-ttu-id="98d86-152">Значения, хранящиеся в *куче* (т `IsHeapType == true` . е.), можно считывать с помощью:</span><span class="sxs-lookup"><span data-stu-id="98d86-152">Values that are stored in the *heap* (that is, `IsHeapType == true`) can be read using:</span></span>

- <span data-ttu-id="98d86-153">`iSTRING`: **IMetadataTables. GetString**</span><span class="sxs-lookup"><span data-stu-id="98d86-153">`iSTRING`: **IMetadataTables.GetString**</span></span>
- <span data-ttu-id="98d86-154">`iGUID`: **IMetadataTables. с GUID**</span><span class="sxs-lookup"><span data-stu-id="98d86-154">`iGUID`: **IMetadataTables.GetGUID**</span></span>
- <span data-ttu-id="98d86-155">`iBLOB`: **IMetadataTables. BLOB**</span><span class="sxs-lookup"><span data-stu-id="98d86-155">`iBLOB`: **IMetadataTables.GetBlob**</span></span>

> [!IMPORTANT]
> <span data-ttu-id="98d86-156">Чтобы использовать константы, определенные в приведенной выше таблице, включите директиву, `#define _DEFINE_META_DATA_META_CONSTANTS` предоставленную файлом заголовка *COR. h* .</span><span class="sxs-lookup"><span data-stu-id="98d86-156">To use the constants defined in the table above, include the directive `#define _DEFINE_META_DATA_META_CONSTANTS` provided by the *cor.h* header file.</span></span>

## <a name="requirements"></a><span data-ttu-id="98d86-157">Требования</span><span class="sxs-lookup"><span data-stu-id="98d86-157">Requirements</span></span>  

 <span data-ttu-id="98d86-158">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98d86-158">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98d86-159">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="98d86-159">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="98d86-160">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="98d86-160">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="98d86-161">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98d86-161">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98d86-162">См. также</span><span class="sxs-lookup"><span data-stu-id="98d86-162">See also</span></span>

- [<span data-ttu-id="98d86-163">Интерфейс IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="98d86-163">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="98d86-164">Интерфейс IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="98d86-164">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
