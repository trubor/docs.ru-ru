---
description: Дополнительные сведения о функции Жетидентитяусорити
title: Функция GetIdentityAuthority
ms.date: 03/30/2017
api_name:
- GetIdentityAuthority
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- GetIdentityAuthority
helpviewer_keywords:
- GetIdentityAuthority function [.NET Framework fusion]
ms.assetid: 843cd5ab-d2b7-4ff6-86bd-e68c7a91c098
topic_type:
- apiref
ms.openlocfilehash: 5126aa9b319af41f7ecd30845a9f74ba69016588
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761002"
---
# <a name="getidentityauthority-function"></a><span data-ttu-id="8a8c2-103">Функция GetIdentityAuthority</span><span class="sxs-lookup"><span data-stu-id="8a8c2-103">GetIdentityAuthority Function</span></span>

<span data-ttu-id="8a8c2-104">Возвращает указатель на экземпляр [IIdentityAuthority](iidentityauthority-interface.md) , который управляет ключами для объектов кода.</span><span class="sxs-lookup"><span data-stu-id="8a8c2-104">Gets a pointer to an [IIdentityAuthority](iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a8c2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8a8c2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetIdentityAuthority (  
    [out] IIdentityAuthority   **ppIIdentityAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a8c2-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8a8c2-106">Parameters</span></span>  

 `ppIIdentityAuthority`  
 <span data-ttu-id="8a8c2-107">заполняет Возвращаемый `IIdentityAuthority` указатель.</span><span class="sxs-lookup"><span data-stu-id="8a8c2-107">[out] The returned `IIdentityAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a8c2-108">Требования</span><span class="sxs-lookup"><span data-stu-id="8a8c2-108">Requirements</span></span>  

 <span data-ttu-id="8a8c2-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a8c2-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a8c2-110">**Заголовок:** Изоляция. h</span><span class="sxs-lookup"><span data-stu-id="8a8c2-110">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="8a8c2-111">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a8c2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a8c2-112">См. также</span><span class="sxs-lookup"><span data-stu-id="8a8c2-112">See also</span></span>

- [<span data-ttu-id="8a8c2-113">Интерфейс IIdentityAuthority</span><span class="sxs-lookup"><span data-stu-id="8a8c2-113">IIdentityAuthority Interface</span></span>](iidentityauthority-interface.md)
- [<span data-ttu-id="8a8c2-114">Глобальные статические функции Fusion</span><span class="sxs-lookup"><span data-stu-id="8a8c2-114">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
