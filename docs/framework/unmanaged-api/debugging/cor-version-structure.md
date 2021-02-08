---
description: 'Дополнительные сведения: структура COR_VERSION'
title: Структура COR_VERSION
ms.date: 03/30/2017
api_name:
- COR_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_VERSION
helpviewer_keywords:
- COR_VERSION structure [.NET Framework debugging]
ms.assetid: 5efaee1c-a001-4c73-9525-4160f4c71567
topic_type:
- apiref
ms.openlocfilehash: abdbe2a62d89db9dd673a429d81209fc42c34b73
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801778"
---
# <a name="cor_version-structure"></a><span data-ttu-id="c4f97-103">Структура COR_VERSION</span><span class="sxs-lookup"><span data-stu-id="c4f97-103">COR_VERSION Structure</span></span>

<span data-ttu-id="c4f97-104">Содержит стандартный номер версии среды CLR, состоящий из четырех частей.</span><span class="sxs-lookup"><span data-stu-id="c4f97-104">Stores the standard four-part version number of the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4f97-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c4f97-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="c4f97-106">Члены</span><span class="sxs-lookup"><span data-stu-id="c4f97-106">Members</span></span>  
  
|<span data-ttu-id="c4f97-107">Член</span><span class="sxs-lookup"><span data-stu-id="c4f97-107">Member</span></span>|<span data-ttu-id="c4f97-108">Описание</span><span class="sxs-lookup"><span data-stu-id="c4f97-108">Description</span></span>|  
|------------|-----------------|  
|`dwMajor`|<span data-ttu-id="c4f97-109">Основной номер версии.</span><span class="sxs-lookup"><span data-stu-id="c4f97-109">The major version number.</span></span>|  
|`dwMinor`|<span data-ttu-id="c4f97-110">Дополнительный номер версии.</span><span class="sxs-lookup"><span data-stu-id="c4f97-110">The minor version number.</span></span>|  
|`dwBuild`|<span data-ttu-id="c4f97-111">Номер построения.</span><span class="sxs-lookup"><span data-stu-id="c4f97-111">The build number.</span></span>|  
|`dwSubBuild`|<span data-ttu-id="c4f97-112">Номер подсборки.</span><span class="sxs-lookup"><span data-stu-id="c4f97-112">The sub-build number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4f97-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="c4f97-113">Remarks</span></span>  

 <span data-ttu-id="c4f97-114">Если номер версии — 1.0.3705.288, то 1 — основной номер версии, 0 — дополнительный номер версии, 3705 — номер сборки, а 288 — номер подсборки.</span><span class="sxs-lookup"><span data-stu-id="c4f97-114">If the version number is 1.0.3705.288, 1 is the major version number, 0 is the minor version number, 3705 is the build number, and 288 is the sub-build number.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4f97-115">Требования</span><span class="sxs-lookup"><span data-stu-id="c4f97-115">Requirements</span></span>  

 <span data-ttu-id="c4f97-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4f97-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4f97-117">**Заголовок:** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="c4f97-117">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="c4f97-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4f97-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4f97-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4f97-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4f97-120">См. также</span><span class="sxs-lookup"><span data-stu-id="c4f97-120">See also</span></span>

- [<span data-ttu-id="c4f97-121">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="c4f97-121">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="c4f97-122">Отладка</span><span class="sxs-lookup"><span data-stu-id="c4f97-122">Debugging</span></span>](index.md)
