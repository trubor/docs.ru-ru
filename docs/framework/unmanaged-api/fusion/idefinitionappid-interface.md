---
description: 'Дополнительные сведения о: интерфейс IDefinitionAppId'
title: Интерфейс IDefinitionAppId
ms.date: 03/30/2017
api_name:
- IDefinitionAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionAppId
helpviewer_keywords:
- IDefinitionAppId interface [.NET Framework fusion]
ms.assetid: e72f2550-bdec-4a20-a2f4-2e14847266c1
topic_type:
- apiref
ms.openlocfilehash: 3c68044e7e747521e190fad404e89d6d0a994611
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760671"
---
# <a name="idefinitionappid-interface"></a><span data-ttu-id="637b9-103">Интерфейс IDefinitionAppId</span><span class="sxs-lookup"><span data-stu-id="637b9-103">IDefinitionAppId Interface</span></span>

<span data-ttu-id="637b9-104">Представляет уникальный идентификатор для кода, определяющего приложение в текущей области.</span><span class="sxs-lookup"><span data-stu-id="637b9-104">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="637b9-105">Методы</span><span class="sxs-lookup"><span data-stu-id="637b9-105">Methods</span></span>  
  
|<span data-ttu-id="637b9-106">Метод</span><span class="sxs-lookup"><span data-stu-id="637b9-106">Method</span></span>|<span data-ttu-id="637b9-107">Описание</span><span class="sxs-lookup"><span data-stu-id="637b9-107">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|<span data-ttu-id="637b9-108">Возвращает отформатированную строку, которая представляет код в этом `IDefinitionAppId` объекте.</span><span class="sxs-lookup"><span data-stu-id="637b9-108">Gets a formatted string that represents the code in this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_Codebase`|<span data-ttu-id="637b9-109">Задает код этого `IDefinitionAppId` объекта в указанном форматированном строковом значении.</span><span class="sxs-lookup"><span data-stu-id="637b9-109">Sets the code of this `IDefinitionAppId` object to the specified formatted string value.</span></span>|  
|`IDefinitionAppId::EnumAppPath`|<span data-ttu-id="637b9-110">Возвращает указатель интерфейса на объект [иенумдефинитионидентити](ienumdefinitionidentity-interface.md) , содержащий сборки в текущем пути приложения.</span><span class="sxs-lookup"><span data-stu-id="637b9-110">Gets an interface pointer to an [IEnumDefinitionIdentity](ienumdefinitionidentity-interface.md) object that contains the assemblies in the current application path.</span></span>|  
|`IDefinitionAppId::SetAppPath`|<span data-ttu-id="637b9-111">Задает путь приложения для сборки в текущей области к значению, на которое ссылается указанный объект [идефинитионидентити](idefinitionidentity-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="637b9-111">Sets the application path for the assembly in the current scope to the value referenced by the specified [IDefinitionIdentity](idefinitionidentity-interface.md) object.</span></span>|  
|`IDefinitionAppId::get_SubscriptionId`|<span data-ttu-id="637b9-112">Возвращает указатель на строковое представление идентификатора маркера для подписки на этот `IDefinitionAppId` объект.</span><span class="sxs-lookup"><span data-stu-id="637b9-112">Gets a pointer to a string representation of the token identifier for a subscription to this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_SubscriptionId`|<span data-ttu-id="637b9-113">Устанавливает идентификатор маркера для подписки на этот `IDefinitionAppId` объект в указанном строковом значении.</span><span class="sxs-lookup"><span data-stu-id="637b9-113">Sets the token identifier for a subscription to this `IDefinitionAppId` object to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="637b9-114">Требования</span><span class="sxs-lookup"><span data-stu-id="637b9-114">Requirements</span></span>  

 <span data-ttu-id="637b9-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="637b9-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="637b9-116">**Заголовок:** Изоляция. h</span><span class="sxs-lookup"><span data-stu-id="637b9-116">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="637b9-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="637b9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="637b9-118">См. также</span><span class="sxs-lookup"><span data-stu-id="637b9-118">See also</span></span>

- [<span data-ttu-id="637b9-119">Fusion-интерфейсы</span><span class="sxs-lookup"><span data-stu-id="637b9-119">Fusion Interfaces</span></span>](fusion-interfaces.md)
