---
description: 'Дополнительные сведения о методе: ICorDebugThread2:: GetActiveFunctions'
title: Метод ICorDebugThread2::GetActiveFunctions
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetActiveFunctions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetActiveFunctions
helpviewer_keywords:
- GetActiveFunctions method [.NET Framework debugging]
- ICorDebugThread2::GetActiveFunctions method [.NET Framework debugging]
ms.assetid: 27fae01a-ecec-423a-973e-24f8de55826c
topic_type:
- apiref
ms.openlocfilehash: 841e8ff17f15cfb14e1c1bf65c651a5177db2eaa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658767"
---
# <a name="icordebugthread2getactivefunctions-method"></a><span data-ttu-id="e7ec4-103">Метод ICorDebugThread2::GetActiveFunctions</span><span class="sxs-lookup"><span data-stu-id="e7ec4-103">ICorDebugThread2::GetActiveFunctions Method</span></span>

<span data-ttu-id="e7ec4-104">Возвращает сведения об активной функции в каждом кадре этого потока.</span><span class="sxs-lookup"><span data-stu-id="e7ec4-104">Gets information about the active function in each of this thread's frames.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7ec4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e7ec4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7ec4-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e7ec4-106">Parameters</span></span>  

 `cFunctions`  
 <span data-ttu-id="e7ec4-107">[in] Размер массива `pFunctions`.</span><span class="sxs-lookup"><span data-stu-id="e7ec4-107">[in] The size of the `pFunctions` array.</span></span>  
  
 `pcFunctions`  
 <span data-ttu-id="e7ec4-108">заполняет Указатель на число объектов, возвращаемых в `pFunctions` массиве.</span><span class="sxs-lookup"><span data-stu-id="e7ec4-108">[out] A pointer to the number of objects returned in the `pFunctions` array.</span></span> <span data-ttu-id="e7ec4-109">Число возвращаемых объектов будет равно числу управляемых кадров в стеке.</span><span class="sxs-lookup"><span data-stu-id="e7ec4-109">The number of objects returned will be equal to the number of managed frames on the stack.</span></span>  
  
 `pFunctions`  
 <span data-ttu-id="e7ec4-110">[вход, выход] Массив объектов COR_ACTIVE_FUNCTION, каждый из которых содержит сведения об активных функциях в кадрах этого потока.</span><span class="sxs-lookup"><span data-stu-id="e7ec4-110">[in, out] An array of COR_ACTIVE_FUNCTION objects, each of which contains information about the active functions in this thread's frames.</span></span>  
  
 <span data-ttu-id="e7ec4-111">Первый элемент будет использоваться для конечного фрейма и так далее — в корне стека.</span><span class="sxs-lookup"><span data-stu-id="e7ec4-111">The first element will be used for the leaf frame, and so on back to the root of the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7ec4-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="e7ec4-112">Remarks</span></span>  

 <span data-ttu-id="e7ec4-113">Если `pFunctions` для входных данных задано значение null, `GetActiveFunctions` функция возвращает только число функций в стеке.</span><span class="sxs-lookup"><span data-stu-id="e7ec4-113">If `pFunctions` is null on input, `GetActiveFunctions` returns only the number of functions that are on the stack.</span></span> <span data-ttu-id="e7ec4-114">То есть если `pFunctions` во входных данных параметр имеет значение null, `GetActiveFunctions` возвращает значение только в `pcFunctions` .</span><span class="sxs-lookup"><span data-stu-id="e7ec4-114">That is, If `pFunctions` is null on input, `GetActiveFunctions` returns a value only in `pcFunctions`.</span></span>  
  
 <span data-ttu-id="e7ec4-115">`GetActiveFunctions`Метод предназначен для оптимизации при получении тех же сведений из кадров в трассировке стека и включает только те кадры, для которых в полной трассировке стека был бы объект ICorDebugILFrame.</span><span class="sxs-lookup"><span data-stu-id="e7ec4-115">The `GetActiveFunctions` method is intended as an optimization over getting the same information from frames in a stack trace, and includes only frames that would have had an ICorDebugILFrame object for them in the full stack trace.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7ec4-116">Требования</span><span class="sxs-lookup"><span data-stu-id="e7ec4-116">Requirements</span></span>  

 <span data-ttu-id="e7ec4-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7ec4-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7ec4-118">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e7ec4-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7ec4-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7ec4-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7ec4-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7ec4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
