---
description: Дополнительные сведения о функции Креатеассембликаче
title: Функция CreateAssemblyCache
ms.date: 03/30/2017
api_name:
- CreateAssemblyCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyCache
helpviewer_keywords:
- CreateAssemblyCache function [.NET Framework fusion]
ms.assetid: 348c7c8c-8578-46ae-97cf-480d6015c3c6
topic_type:
- apiref
ms.openlocfilehash: 1646e1d33401c557b13ae5c025f53aef48042004
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761165"
---
# <a name="createassemblycache-function"></a><span data-ttu-id="3faa5-103">Функция CreateAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="3faa5-103">CreateAssemblyCache Function</span></span>

<span data-ttu-id="3faa5-104">Возвращает указатель на новый экземпляр [IAssemblyCache](iassemblycache-interface.md) , представляющий глобальный кэш сборок.</span><span class="sxs-lookup"><span data-stu-id="3faa5-104">Gets a pointer to a new [IAssemblyCache](iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3faa5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3faa5-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCache (  
    [out] IAssemblyCache  **ppAsmCache,  
    [in]  DWORD           dwReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="3faa5-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="3faa5-106">Parameters</span></span>  

 `ppAsmCache`  
 <span data-ttu-id="3faa5-107">заполняет Возвращаемый `IAssemblyCache` указатель.</span><span class="sxs-lookup"><span data-stu-id="3faa5-107">[out] The returned `IAssemblyCache` pointer.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="3faa5-108">окне Зарезервировано для будущего расширения.</span><span class="sxs-lookup"><span data-stu-id="3faa5-108">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="3faa5-109">`dwReserved` значение должно быть равно 0 (нулю).</span><span class="sxs-lookup"><span data-stu-id="3faa5-109">`dwReserved` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3faa5-110">Требования</span><span class="sxs-lookup"><span data-stu-id="3faa5-110">Requirements</span></span>  

 <span data-ttu-id="3faa5-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3faa5-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3faa5-112">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="3faa5-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="3faa5-113">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3faa5-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3faa5-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3faa5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3faa5-115">См. также</span><span class="sxs-lookup"><span data-stu-id="3faa5-115">See also</span></span>

- [<span data-ttu-id="3faa5-116">Интерфейс IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="3faa5-116">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="3faa5-117">Глобальные статические функции Fusion</span><span class="sxs-lookup"><span data-stu-id="3faa5-117">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="3faa5-118">Глобальный кэш сборок</span><span class="sxs-lookup"><span data-stu-id="3faa5-118">Global Assembly Cache</span></span>](../../app-domains/gac.md)
