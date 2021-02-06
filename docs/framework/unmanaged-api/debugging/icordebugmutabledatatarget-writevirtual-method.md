---
description: 'Дополнительные сведения о методе: Икордебугмутабледататаржет:: WriteVirtual'
title: Метод ICorDebugMutableDataTarget::WriteVirtual
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
ms.openlocfilehash: 3f3400456b7af51f4b24d7e14e35d641f03a8bfd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637824"
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a><span data-ttu-id="c2fba-103">Метод ICorDebugMutableDataTarget::WriteVirtual</span><span class="sxs-lookup"><span data-stu-id="c2fba-103">ICorDebugMutableDataTarget::WriteVirtual Method</span></span>

<span data-ttu-id="c2fba-104">Записывает память в адресное пространство целевого процесса.</span><span class="sxs-lookup"><span data-stu-id="c2fba-104">Writes memory into the target process address space.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2fba-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c2fba-105">Syntax</span></span>  
  
```cpp  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2fba-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c2fba-106">Parameters</span></span>  

 `address`  
 <span data-ttu-id="c2fba-107">[in] Адрес для записи содержимого `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="c2fba-107">[in] The address at which to write the contents of `pBuffer`.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="c2fba-108">[в] Указатель на массив байтов, содержащий байты для записи.</span><span class="sxs-lookup"><span data-stu-id="c2fba-108">[in] A pointer to a byte array that contains the bytes to be written.</span></span>  
  
 `address`  
 <span data-ttu-id="c2fba-109">[in] Количество байтов в `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="c2fba-109">[in] The number of bytes in `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2fba-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="c2fba-110">Return Value</span></span>  

 <span data-ttu-id="c2fba-111">Значение `S_OK` при успешном выполнении или любое другое значение `HRESULT` в случае сбоя.</span><span class="sxs-lookup"><span data-stu-id="c2fba-111">`S_OK` on success, or any other `HRESULT` on failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2fba-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="c2fba-112">Remarks</span></span>  

 <span data-ttu-id="c2fba-113">Если не удается записать все байты, вызов метода завершается ошибкой без изменения каких-либо байтов в целевом адресном пространстве.</span><span class="sxs-lookup"><span data-stu-id="c2fba-113">If any bytes cannot be written, the method call fails without changing any bytes in the target address space.</span></span> <span data-ttu-id="c2fba-114">(В противном случае целевое адресное пространство оказалось бы в несогласованном состоянии, что сделало бы ненадежной дальнейшую отладку.)</span><span class="sxs-lookup"><span data-stu-id="c2fba-114">(Otherwise, the target would be in an inconsistent state that makes further debugging unreliable.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2fba-115">Требования</span><span class="sxs-lookup"><span data-stu-id="c2fba-115">Requirements</span></span>  

 <span data-ttu-id="c2fba-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2fba-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2fba-117">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c2fba-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2fba-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2fba-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2fba-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2fba-119">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2fba-120">См. также</span><span class="sxs-lookup"><span data-stu-id="c2fba-120">See also</span></span>

- [<span data-ttu-id="c2fba-121">Интерфейс ICorDebugMutableDataTarget</span><span class="sxs-lookup"><span data-stu-id="c2fba-121">ICorDebugMutableDataTarget Interface</span></span>](icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="c2fba-122">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="c2fba-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
