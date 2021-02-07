---
description: 'Дополнительные сведения о методе: ICorDebugNativeFrame2:: GetStackParameterSize'
title: Метод ICorDebugNativeFrame2::GetStackParameterSize
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.GetStackParameterSize Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize
helpviewer_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize method [.NET Framework debugging]
- GetStackParameterSize method [.NET Framework debugging]
ms.assetid: f6a449c8-a941-43ba-9a90-c98b29ae3c36
topic_type:
- apiref
ms.openlocfilehash: 08a17ced0be75737c1c49aa3f9bb42b13bbe8aa0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722338"
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a><span data-ttu-id="8a944-103">Метод ICorDebugNativeFrame2::GetStackParameterSize</span><span class="sxs-lookup"><span data-stu-id="8a944-103">ICorDebugNativeFrame2::GetStackParameterSize Method</span></span>

<span data-ttu-id="8a944-104">Возвращает совокупный размер параметров в стеке в операционных системах x86.</span><span class="sxs-lookup"><span data-stu-id="8a944-104">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a944-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8a944-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a944-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8a944-106">Parameters</span></span>  

 `pSize`  
 <span data-ttu-id="8a944-107">заполняет Указатель на совокупный размер параметров в стеке.</span><span class="sxs-lookup"><span data-stu-id="8a944-107">[out] A pointer to the cumulative size of the parameters on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8a944-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="8a944-108">Return Value</span></span>  

 <span data-ttu-id="8a944-109">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="8a944-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8a944-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8a944-110">HRESULT</span></span>|<span data-ttu-id="8a944-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="8a944-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8a944-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="8a944-112">S_OK</span></span>|<span data-ttu-id="8a944-113">Размер стека успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="8a944-113">The stack size was successfully returned.</span></span>|  
|<span data-ttu-id="8a944-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="8a944-114">S_FALSE</span></span>|<span data-ttu-id="8a944-115">`GetStackParameterSize` был вызван на платформе, отличной от x86.</span><span class="sxs-lookup"><span data-stu-id="8a944-115">`GetStackParameterSize` was called on a non-x86 platform.</span></span>|  
|<span data-ttu-id="8a944-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8a944-116">E_FAIL</span></span>|<span data-ttu-id="8a944-117">`The size of the parameters could not be returned`.</span><span class="sxs-lookup"><span data-stu-id="8a944-117">`The size of the parameters could not be returned`.</span></span>|  
|<span data-ttu-id="8a944-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8a944-118">E_INVALIDARG</span></span>|<span data-ttu-id="8a944-119">`pSize` Имеет `null` .</span><span class="sxs-lookup"><span data-stu-id="8a944-119">`pSize` Is `null`.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="8a944-120">Исключения</span><span class="sxs-lookup"><span data-stu-id="8a944-120">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a944-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="8a944-121">Remarks</span></span>  

 <span data-ttu-id="8a944-122">Методы [икордебугстакквалк](icordebugstackwalk-interface.md) не настраивают указатель стека для параметров, помещаемых в стек.</span><span class="sxs-lookup"><span data-stu-id="8a944-122">The [ICorDebugStackWalk](icordebugstackwalk-interface.md) methods do not adjust the stack pointer for parameters that are pushed on the stack.</span></span> <span data-ttu-id="8a944-123">Вместо этого можно использовать значение, возвращаемое методом, `GetStackParameterSize` чтобы настроить указатель стека на заполнение собственного, неуправляемого кода, который корректируется для параметров.</span><span class="sxs-lookup"><span data-stu-id="8a944-123">Instead, you can use the value returned by `GetStackParameterSize` to adjust the stack pointer to seed a native unwinder, which does adjust for the parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a944-124">Требования</span><span class="sxs-lookup"><span data-stu-id="8a944-124">Requirements</span></span>  

 <span data-ttu-id="8a944-125">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a944-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a944-126">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a944-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a944-127">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a944-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a944-128">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a944-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a944-129">См. также</span><span class="sxs-lookup"><span data-stu-id="8a944-129">See also</span></span>

- [<span data-ttu-id="8a944-130">Интерфейс ICorDebugNativeFrame2</span><span class="sxs-lookup"><span data-stu-id="8a944-130">ICorDebugNativeFrame2 Interface</span></span>](icordebugnativeframe2-interface.md)
- [<span data-ttu-id="8a944-131">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="8a944-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="8a944-132">Отладка</span><span class="sxs-lookup"><span data-stu-id="8a944-132">Debugging</span></span>](index.md)
