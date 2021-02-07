---
description: 'Дополнительные сведения о методе: ICLRDataTarget:: ReadVirtual'
title: Метод ICLRDataTarget::ReadVirtual
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.ReadVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::ReadVirtual
helpviewer_keywords:
- ReadVirtual method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::ReadVirtual method [.NET Framework debugging]
ms.assetid: da3769eb-1828-4aa1-b9ed-db4842136a43
topic_type:
- apiref
ms.openlocfilehash: 740a89c95092cfad7974d6bc708c5d8b0d2a9172
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738212"
---
# <a name="iclrdatatargetreadvirtual-method"></a><span data-ttu-id="a98b9-103">Метод ICLRDataTarget::ReadVirtual</span><span class="sxs-lookup"><span data-stu-id="a98b9-103">ICLRDataTarget::ReadVirtual Method</span></span>

<span data-ttu-id="a98b9-104">Считывает данные из указанного адреса виртуальной памяти в указанный буфер.</span><span class="sxs-lookup"><span data-stu-id="a98b9-104">Reads data from the specified virtual memory address into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a98b9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a98b9-105">Syntax</span></span>  
  
```cpp  
HRESULT ReadVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [out, size_is(bytesRequested), length_is(*bytesRead)]
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a98b9-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a98b9-106">Parameters</span></span>  

 `address`  
 <span data-ttu-id="a98b9-107">окне CLRDATA_ADDRESS, в которой хранится адрес виртуальной памяти.</span><span class="sxs-lookup"><span data-stu-id="a98b9-107">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="a98b9-108">заполняет Указатель на буфер, который получает данные.</span><span class="sxs-lookup"><span data-stu-id="a98b9-108">[out] A pointer to a buffer that receives the data.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="a98b9-109">окне Длина буфера.</span><span class="sxs-lookup"><span data-stu-id="a98b9-109">[in] The length of the buffer.</span></span>  
  
 `bytesRead`  
 <span data-ttu-id="a98b9-110">заполняет Указатель на число возвращаемых байтов.</span><span class="sxs-lookup"><span data-stu-id="a98b9-110">[out] A pointer to the number of bytes returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a98b9-111">Требования</span><span class="sxs-lookup"><span data-stu-id="a98b9-111">Requirements</span></span>  

 <span data-ttu-id="a98b9-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a98b9-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a98b9-113">**Заголовок:** Клрдата. idl, Клрдата. h</span><span class="sxs-lookup"><span data-stu-id="a98b9-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="a98b9-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a98b9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a98b9-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a98b9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a98b9-116">См. также</span><span class="sxs-lookup"><span data-stu-id="a98b9-116">See also</span></span>

- [<span data-ttu-id="a98b9-117">Интерфейс ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="a98b9-117">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
