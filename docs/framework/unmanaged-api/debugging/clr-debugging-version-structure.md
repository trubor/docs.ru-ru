---
description: 'Дополнительные сведения: структура CLR_DEBUGGING_VERSION'
title: Структура CLR_DEBUGGING_VERSION
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_VERSION
helpviewer_keywords:
- CLR_DEBUGGING_VERSION structure [.NET Framework debugging]
ms.assetid: 4d821186-3ddf-405a-ac44-d79438a9f7f3
topic_type:
- apiref
ms.openlocfilehash: 2d274a91948b98dc309cd5670c3dd3bf6cd01e2b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772787"
---
# <a name="clr_debugging_version-structure"></a><span data-ttu-id="356ec-103">Структура CLR_DEBUGGING_VERSION</span><span class="sxs-lookup"><span data-stu-id="356ec-103">CLR_DEBUGGING_VERSION Structure</span></span>

<span data-ttu-id="356ec-104">Определяет версию продукта среды CLR, предназначенную для отладки.</span><span class="sxs-lookup"><span data-stu-id="356ec-104">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="356ec-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="356ec-105">Syntax</span></span>  
  
```cpp  
typedef struct _CLR_DEBUGGING_VERSION  
{  
    WORD wStructVersion;
    WORD wMajor;
    WORD wMinor;
    WORD wBuild;
    WORD wRevision;
} CLR_DEBUGGING_VERSION;
```  
  
## <a name="members"></a><span data-ttu-id="356ec-106">Члены</span><span class="sxs-lookup"><span data-stu-id="356ec-106">Members</span></span>  
  
|<span data-ttu-id="356ec-107">Член</span><span class="sxs-lookup"><span data-stu-id="356ec-107">Member</span></span>|<span data-ttu-id="356ec-108">Описание</span><span class="sxs-lookup"><span data-stu-id="356ec-108">Description</span></span>|  
|------------|-----------------|  
|`wStructVersion`|<span data-ttu-id="356ec-109">Номер версии структуры</span><span class="sxs-lookup"><span data-stu-id="356ec-109">The structure version number</span></span>|  
|`wMajor`|<span data-ttu-id="356ec-110">Основной номер версии.</span><span class="sxs-lookup"><span data-stu-id="356ec-110">The major version number.</span></span>|  
|`wMinor`|<span data-ttu-id="356ec-111">Дополнительный номер версии.</span><span class="sxs-lookup"><span data-stu-id="356ec-111">The minor version number.</span></span>|  
|`wBuild`|<span data-ttu-id="356ec-112">Номер построения.</span><span class="sxs-lookup"><span data-stu-id="356ec-112">The build number.</span></span>|  
|`wRevision`|<span data-ttu-id="356ec-113">Номер редакции сборки.</span><span class="sxs-lookup"><span data-stu-id="356ec-113">The revision number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="356ec-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="356ec-114">Remarks</span></span>  

 <span data-ttu-id="356ec-115">Структура аналогична `CLR_DEBUGGING_VERSION` структуре COR_VERSION, однако `CLR_DEBUGGING_VERSION` Структура предоставляет дополнительное поле версии структуры ( `wStructVersion` ).</span><span class="sxs-lookup"><span data-stu-id="356ec-115">The `CLR_DEBUGGING_VERSION` structure is the same as the COR_VERSION structure, however, the `CLR_DEBUGGING_VERSION` structure provides an additional structure version field (`wStructVersion`).</span></span> <span data-ttu-id="356ec-116">В настоящее время для этого поля необходимо задать значение 0.</span><span class="sxs-lookup"><span data-stu-id="356ec-116">Currently, this field must be set to zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="356ec-117">Требования</span><span class="sxs-lookup"><span data-stu-id="356ec-117">Requirements</span></span>  

 <span data-ttu-id="356ec-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="356ec-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="356ec-119">**Заголовок:** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="356ec-119">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="356ec-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="356ec-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="356ec-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="356ec-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="356ec-122">См. также</span><span class="sxs-lookup"><span data-stu-id="356ec-122">See also</span></span>

- [<span data-ttu-id="356ec-123">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="356ec-123">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="356ec-124">Отладка</span><span class="sxs-lookup"><span data-stu-id="356ec-124">Debugging</span></span>](index.md)
