---
description: 'Дополнительные сведения о: интерфейс Иклрдатаенуммеморирегионскаллбакк'
title: Интерфейс ICLRDataEnumMemoryRegionsCallback
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegionsCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegionsCallback
helpviewer_keywords:
- ICLRDataEnumMemoryRegionsCallback interface [.NET Framework debugging]
ms.assetid: 3f1af8b0-8478-48e0-a7ec-3e90e0b97649
topic_type:
- apiref
ms.openlocfilehash: 863192844c4d4d8a35d1e73d38adea3a513bc944
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801375"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a><span data-ttu-id="6a7e3-103">Интерфейс ICLRDataEnumMemoryRegionsCallback</span><span class="sxs-lookup"><span data-stu-id="6a7e3-103">ICLRDataEnumMemoryRegionsCallback Interface</span></span>

<span data-ttu-id="6a7e3-104">Предоставляет метод обратного вызова для [иклрдатаенуммеморирегионс:: енуммеморирегионс](iclrdataenummemoryregions-enummemoryregions-method.md) , сообщающий отладчику результат попытки перечисления заданной области памяти.</span><span class="sxs-lookup"><span data-stu-id="6a7e3-104">Provides a callback method for [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6a7e3-105">Методы</span><span class="sxs-lookup"><span data-stu-id="6a7e3-105">Methods</span></span>  
  
|<span data-ttu-id="6a7e3-106">Метод</span><span class="sxs-lookup"><span data-stu-id="6a7e3-106">Method</span></span>|<span data-ttu-id="6a7e3-107">Описание</span><span class="sxs-lookup"><span data-stu-id="6a7e3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6a7e3-108">Метод EnumMemoryRegion</span><span class="sxs-lookup"><span data-stu-id="6a7e3-108">EnumMemoryRegion Method</span></span>](iclrdataenummemoryregionscallback-enummemoryregion-method.md)|<span data-ttu-id="6a7e3-109">Вызывается с помощью `ICLRDataEnumMemoryRegions::EnumMemoryRegions` для передачи в отладчик результата попытки перечисления заданной области памяти.</span><span class="sxs-lookup"><span data-stu-id="6a7e3-109">Called by `ICLRDataEnumMemoryRegions::EnumMemoryRegions` to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6a7e3-110">Требования</span><span class="sxs-lookup"><span data-stu-id="6a7e3-110">Requirements</span></span>  

 <span data-ttu-id="6a7e3-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a7e3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a7e3-112">**Заголовок:** Клрдата. idl, Клрдата. h</span><span class="sxs-lookup"><span data-stu-id="6a7e3-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="6a7e3-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a7e3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a7e3-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a7e3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a7e3-115">См. также</span><span class="sxs-lookup"><span data-stu-id="6a7e3-115">See also</span></span>

- [<span data-ttu-id="6a7e3-116">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="6a7e3-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
