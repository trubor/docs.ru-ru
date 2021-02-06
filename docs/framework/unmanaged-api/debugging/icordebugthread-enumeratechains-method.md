---
description: 'Дополнительные сведения о методе ICorDebugThread:: EnumerateChains'
title: Метод ICorDebugThread::EnumerateChains
ms.date: 03/30/2017
api_name:
- ICorDebugThread.EnumerateChains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::EnumerateChains
helpviewer_keywords:
- EnumerateChains method [.NET Framework debugging]
- ICorDebugThread::EnumerateChains method [.NET Framework debugging]
ms.assetid: ec00bc21-117e-4acd-9301-2cfafd5be8d3
topic_type:
- apiref
ms.openlocfilehash: b9184a1b298e1d29970c5e56ceca76715b0ed096
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659300"
---
# <a name="icordebugthreadenumeratechains-method"></a><span data-ttu-id="1b137-103">Метод ICorDebugThread::EnumerateChains</span><span class="sxs-lookup"><span data-stu-id="1b137-103">ICorDebugThread::EnumerateChains Method</span></span>

<span data-ttu-id="1b137-104">Получает указатель интерфейса на перечислитель Икордебугчаиненум, который содержит все цепочки стека в этом объекте ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="1b137-104">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b137-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1b137-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b137-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1b137-106">Parameters</span></span>  

 `ppChains`  
 <span data-ttu-id="1b137-107">заполняет Указатель на адрес `ICorDebugChainEnum` объекта, который допускает перечисление всех цепочек стека в этом потоке, начиная с активной (то есть самой последней) цепочки.</span><span class="sxs-lookup"><span data-stu-id="1b137-107">[out] A pointer to the address of an `ICorDebugChainEnum` object that allows enumeration of all the stack chains in this thread, starting at the active (that is, the most recent) chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b137-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="1b137-108">Remarks</span></span>  

 <span data-ttu-id="1b137-109">Цепочка стека представляет физический стек вызовов для потока.</span><span class="sxs-lookup"><span data-stu-id="1b137-109">The stack chain represents the physical call stack for the thread.</span></span> <span data-ttu-id="1b137-110">В следующих случаях создается граница цепочки стеков:</span><span class="sxs-lookup"><span data-stu-id="1b137-110">The following circumstances create a stack chain boundary:</span></span>  
  
- <span data-ttu-id="1b137-111">Переход с управляемого на неуправляемый или неуправляемый на управляемый.</span><span class="sxs-lookup"><span data-stu-id="1b137-111">A managed-to-unmanaged or unmanaged-to-managed transition.</span></span>  
  
- <span data-ttu-id="1b137-112">Переключение контекста.</span><span class="sxs-lookup"><span data-stu-id="1b137-112">A context switch.</span></span>  
  
- <span data-ttu-id="1b137-113">Перехват пользовательского потока отладчиком.</span><span class="sxs-lookup"><span data-stu-id="1b137-113">A debugger hijacking of a user thread.</span></span>  
  
 <span data-ttu-id="1b137-114">В простом случае для потока, в котором выполняется исключительно управляемый код в одном контексте, между потоками и цепочками стеков будет существовать соответствие "один к одному".</span><span class="sxs-lookup"><span data-stu-id="1b137-114">In the simple case for a thread that is running purely managed code in a single context, a one-to-one correspondence will exist between threads and stack chains.</span></span>  
  
 <span data-ttu-id="1b137-115">Отладчик может захотеть перераспределить физические стеки вызовов всех потоков на логические стеки вызовов.</span><span class="sxs-lookup"><span data-stu-id="1b137-115">A debugger may want to rearrange the physical call stacks of all threads into logical call stacks.</span></span> <span data-ttu-id="1b137-116">Это может привести к сортировке всех цепочек потоков по связям "Вызывающий/вызываемый" и их перегруппировку.</span><span class="sxs-lookup"><span data-stu-id="1b137-116">This would involve sorting all the threads' chains by their caller/callee relationships and regrouping them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b137-117">Требования</span><span class="sxs-lookup"><span data-stu-id="1b137-117">Requirements</span></span>  

 <span data-ttu-id="1b137-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b137-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b137-119">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b137-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b137-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b137-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b137-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b137-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
