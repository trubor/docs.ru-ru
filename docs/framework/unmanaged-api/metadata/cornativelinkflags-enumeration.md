---
description: Дополнительные сведения о перечислении CorNativeLinkFlags
title: Перечисление CorNativeLinkFlags
ms.date: 03/30/2017
api_name:
- CorNativeLinkFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkFlags
helpviewer_keywords:
- CorNativeLinkFlags enumeration [.NET Framework metadata]
ms.assetid: 8027df7c-cfad-4724-bda0-7538d9519070
topic_type:
- apiref
ms.openlocfilehash: 9025d192ca92c1160c1b072b0dcfe045fa3ceab7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784357"
---
# <a name="cornativelinkflags-enumeration"></a><span data-ttu-id="4af83-103">Перечисление CorNativeLinkFlags</span><span class="sxs-lookup"><span data-stu-id="4af83-103">CorNativeLinkFlags Enumeration</span></span>

<span data-ttu-id="4af83-104">Предоставляет значения флагов, используемые компоновщиком при связывании машинного кода.</span><span class="sxs-lookup"><span data-stu-id="4af83-104">Provides flag values used by the linker when linking native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4af83-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4af83-105">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    nlfNone         = 0x00,  
    nlfLastError    = 0x01,  
    nlfNoMangle     = 0x02,  
    nlfMaxValue     = 0x03  
} CorNativeLinkFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="4af83-106">Члены</span><span class="sxs-lookup"><span data-stu-id="4af83-106">Members</span></span>  
  
|<span data-ttu-id="4af83-107">Член</span><span class="sxs-lookup"><span data-stu-id="4af83-107">Member</span></span>|<span data-ttu-id="4af83-108">Описание</span><span class="sxs-lookup"><span data-stu-id="4af83-108">Description</span></span>|  
|------------|-----------------|  
|`nlfNone`|<span data-ttu-id="4af83-109">Указывает, что флаги отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="4af83-109">Indicates no flags.</span></span>|  
|`nlfLastError`|<span data-ttu-id="4af83-110">Указывает `setLastError` ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="4af83-110">Indicates a `setLastError` keyword.</span></span>|  
|`nlfNoMangle`|<span data-ttu-id="4af83-111">Указывает `nomangle` ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="4af83-111">Indicates a `nomangle` keyword.</span></span>|  
|`nlfMaxValue`|<span data-ttu-id="4af83-112">Не используется.</span><span class="sxs-lookup"><span data-stu-id="4af83-112">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4af83-113">Требования</span><span class="sxs-lookup"><span data-stu-id="4af83-113">Requirements</span></span>  

 <span data-ttu-id="4af83-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4af83-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4af83-115">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="4af83-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4af83-116">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4af83-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4af83-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4af83-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4af83-118">См. также</span><span class="sxs-lookup"><span data-stu-id="4af83-118">See also</span></span>

- [<span data-ttu-id="4af83-119">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="4af83-119">Metadata Enumerations</span></span>](metadata-enumerations.md)
