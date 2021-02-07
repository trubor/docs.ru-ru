---
description: 'Дополнительные сведения о методе: метод icordebugdatatarget2:: Креатевиртуалунвиндер'
title: Метод ICorDebugDataTarget2::CreateVirtualUnwinder
ms.date: 03/30/2017
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
ms.openlocfilehash: 0646c85000f42b303769d6587354b3105e2deabd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764415"
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a><span data-ttu-id="17427-103">Метод ICorDebugDataTarget2::CreateVirtualUnwinder</span><span class="sxs-lookup"><span data-stu-id="17427-103">ICorDebugDataTarget2::CreateVirtualUnwinder Method</span></span>

<span data-ttu-id="17427-104">Создает новый элемент очистки стека, запускающий операцию очистки, начиная с исходного контекста (который не обязательно является концом потока).</span><span class="sxs-lookup"><span data-stu-id="17427-104">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17427-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="17427-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
## <a name="parameters"></a><span data-ttu-id="17427-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="17427-106">Parameters</span></span>  

 <span data-ttu-id="17427-107">nativeThreadID</span><span class="sxs-lookup"><span data-stu-id="17427-107">nativeThreadID</span></span>  
 <span data-ttu-id="17427-108">[входной] Идентификатор собственного потока, стек которого должен быть очищен.</span><span class="sxs-lookup"><span data-stu-id="17427-108">[in] The native thread ID of the thread whose stack is to be unwound.</span></span>  
  
 <span data-ttu-id="17427-109">contextFlags</span><span class="sxs-lookup"><span data-stu-id="17427-109">contextFlags</span></span>  
 <span data-ttu-id="17427-110">[входной] Флаги, указывающие, какие части контекста определены в `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="17427-110">[in] Flags that specify which parts of the context are defined in `initialContext`.</span></span>  
  
 <span data-ttu-id="17427-111">cbContext</span><span class="sxs-lookup"><span data-stu-id="17427-111">cbContext</span></span>  
 <span data-ttu-id="17427-112">[входной] Размер `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="17427-112">[in] The size of `initialContext`.</span></span>  
  
 <span data-ttu-id="17427-113">initialContext</span><span class="sxs-lookup"><span data-stu-id="17427-113">initialContext</span></span>  
 <span data-ttu-id="17427-114">[входной] Данные в контексте.</span><span class="sxs-lookup"><span data-stu-id="17427-114">[in] The data in the context.</span></span>  
  
 <span data-ttu-id="17427-115">ppUnwinder</span><span class="sxs-lookup"><span data-stu-id="17427-115">ppUnwinder</span></span>  
 <span data-ttu-id="17427-116">[выходной] Указатель на адрес объекта интерфейса ICorDebugVirtualUnwinder.</span><span class="sxs-lookup"><span data-stu-id="17427-116">[out] A pointer to the address of an ICorDebugVirtualUnwinder interface object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17427-117">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="17427-117">Return Value</span></span>  

 <span data-ttu-id="17427-118">`S_OK` в случае успешного выполнения.</span><span class="sxs-lookup"><span data-stu-id="17427-118">`S_OK` if successful.</span></span> <span data-ttu-id="17427-119">Любое другое значение `HRESULT` указывает на ошибку.</span><span class="sxs-lookup"><span data-stu-id="17427-119">Any other `HRESULT` indicates failure.</span></span> <span data-ttu-id="17427-120">Любой сбой `HRESULT` , полученный mscordbi, считается неустранимым и приводит к возврату методов [ICorDebug](icordebug-interface.md) `CORDBG_E_DATA_TARGET_ERROR` .</span><span class="sxs-lookup"><span data-stu-id="17427-120">Any failing `HRESULT` received by mscordbi is considered fatal and causes [ICorDebug](icordebug-interface.md) methods to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17427-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="17427-121">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="17427-122">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="17427-122">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17427-123">Требования</span><span class="sxs-lookup"><span data-stu-id="17427-123">Requirements</span></span>  

 <span data-ttu-id="17427-124">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17427-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17427-125">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="17427-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17427-126">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17427-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17427-127">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17427-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17427-128">См. также</span><span class="sxs-lookup"><span data-stu-id="17427-128">See also</span></span>

- [<span data-ttu-id="17427-129">Интерфейс ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="17427-129">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="17427-130">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="17427-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
