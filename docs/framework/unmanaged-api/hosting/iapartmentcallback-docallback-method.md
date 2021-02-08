---
description: 'Дополнительные сведения о методе: Иапартменткаллбакк::D Окаллбакк'
title: Метод IApartmentCallback::DoCallback
ms.date: 03/30/2017
api_name:
- IApartmentCallback.DoCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- DoCallback
helpviewer_keywords:
- IApartmentCallback::DoCallback method [.NET Framework hosting]
- DoCallback method [.NET Framework hosting]
ms.assetid: 8edad30c-30ff-4bee-813c-75525a82fc93
topic_type:
- apiref
ms.openlocfilehash: 65b7f496f953f08e099bf13ef8212c7d6e1026ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785112"
---
# <a name="iapartmentcallbackdocallback-method"></a><span data-ttu-id="cd468-103">Метод IApartmentCallback::DoCallback</span><span class="sxs-lookup"><span data-stu-id="cd468-103">IApartmentCallback::DoCallback Method</span></span>

<span data-ttu-id="cd468-104">Выполняет указанную функцию в апартаменте.</span><span class="sxs-lookup"><span data-stu-id="cd468-104">Executes the specified function within an apartment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd468-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cd468-105">Syntax</span></span>  
  
```cpp  
HRESULT _stdcall DoCallback(  
    [in] SIZE_T pFunc,  
    [in] SIZE_T pData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd468-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="cd468-106">Parameters</span></span>  

 `pFunc`  
 <span data-ttu-id="cd468-107">окне Указатель на функцию, которая должна быть выполнена в апартаменте.</span><span class="sxs-lookup"><span data-stu-id="cd468-107">[in] A pointer to the function to be executed within the apartment.</span></span>  
  
 `pData`  
 <span data-ttu-id="cd468-108">окне Указатель на аргумент функции.</span><span class="sxs-lookup"><span data-stu-id="cd468-108">[in] A pointer to the function's argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd468-109">Требования</span><span class="sxs-lookup"><span data-stu-id="cd468-109">Requirements</span></span>  

 <span data-ttu-id="cd468-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd468-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd468-111">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cd468-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cd468-112">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cd468-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cd468-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd468-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd468-114">См. также</span><span class="sxs-lookup"><span data-stu-id="cd468-114">See also</span></span>

- [<span data-ttu-id="cd468-115">Интерфейс IApartmentCallback</span><span class="sxs-lookup"><span data-stu-id="cd468-115">IApartmentCallback Interface</span></span>](iapartmentcallback-interface.md)
