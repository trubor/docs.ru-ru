---
description: 'Дополнительные сведения о: интерфейс Иенумреференцеидентити'
title: Интерфейс IEnumReferenceIdentity
ms.date: 03/30/2017
api_name:
- IEnumReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumReferenceIdentity
helpviewer_keywords:
- IEnumReferenceIdentity interface [.NET Framework fusion]
ms.assetid: a17b3155-7216-4e16-8c9f-abce21f549e7
topic_type:
- apiref
ms.openlocfilehash: a7f17793fd737b5153c27dae59fb2aa87b46cf48
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100465305"
---
# <a name="ienumreferenceidentity-interface"></a><span data-ttu-id="148f0-103">Интерфейс IEnumReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="148f0-103">IEnumReferenceIdentity Interface</span></span>

<span data-ttu-id="148f0-104">Служит в качестве перечислителя для коллекции `IReferenceIdentity` объектов.</span><span class="sxs-lookup"><span data-stu-id="148f0-104">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="148f0-105">Методы</span><span class="sxs-lookup"><span data-stu-id="148f0-105">Methods</span></span>  
  
|<span data-ttu-id="148f0-106">Метод</span><span class="sxs-lookup"><span data-stu-id="148f0-106">Method</span></span>|<span data-ttu-id="148f0-107">Описание</span><span class="sxs-lookup"><span data-stu-id="148f0-107">Description</span></span>|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|<span data-ttu-id="148f0-108">Возвращает указатель интерфейса на новый объект `IEnumReferenceIdentity` , содержащий те же элементы, что и этот объект `IEnumReferenceIdentity` .</span><span class="sxs-lookup"><span data-stu-id="148f0-108">Gets an interface pointer to a new `IEnumReferenceIdentity` that contains the same members as this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Next`|<span data-ttu-id="148f0-109">Возвращает указанное число `IReferenceIdentity` объектов, начиная с текущей позиции.</span><span class="sxs-lookup"><span data-stu-id="148f0-109">Gets the specified number of `IReferenceIdentity` objects, starting at the current position.</span></span>|  
|`IEnumReferenceIdentity::Reset`|<span data-ttu-id="148f0-110">Перемещает указатель инструкций в начало `IEnumReferenceIdentity` .</span><span class="sxs-lookup"><span data-stu-id="148f0-110">Moves the instruction pointer to the beginning of this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Skip`|<span data-ttu-id="148f0-111">Перемещает указатель инструкции вперед на указанное число элементов, начиная с текущей позиции.</span><span class="sxs-lookup"><span data-stu-id="148f0-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="148f0-112">Требования</span><span class="sxs-lookup"><span data-stu-id="148f0-112">Requirements</span></span>  

 <span data-ttu-id="148f0-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="148f0-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="148f0-114">**Заголовок:** Изоляция. h</span><span class="sxs-lookup"><span data-stu-id="148f0-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="148f0-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="148f0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="148f0-116">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="148f0-116">See also</span></span>

- [<span data-ttu-id="148f0-117">Fusion-интерфейсы</span><span class="sxs-lookup"><span data-stu-id="148f0-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="148f0-118">Интерфейс IReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="148f0-118">IReferenceIdentity Interface</span></span>](ireferenceidentity-interface.md)
