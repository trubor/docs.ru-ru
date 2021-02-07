---
description: 'Дополнительные сведения о: структура Кустомдумпитем'
title: Структура CustomDumpItem
ms.date: 03/30/2017
api_name:
- CustomDumpItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CustomDumpItem
helpviewer_keywords:
- CustomDumpItem structure [.NET Framework hosting]
ms.assetid: fd9085ff-7beb-4c38-97f0-037cd8ba4f65
topic_type:
- apiref
ms.openlocfilehash: 9bd7b2bb59675bc01e24dc6e6d0ce524f3d35466
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716904"
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="54920-103">Структура CustomDumpItem</span><span class="sxs-lookup"><span data-stu-id="54920-103">CustomDumpItem Structure</span></span>

<span data-ttu-id="54920-104">Описывает элемент, добавляемый в пользовательский дамп в отчетах об ошибках.</span><span class="sxs-lookup"><span data-stu-id="54920-104">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54920-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="54920-105">Syntax</span></span>  
  
```cpp  
struct {  
    ECustomDumpItemKind itemKind;
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="54920-106">Члены</span><span class="sxs-lookup"><span data-stu-id="54920-106">Members</span></span>  
  
|<span data-ttu-id="54920-107">Член</span><span class="sxs-lookup"><span data-stu-id="54920-107">Member</span></span>|<span data-ttu-id="54920-108">Описание</span><span class="sxs-lookup"><span data-stu-id="54920-108">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="54920-109">Значение [екустомдумпитемкинд](ecustomdumpitemkind-enumeration.md) , указывающее тип добавляемого элемента.</span><span class="sxs-lookup"><span data-stu-id="54920-109">An [ECustomDumpItemKind](ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="54920-110">В настоящий момент не используется.</span><span class="sxs-lookup"><span data-stu-id="54920-110">Not currently used.</span></span> <span data-ttu-id="54920-111">Все элементы, добавляемые в объединение, не должны быть больше размера указателя.</span><span class="sxs-lookup"><span data-stu-id="54920-111">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="54920-112">Если `struct` требуется, необходимо выделить его отдельно и указать на него.</span><span class="sxs-lookup"><span data-stu-id="54920-112">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54920-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="54920-113">Remarks</span></span>  

 <span data-ttu-id="54920-114">[Iclrerrorreportingmanagergetbucketparametersforcurrentexception:: BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) принимает параметр типа `CustomDumpItem` .</span><span class="sxs-lookup"><span data-stu-id="54920-114">[ICLRErrorReportingManager::BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54920-115">Требования</span><span class="sxs-lookup"><span data-stu-id="54920-115">Requirements</span></span>  

 <span data-ttu-id="54920-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54920-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54920-117">**Заголовок:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="54920-117">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="54920-118">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="54920-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="54920-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54920-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54920-120">См. также</span><span class="sxs-lookup"><span data-stu-id="54920-120">See also</span></span>

- [<span data-ttu-id="54920-121">Структуры размещения</span><span class="sxs-lookup"><span data-stu-id="54920-121">Hosting Structures</span></span>](hosting-structures.md)
