---
description: 'Дополнительные сведения о: интерфейс Иреференцеидентити'
title: Интерфейс IReferenceIdentity
ms.date: 03/30/2017
api_name:
- IReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceIdentity
helpviewer_keywords:
- IReferenceIdentity interface [.NET Framework fusion]
ms.assetid: 9180ac5a-7019-4716-9f83-8a91d157239a
topic_type:
- apiref
ms.openlocfilehash: a29aaa1f4fb928c136af4168619d27900537c779
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800049"
---
# <a name="ireferenceidentity-interface"></a><span data-ttu-id="7584a-103">Интерфейс IReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="7584a-103">IReferenceIdentity Interface</span></span>

<span data-ttu-id="7584a-104">Представляет ссылку на уникальную сигнатуру объекта кода.</span><span class="sxs-lookup"><span data-stu-id="7584a-104">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7584a-105">Методы</span><span class="sxs-lookup"><span data-stu-id="7584a-105">Methods</span></span>  
  
|<span data-ttu-id="7584a-106">Метод</span><span class="sxs-lookup"><span data-stu-id="7584a-106">Method</span></span>|<span data-ttu-id="7584a-107">Описание</span><span class="sxs-lookup"><span data-stu-id="7584a-107">Description</span></span>|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|<span data-ttu-id="7584a-108">Возвращает указатель интерфейса на новый `IReferenceIdentity` экземпляр, идентичный этому `IReferenceIdentity` , за исключением изменения указанного атрибута.</span><span class="sxs-lookup"><span data-stu-id="7584a-108">Gets an interface pointer to a new `IReferenceIdentity` instance that is identical to this `IReferenceIdentity`, except for the specified attribute changes.</span></span>|  
|`IReferenceIdentity::EnumAttributes`|<span data-ttu-id="7584a-109">Возвращает указатель интерфейса на `IEnumIDENTITY_ATTRIBUTE` экземпляр, содержащий атрибуты, связанные с этим `IReferenceIdentity` .</span><span class="sxs-lookup"><span data-stu-id="7584a-109">Gets an interface pointer to an `IEnumIDENTITY_ATTRIBUTE` instance that contains the attributes associated with this `IReferenceIdentity`.</span></span>|  
|`IReferenceIdentity::GetAttribute`|<span data-ttu-id="7584a-110">Возвращает значение атрибута в указанном пространстве имен с указанным именем.</span><span class="sxs-lookup"><span data-stu-id="7584a-110">Gets the value of the attribute in the specified namespace, with the specified name.</span></span>|  
|`IReferenceIdentity::SetAttribute`|<span data-ttu-id="7584a-111">Задает для атрибута, имеющего указанное пространство имен и указанное имя, указанное значение.</span><span class="sxs-lookup"><span data-stu-id="7584a-111">Sets the attribute that has the specified namespace and the specified name to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7584a-112">Требования</span><span class="sxs-lookup"><span data-stu-id="7584a-112">Requirements</span></span>  

 <span data-ttu-id="7584a-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7584a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7584a-114">**Заголовок:** Изоляция. h</span><span class="sxs-lookup"><span data-stu-id="7584a-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="7584a-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7584a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7584a-116">См. также</span><span class="sxs-lookup"><span data-stu-id="7584a-116">See also</span></span>

- [<span data-ttu-id="7584a-117">Fusion-интерфейсы</span><span class="sxs-lookup"><span data-stu-id="7584a-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="7584a-118">Интерфейс IEnumIDENTITY_ATTRIBUTE</span><span class="sxs-lookup"><span data-stu-id="7584a-118">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](ienumidentity-attribute-interface.md)
