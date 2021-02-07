---
description: 'Дополнительные сведения: структура COR_FIELD_OFFSET'
title: Структура COR_FIELD_OFFSET
ms.date: 03/30/2017
api_name:
- COR_FIELD_OFFSET
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_FIELD_OFFSET
helpviewer_keywords:
- COR_FIELD_OFFSET structure [.NET Framework metadata]
ms.assetid: cced5298-277f-4a5a-8ecf-a0050c1096ea
topic_type:
- apiref
ms.openlocfilehash: 7976e79a5484fa467d7ac887a4e1a7fa324abf69
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678637"
---
# <a name="cor_field_offset-structure"></a><span data-ttu-id="3788a-103">Структура COR_FIELD_OFFSET</span><span class="sxs-lookup"><span data-stu-id="3788a-103">COR_FIELD_OFFSET Structure</span></span>

<span data-ttu-id="3788a-104">Хранит смещение указанного поля в пределах класса.</span><span class="sxs-lookup"><span data-stu-id="3788a-104">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3788a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3788a-105">Syntax</span></span>  
  
```cpp  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="3788a-106">Члены</span><span class="sxs-lookup"><span data-stu-id="3788a-106">Members</span></span>  
  
|<span data-ttu-id="3788a-107">Член</span><span class="sxs-lookup"><span data-stu-id="3788a-107">Member</span></span>|<span data-ttu-id="3788a-108">Описание</span><span class="sxs-lookup"><span data-stu-id="3788a-108">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="3788a-109">`mdFieldDef`Токен метаданных, представляющий поле.</span><span class="sxs-lookup"><span data-stu-id="3788a-109">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="3788a-110">Смещение поля в его классе.</span><span class="sxs-lookup"><span data-stu-id="3788a-110">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3788a-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="3788a-111">Remarks</span></span>  

 <span data-ttu-id="3788a-112">Методы [IMetaDataImport:: GetClassLayout](imetadataimport-getclasslayout-method.md) и [IMetaDataEmit:: сеткласслайаут](imetadataemit-setclasslayout-method.md) принимают параметр типа `COR_FIELD_OFFSET` .</span><span class="sxs-lookup"><span data-stu-id="3788a-112">[IMetaDataImport::GetClassLayout](imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3788a-113">Требования</span><span class="sxs-lookup"><span data-stu-id="3788a-113">Requirements</span></span>  

 <span data-ttu-id="3788a-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3788a-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3788a-115">**Заголовок:** Корхдр. h, CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="3788a-115">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 <span data-ttu-id="3788a-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3788a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3788a-117">См. также</span><span class="sxs-lookup"><span data-stu-id="3788a-117">See also</span></span>

- [<span data-ttu-id="3788a-118">Структуры метаданных</span><span class="sxs-lookup"><span data-stu-id="3788a-118">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="3788a-119">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="3788a-119">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="3788a-120">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="3788a-120">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
