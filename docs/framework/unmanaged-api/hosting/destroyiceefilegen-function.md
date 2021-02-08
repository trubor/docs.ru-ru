---
description: Дополнительные сведения о функции Дестройицеефилежен
title: Функция DestroyICeeFileGen
ms.date: 03/30/2017
api_name:
- DestroyICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- DestroyICeeFileGen
helpviewer_keywords:
- DestroyICeeFileGen function [.NET Framework hosting]
ms.assetid: dc1e2235-e721-4cb2-a0b8-6b0c030d7bab
topic_type:
- apiref
ms.openlocfilehash: 14ae990999247b90f16b10115dea3408b965a04a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785657"
---
# <a name="destroyiceefilegen-function"></a><span data-ttu-id="2a920-103">Функция DestroyICeeFileGen</span><span class="sxs-lookup"><span data-stu-id="2a920-103">DestroyICeeFileGen Function</span></span>

<span data-ttu-id="2a920-104">Уничтожает объект [ицеефилежен](iceefilegen-class.md) .</span><span class="sxs-lookup"><span data-stu-id="2a920-104">Destroys an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="2a920-105">Эта функция является устаревшей в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="2a920-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a920-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2a920-106">Syntax</span></span>  
  
```cpp  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a920-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="2a920-107">Parameters</span></span>  

 `ceeFileGen`  
 <span data-ttu-id="2a920-108">окне `ICeeFileGen` Объект для уничтожения.</span><span class="sxs-lookup"><span data-stu-id="2a920-108">[in] The `ICeeFileGen` object to destroy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2a920-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="2a920-109">Return Value</span></span>  

 <span data-ttu-id="2a920-110">Этот метод возвращает стандартные коды ошибок COM.</span><span class="sxs-lookup"><span data-stu-id="2a920-110">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a920-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="2a920-111">Remarks</span></span>  

 <span data-ttu-id="2a920-112">`DestroyICeeFileGen` уничтожает `ICeeFileGen` объект, созданный функцией [креатеицеефилежен](createiceefilegen-function.md) .</span><span class="sxs-lookup"><span data-stu-id="2a920-112">`DestroyICeeFileGen` destroys the `ICeeFileGen` object created by the [CreateICeeFileGen](createiceefilegen-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a920-113">Требования</span><span class="sxs-lookup"><span data-stu-id="2a920-113">Requirements</span></span>  

 <span data-ttu-id="2a920-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a920-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a920-115">**Заголовок:** Ицеефилежен. h</span><span class="sxs-lookup"><span data-stu-id="2a920-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="2a920-116">**Библиотека:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="2a920-116">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="2a920-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a920-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a920-118">См. также</span><span class="sxs-lookup"><span data-stu-id="2a920-118">See also</span></span>

- [<span data-ttu-id="2a920-119">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="2a920-119">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
