---
description: См. Дополнительные сведения о методе ICorDebugRegisterSet2::, регистрирующих
title: Метод ICorDebugRegisterSet2::GetRegisters
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegisters method [.NET Framework debugging]
ms.assetid: dbc498a8-ba3f-42f2-bdd9-b623c77a1019
topic_type:
- apiref
ms.openlocfilehash: 58af939b0e88185e2be23b69ca70d28e93ff873f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794797"
---
# <a name="icordebugregisterset2getregisters-method"></a><span data-ttu-id="af190-103">Метод ICorDebugRegisterSet2::</span><span class="sxs-lookup"><span data-stu-id="af190-103">ICorDebugRegisterSet2::GetRegisters method</span></span>

<span data-ttu-id="af190-104">Возвращает значение каждого регистра (для платформы, в которой код выполняется в данный момент), заданный заданной битовой маской.</span><span class="sxs-lookup"><span data-stu-id="af190-104">Gets the value of each register (for the platform on which code is currently executing) that is specified by the given bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af190-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="af190-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af190-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="af190-106">Parameters</span></span>

 `maskCount`  
 <span data-ttu-id="af190-107">окне Размер массива в байтах `mask` .</span><span class="sxs-lookup"><span data-stu-id="af190-107">[in] The size, in bytes, of the `mask` array.</span></span>  
  
 `mask`  
 <span data-ttu-id="af190-108">окне Массив байтов, каждый бит которого соответствует регистру.</span><span class="sxs-lookup"><span data-stu-id="af190-108">[in] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="af190-109">Если бит равен 1, будет получено соответствующее значение регистра.</span><span class="sxs-lookup"><span data-stu-id="af190-109">If the bit is 1, the corresponding register's value will be retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="af190-110">окне Число возвращаемых значений регистров.</span><span class="sxs-lookup"><span data-stu-id="af190-110">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="af190-111">заполняет Массив `CORDB_REGISTER` объектов, каждый из которых получает значение регистра.</span><span class="sxs-lookup"><span data-stu-id="af190-111">[out] An array of `CORDB_REGISTER` objects, each of which receives the value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af190-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="af190-112">Remarks</span></span>

 <span data-ttu-id="af190-113">`GetRegisters`Метод возвращает массив значений из регистров, заданных маской.</span><span class="sxs-lookup"><span data-stu-id="af190-113">The `GetRegisters` method returns an array of values from the registers that are specified by the mask.</span></span> <span data-ttu-id="af190-114">Массив не содержит значений регистров, бит маски которых не задан.</span><span class="sxs-lookup"><span data-stu-id="af190-114">The array does not contain values of registers whose mask bit is not set.</span></span> <span data-ttu-id="af190-115">Таким `regBuffer` же размером массива должно быть значение, равное количеству 1 в маске.</span><span class="sxs-lookup"><span data-stu-id="af190-115">Thus, the size of the `regBuffer` array must be equal to the number of 1's in the mask.</span></span> <span data-ttu-id="af190-116">Если значение `regCount` слишком мало для количества регистров, указанных маской, значения более высоких регистров будут обрезаны из набора.</span><span class="sxs-lookup"><span data-stu-id="af190-116">If the value of `regCount` is too small for the number of registers indicated by the mask, the values of the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="af190-117">Если `regCount` значение слишком велико, неиспользуемые `regBuffer` элементы будут неизменными.</span><span class="sxs-lookup"><span data-stu-id="af190-117">If `regCount` is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="af190-118">Если недоступная ККМ обозначается маской, для этой регистрации будет возвращено неопределенное значение.</span><span class="sxs-lookup"><span data-stu-id="af190-118">If an unavailable register is indicated by the mask, an indeterminate value will be returned for that register.</span></span>  
  
 <span data-ttu-id="af190-119">Этот `ICorDebugRegisterSet2::GetRegisters` метод необходим для платформ, имеющих более 64 регистров.</span><span class="sxs-lookup"><span data-stu-id="af190-119">The `ICorDebugRegisterSet2::GetRegisters` method is necessary for platforms that have more than 64 registers.</span></span> <span data-ttu-id="af190-120">Например, IA64 имеет 128 регистров общего назначения и 128 регистров с плавающей запятой, поэтому в битовой маске требуется более 64 бит.</span><span class="sxs-lookup"><span data-stu-id="af190-120">For example, IA64 has 128 general purpose registers and 128 floating-point registers, so you need more than 64 bits in the bit mask.</span></span>  
  
 <span data-ttu-id="af190-121">Если у вас больше 64 регистров, как в случае с платформами, такими как x86, `GetRegisters` метод просто преобразует байты в `mask` массиве байтов в, `ULONG64` а затем вызывает метод [ICorDebugRegisterSet::](icordebugregisterset-getregisters-method.md) GetBytes, который принимает `ULONG64` маску.</span><span class="sxs-lookup"><span data-stu-id="af190-121">If you don't have more than 64 registers, as is the case on platforms such as x86, the `GetRegisters` method just translates the bytes in the `mask` byte array into a `ULONG64` and then calls the [ICorDebugRegisterSet::GetRegisters](icordebugregisterset-getregisters-method.md) method, which takes the `ULONG64` mask.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af190-122">Требования</span><span class="sxs-lookup"><span data-stu-id="af190-122">Requirements</span></span>

 <span data-ttu-id="af190-123">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af190-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af190-124">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="af190-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af190-125">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af190-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af190-126">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af190-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af190-127">См. также</span><span class="sxs-lookup"><span data-stu-id="af190-127">See also</span></span>

- [<span data-ttu-id="af190-128">Интерфейс ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="af190-128">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
- [<span data-ttu-id="af190-129">Интерфейс ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="af190-129">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
