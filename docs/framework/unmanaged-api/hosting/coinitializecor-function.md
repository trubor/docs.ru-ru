---
description: Дополнительные сведения о функции Коинитиализекор
title: Функция CoInitializeCor
ms.date: 03/30/2017
api_name:
- CoInitializeCor
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeCor
helpviewer_keywords:
- CoInitializeCor function [.NET Framework hosting]
ms.assetid: 9b9079fb-579e-4141-b3f0-791072dd40dc
topic_type:
- apiref
ms.openlocfilehash: e1db9914cce8a92cecf78123a2e247d75ec74acf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799854"
---
# <a name="coinitializecor-function"></a><span data-ttu-id="bd0fc-103">Функция CoInitializeCor</span><span class="sxs-lookup"><span data-stu-id="bd0fc-103">CoInitializeCor Function</span></span>

<span data-ttu-id="bd0fc-104">`CoInitializeCor` устарел.</span><span class="sxs-lookup"><span data-stu-id="bd0fc-104">`CoInitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd0fc-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bd0fc-105">Syntax</span></span>  
  
```cpp  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="bd0fc-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="bd0fc-106">Remarks</span></span>  

 <span data-ttu-id="bd0fc-107">Чтобы инициализировать среду CLR, используйте либо [CorBindToRuntimeEx](corbindtoruntimeex-function.md) , либо [корбиндтокуррентрунтиме](corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="bd0fc-107">To initialize the common language runtime, use either [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd0fc-108">Требования</span><span class="sxs-lookup"><span data-stu-id="bd0fc-108">Requirements</span></span>  

 <span data-ttu-id="bd0fc-109">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="bd0fc-109">**Header:** Cor.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd0fc-110">См. также</span><span class="sxs-lookup"><span data-stu-id="bd0fc-110">See also</span></span>

- [<span data-ttu-id="bd0fc-111">Глобальные статические функции метаданных</span><span class="sxs-lookup"><span data-stu-id="bd0fc-111">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
