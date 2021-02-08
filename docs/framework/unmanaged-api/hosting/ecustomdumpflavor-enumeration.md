---
description: Дополнительные сведения о перечислении Екустомдумпфлавор
title: Перечисление ECustomDumpFlavor
ms.date: 03/30/2017
api_name:
- ECustomDumpFlavor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ECustomDumpFlavor
helpviewer_keywords:
- ECustomDumpFlavor enumeration [.NET Framework hosting]
ms.assetid: b39b3320-fac7-41f1-9a03-ab6fb0cd89c7
topic_type:
- apiref
ms.openlocfilehash: 3ef118368fc827472bdaacb0b03d8c2011275056
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785536"
---
# <a name="ecustomdumpflavor-enumeration"></a><span data-ttu-id="cf6f0-103">Перечисление ECustomDumpFlavor</span><span class="sxs-lookup"><span data-stu-id="cf6f0-103">ECustomDumpFlavor Enumeration</span></span>

<span data-ttu-id="cf6f0-104">Содержит значения, указывающие, какие элементы следует включать в пользовательское подмножество дампа кучи при сообщении об ошибках.</span><span class="sxs-lookup"><span data-stu-id="cf6f0-104">Contains values that indicate which items to include in a custom subset of a heap dump when reporting errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf6f0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cf6f0-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a><span data-ttu-id="cf6f0-106">Члены</span><span class="sxs-lookup"><span data-stu-id="cf6f0-106">Members</span></span>  
  
|<span data-ttu-id="cf6f0-107">Член</span><span class="sxs-lookup"><span data-stu-id="cf6f0-107">Member</span></span>|<span data-ttu-id="cf6f0-108">Описание</span><span class="sxs-lookup"><span data-stu-id="cf6f0-108">Description</span></span>|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|<span data-ttu-id="cf6f0-109">Указывает, что дамп пользовательской кучи должен запускаться как Малый дамп и включать дополнительные данные, указанные любыми экземплярами [кустомдумпитем](customdumpitem-structure.md) , передаваемыми в один и тот же метод.</span><span class="sxs-lookup"><span data-stu-id="cf6f0-109">Specifies that the custom heap dump should start as a minidump and include extra data specified by any [CustomDumpItem](customdumpitem-structure.md) instances passed to the same method.</span></span>|  
|`DUMP_FLAVOR_NonHeapCLRState`|<span data-ttu-id="cf6f0-110">Указывает, что дамп пользовательской кучи должен собирать все данные состояния времени выполнения, которые не были выделены динамически.</span><span class="sxs-lookup"><span data-stu-id="cf6f0-110">Specifies that the custom heap dump should gather all run-time state data that was not dynamically allocated.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf6f0-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="cf6f0-111">Remarks</span></span>  

 <span data-ttu-id="cf6f0-112">Параметр типа `ECustomDumpFlavor` передается методу [iclrerrorreportingmanagergetbucketparametersforcurrentexception:: BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) .</span><span class="sxs-lookup"><span data-stu-id="cf6f0-112">A parameter of type `ECustomDumpFlavor` is passed to the [ICLRErrorReportingManager::BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf6f0-113">Требования</span><span class="sxs-lookup"><span data-stu-id="cf6f0-113">Requirements</span></span>  

 <span data-ttu-id="cf6f0-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf6f0-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf6f0-115">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cf6f0-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cf6f0-116">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cf6f0-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf6f0-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf6f0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf6f0-118">См. также</span><span class="sxs-lookup"><span data-stu-id="cf6f0-118">See also</span></span>

- [<span data-ttu-id="cf6f0-119">Перечисление ECustomDumpItemKind</span><span class="sxs-lookup"><span data-stu-id="cf6f0-119">ECustomDumpItemKind Enumeration</span></span>](ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="cf6f0-120">Интерфейс ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="cf6f0-120">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="cf6f0-121">Размещение перечислений</span><span class="sxs-lookup"><span data-stu-id="cf6f0-121">Hosting Enumerations</span></span>](hosting-enumerations.md)
