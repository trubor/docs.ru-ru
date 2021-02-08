---
description: Дополнительные сведения о перечислении CorPropertyAttr
title: Перечисление CorPropertyAttr
ms.date: 03/30/2017
api_name:
- CorPropertyAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPropertyAttr
helpviewer_keywords:
- CorPropertyAttr enumeration [.NET Framework metadata]
ms.assetid: 58ac8202-854d-4efd-acfb-d2da8b446e12
topic_type:
- apiref
ms.openlocfilehash: 1f3e2fccb11a067c6c46350a2c36d47007875755
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784240"
---
# <a name="corpropertyattr-enumeration"></a><span data-ttu-id="4c57d-103">Перечисление CorPropertyAttr</span><span class="sxs-lookup"><span data-stu-id="4c57d-103">CorPropertyAttr Enumeration</span></span>

<span data-ttu-id="4c57d-104">Содержит значения, описывающие метаданные свойства.</span><span class="sxs-lookup"><span data-stu-id="4c57d-104">Contains values that describe the metadata of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c57d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4c57d-105">Syntax</span></span>  
  
```cpp  
typedef enum CorPropertyAttr {  
  
    prSpecialName           =   0x0200,
    prReservedMask          =   0xf400,  
    prRTSpecialName         =   0x0400,  
    prHasDefault            =   0x1000,  
    prUnused                =   0xe9ff  
  
} CorPropertyAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="4c57d-106">Члены</span><span class="sxs-lookup"><span data-stu-id="4c57d-106">Members</span></span>  
  
|<span data-ttu-id="4c57d-107">Член</span><span class="sxs-lookup"><span data-stu-id="4c57d-107">Member</span></span>|<span data-ttu-id="4c57d-108">Описание</span><span class="sxs-lookup"><span data-stu-id="4c57d-108">Description</span></span>|  
|------------|-----------------|  
|`prSpecialName`|<span data-ttu-id="4c57d-109">Указывает, что свойство является специальным, и что его имя описывает, как это делать.</span><span class="sxs-lookup"><span data-stu-id="4c57d-109">Specifies that the property is special, and that its name describes how.</span></span>|  
|`prReservedMask`|<span data-ttu-id="4c57d-110">Зарезервировано для внутреннего использования средой CLR.</span><span class="sxs-lookup"><span data-stu-id="4c57d-110">Reserved for internal use by the common language runtime.</span></span>|  
|`prRTSpecialName`|<span data-ttu-id="4c57d-111">Указывает, что внутренние API метаданных среды CLR должны проверять кодировку имени свойства.</span><span class="sxs-lookup"><span data-stu-id="4c57d-111">Specifies that the common language runtime metadata internal APIs should check the encoding of the property name.</span></span>|  
|`prHasDefault`|<span data-ttu-id="4c57d-112">Указывает, что свойство имеет значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="4c57d-112">Specifies that the property has a default value.</span></span>|  
|`prUnused`|<span data-ttu-id="4c57d-113">Не используется.</span><span class="sxs-lookup"><span data-stu-id="4c57d-113">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4c57d-114">Требования</span><span class="sxs-lookup"><span data-stu-id="4c57d-114">Requirements</span></span>  

 <span data-ttu-id="4c57d-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c57d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c57d-116">**Заголовок:** Корхдр. h</span><span class="sxs-lookup"><span data-stu-id="4c57d-116">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="4c57d-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c57d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c57d-118">См. также</span><span class="sxs-lookup"><span data-stu-id="4c57d-118">See also</span></span>

- [<span data-ttu-id="4c57d-119">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="4c57d-119">Metadata Enumerations</span></span>](metadata-enumerations.md)
