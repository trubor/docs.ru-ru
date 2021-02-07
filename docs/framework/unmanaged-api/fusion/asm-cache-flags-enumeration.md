---
description: 'Дополнительные сведения: перечисление ASM_CACHE_FLAGS'
title: Перечисление ASM_CACHE_FLAGS
ms.date: 03/30/2017
api_name:
- ASM_CACHE_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_CACHE_FLAGS
helpviewer_keywords:
- ASM_CACHE_FLAGS enumeration [.NET Framework fusion]
ms.assetid: 82e9a7da-321b-48b8-b239-52eaffda6be8
topic_type:
- apiref
ms.openlocfilehash: 866f61d2960074495ed036e3a8e89ebceec74e87
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761438"
---
# <a name="asm_cache_flags-enumeration"></a><span data-ttu-id="e5cf9-103">Перечисление ASM_CACHE_FLAGS</span><span class="sxs-lookup"><span data-stu-id="e5cf9-103">ASM_CACHE_FLAGS Enumeration</span></span>

<span data-ttu-id="e5cf9-104">Указывает источник сборки, представленной [IAssemblyCacheItem](iassemblycacheitem-interface.md) в глобальном кэше сборок.</span><span class="sxs-lookup"><span data-stu-id="e5cf9-104">Indicates the source of an assembly that is represented by [IAssemblyCacheItem](iassemblycacheitem-interface.md) in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5cf9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e5cf9-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    ASM_CACHE_ZAP       = 0x01,  
    ASM_CACHE_GAC       = 0x02,  
    ASM_CACHE_DOWNLOAD  = 0x04,  
    ASM_CACHE_ROOT      = 0x08,  
    ASM_CACHE_ROOT_EX   = 0x80  
} ASM_CACHE_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="e5cf9-106">Члены</span><span class="sxs-lookup"><span data-stu-id="e5cf9-106">Members</span></span>  
  
|<span data-ttu-id="e5cf9-107">Член</span><span class="sxs-lookup"><span data-stu-id="e5cf9-107">Member</span></span>|<span data-ttu-id="e5cf9-108">Описание</span><span class="sxs-lookup"><span data-stu-id="e5cf9-108">Description</span></span>|  
|------------|-----------------|  
|`ASM_CACHE_ZAP`|<span data-ttu-id="e5cf9-109">Перечисляет кэш предварительно скомпилированных сборок с помощью Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="e5cf9-109">Enumerates the cache of precompiled assemblies by using Ngen.exe.</span></span>|  
|`ASM_CACHE_GAC`|<span data-ttu-id="e5cf9-110">Перечисляет глобальный кэш сборок.</span><span class="sxs-lookup"><span data-stu-id="e5cf9-110">Enumerates the global assembly cache.</span></span>|  
|`ASM_CACHE_DOWNLOAD`|<span data-ttu-id="e5cf9-111">Перечисляет сборки, скачанные по запросу или теневые копии.</span><span class="sxs-lookup"><span data-stu-id="e5cf9-111">Enumerates the assemblies that have been downloaded on demand or that have been shadow-copied.</span></span>|  
|`ASM_CACHE_ROOT`|<span data-ttu-id="e5cf9-112">Указывает, что функция [жеткачепас](getcachepath-function.md) должна возвращать путь к глобальному кэшу сборок для общеязыковой среды выполнения (CLR) версии 2,0.</span><span class="sxs-lookup"><span data-stu-id="e5cf9-112">Indicates that the [GetCachePath](getcachepath-function.md) function should return the path to the global assembly cache for the common language runtime (CLR) version 2.0.</span></span> <span data-ttu-id="e5cf9-113">Имеет смысл только в контексте вызова [жеткачепас](getcachepath-function.md).</span><span class="sxs-lookup"><span data-stu-id="e5cf9-113">Meaningful only in the context of a call to [GetCachePath](getcachepath-function.md).</span></span>|  
|`ASM_CACHE_ROOT_EX`|<span data-ttu-id="e5cf9-114">Указывает, что функция [жеткачепас](getcachepath-function.md) должна возвращать путь к глобальному кэшу сборок для CLR версии 4.</span><span class="sxs-lookup"><span data-stu-id="e5cf9-114">Indicates that the [GetCachePath](getcachepath-function.md) function should return the path to the global assembly cache for CLR version 4.</span></span> <span data-ttu-id="e5cf9-115">Имеет смысл только в контексте вызова [жеткачепас](getcachepath-function.md).</span><span class="sxs-lookup"><span data-stu-id="e5cf9-115">Meaningful only in the context of a call to [GetCachePath](getcachepath-function.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e5cf9-116">Требования</span><span class="sxs-lookup"><span data-stu-id="e5cf9-116">Requirements</span></span>  

 <span data-ttu-id="e5cf9-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5cf9-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5cf9-118">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="e5cf9-118">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e5cf9-119">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e5cf9-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e5cf9-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5cf9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5cf9-121">См. также</span><span class="sxs-lookup"><span data-stu-id="e5cf9-121">See also</span></span>

- [<span data-ttu-id="e5cf9-122">Функция GetCachePath</span><span class="sxs-lookup"><span data-stu-id="e5cf9-122">GetCachePath Function</span></span>](getcachepath-function.md)
- [<span data-ttu-id="e5cf9-123">Интерфейс IAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="e5cf9-123">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
- [<span data-ttu-id="e5cf9-124">Перечисления Fusion</span><span class="sxs-lookup"><span data-stu-id="e5cf9-124">Fusion Enumerations</span></span>](fusion-enumerations.md)
