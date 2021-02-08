---
description: 'Дополнительные сведения о методе: Иклрдатаенуммеморирегионс:: Енуммеморирегионс'
title: Метод ICLRDataEnumMemoryRegions::EnumMemoryRegions
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegions.EnumMemoryRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions
helpviewer_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions method [.NET Framework debugging]
- EnumMemoryRegions method [.NET Framework debugging]
ms.assetid: 22d2e339-f174-40b5-a478-0b744501566f
topic_type:
- apiref
ms.openlocfilehash: 48887defab38d6ac99c718e14646d39166927438
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785735"
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a><span data-ttu-id="f6da1-103">Метод ICLRDataEnumMemoryRegions::EnumMemoryRegions</span><span class="sxs-lookup"><span data-stu-id="f6da1-103">ICLRDataEnumMemoryRegions::EnumMemoryRegions Method</span></span>

<span data-ttu-id="f6da1-104">Перечисляет указанные области памяти.</span><span class="sxs-lookup"><span data-stu-id="f6da1-104">Enumerates specified areas of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6da1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f6da1-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6da1-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f6da1-106">Parameters</span></span>  

 `callback`  
 <span data-ttu-id="f6da1-107">окне Указатель на экземпляр [иклрдатаенуммеморирегионскаллбакк](iclrdataenummemoryregionscallback-interface.md) , вызываемый этим методом для каждой области памяти, перечисленной для уведомления отладчика о результатах.</span><span class="sxs-lookup"><span data-stu-id="f6da1-107">[in] A pointer to an [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) instance that is called by this method for each memory region being enumerated to notify the debugger of the result.</span></span>  
  
 <span data-ttu-id="f6da1-108">Перечисление областей памяти продолжится, даже если обратный вызов указывает на сбой.</span><span class="sxs-lookup"><span data-stu-id="f6da1-108">The enumeration of memory regions continues even if the callback indicates a failure.</span></span>  
  
 `miniDumpFlags`  
 <span data-ttu-id="f6da1-109">[in] Не используется.</span><span class="sxs-lookup"><span data-stu-id="f6da1-109">[in] Not used.</span></span>  
  
 `clrFlags`  
 <span data-ttu-id="f6da1-110">окне Значение перечисления [CLRDataEnumMemoryFlags](clrdataenummemoryflags-enumeration.md) , указывающее области памяти для перечисления.</span><span class="sxs-lookup"><span data-stu-id="f6da1-110">[in] A value of the [CLRDataEnumMemoryFlags](clrdataenummemoryflags-enumeration.md) enumeration that specifies the regions of memory to be enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6da1-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="f6da1-111">Remarks</span></span>  

 <span data-ttu-id="f6da1-112">Этот метод использует указанный экземпляр [иклрдатаенуммеморирегионскаллбакк](iclrdataenummemoryregionscallback-interface.md) для уведомления вызывающего объекта о результатах.</span><span class="sxs-lookup"><span data-stu-id="f6da1-112">This method uses the specified [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) instance to notify the caller of results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6da1-113">Требования</span><span class="sxs-lookup"><span data-stu-id="f6da1-113">Requirements</span></span>  

 <span data-ttu-id="f6da1-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6da1-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6da1-115">**Заголовок:** Клрдата. idl, Клрдата. h</span><span class="sxs-lookup"><span data-stu-id="f6da1-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="f6da1-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6da1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6da1-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6da1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6da1-118">См. также</span><span class="sxs-lookup"><span data-stu-id="f6da1-118">See also</span></span>

- [<span data-ttu-id="f6da1-119">Интерфейс ICLRDataEnumMemoryRegions</span><span class="sxs-lookup"><span data-stu-id="f6da1-119">ICLRDataEnumMemoryRegions Interface</span></span>](iclrdataenummemoryregions-interface.md)
