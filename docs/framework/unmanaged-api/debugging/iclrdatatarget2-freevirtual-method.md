---
description: 'Дополнительные сведения о методе: ICLRDataTarget2:: Фривиртуал'
title: Метод ICLRDataTarget2::FreeVirtual
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.FreeVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::FreeVirtual
helpviewer_keywords:
- ICLRDataTarget::FreeVirtual method [.NET Framework debugging]
- FreeVirtual method [.NET Framework debugging]
ms.assetid: 26fb69f8-1467-4711-bd24-cb117c63938f
topic_type:
- apiref
ms.openlocfilehash: ef4048f421fcdc7d284663036f8cc9f2614f4e13
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729254"
---
# <a name="iclrdatatarget2freevirtual-method"></a><span data-ttu-id="c8224-103">Метод ICLRDataTarget2::FreeVirtual</span><span class="sxs-lookup"><span data-stu-id="c8224-103">ICLRDataTarget2::FreeVirtual Method</span></span>

<span data-ttu-id="c8224-104">Вызывается службами доступа к данным среды CLR для освобождения памяти, которая была ранее выделена в адресном пространстве целевого процесса.</span><span class="sxs-lookup"><span data-stu-id="c8224-104">Called by the common language runtime (CLR) data access services to free memory that was previously allocated in the address space of the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8224-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c8224-105">Syntax</span></span>  
  
```cpp  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8224-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c8224-106">Parameters</span></span>  

 `addr`  
 <span data-ttu-id="c8224-107">окне `CLRDATA_ADDRESS` Значение, указывающее начальный адрес памяти для высвобождения.</span><span class="sxs-lookup"><span data-stu-id="c8224-107">[in] A `CLRDATA_ADDRESS` value that specifies the starting address of the memory to be freed.</span></span>  
  
 `size`  
 <span data-ttu-id="c8224-108">окне Размер (в байтах) памяти, которая должна быть освобождена.</span><span class="sxs-lookup"><span data-stu-id="c8224-108">[in] The size, in bytes, of the memory to be freed.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="c8224-109">окне Флаги, управляющие освобождением памяти.</span><span class="sxs-lookup"><span data-stu-id="c8224-109">[in] Flags that control the freeing of memory.</span></span> <span data-ttu-id="c8224-110">См. раздел `VirtualFree` функция Win32.</span><span class="sxs-lookup"><span data-stu-id="c8224-110">See the Win32 `VirtualFree` function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8224-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="c8224-111">Remarks</span></span>  

 <span data-ttu-id="c8224-112">`FreeVirtual`Метод служит логической оболочкой для `VirtualFree` функции Win32.</span><span class="sxs-lookup"><span data-stu-id="c8224-112">The `FreeVirtual` method serves as a logical wrapper for the Win32 `VirtualFree` function.</span></span>  
  
 <span data-ttu-id="c8224-113">Этот метод реализуется модулем записи отладчика.</span><span class="sxs-lookup"><span data-stu-id="c8224-113">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8224-114">Требования</span><span class="sxs-lookup"><span data-stu-id="c8224-114">Requirements</span></span>  

 <span data-ttu-id="c8224-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8224-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8224-116">**Заголовок:** Клрдата. idl, Клрдата. h</span><span class="sxs-lookup"><span data-stu-id="c8224-116">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="c8224-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8224-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8224-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8224-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8224-119">См. также</span><span class="sxs-lookup"><span data-stu-id="c8224-119">See also</span></span>

- [<span data-ttu-id="c8224-120">Интерфейс ICLRDataTarget2</span><span class="sxs-lookup"><span data-stu-id="c8224-120">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="c8224-121">Метод AllocVirtual</span><span class="sxs-lookup"><span data-stu-id="c8224-121">AllocVirtual Method</span></span>](iclrdatatarget2-allocvirtual-method.md)
