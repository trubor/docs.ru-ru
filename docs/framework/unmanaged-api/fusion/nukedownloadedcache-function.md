---
description: Дополнительные сведения о функции NukeDownloadedCache
title: Функция NukeDownloadedCache
ms.date: 03/30/2017
api_name:
- NukeDownloadedCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- NukeDownloadedCache
helpviewer_keywords:
- NukeDownloadedCache function [.NET Framework fusion]
ms.assetid: fac2b1c6-6fa3-4818-805b-b63972024c86
topic_type:
- apiref
ms.openlocfilehash: 2239473b8e6e43a539b0507c8255d40f87e72043
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800036"
---
# <a name="nukedownloadedcache-function"></a><span data-ttu-id="1f0a7-103">Функция NukeDownloadedCache</span><span class="sxs-lookup"><span data-stu-id="1f0a7-103">NukeDownloadedCache Function</span></span>

<span data-ttu-id="1f0a7-104">Удаляет кэш загрузки среды CLR.</span><span class="sxs-lookup"><span data-stu-id="1f0a7-104">Deletes the common language runtime (CLR) download cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f0a7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1f0a7-105">Syntax</span></span>  
  
```cpp  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a><span data-ttu-id="1f0a7-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="1f0a7-106">Return Value</span></span>  

 <span data-ttu-id="1f0a7-107">Этот метод возвращает стандартные коды ошибок COM, как определено в файле WinError. h.</span><span class="sxs-lookup"><span data-stu-id="1f0a7-107">This method returns standard COM error codes, as defined in WinError.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f0a7-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="1f0a7-108">Remarks</span></span>  

 <span data-ttu-id="1f0a7-109">Кэш загрузки среды CLR — это область, в которой хранятся сборки со строгими именами, загружаемые из URL-адреса для возможного повторного использования.</span><span class="sxs-lookup"><span data-stu-id="1f0a7-109">The CLR download cache is the area where strong-named assemblies that are downloaded from a URL are stored for possible reuse.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f0a7-110">Требования</span><span class="sxs-lookup"><span data-stu-id="1f0a7-110">Requirements</span></span>  

 <span data-ttu-id="1f0a7-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f0a7-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f0a7-112">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="1f0a7-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="1f0a7-113">**Библиотека:** Fusion.dll и Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="1f0a7-113">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="1f0a7-114">Используйте Fusion.dll вместо Mscorwks.dll, чтобы убедиться в правильности целевой версии платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1f0a7-114">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="1f0a7-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f0a7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f0a7-116">См. также</span><span class="sxs-lookup"><span data-stu-id="1f0a7-116">See also</span></span>

- [<span data-ttu-id="1f0a7-117">Функция CreateHistoryReader</span><span class="sxs-lookup"><span data-stu-id="1f0a7-117">CreateHistoryReader Function</span></span>](createhistoryreader-function.md)
- [<span data-ttu-id="1f0a7-118">Функция GetHistoryFileDirectory</span><span class="sxs-lookup"><span data-stu-id="1f0a7-118">GetHistoryFileDirectory Function</span></span>](gethistoryfiledirectory-function.md)
- [<span data-ttu-id="1f0a7-119">Глобальные статические функции Fusion</span><span class="sxs-lookup"><span data-stu-id="1f0a7-119">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
