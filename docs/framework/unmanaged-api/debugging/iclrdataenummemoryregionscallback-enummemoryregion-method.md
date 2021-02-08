---
description: 'Дополнительные сведения о методе: Иклрдатаенуммеморирегионскаллбакк:: Енуммеморирегион'
title: Метод ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegionsCallback.EnumMemoryRegion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion
helpviewer_keywords:
- EnumMemoryRegion method [.NET Framework debugging]
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion method [.NET Framework debugging]
ms.assetid: 9bb93fab-57e8-4f9a-9ef3-1794504fa896
topic_type:
- apiref
ms.openlocfilehash: 733911f71898ea7019a0b8d854fb1c1bf61a2474
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801401"
---
# <a name="iclrdataenummemoryregionscallbackenummemoryregion-method"></a><span data-ttu-id="89e0a-103">Метод ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion</span><span class="sxs-lookup"><span data-stu-id="89e0a-103">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Method</span></span>

<span data-ttu-id="89e0a-104">Вызывается методом [иклрдатаенуммеморирегионс:: енуммеморирегионс](iclrdataenummemoryregions-enummemoryregions-method.md) для передачи в отладчик результата попытки перечисления указанной области памяти.</span><span class="sxs-lookup"><span data-stu-id="89e0a-104">Called by [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89e0a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="89e0a-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemoryRegion (  
    [in] CLRDATA_ADDRESS  address,  
    [in] ULONG32          size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89e0a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="89e0a-106">Parameters</span></span>  

 `address`  
 <span data-ttu-id="89e0a-107">окне Начальный адрес области памяти, которая должна быть перечислена.</span><span class="sxs-lookup"><span data-stu-id="89e0a-107">[in] The starting address of the memory region that was to be enumerated.</span></span>  
  
 `size`  
 <span data-ttu-id="89e0a-108">окне Размер области памяти в байтах.</span><span class="sxs-lookup"><span data-stu-id="89e0a-108">[in] The size, in bytes, of the memory region.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89e0a-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="89e0a-109">Remarks</span></span>  

 <span data-ttu-id="89e0a-110">`ICLRDataEnumMemoryRegions::EnumMemoryRegions`Метод будет вызывать этот метод обратного вызова после каждой попытки перечисления области памяти.</span><span class="sxs-lookup"><span data-stu-id="89e0a-110">The `ICLRDataEnumMemoryRegions::EnumMemoryRegions` method will call this callback method after each attempt to enumerate a memory region.</span></span> <span data-ttu-id="89e0a-111">Перечисление продолжится, даже если этот метод возвращает значение HRESULT, указывающее на сбой.</span><span class="sxs-lookup"><span data-stu-id="89e0a-111">The enumeration will continue even if this method returns an HRESULT indicating failure.</span></span>  
  
 <span data-ttu-id="89e0a-112">Регионы, сообщаемые этим обратным вызовом, могут быть дубликатами или перекрывающимися областями.</span><span class="sxs-lookup"><span data-stu-id="89e0a-112">Regions reported by this callback may be duplicates or overlapping regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89e0a-113">Требования</span><span class="sxs-lookup"><span data-stu-id="89e0a-113">Requirements</span></span>  

 <span data-ttu-id="89e0a-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89e0a-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89e0a-115">**Заголовок:** Клрдата. idl, Клрдата. h</span><span class="sxs-lookup"><span data-stu-id="89e0a-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="89e0a-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89e0a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89e0a-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89e0a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89e0a-118">См. также</span><span class="sxs-lookup"><span data-stu-id="89e0a-118">See also</span></span>

- [<span data-ttu-id="89e0a-119">Интерфейс ICLRDataEnumMemoryRegionsCallback</span><span class="sxs-lookup"><span data-stu-id="89e0a-119">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](iclrdataenummemoryregionscallback-interface.md)
