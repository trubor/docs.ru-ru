---
description: 'Дополнительные сведения: структура IDENTITY_ATTRIBUTE'
title: Структура IDENTITY_ATTRIBUTE
ms.date: 03/30/2017
api_name:
- IDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDENTITY_ATTRIBUTE
helpviewer_keywords:
- IDENTITY_ATTRIBUTE structure [.NET Framework fusion]
ms.assetid: 1ee7c434-9681-4fa8-badd-652cb1a9742b
topic_type:
- apiref
ms.openlocfilehash: 52610961ab202fc79351073eac1846a1a63889e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800179"
---
# <a name="identity_attribute-structure"></a><span data-ttu-id="bac30-103">Структура IDENTITY_ATTRIBUTE</span><span class="sxs-lookup"><span data-stu-id="bac30-103">IDENTITY_ATTRIBUTE Structure</span></span>

<span data-ttu-id="bac30-104">Содержит сведения об атрибутах метаданных для экземпляра [идефинитионидентити](idefinitionidentity-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="bac30-104">Contains metadata attribute information about an [IDefinitionIdentity](idefinitionidentity-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bac30-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bac30-105">Syntax</span></span>  
  
```cpp  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a><span data-ttu-id="bac30-106">Члены</span><span class="sxs-lookup"><span data-stu-id="bac30-106">Members</span></span>  
  
|<span data-ttu-id="bac30-107">Член</span><span class="sxs-lookup"><span data-stu-id="bac30-107">Member</span></span>|<span data-ttu-id="bac30-108">Описание</span><span class="sxs-lookup"><span data-stu-id="bac30-108">Description</span></span>|  
|------------|-----------------|  
|`pszNamespace`|<span data-ttu-id="bac30-109">Указатель на строку символов, завершающуюся нулем, которая содержит пространство имен, в котором находится атрибут.</span><span class="sxs-lookup"><span data-stu-id="bac30-109">A pointer to a null-terminated character string that contains the namespace the attribute is in.</span></span>|  
|`pszName`|<span data-ttu-id="bac30-110">Указатель на строку символов, завершающуюся нулем, которая содержит имя атрибута.</span><span class="sxs-lookup"><span data-stu-id="bac30-110">A pointer to a null-terminated character string that contains the name of the attribute.</span></span>|  
|`pszValue`|<span data-ttu-id="bac30-111">Указатель на строку символов, завершающуюся нулем, которая содержит значение атрибута.</span><span class="sxs-lookup"><span data-stu-id="bac30-111">A pointer to a null-terminated character string that contains the value of the attribute.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bac30-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="bac30-112">Remarks</span></span>  

 <span data-ttu-id="bac30-113">`IDENTITY_ATTRIBUTE`Структура содержит три указателя на строки символов, заканчивающиеся нулем.</span><span class="sxs-lookup"><span data-stu-id="bac30-113">The `IDENTITY_ATTRIBUTE` structure contains three pointers to null-terminated character strings.</span></span> <span data-ttu-id="bac30-114">Эти три строки описывают один атрибут.</span><span class="sxs-lookup"><span data-stu-id="bac30-114">These three strings describe one attribute.</span></span>  
  
 <span data-ttu-id="bac30-115">Экземпляр `IDENTITY_ATTRIBUTE` структуры связан с экземпляром структуры [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="bac30-115">An instance of an `IDENTITY_ATTRIBUTE` structure is associated with an instance of an [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) structure.</span></span> <span data-ttu-id="bac30-116">`IDENTITY_ATTRIBUTE`Структура содержит фактические строки, а соответствующая `IDENTITY_ATTRIBUTE_BLOB` Структура перечисляет смещения для трех строк, перечисленных в `IDENTITY_ATTRIBUTE` структуре.</span><span class="sxs-lookup"><span data-stu-id="bac30-116">The `IDENTITY_ATTRIBUTE` structure contains the actual strings, and the corresponding `IDENTITY_ATTRIBUTE_BLOB` structure lists the offsets to the three strings listed in the `IDENTITY_ATTRIBUTE` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bac30-117">Требования</span><span class="sxs-lookup"><span data-stu-id="bac30-117">Requirements</span></span>  

 <span data-ttu-id="bac30-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bac30-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bac30-119">**Заголовок:** Изоляция. h</span><span class="sxs-lookup"><span data-stu-id="bac30-119">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="bac30-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bac30-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bac30-121">См. также</span><span class="sxs-lookup"><span data-stu-id="bac30-121">See also</span></span>

- [<span data-ttu-id="bac30-122">Интерфейс IDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="bac30-122">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)
- [<span data-ttu-id="bac30-123">Структура IDENTITY_ATTRIBUTE_BLOB</span><span class="sxs-lookup"><span data-stu-id="bac30-123">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>](identity-attribute-blob-structure.md)
- [<span data-ttu-id="bac30-124">Структуры Fusion</span><span class="sxs-lookup"><span data-stu-id="bac30-124">Fusion Structures</span></span>](fusion-structures.md)
