---
description: 'Дополнительные сведения о: интерфейс Иреференцеаппид'
title: Интерфейс IReferenceAppId
ms.date: 03/30/2017
api_name:
- IReferenceAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceAppId
helpviewer_keywords:
- IReferenceAppId interface [.NET Framework fusion]
ms.assetid: 8eb9e565-f358-43ce-900e-a8f8a5aa6cfb
topic_type:
- apiref
ms.openlocfilehash: 66838d6ae66aa7de05d899e9fa980308718e2a38
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800075"
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="ae664-103">Интерфейс IReferenceAppId</span><span class="sxs-lookup"><span data-stu-id="ae664-103">IReferenceAppId Interface</span></span>

<span data-ttu-id="ae664-104">Представляет ссылку на уникальный идентификатор приложения в текущей области.</span><span class="sxs-lookup"><span data-stu-id="ae664-104">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ae664-105">Методы</span><span class="sxs-lookup"><span data-stu-id="ae664-105">Methods</span></span>  
  
|<span data-ttu-id="ae664-106">Метод</span><span class="sxs-lookup"><span data-stu-id="ae664-106">Method</span></span>|<span data-ttu-id="ae664-107">Описание</span><span class="sxs-lookup"><span data-stu-id="ae664-107">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="ae664-108">Возвращает указатель на строковое представление идентификатора кода для приложения, на которое ссылается this `IReferenceAppId` .</span><span class="sxs-lookup"><span data-stu-id="ae664-108">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="ae664-109">Задает идентификатор кода для приложения, на которое ссылается this `IReferenceAppId` .</span><span class="sxs-lookup"><span data-stu-id="ae664-109">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="ae664-110">Возвращает указатель интерфейса на `IEnumReferenceIdentity` экземпляр `IReferenceIdentity` , содержащий экземпляры, представляющие члены этого объекта `IReferenceAppId` .</span><span class="sxs-lookup"><span data-stu-id="ae664-110">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="ae664-111">Возвращает указатель на строковое представление идентификатора маркера для подписки на этот объект `IReferenceAppId` .</span><span class="sxs-lookup"><span data-stu-id="ae664-111">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="ae664-112">Задает для идентификатора маркера подписки это `IReferenceAppId` значение в указанном строковом значении.</span><span class="sxs-lookup"><span data-stu-id="ae664-112">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ae664-113">Требования</span><span class="sxs-lookup"><span data-stu-id="ae664-113">Requirements</span></span>  

 <span data-ttu-id="ae664-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae664-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae664-115">**Заголовок:** Изоляция. h</span><span class="sxs-lookup"><span data-stu-id="ae664-115">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="ae664-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae664-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae664-117">См. также</span><span class="sxs-lookup"><span data-stu-id="ae664-117">See also</span></span>

- [<span data-ttu-id="ae664-118">Fusion-интерфейсы</span><span class="sxs-lookup"><span data-stu-id="ae664-118">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="ae664-119">Интерфейс IEnumReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="ae664-119">IEnumReferenceIdentity Interface</span></span>](ienumreferenceidentity-interface.md)
- [<span data-ttu-id="ae664-120">Интерфейс IReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="ae664-120">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)
