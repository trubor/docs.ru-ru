---
description: Дополнительные сведения о перечислении Кормесодсемантиксаттр
title: Перечисление CorMethodSemanticsAttr
ms.date: 03/30/2017
api_name:
- CorMethodSemanticsAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodSemanticsAttr
helpviewer_keywords:
- CorMethodSemanticsAttr enumeration [.NET Framework metadata]
ms.assetid: ca2af325-eb9d-4a91-90e4-267e45b98611
topic_type:
- apiref
ms.openlocfilehash: 4079e81ae2389ff0684fd11d0751b191a7289932
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784370"
---
# <a name="cormethodsemanticsattr-enumeration"></a><span data-ttu-id="46dae-103">Перечисление CorMethodSemanticsAttr</span><span class="sxs-lookup"><span data-stu-id="46dae-103">CorMethodSemanticsAttr Enumeration</span></span>

<span data-ttu-id="46dae-104">Содержит значения, описывающие связь между методом и соответствующим свойством или событием.</span><span class="sxs-lookup"><span data-stu-id="46dae-104">Contains values that describe the relationship between a method and an associated property or event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46dae-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="46dae-105">Syntax</span></span>  
  
```cpp  
typedef enum CorMethodSemanticsAttr {  
  
    msSetter    =   0x0001,  
    msGetter    =   0x0002,  
    msOther     =   0x0004,  
    msAddOn     =   0x0008,  
    msRemoveOn  =   0x0010,  
    msFire      =   0x0020,  
  
} CorMethodSemanticsAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="46dae-106">Члены</span><span class="sxs-lookup"><span data-stu-id="46dae-106">Members</span></span>  
  
|<span data-ttu-id="46dae-107">Член</span><span class="sxs-lookup"><span data-stu-id="46dae-107">Member</span></span>|<span data-ttu-id="46dae-108">Описание</span><span class="sxs-lookup"><span data-stu-id="46dae-108">Description</span></span>|  
|------------|-----------------|  
|`msSetter`|<span data-ttu-id="46dae-109">Указывает, что метод является методом `set` доступа для свойства.</span><span class="sxs-lookup"><span data-stu-id="46dae-109">Specifies that the method is a `set` accessor for a property.</span></span>|  
|`msGetter`|<span data-ttu-id="46dae-110">Указывает, что метод является методом `get` доступа для свойства.</span><span class="sxs-lookup"><span data-stu-id="46dae-110">Specifies that the method is a `get` accessor for a property.</span></span>|  
|`msOther`|<span data-ttu-id="46dae-111">Указывает, что метод имеет связь со свойством или событием, отличным от указанных здесь.</span><span class="sxs-lookup"><span data-stu-id="46dae-111">Specifies that the method has a relationship to a property or an event other than those defined here.</span></span>|  
|`msAddOn`|<span data-ttu-id="46dae-112">Указывает, что метод добавляет методы обработчика для события.</span><span class="sxs-lookup"><span data-stu-id="46dae-112">Specifies that the method adds handler methods for an event.</span></span>|  
|`msRemoveOn`|<span data-ttu-id="46dae-113">Указывает, что метод удаляет методы обработчика для события.</span><span class="sxs-lookup"><span data-stu-id="46dae-113">Specifies that the method removes handler methods for an event.</span></span>|  
|`msFire`|<span data-ttu-id="46dae-114">Указывает, что метод вызывает событие.</span><span class="sxs-lookup"><span data-stu-id="46dae-114">Specifies that the method raises an event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="46dae-115">Требования</span><span class="sxs-lookup"><span data-stu-id="46dae-115">Requirements</span></span>  

 <span data-ttu-id="46dae-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46dae-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46dae-117">**Заголовок:** Корхдр. h</span><span class="sxs-lookup"><span data-stu-id="46dae-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="46dae-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46dae-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46dae-119">См. также</span><span class="sxs-lookup"><span data-stu-id="46dae-119">See also</span></span>

- [<span data-ttu-id="46dae-120">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="46dae-120">Metadata Enumerations</span></span>](metadata-enumerations.md)
