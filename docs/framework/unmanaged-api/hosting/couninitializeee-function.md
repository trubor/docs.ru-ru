---
description: Дополнительные сведения о функции CoUninitializeEE
title: Функция CoUninitializeEE
ms.date: 03/30/2017
api_name:
- CoUninitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeEE
helpviewer_keywords:
- CoUninitializeEE function [.NET Framework hosting]
ms.assetid: 5f5a311a-839a-465f-89d9-ff1c74da9736
topic_type:
- apiref
ms.openlocfilehash: e356135ea027bd52520eff9084ad2f7f09e1fe0b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746169"
---
# <a name="couninitializeee-function"></a><span data-ttu-id="4ada6-103">Функция CoUninitializeEE</span><span class="sxs-lookup"><span data-stu-id="4ada6-103">CoUninitializeEE Function</span></span>

<span data-ttu-id="4ada6-104">`CoUninitializeEE` является устаревшим и не предоставляет никаких функциональных возможностей.</span><span class="sxs-lookup"><span data-stu-id="4ada6-104">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ada6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4ada6-105">Syntax</span></span>  
  
```cpp  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="4ada6-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="4ada6-106">Remarks</span></span>  

 <span data-ttu-id="4ada6-107">Подсистема выполнения среды CLR не может быть выгружена из процесса.</span><span class="sxs-lookup"><span data-stu-id="4ada6-107">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="4ada6-108">Чтобы завершить работу подсистемы выполнения, [корекситпроцесс](corexitprocess-function.md)вызов.</span><span class="sxs-lookup"><span data-stu-id="4ada6-108">To shut down the execution engine call [CorExitProcess](corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ada6-109">См. также</span><span class="sxs-lookup"><span data-stu-id="4ada6-109">See also</span></span>

- [<span data-ttu-id="4ada6-110">Функция CoInitializeEE</span><span class="sxs-lookup"><span data-stu-id="4ada6-110">CoInitializeEE Function</span></span>](coinitializeee-function.md)
- [<span data-ttu-id="4ada6-111">Глобальные статические функции метаданных</span><span class="sxs-lookup"><span data-stu-id="4ada6-111">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
