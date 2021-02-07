---
description: Дополнительные сведения о функции Жеткачепас
title: Функция GetCachePath
ms.date: 03/30/2017
api_name:
- GetCachePath
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- GetCachePath
helpviewer_keywords:
- GetCachePath function [.NET Framework fusion]
ms.assetid: d977ad29-6619-42e1-b0be-bc25ea950e80
topic_type:
- apiref
ms.openlocfilehash: 4f5045d4110ca9aae33ef54eb85a2146f855e6c7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761048"
---
# <a name="getcachepath-function"></a><span data-ttu-id="dc544-103">Функция GetCachePath</span><span class="sxs-lookup"><span data-stu-id="dc544-103">GetCachePath Function</span></span>

<span data-ttu-id="dc544-104">Возвращает путь к кэшированной сборке с использованием указанных флагов.</span><span class="sxs-lookup"><span data-stu-id="dc544-104">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc544-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dc544-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc544-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="dc544-106">Parameters</span></span>  

 `dwCacheFlags`  
 <span data-ttu-id="dc544-107">окне Значение [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) , указывающее источник кэшированной сборки.</span><span class="sxs-lookup"><span data-stu-id="dc544-107">[in] An [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) value that indicates the source of the cached assembly.</span></span>  
  
 `pwzCachePath`  
 <span data-ttu-id="dc544-108">заполняет Возвращаемый указатель на путь.</span><span class="sxs-lookup"><span data-stu-id="dc544-108">[out] The returned pointer to the path.</span></span>  
  
 `pcchPath`  
 <span data-ttu-id="dc544-109">[вход, выход] Запрошенная максимальная длина `pwzCachePath` и при возврате фактической длины `pwzCachePath` .</span><span class="sxs-lookup"><span data-stu-id="dc544-109">[in, out] The requested maximum length of `pwzCachePath`, and upon return, the actual length of `pwzCachePath`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc544-110">Требования</span><span class="sxs-lookup"><span data-stu-id="dc544-110">Requirements</span></span>  

 <span data-ttu-id="dc544-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc544-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc544-112">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="dc544-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="dc544-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc544-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc544-114">См. также</span><span class="sxs-lookup"><span data-stu-id="dc544-114">See also</span></span>

- [<span data-ttu-id="dc544-115">Перечисление ASM_CACHE_FLAGS</span><span class="sxs-lookup"><span data-stu-id="dc544-115">ASM_CACHE_FLAGS Enumeration</span></span>](asm-cache-flags-enumeration.md)
- [<span data-ttu-id="dc544-116">Глобальные статические функции Fusion</span><span class="sxs-lookup"><span data-stu-id="dc544-116">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
