---
description: 'Дополнительные сведения о методе: ICorDebugThread3:: Креатестакквалк'
title: Метод ICorDebugThread3::CreateStackWalk
ms.date: 03/30/2017
api_name:
- ICorDebugThread3.CreateStackWalk Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::CreateStackWalk
helpviewer_keywords:
- CreateStackWalk method [.NET Framework debugging]
- ICorDebugThread3::CreateStackWalk method [.NET Framework debugging]
ms.assetid: c55e35d9-f9aa-4268-94b5-dce44c61acf2
topic_type:
- apiref
ms.openlocfilehash: b36252160dbad14ca1bee0674b6d042072a36359
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800998"
---
# <a name="icordebugthread3createstackwalk-method"></a><span data-ttu-id="2934d-103">Метод ICorDebugThread3::CreateStackWalk</span><span class="sxs-lookup"><span data-stu-id="2934d-103">ICorDebugThread3::CreateStackWalk Method</span></span>

<span data-ttu-id="2934d-104">Создает объект [икордебугстакквалк](icordebugstackwalk-interface.md) для потока, стек которого нужно очистить.</span><span class="sxs-lookup"><span data-stu-id="2934d-104">Creates an [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2934d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2934d-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2934d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="2934d-106">Parameters</span></span>  

 `ppStackWalk`  
 <span data-ttu-id="2934d-107">заполняет Указатель на адрес объекта [икордебугстакквалк](icordebugstackwalk-interface.md) для потока, стек которого нужно очистить.</span><span class="sxs-lookup"><span data-stu-id="2934d-107">[out] A pointer to address of the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2934d-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="2934d-108">Return Value</span></span>  

 <span data-ttu-id="2934d-109">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="2934d-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="2934d-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2934d-110">HRESULT</span></span>|<span data-ttu-id="2934d-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="2934d-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2934d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="2934d-112">S_OK</span></span>|<span data-ttu-id="2934d-113">`ICorDebugStackWalk`Объект успешно создан.</span><span class="sxs-lookup"><span data-stu-id="2934d-113">The `ICorDebugStackWalk` object was successfully created.</span></span>|  
|<span data-ttu-id="2934d-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2934d-114">E_FAIL</span></span>|<span data-ttu-id="2934d-115">`ICorDebugStackWalk`Объект не был создан.</span><span class="sxs-lookup"><span data-stu-id="2934d-115">The `ICorDebugStackWalk` object was not created.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="2934d-116">Исключения</span><span class="sxs-lookup"><span data-stu-id="2934d-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2934d-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="2934d-117">Remarks</span></span>  

 <span data-ttu-id="2934d-118">Если `CreateStackWalk` метод выполнен, контекст возвращаемого `ICorDebugStackWalk` объекта устанавливается в текущий контекст потока.</span><span class="sxs-lookup"><span data-stu-id="2934d-118">If the `CreateStackWalk` method succeeds, the returned `ICorDebugStackWalk` object's context is set to the thread's current context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2934d-119">Требования</span><span class="sxs-lookup"><span data-stu-id="2934d-119">Requirements</span></span>  

 <span data-ttu-id="2934d-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2934d-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2934d-121">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2934d-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2934d-122">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2934d-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2934d-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2934d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2934d-124">См. также</span><span class="sxs-lookup"><span data-stu-id="2934d-124">See also</span></span>

- [<span data-ttu-id="2934d-125">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="2934d-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="2934d-126">Отладка</span><span class="sxs-lookup"><span data-stu-id="2934d-126">Debugging</span></span>](index.md)
