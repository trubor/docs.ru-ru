---
description: 'Дополнительные сведения о: Цеесектионрелоцекстра Union'
title: Объединение CeeSectionRelocExtra
ms.date: 03/30/2017
api_name:
- CeeSectionRelocExtra Union
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionRelocExtra
helpviewer_keywords:
- CeeSectionRelocExtra union [.NET Framework metadata]
ms.assetid: d9568cf6-7f98-4cd6-ab36-0a2bd509afcc
topic_type:
- apiref
ms.openlocfilehash: 40001c1a0772e24633f4232da8e7817f3747f8ea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678852"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="e49b9-103">Объединение CeeSectionRelocExtra</span><span class="sxs-lookup"><span data-stu-id="e49b9-103">CeeSectionRelocExtra Union</span></span>

<span data-ttu-id="e49b9-104">Представляет смещение адреса, используемое интерфейсом [ICeeGen](iceegen-interface.md) для перемещения раздела.</span><span class="sxs-lookup"><span data-stu-id="e49b9-104">Represents an address offset that is used by the [ICeeGen](iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e49b9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e49b9-105">Syntax</span></span>  
  
```cpp  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="e49b9-106">Члены</span><span class="sxs-lookup"><span data-stu-id="e49b9-106">Members</span></span>  
  
|<span data-ttu-id="e49b9-107">Член</span><span class="sxs-lookup"><span data-stu-id="e49b9-107">Member</span></span>|<span data-ttu-id="e49b9-108">Описание</span><span class="sxs-lookup"><span data-stu-id="e49b9-108">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="e49b9-109">Корректировка верхнего адреса для раздела.</span><span class="sxs-lookup"><span data-stu-id="e49b9-109">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e49b9-110">Требования</span><span class="sxs-lookup"><span data-stu-id="e49b9-110">Requirements</span></span>  

 <span data-ttu-id="e49b9-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e49b9-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e49b9-112">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="e49b9-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e49b9-113">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e49b9-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e49b9-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e49b9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e49b9-115">См. также</span><span class="sxs-lookup"><span data-stu-id="e49b9-115">See also</span></span>

- [<span data-ttu-id="e49b9-116">Объединения метаданных</span><span class="sxs-lookup"><span data-stu-id="e49b9-116">Metadata Unions</span></span>](metadata-unions.md)
