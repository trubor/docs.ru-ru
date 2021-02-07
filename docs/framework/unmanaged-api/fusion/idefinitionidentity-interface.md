---
description: 'Дополнительные сведения о: интерфейс Идефинитионидентити'
title: Интерфейс IDefinitionIdentity
ms.date: 03/30/2017
api_name:
- IDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionIdentity
helpviewer_keywords:
- IDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: ce5ba888-5fbe-4efd-91cf-f0ff94d8428b
topic_type:
- apiref
ms.openlocfilehash: 3471879cc822b655b786dd9d8234950cb4b99c1d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760658"
---
# <a name="idefinitionidentity-interface"></a><span data-ttu-id="df30d-103">Интерфейс IDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="df30d-103">IDefinitionIdentity Interface</span></span>

<span data-ttu-id="df30d-104">Представляет уникальную сигнатуру кода, определяющего приложение в текущей области.</span><span class="sxs-lookup"><span data-stu-id="df30d-104">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="df30d-105">Методы</span><span class="sxs-lookup"><span data-stu-id="df30d-105">Methods</span></span>  
  
|<span data-ttu-id="df30d-106">Метод</span><span class="sxs-lookup"><span data-stu-id="df30d-106">Method</span></span>|<span data-ttu-id="df30d-107">Описание</span><span class="sxs-lookup"><span data-stu-id="df30d-107">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|<span data-ttu-id="df30d-108">Получает указатель интерфейса на новый `IDefinitionIdentity` объект, идентичный этому объекту `IDefinitionIdentity` , за исключением изменений указанного атрибута.</span><span class="sxs-lookup"><span data-stu-id="df30d-108">Gets an interface pointer to a new `IDefinitionIdentity` object that is identical to this `IDefinitionIdentity`, except for the specified attribute changes.</span></span>|  
|`IDefinitionIdentity::EnumAttributes`|<span data-ttu-id="df30d-109">Возвращает указатель интерфейса на объект [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) , содержащий атрибуты, связанные с этим объектом `IDefinitionIdentity` .</span><span class="sxs-lookup"><span data-stu-id="df30d-109">Gets an interface pointer to an [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) object that contains the attributes associated with this `IDefinitionIdentity`.</span></span>|  
|`IDefinitionIdentity::GetAttribute`|<span data-ttu-id="df30d-110">Возвращает значение атрибута с указанным именем в указанном пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="df30d-110">Gets the value of the attribute with the specified name in the specified namespace.</span></span>|  
|`IDefinitionIdentity::SetAttribute`|<span data-ttu-id="df30d-111">Задает для атрибута с указанным именем в указанном пространстве имен указанное значение.</span><span class="sxs-lookup"><span data-stu-id="df30d-111">Sets the attribute that has the specified name in the specified namespace to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="df30d-112">Требования</span><span class="sxs-lookup"><span data-stu-id="df30d-112">Requirements</span></span>  

 <span data-ttu-id="df30d-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df30d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df30d-114">**Заголовок:** Изоляция. h</span><span class="sxs-lookup"><span data-stu-id="df30d-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="df30d-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df30d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df30d-116">См. также</span><span class="sxs-lookup"><span data-stu-id="df30d-116">See also</span></span>

- [<span data-ttu-id="df30d-117">Fusion-интерфейсы</span><span class="sxs-lookup"><span data-stu-id="df30d-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
