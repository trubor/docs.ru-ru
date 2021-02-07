---
description: 'Дополнительные сведения о методе: ICLRDataTarget2:: Аллоквиртуал'
title: Метод ICLRDataTarget2::AllocVirtual
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.AllocVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::AllocVirtual
helpviewer_keywords:
- ICLRDataTarget2::AllocVirtual method [.NET Framework debugging]
- AllocVirtual method [.NET Framework debugging]
ms.assetid: e3226230-964b-47fb-9f53-d6fdbeda1e9e
topic_type:
- apiref
ms.openlocfilehash: d81474e4067599178285b6fa876919298617919d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729345"
---
# <a name="iclrdatatarget2allocvirtual-method"></a><span data-ttu-id="b0431-103">Метод ICLRDataTarget2::AllocVirtual</span><span class="sxs-lookup"><span data-stu-id="b0431-103">ICLRDataTarget2::AllocVirtual Method</span></span>

<span data-ttu-id="b0431-104">Вызывается службами доступа к данным среды CLR для выделения памяти в адресном пространстве этого целевого процесса.</span><span class="sxs-lookup"><span data-stu-id="b0431-104">Called by the common language runtime (CLR) data access services to allocate memory in the address space of this target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0431-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b0431-105">Syntax</span></span>  
  
```cpp  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0431-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0431-106">Parameters</span></span>  

 `addr`  
 <span data-ttu-id="b0431-107">окне `CLRDATA_ADDRESS` Значение типа, указывающее запрошенный начальный адрес выделяемой памяти.</span><span class="sxs-lookup"><span data-stu-id="b0431-107">[in] A `CLRDATA_ADDRESS` value that specifies the requested starting address of the memory to be allocated.</span></span>  
  
 `size`  
 <span data-ttu-id="b0431-108">окне Размер выделяемой памяти в байтах.</span><span class="sxs-lookup"><span data-stu-id="b0431-108">[in] The size, in bytes, of the memory to be allocated.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="b0431-109">окне Флаги, управляющие выделением памяти.</span><span class="sxs-lookup"><span data-stu-id="b0431-109">[in] Flags that control the allocation of memory.</span></span> <span data-ttu-id="b0431-110">См. раздел `VirtualAlloc` функция Win32.</span><span class="sxs-lookup"><span data-stu-id="b0431-110">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `protectFlags`  
 <span data-ttu-id="b0431-111">окне Атрибуты защиты для выделенной памяти.</span><span class="sxs-lookup"><span data-stu-id="b0431-111">[in] The protection attributes for the allocated memory.</span></span> <span data-ttu-id="b0431-112">См. раздел `VirtualAlloc` функция Win32.</span><span class="sxs-lookup"><span data-stu-id="b0431-112">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `virt`  
 <span data-ttu-id="b0431-113">заполняет Указатель на `CLRDATA_ADDRESS` значение, указывающее фактический начальный адрес выделенной памяти.</span><span class="sxs-lookup"><span data-stu-id="b0431-113">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the actual starting address of the allocated memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0431-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="b0431-114">Remarks</span></span>  

 <span data-ttu-id="b0431-115">`AllocVirtual`Метод служит логической оболочкой для `VirtualAlloc` функции Win32.</span><span class="sxs-lookup"><span data-stu-id="b0431-115">The `AllocVirtual` method serves as a logical wrapper for the Win32 `VirtualAlloc` function.</span></span>  
  
 <span data-ttu-id="b0431-116">Этот метод реализуется модулем записи отладчика.</span><span class="sxs-lookup"><span data-stu-id="b0431-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0431-117">Требования</span><span class="sxs-lookup"><span data-stu-id="b0431-117">Requirements</span></span>  

 <span data-ttu-id="b0431-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0431-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0431-119">**Заголовок:** Клрдата. idl, Клрдата. h</span><span class="sxs-lookup"><span data-stu-id="b0431-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="b0431-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0431-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0431-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0431-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0431-122">См. также</span><span class="sxs-lookup"><span data-stu-id="b0431-122">See also</span></span>

- [<span data-ttu-id="b0431-123">Интерфейс ICLRDataTarget2</span><span class="sxs-lookup"><span data-stu-id="b0431-123">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="b0431-124">Метод FreeVirtual</span><span class="sxs-lookup"><span data-stu-id="b0431-124">FreeVirtual Method</span></span>](iclrdatatarget2-freevirtual-method.md)
