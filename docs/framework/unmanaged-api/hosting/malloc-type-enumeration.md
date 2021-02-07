---
description: 'Дополнительные сведения: перечисление MALLOC_TYPE'
title: MALLOC_TYPE - перечисление
ms.date: 03/30/2017
api_name:
- MALLOC_TYPE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MALLOC_TYPE
helpviewer_keywords:
- MALLOC_TYPE Enumeration
ms.assetid: c02476f9-23a2-4af7-9282-aa9c42c7429b
topic_type:
- apiref
ms.openlocfilehash: 47eb58107d79309c34af5f0acdf614804d1f208f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679807"
---
# <a name="malloc_type-enumeration"></a><span data-ttu-id="dbb46-103">MALLOC_TYPE - перечисление</span><span class="sxs-lookup"><span data-stu-id="dbb46-103">MALLOC_TYPE Enumeration</span></span>

<span data-ttu-id="dbb46-104">Содержит значения, указывающие характеристики выделяемой памяти.</span><span class="sxs-lookup"><span data-stu-id="dbb46-104">Contains values that specify the characteristics of the memory that is being allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbb46-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dbb46-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="dbb46-106">Члены</span><span class="sxs-lookup"><span data-stu-id="dbb46-106">Members</span></span>  
  
|<span data-ttu-id="dbb46-107">Член</span><span class="sxs-lookup"><span data-stu-id="dbb46-107">Member</span></span>|<span data-ttu-id="dbb46-108">Описание</span><span class="sxs-lookup"><span data-stu-id="dbb46-108">Description</span></span>|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|<span data-ttu-id="dbb46-109">Выделенная память может содержать исполняемый файл.</span><span class="sxs-lookup"><span data-stu-id="dbb46-109">The allocated memory can contain an executable file.</span></span>|  
|`MALLOC_THREADSAFE`|<span data-ttu-id="dbb46-110">Выделенная память является потокобезопасной.</span><span class="sxs-lookup"><span data-stu-id="dbb46-110">The allocated memory is thread-safe.</span></span> <span data-ttu-id="dbb46-111">То есть доступ к памяти может осуществляться несколькими потоками без синхронизации.</span><span class="sxs-lookup"><span data-stu-id="dbb46-111">That is, the memory can be accessed by multiple threads without any synchronization.</span></span><br /><br /> <span data-ttu-id="dbb46-112">Если этот флаг не установлен, вызовы для объекта должны быть сериализованы.</span><span class="sxs-lookup"><span data-stu-id="dbb46-112">If this flag is not set, calls on the object must be serialized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dbb46-113">Требования</span><span class="sxs-lookup"><span data-stu-id="dbb46-113">Requirements</span></span>  

 <span data-ttu-id="dbb46-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbb46-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbb46-115">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="dbb46-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dbb46-116">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dbb46-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dbb46-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbb46-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbb46-118">См. также</span><span class="sxs-lookup"><span data-stu-id="dbb46-118">See also</span></span>

- [<span data-ttu-id="dbb46-119">Размещение перечислений</span><span class="sxs-lookup"><span data-stu-id="dbb46-119">Hosting Enumerations</span></span>](hosting-enumerations.md)
