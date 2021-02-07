---
description: См. Дополнительные сведения о методе ICorDebugRegisterSet::, регистрирующих
title: Метод ICorDebugRegisterSet::GetRegisters
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type:
- apiref
ms.openlocfilehash: efb0f19fe9eb823912203b82267803739fc3e2cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690851"
---
# <a name="icordebugregistersetgetregisters-method"></a><span data-ttu-id="c0ab1-103">Метод ICorDebugRegisterSet::GetRegisters</span><span class="sxs-lookup"><span data-stu-id="c0ab1-103">ICorDebugRegisterSet::GetRegisters Method</span></span>

<span data-ttu-id="c0ab1-104">Возвращает значение каждого регистра (на компьютере, выполняющем в данный момент код), который задается битовой маской.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-104">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0ab1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c0ab1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG64       mask,
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0ab1-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c0ab1-106">Parameters</span></span>  

 `mask`  
 <span data-ttu-id="c0ab1-107">окне Битовая маска, указывающая, какие значения регистров должны быть извлечены.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-107">[in] A bit mask that specifies which register values are to be retrieved.</span></span> <span data-ttu-id="c0ab1-108">Каждый бит соответствует регистру.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-108">Each bit corresponds to a register.</span></span> <span data-ttu-id="c0ab1-109">Если бит задан равным 1, то значение регистра извлекается; в противном случае значение регистра не извлекается.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-109">If a bit is set to one, the register's value is retrieved; otherwise, the register's value is not retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="c0ab1-110">окне Число возвращаемых значений регистров.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-110">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="c0ab1-111">заполняет Массив `CORDB_REGISTER` объектов, каждый из которых получает значение регистра.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-111">[out] An array of `CORDB_REGISTER` objects, each of which receives a value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0ab1-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="c0ab1-112">Remarks</span></span>  

 <span data-ttu-id="c0ab1-113">Размер массива должен быть равен числу битов, равным одному в битовой маске.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-113">The size of the array should be equal to the number of bits set to one in the bit mask.</span></span> <span data-ttu-id="c0ab1-114">`regCount`Параметр задает количество элементов в буфере, которые будут принимать значения регистров.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-114">The `regCount` parameter specifies the number of elements in the buffer that will receive the register values.</span></span> <span data-ttu-id="c0ab1-115">Если `regCount` значение слишком мало для количества регистров, указанных маской, то более высокие числовые регистры будут обрезаны из набора.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-115">If the `regCount` value is too small for the number of registers indicated by the mask, the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="c0ab1-116">Если `regCount` значение слишком велико, неиспользуемые `regBuffer` элементы будут неизменными.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-116">If the `regCount` value is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="c0ab1-117">Если битовая маска указывает недоступный регистр, `GetRegisters` возвращает неопределенное значение для этого регистра.</span><span class="sxs-lookup"><span data-stu-id="c0ab1-117">If the bit mask specifies a register that is unavailable, `GetRegisters` returns an indeterminate value for that register.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0ab1-118">Требования</span><span class="sxs-lookup"><span data-stu-id="c0ab1-118">Requirements</span></span>  

 <span data-ttu-id="c0ab1-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0ab1-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0ab1-120">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c0ab1-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c0ab1-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0ab1-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0ab1-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0ab1-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0ab1-123">См. также</span><span class="sxs-lookup"><span data-stu-id="c0ab1-123">See also</span></span>

- [<span data-ttu-id="c0ab1-124">Интерфейс ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="c0ab1-124">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="c0ab1-125">Интерфейс ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="c0ab1-125">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
