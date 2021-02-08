---
description: Дополнительные сведения о IEnumIDENTITY_ATTRIBUTE интерфейсе
title: Интерфейс IEnumIDENTITY_ATTRIBUTE
ms.date: 03/30/2017
api_name:
- IEnumIDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumIDENTITY_ATTRIBUTE
helpviewer_keywords:
- IEnumIDENTITY_ATTRIBUTE interface [.NET Framework fusion]
ms.assetid: c2ec2748-e9ae-4e1b-80db-6fcec5cb81a1
topic_type:
- apiref
ms.openlocfilehash: b621a722e35d5b31f487e8823b1627fdfe1e7888
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800153"
---
# <a name="ienumidentity_attribute-interface"></a><span data-ttu-id="7a31c-103">Интерфейс IEnumIDENTITY_ATTRIBUTE</span><span class="sxs-lookup"><span data-stu-id="7a31c-103">IEnumIDENTITY_ATTRIBUTE Interface</span></span>

<span data-ttu-id="7a31c-104">Служит в качестве перечислителя для атрибутов объекта Code в текущей области.</span><span class="sxs-lookup"><span data-stu-id="7a31c-104">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7a31c-105">Методы</span><span class="sxs-lookup"><span data-stu-id="7a31c-105">Methods</span></span>  
  
|<span data-ttu-id="7a31c-106">Метод</span><span class="sxs-lookup"><span data-stu-id="7a31c-106">Method</span></span>|<span data-ttu-id="7a31c-107">Описание</span><span class="sxs-lookup"><span data-stu-id="7a31c-107">Description</span></span>|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|<span data-ttu-id="7a31c-108">Возвращает указатель интерфейса на новый объект `IEnumIDENTITY_ATTRIBUTE` , содержащий те же элементы, что и этот объект `IEnumIDENTITY_ATTRIBUTE` .</span><span class="sxs-lookup"><span data-stu-id="7a31c-108">Gets an interface pointer to a new `IEnumIDENTITY_ATTRIBUTE` that contains the same members as this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|<span data-ttu-id="7a31c-109">Записывает данные, содержащиеся в элементах этого объекта `IEnumIDENTITY_ATTRIBUTE` , в указанный буфер данных.</span><span class="sxs-lookup"><span data-stu-id="7a31c-109">Writes the data contained in the elements of this `IEnumIDENTITY_ATTRIBUTE` to the specified data buffer.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|<span data-ttu-id="7a31c-110">Возвращает указанное число атрибутов, начиная с текущей позиции.</span><span class="sxs-lookup"><span data-stu-id="7a31c-110">Gets the specified number of attributes, starting at the current position.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|<span data-ttu-id="7a31c-111">Перемещает указатель инструкций в начало `IEnumIDENTITY_ATTRIBUTE` .</span><span class="sxs-lookup"><span data-stu-id="7a31c-111">Moves the instruction pointer to the beginning of this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|<span data-ttu-id="7a31c-112">Перемещает указатель инструкции вперед на указанное число элементов, начиная с текущей позиции.</span><span class="sxs-lookup"><span data-stu-id="7a31c-112">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7a31c-113">Требования</span><span class="sxs-lookup"><span data-stu-id="7a31c-113">Requirements</span></span>  

 <span data-ttu-id="7a31c-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a31c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a31c-115">**Заголовок:** Изоляция. h</span><span class="sxs-lookup"><span data-stu-id="7a31c-115">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="7a31c-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a31c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a31c-117">См. также</span><span class="sxs-lookup"><span data-stu-id="7a31c-117">See also</span></span>

- [<span data-ttu-id="7a31c-118">Fusion-интерфейсы</span><span class="sxs-lookup"><span data-stu-id="7a31c-118">Fusion Interfaces</span></span>](fusion-interfaces.md)
