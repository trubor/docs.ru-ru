---
description: 'Дополнительные сведения о методе: ICorDebugDataTarget:: ReadVirtual'
title: Метод ICorDebugDataTarget::ReadVirtual
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.ReadVirtual Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::ReadVirtual
helpviewer_keywords:
- ICorDebugDataTarget::ReadVirtual method [.NET Framework debugging]
- ReadVirtual method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: 55e57640-b3d2-413d-b4f4-fbc27fb8e37c
topic_type:
- apiref
ms.openlocfilehash: 4525ba1e5dc685813d963dab96879b886987f38f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710612"
---
# <a name="icordebugdatatargetreadvirtual-method"></a><span data-ttu-id="4d323-103">Метод ICorDebugDataTarget::ReadVirtual</span><span class="sxs-lookup"><span data-stu-id="4d323-103">ICorDebugDataTarget::ReadVirtual Method</span></span>

<span data-ttu-id="4d323-104">Возвращает блок непрерывной памяти, начиная с указанного адреса, и возвращает его в указанном буфере.</span><span class="sxs-lookup"><span data-stu-id="4d323-104">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d323-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4d323-105">Syntax</span></span>  
  
```cpp  
HRESULT ReadVirtual(  
    [in] CORDB_ADDRESS   address,  
    [out, size_is(bytesRequested), length_is(*pBytesRead)]  
          BYTE *     pBuffer,  
    [in]  ULONG32    bytesRequested,  
    [out] ULONG32 *  pBytesRead);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d323-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="4d323-106">Parameters</span></span>  

 `address`  
 <span data-ttu-id="4d323-107">окне Начальный адрес запрошенной памяти.</span><span class="sxs-lookup"><span data-stu-id="4d323-107">[in] The start address of requested memory.</span></span>  
  
 `pbuffer`  
 <span data-ttu-id="4d323-108">заполняет Буфер, в котором будет храниться память.</span><span class="sxs-lookup"><span data-stu-id="4d323-108">[out] The buffer where the memory will be stored.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="4d323-109">окне Число байтов, получаемых с целевого адреса.</span><span class="sxs-lookup"><span data-stu-id="4d323-109">[in] The number of bytes to get from the target address.</span></span>  
  
 `pBytesRead`  
 <span data-ttu-id="4d323-110">заполняет Число байтов, фактически считанных из целевого адреса.</span><span class="sxs-lookup"><span data-stu-id="4d323-110">[out] The number of bytes actually read from the target address.</span></span> <span data-ttu-id="4d323-111">Это может быть меньше `bytesRequested` , чем.</span><span class="sxs-lookup"><span data-stu-id="4d323-111">This can be fewer than `bytesRequested`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d323-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="4d323-112">Remarks</span></span>  

 <span data-ttu-id="4d323-113">Если можно считать первый байт (с указанным начальным адресом), вызов должен вернуть результат (для поддержки эффективного чтения структур данных с самоописывающей длиной, например со строками, завершающимися нулем).</span><span class="sxs-lookup"><span data-stu-id="4d323-113">If the first byte (at the specified start address) can be read, the call should return success (to support efficient reading of data structures with self-describing length, like null-terminated strings).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d323-114">Требования</span><span class="sxs-lookup"><span data-stu-id="4d323-114">Requirements</span></span>  

 <span data-ttu-id="4d323-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d323-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d323-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4d323-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4d323-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d323-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d323-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d323-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d323-119">См. также</span><span class="sxs-lookup"><span data-stu-id="4d323-119">See also</span></span>

- [<span data-ttu-id="4d323-120">Интерфейс ICorDebugDataTarget</span><span class="sxs-lookup"><span data-stu-id="4d323-120">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="4d323-121">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="4d323-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="4d323-122">Отладка</span><span class="sxs-lookup"><span data-stu-id="4d323-122">Debugging</span></span>](index.md)
