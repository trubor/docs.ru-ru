---
description: Дополнительные сведения о перечислении Кореррорифемитаутофордер
title: Перечисление CorErrorIfEmitOutOfOrder
ms.date: 03/30/2017
api_name:
- CorErrorIfEmitOutOfOrder
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorErrorIfEmitOutOfOrder
helpviewer_keywords:
- CorErrorIfEmitOutOfOrder enumeration [.NET Framework metadata]
ms.assetid: 6d758aad-29a7-44fe-9481-bbff5b799a32
topic_type:
- apiref
ms.openlocfilehash: b45d3204ae386b7ad9d7ab1daccdfdef35e2ad9e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784530"
---
# <a name="corerrorifemitoutoforder-enumeration"></a><span data-ttu-id="f63e5-103">Перечисление CorErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="f63e5-103">CorErrorIfEmitOutOfOrder Enumeration</span></span>

<span data-ttu-id="f63e5-104">Содержит значения флагов, указывающие условия, при которых должно создаваться сообщение об ошибке при беспорядочном выводе метаданных.</span><span class="sxs-lookup"><span data-stu-id="f63e5-104">Contains flag values that indicate the conditions under which an error message should be generated when metadata is emitted out of order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f63e5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f63e5-105">Syntax</span></span>  
  
```cpp  
typedef enum CorErrorIfEmitOutOfOrder {  
  
    MDErrorOutOfOrderDefault    = 0x00000000,  
    MDErrorOutOfOrderNone       = 0x00000000,  
    MDErrorOutOfOrderAll        = 0xffffffff,  
    MDMethodOutOfOrder          = 0x00000001,  
    MDFieldOutOfOrder           = 0x00000002,  
    MDParamOutOfOrder           = 0x00000004,  
    MDPropertyOutOfOrder        = 0x00000008,  
    MDEventOutOfOrder           = 0x00000010  
  
} CorErrorIfEmitOutOfOrder;  
```  
  
## <a name="members"></a><span data-ttu-id="f63e5-106">Члены</span><span class="sxs-lookup"><span data-stu-id="f63e5-106">Members</span></span>  
  
|<span data-ttu-id="f63e5-107">Член</span><span class="sxs-lookup"><span data-stu-id="f63e5-107">Member</span></span>|<span data-ttu-id="f63e5-108">Описание</span><span class="sxs-lookup"><span data-stu-id="f63e5-108">Description</span></span>|  
|------------|-----------------|  
|`MDErrorOutOfOrderDefault`|<span data-ttu-id="f63e5-109">Указывает поведение по умолчанию, при котором не создаются сообщения об ошибках.</span><span class="sxs-lookup"><span data-stu-id="f63e5-109">Indicates the default behavior, which does not generate error messages.</span></span>|  
|`MDErrorOutOfOrderNone`|<span data-ttu-id="f63e5-110">Указывает, что компилятор не должен создавать сообщения об ошибках.</span><span class="sxs-lookup"><span data-stu-id="f63e5-110">Indicates that the compiler should not generate error messages.</span></span>|  
|`MDErrorOutOfOrderAll`|<span data-ttu-id="f63e5-111">Указывает, что компилятор должен создать сообщение об ошибке, когда поле, свойство, событие, метод или параметр выдаются в неопределенном порядке.</span><span class="sxs-lookup"><span data-stu-id="f63e5-111">Indicates that the compiler should generate an error message when a field, property, event, method, or parameter is emitted out of order.</span></span>|  
|`MDMethodOutOfOrder`|<span data-ttu-id="f63e5-112">Указывает, что компилятор должен создать сообщение об ошибке, если метод выдается не по порядку.</span><span class="sxs-lookup"><span data-stu-id="f63e5-112">Indicates that the compiler should generate an error message when a method is emitted out of order.</span></span>|  
|`MDFieldOutOfOrder`|<span data-ttu-id="f63e5-113">Указывает, что компилятор должен создать сообщение об ошибке, если поле выдается не по порядку.</span><span class="sxs-lookup"><span data-stu-id="f63e5-113">Indicates that the compiler should generate an error message when a field is emitted out of order.</span></span>|  
|`MDParamOutOfOrder`|<span data-ttu-id="f63e5-114">Указывает, что компилятор должен создать сообщение об ошибке, если параметр выдается не по порядку.</span><span class="sxs-lookup"><span data-stu-id="f63e5-114">Indicates that the compiler should generate an error message when a parameter is emitted out of order.</span></span>|  
|`MDPropertyOutOfOrder`|<span data-ttu-id="f63e5-115">Указывает, что компилятор должен создать сообщение об ошибке, если свойство выдается не по порядку.</span><span class="sxs-lookup"><span data-stu-id="f63e5-115">Indicates that the compiler should generate an error message when a property is emitted out of order.</span></span>|  
|`MDEventOutOfOrder`|<span data-ttu-id="f63e5-116">Указывает, что компилятор должен создать сообщение об ошибке, если событие выдается не по порядку.</span><span class="sxs-lookup"><span data-stu-id="f63e5-116">Indicates that the compiler should generate an error message when an event is emitted out of order.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f63e5-117">Требования</span><span class="sxs-lookup"><span data-stu-id="f63e5-117">Requirements</span></span>  

 <span data-ttu-id="f63e5-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f63e5-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f63e5-119">**Заголовок:** Корхдр. h</span><span class="sxs-lookup"><span data-stu-id="f63e5-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="f63e5-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f63e5-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f63e5-121">См. также</span><span class="sxs-lookup"><span data-stu-id="f63e5-121">See also</span></span>

- [<span data-ttu-id="f63e5-122">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="f63e5-122">Metadata Enumerations</span></span>](metadata-enumerations.md)
