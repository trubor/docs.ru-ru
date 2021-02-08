---
description: 'Дополнительные сведения о: структура Буккетпараметерс'
title: Структура BucketParameters
ms.date: 03/30/2017
api_name:
- BucketParameters
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- BucketParameters
helpviewer_keywords:
- BucketParameters structure [.NET Framework hosting]
ms.assetid: 9432487e-f276-45d6-9a13-9a68024dbd46
topic_type:
- apiref
ms.openlocfilehash: e2d701caa0e2374cb6b44d5fb5537f2ecc7e34fd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799971"
---
# <a name="bucketparameters-structure"></a><span data-ttu-id="7f924-103">Структура BucketParameters</span><span class="sxs-lookup"><span data-stu-id="7f924-103">BucketParameters Structure</span></span>

<span data-ttu-id="7f924-104">Хранит имя типа события и параметры для текущего исключения, связанного с событием.</span><span class="sxs-lookup"><span data-stu-id="7f924-104">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f924-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7f924-105">Syntax</span></span>  
  
```cpp  
typedef struct _BucketParameters {  
    BOOL  fInited;
    WCHAR pszEventTypeName[255];
    WCHAR pszParams[10][255];
} BucketParameters;  
```  
  
## <a name="members"></a><span data-ttu-id="7f924-106">Члены</span><span class="sxs-lookup"><span data-stu-id="7f924-106">Members</span></span>  
  
|<span data-ttu-id="7f924-107">Член</span><span class="sxs-lookup"><span data-stu-id="7f924-107">Member</span></span>|<span data-ttu-id="7f924-108">Описание</span><span class="sxs-lookup"><span data-stu-id="7f924-108">Description</span></span>|  
|------------|-----------------|  
|`fInited`|<span data-ttu-id="7f924-109">`true`значение, если оставшаяся часть этой структуры является допустимой. в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="7f924-109">`true`, if the rest of this structure is valid; otherwise, `false`.</span></span>|  
|`pszEventTypeName`|<span data-ttu-id="7f924-110">Имя типа события.</span><span class="sxs-lookup"><span data-stu-id="7f924-110">Name of the event type.</span></span>|  
|`pszParams`|<span data-ttu-id="7f924-111">Массив строк, каждый из которых задает параметр для текущего исключения, связанного с событием.</span><span class="sxs-lookup"><span data-stu-id="7f924-111">An array of strings, each of which specifies a parameter for the current exception associated with the event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7f924-112">Требования</span><span class="sxs-lookup"><span data-stu-id="7f924-112">Requirements</span></span>  

 <span data-ttu-id="7f924-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f924-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f924-114">**Заголовок:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="7f924-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="7f924-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f924-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f924-116">См. также</span><span class="sxs-lookup"><span data-stu-id="7f924-116">See also</span></span>

- [<span data-ttu-id="7f924-117">Структуры размещения</span><span class="sxs-lookup"><span data-stu-id="7f924-117">Hosting Structures</span></span>](hosting-structures.md)
