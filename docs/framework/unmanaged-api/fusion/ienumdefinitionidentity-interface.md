---
description: 'Дополнительные сведения о: интерфейс Иенумдефинитионидентити'
title: Интерфейс IEnumDefinitionIdentity
ms.date: 03/30/2017
api_name:
- IEnumDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumDefinitionIdentity
helpviewer_keywords:
- IEnumDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: 8263e75d-251b-4abc-8a1a-c62884142232
topic_type:
- apiref
ms.openlocfilehash: 1055031c064115410334bbe4b20b48deee7ec4c4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800166"
---
# <a name="ienumdefinitionidentity-interface"></a><span data-ttu-id="7d3e0-103">Интерфейс IEnumDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="7d3e0-103">IEnumDefinitionIdentity Interface</span></span>

<span data-ttu-id="7d3e0-104">Служит в качестве перечислителя для коллекции `IDefinitionIdentity` объектов.</span><span class="sxs-lookup"><span data-stu-id="7d3e0-104">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d3e0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7d3e0-105">Syntax</span></span>  
  
```cpp  
IEnumDefinitionIdentity : IUnknown {  
  
    HRESULT Clone (  
        [out] IEnumDefinitionIdentity **ppIEnumDefinitionIdentity  
    );  
  
    HRESULT Next (  
        [in]  ULONG               celt,  
        [out, length_is(celt), size_is(*pceltWritten)]  
              IDefinitionIdentity *rgpIDefinitionIdentity[],  
        [out] ULONG               *pceltWritten  
    );  
  
    HRESULT Reset ();  
  
    HRESULT Skip (  
        [in] ULONG celt  
    );  
  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7d3e0-106">Методы</span><span class="sxs-lookup"><span data-stu-id="7d3e0-106">Methods</span></span>  
  
|<span data-ttu-id="7d3e0-107">Метод</span><span class="sxs-lookup"><span data-stu-id="7d3e0-107">Method</span></span>|<span data-ttu-id="7d3e0-108">Описание</span><span class="sxs-lookup"><span data-stu-id="7d3e0-108">Description</span></span>|  
|------------|-----------------|  
|`IEnumDefinitionIdentity::Clone`|<span data-ttu-id="7d3e0-109">Возвращает указатель интерфейса на новый `IEnumDefinitionIdentity` объект, содержащий те же элементы, что и этот `IEnumDefinitionIdentity` .</span><span class="sxs-lookup"><span data-stu-id="7d3e0-109">Gets an interface pointer to a new `IEnumDefinitionIdentity` object that contains the same members as this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Next`|<span data-ttu-id="7d3e0-110">Возвращает указанное число `IDefinitionIdentity` объектов, начиная с текущей позиции.</span><span class="sxs-lookup"><span data-stu-id="7d3e0-110">Gets the specified number of `IDefinitionIdentity` objects, starting at the current position.</span></span>|  
|`IEnumDefinitionIdentity::Reset`|<span data-ttu-id="7d3e0-111">Перемещает указатель инструкций в начало `IEnumDefinitionIdentity` .</span><span class="sxs-lookup"><span data-stu-id="7d3e0-111">Moves the instruction pointer to the beginning of this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Skip`|<span data-ttu-id="7d3e0-112">Перемещает указатель инструкции вперед на указанное число элементов, начиная с текущей позиции.</span><span class="sxs-lookup"><span data-stu-id="7d3e0-112">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7d3e0-113">Требования</span><span class="sxs-lookup"><span data-stu-id="7d3e0-113">Requirements</span></span>  

 <span data-ttu-id="7d3e0-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d3e0-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d3e0-115">**Заголовок:** Изоляция. h</span><span class="sxs-lookup"><span data-stu-id="7d3e0-115">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="7d3e0-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d3e0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d3e0-117">См. также</span><span class="sxs-lookup"><span data-stu-id="7d3e0-117">See also</span></span>

- [<span data-ttu-id="7d3e0-118">Fusion-интерфейсы</span><span class="sxs-lookup"><span data-stu-id="7d3e0-118">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="7d3e0-119">Интерфейс IDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="7d3e0-119">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)
