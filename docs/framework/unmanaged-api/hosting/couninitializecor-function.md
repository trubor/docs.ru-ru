---
description: Дополнительные сведения о функции Каунинитиализекор
title: Функция CoUninitializeCor
ms.date: 03/30/2017
api_name:
- CoUninitializeCor
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeCor
helpviewer_keywords:
- CoUninitializeCor function [.NET Framework hosting]
ms.assetid: 50a95b8b-9766-470e-bb29-2c7ecddfd4a1
topic_type:
- apiref
ms.openlocfilehash: 1aa3482b6891779b4c85c29079ccd26d7170934e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746208"
---
# <a name="couninitializecor-function"></a><span data-ttu-id="96ee0-103">Функция CoUninitializeCor</span><span class="sxs-lookup"><span data-stu-id="96ee0-103">CoUninitializeCor Function</span></span>

<span data-ttu-id="96ee0-104">`CoUninitializeCor` устарел.</span><span class="sxs-lookup"><span data-stu-id="96ee0-104">`CoUninitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96ee0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="96ee0-105">Syntax</span></span>  
  
```cpp  
STDAPI_(void) CoUninitializeCor(void);  
```  
  
## <a name="remarks"></a><span data-ttu-id="96ee0-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="96ee0-106">Remarks</span></span>  

 <span data-ttu-id="96ee0-107">Среду CLR невозможно выгрузить из процесса.</span><span class="sxs-lookup"><span data-stu-id="96ee0-107">The common language runtime cannot be unloaded from a process.</span></span> <span data-ttu-id="96ee0-108">Чтобы полностью удалить среду выполнения из выполняющегося процесса, необходимо завершить этот процесс.</span><span class="sxs-lookup"><span data-stu-id="96ee0-108">To completely remove the runtime from a running process, you must shut down that process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96ee0-109">См. также</span><span class="sxs-lookup"><span data-stu-id="96ee0-109">See also</span></span>

- [<span data-ttu-id="96ee0-110">Глобальные статические функции метаданных</span><span class="sxs-lookup"><span data-stu-id="96ee0-110">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
