---
description: Дополнительные сведения о функции Жетаппидаусорити
title: Функция GetAppIdAuthority
ms.date: 03/30/2017
api_name:
- GetAppIdAuthority
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- GetAppIdAuthority
helpviewer_keywords:
- GetAppIdAuthority function [.NET Framework fusion]
ms.assetid: 9f968dad-0d09-47fb-bebc-94c39a0d16ad
topic_type:
- apiref
ms.openlocfilehash: a0c2a7b754c2b014b189f96fd3c27347571cc0d1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761074"
---
# <a name="getappidauthority-function"></a><span data-ttu-id="425bb-103">Функция GetAppIdAuthority</span><span class="sxs-lookup"><span data-stu-id="425bb-103">GetAppIdAuthority Function</span></span>

<span data-ttu-id="425bb-104">Возвращает указатель на экземпляр [иаппидаусорити](iappidauthority-interface.md) , который управляет ключами для удостоверений приложений и ссылок.</span><span class="sxs-lookup"><span data-stu-id="425bb-104">Gets a pointer to an [IAppIdAuthority](iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="425bb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="425bb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAppIdAuthority (  
    [out] IAppIdAuthority **ppIAppIdAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="425bb-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="425bb-106">Parameters</span></span>  

 `ppIAppIdAuthority`  
 <span data-ttu-id="425bb-107">заполняет Возвращаемый `IAppIdAuthority` указатель.</span><span class="sxs-lookup"><span data-stu-id="425bb-107">[out] The returned `IAppIdAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="425bb-108">Требования</span><span class="sxs-lookup"><span data-stu-id="425bb-108">Requirements</span></span>  

 <span data-ttu-id="425bb-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="425bb-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="425bb-110">**Заголовок:** Изоляция. h</span><span class="sxs-lookup"><span data-stu-id="425bb-110">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="425bb-111">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="425bb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="425bb-112">См. также</span><span class="sxs-lookup"><span data-stu-id="425bb-112">See also</span></span>

- [<span data-ttu-id="425bb-113">Интерфейс IAppIdAuthority</span><span class="sxs-lookup"><span data-stu-id="425bb-113">IAppIdAuthority Interface</span></span>](iappidauthority-interface.md)
- [<span data-ttu-id="425bb-114">Глобальные статические функции Fusion</span><span class="sxs-lookup"><span data-stu-id="425bb-114">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
