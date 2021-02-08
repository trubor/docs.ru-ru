---
description: 'Подробнее о: кокласс comcallunmarshal coclass'
title: Компонентный класс ComCallUnmarshal
ms.date: 03/30/2017
api_name:
- ComCallUnmarshal Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ComCallUnmarshal
helpviewer_keywords:
- ComCallUnmarshal coclass [.NET Framework hosting]
ms.assetid: 2adb5827-2268-4914-a1c6-f62b61880a45
topic_type:
- apiref
ms.openlocfilehash: 508c1183e2862a286e9db0390bc0348629a9db8e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799841"
---
# <a name="comcallunmarshal-coclass"></a><span data-ttu-id="89a4c-103">Компонентный класс ComCallUnmarshal</span><span class="sxs-lookup"><span data-stu-id="89a4c-103">ComCallUnmarshal Coclass</span></span>

<span data-ttu-id="89a4c-104">Предоставляет интерфейсы для управления упаковкой указателей интерфейса.</span><span class="sxs-lookup"><span data-stu-id="89a4c-104">Provides interfaces for managing the marshaling of interface pointers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89a4c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="89a4c-105">Syntax</span></span>  
  
```cpp  
coclass ComCallUnmarshal {  
    [default] interface IMarshal;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="89a4c-106">Интерфейсы</span><span class="sxs-lookup"><span data-stu-id="89a4c-106">Interfaces</span></span>  
  
|<span data-ttu-id="89a4c-107">Интерфейс</span><span class="sxs-lookup"><span data-stu-id="89a4c-107">Interface</span></span>|<span data-ttu-id="89a4c-108">Описание</span><span class="sxs-lookup"><span data-stu-id="89a4c-108">Description</span></span>|  
|---------------|-----------------|  
|`IMarshal`|<span data-ttu-id="89a4c-109">Предоставляет методы для создания, инициализации и управления прокси-сервером в клиентском процессе.</span><span class="sxs-lookup"><span data-stu-id="89a4c-109">Provides methods for creating, initializing, and managing a proxy in a client process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="89a4c-110">Требования</span><span class="sxs-lookup"><span data-stu-id="89a4c-110">Requirements</span></span>  

 <span data-ttu-id="89a4c-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89a4c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89a4c-112">**Заголовок:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="89a4c-112">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="89a4c-113">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="89a4c-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="89a4c-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89a4c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89a4c-115">См. также</span><span class="sxs-lookup"><span data-stu-id="89a4c-115">See also</span></span>

- [<span data-ttu-id="89a4c-116">Размещение коклассов</span><span class="sxs-lookup"><span data-stu-id="89a4c-116">Hosting Coclasses</span></span>](hosting-coclasses.md)
