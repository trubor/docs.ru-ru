---
description: 'Дополнительные сведения о методе: ICorDebugInternalFrame2:: Исклосертолеаф'
title: Метод ICorDebugInternalFrame2::IsCloserToLeaf
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2.IsCloserToLeaf Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf
helpviewer_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf method [.NET Framework debugging]
- IsCloserToLeaf method [.NET Framework debugging]
ms.assetid: c1d3d1eb-8370-4f25-8297-3bd262b4740a
topic_type:
- apiref
ms.openlocfilehash: d773f8670f600a5bcd2a8dad7f23fe243195957c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801284"
---
# <a name="icordebuginternalframe2isclosertoleaf-method"></a><span data-ttu-id="c960a-103">Метод ICorDebugInternalFrame2::IsCloserToLeaf</span><span class="sxs-lookup"><span data-stu-id="c960a-103">ICorDebugInternalFrame2::IsCloserToLeaf Method</span></span>

<span data-ttu-id="c960a-104">Проверяет, `this` находится ли внутренний кадр ближе к конечному объекту, чем указанный объект ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="c960a-104">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c960a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c960a-105">Syntax</span></span>  
  
```cpp  
HRESULT IsCloserToLeaf([in] ICorDebugFrame * pFrameToCompare,  
                       [out] BOOL * pIsCloser);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c960a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c960a-106">Parameters</span></span>  

 `pFrameToCompare`  
 <span data-ttu-id="c960a-107">окне Указатель на `ICorDebugFrame` объект сравнения.</span><span class="sxs-lookup"><span data-stu-id="c960a-107">[in] A pointer to the comparison `ICorDebugFrame` object.</span></span>  
  
 `pIsCloser`  
 <span data-ttu-id="c960a-108">[out] `true` `this` значение, если внутренний кадр находится ближе к конечному объекту, чем кадр, заданный параметром `pFrameToCompare` ; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="c960a-108">[out] `true` if the `this` internal frame is closer to the leaf than the frame specified by `pFrameToCompare`; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c960a-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="c960a-109">Return Value</span></span>  

 <span data-ttu-id="c960a-110">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="c960a-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c960a-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c960a-111">HRESULT</span></span>|<span data-ttu-id="c960a-112">Описание:</span><span class="sxs-lookup"><span data-stu-id="c960a-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c960a-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="c960a-113">S_OK</span></span>|<span data-ttu-id="c960a-114">Сравнение успешно выполнено.</span><span class="sxs-lookup"><span data-stu-id="c960a-114">The comparison was successfully performed.</span></span>|  
|<span data-ttu-id="c960a-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c960a-115">E_FAIL</span></span>|<span data-ttu-id="c960a-116">Не удалось выполнить сравнение.</span><span class="sxs-lookup"><span data-stu-id="c960a-116">The comparison could not be performed.</span></span>|  
|<span data-ttu-id="c960a-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c960a-117">E_INVALIDARG</span></span>|<span data-ttu-id="c960a-118">`pFrameToCompare` или `pIsCloser` равно null.</span><span class="sxs-lookup"><span data-stu-id="c960a-118">`pFrameToCompare` or `pIsCloser` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c960a-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="c960a-119">Remarks</span></span>  

 <span data-ttu-id="c960a-120">`IsCloserToLeaf` может использоваться для реализации политики для поверх внутренних кадров с другими кадрами в стеке.</span><span class="sxs-lookup"><span data-stu-id="c960a-120">`IsCloserToLeaf` can be used to implement a policy for interleaving internal frames with other frames on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c960a-121">Требования</span><span class="sxs-lookup"><span data-stu-id="c960a-121">Requirements</span></span>  

 <span data-ttu-id="c960a-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c960a-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c960a-123">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c960a-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c960a-124">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c960a-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c960a-125">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c960a-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c960a-126">См. также</span><span class="sxs-lookup"><span data-stu-id="c960a-126">See also</span></span>

- [<span data-ttu-id="c960a-127">Интерфейс ICorDebugInternalFrame2</span><span class="sxs-lookup"><span data-stu-id="c960a-127">ICorDebugInternalFrame2 Interface</span></span>](icordebuginternalframe2-interface.md)
- [<span data-ttu-id="c960a-128">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="c960a-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c960a-129">Отладка</span><span class="sxs-lookup"><span data-stu-id="c960a-129">Debugging</span></span>](index.md)
