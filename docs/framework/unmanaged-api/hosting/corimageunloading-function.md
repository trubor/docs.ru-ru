---
description: Дополнительные сведения о функции _CorImageUnloading
title: Функция _CorImageUnloading
ms.date: 03/30/2017
api_name:
- _CorImageUnloading
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorImageUnloading
helpviewer_keywords:
- _CorImageUnloading function [.NET Framework hosting]
ms.assetid: b4367214-6dac-4280-aa11-fd487ff30bc4
topic_type:
- apiref
ms.openlocfilehash: fe10c97be66aab21793b1ad306aa5d90eaa1ade2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716995"
---
# <a name="_corimageunloading-function"></a><span data-ttu-id="40926-103">Функция _CorImageUnloading</span><span class="sxs-lookup"><span data-stu-id="40926-103">_CorImageUnloading Function</span></span>

<span data-ttu-id="40926-104">Уведомляет загрузчик об выгрузке образов управляемого модуля.</span><span class="sxs-lookup"><span data-stu-id="40926-104">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="40926-105">Эта функция не реализована.</span><span class="sxs-lookup"><span data-stu-id="40926-105">This function is not implemented.</span></span> <span data-ttu-id="40926-106">При вызове возвращается E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="40926-106">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40926-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="40926-107">Syntax</span></span>  
  
```cpp  
STDAPI (VOID) _CorImageUnloading(
   [in] PVOID* ImageBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40926-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="40926-108">Parameters</span></span>  

 `ImageBase`  
 <span data-ttu-id="40926-109">окне Указатель на начальное расположение изображения для выгрузки.</span><span class="sxs-lookup"><span data-stu-id="40926-109">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40926-110">Требования</span><span class="sxs-lookup"><span data-stu-id="40926-110">Requirements</span></span>  

 <span data-ttu-id="40926-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40926-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40926-112">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="40926-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="40926-113">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="40926-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="40926-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40926-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40926-115">См. также</span><span class="sxs-lookup"><span data-stu-id="40926-115">See also</span></span>

- [<span data-ttu-id="40926-116">Глобальные статические функции метаданных</span><span class="sxs-lookup"><span data-stu-id="40926-116">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
