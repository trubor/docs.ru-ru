---
description: 'Дополнительные сведения о методе: ICLRDataTarget:: Жетмачинетипе'
title: Метод ICLRDataTarget::GetMachineType
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetMachineType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetMachineType
helpviewer_keywords:
- ICLRDataTarget::GetMachineType method [.NET Framework debugging]
- GetMachineType method [.NET Framework debugging]
ms.assetid: 5f1f9c61-3e3b-48b2-b111-a4395f7623a7
topic_type:
- apiref
ms.openlocfilehash: 5624f734a77f51b4ea6cd9dd0c9df393c72e7d26
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801349"
---
# <a name="iclrdatatargetgetmachinetype-method"></a><span data-ttu-id="d3957-103">Метод ICLRDataTarget::GetMachineType</span><span class="sxs-lookup"><span data-stu-id="d3957-103">ICLRDataTarget::GetMachineType Method</span></span>

<span data-ttu-id="d3957-104">Возвращает идентификатор для типа набора инструкций, используемого целевым процессом.</span><span class="sxs-lookup"><span data-stu-id="d3957-104">Gets the identifier for the kind of instruction set that the target process is using.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3957-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d3957-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMachineType (  
    [out] ULONG32     *machineType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3957-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d3957-106">Parameters</span></span>  

 `machineType`  
 <span data-ttu-id="d3957-107">заполняет Указатель на значение, указывающее набор инструкций, который используется целевым процессом.</span><span class="sxs-lookup"><span data-stu-id="d3957-107">[out] A pointer to a value that indicates the instruction set that the target process is using.</span></span> <span data-ttu-id="d3957-108">Возвращаемое значение `machineType` является одной из IMAGE_FILE_MACHINE констант, которые определены в файле заголовка WinNT. h.</span><span class="sxs-lookup"><span data-stu-id="d3957-108">The returned `machineType` is one of the IMAGE_FILE_MACHINE constants, which are defined in the WinNT.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3957-109">Требования</span><span class="sxs-lookup"><span data-stu-id="d3957-109">Requirements</span></span>  

 <span data-ttu-id="d3957-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3957-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3957-111">**Заголовок:** Клрдата. idl, Клрдата. h</span><span class="sxs-lookup"><span data-stu-id="d3957-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="d3957-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3957-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3957-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3957-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3957-114">См. также</span><span class="sxs-lookup"><span data-stu-id="d3957-114">See also</span></span>

- [<span data-ttu-id="d3957-115">Интерфейс ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="d3957-115">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
