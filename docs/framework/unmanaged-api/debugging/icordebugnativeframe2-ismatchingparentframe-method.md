---
description: 'Дополнительные сведения о методе: ICorDebugNativeFrame2:: IsMatchingParentFrame'
title: Метод ICorDebugNativeFrame2::IsMatchingParentFrame
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.IsMatchingParentFrame Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::IsMatchingParentFrame
helpviewer_keywords:
- IsMatchingParentFrame method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsMatchingParentFrame method [.NET Framework debugging]
ms.assetid: d2ca20db-df22-4528-a0dd-a09ea62c8998
topic_type:
- apiref
ms.openlocfilehash: 6dff1cb7f5205ad742ac4b886f72938dd28bd88f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722208"
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a><span data-ttu-id="77d63-103">Метод ICorDebugNativeFrame2::IsMatchingParentFrame</span><span class="sxs-lookup"><span data-stu-id="77d63-103">ICorDebugNativeFrame2::IsMatchingParentFrame Method</span></span>

<span data-ttu-id="77d63-104">Определяет, является ли указанный кадр родительским по отношению к текущему кадру.</span><span class="sxs-lookup"><span data-stu-id="77d63-104">Determines whether the specified frame is the parent of the current frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77d63-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="77d63-105">Syntax</span></span>  
  
```cpp  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77d63-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="77d63-106">Parameters</span></span>  

 `pPotentialParentFrame`  
 <span data-ttu-id="77d63-107">окне Указатель на объект Frame, для которого необходимо оценить состояние родителя.</span><span class="sxs-lookup"><span data-stu-id="77d63-107">[in] A pointer to the frame object that you want to evaluate for parent status.</span></span>  
  
 `pIsParent`  
 <span data-ttu-id="77d63-108">[out] `true` `pPotentialParentFrame` , если является родительским для текущего кадра; в противном случае — значение `false` .</span><span class="sxs-lookup"><span data-stu-id="77d63-108">[out] `true` if `pPotentialParentFrame` is the current frame’s parent; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77d63-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="77d63-109">Return Value</span></span>  

 <span data-ttu-id="77d63-110">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="77d63-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="77d63-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="77d63-111">HRESULT</span></span>|<span data-ttu-id="77d63-112">Описание:</span><span class="sxs-lookup"><span data-stu-id="77d63-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="77d63-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="77d63-113">S_OK</span></span>|<span data-ttu-id="77d63-114">Состояние родительского объекта успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="77d63-114">The parent status was successfully returned.</span></span>|  
|<span data-ttu-id="77d63-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="77d63-115">E_FAIL</span></span>|<span data-ttu-id="77d63-116">Не удалось вернуть родительское состояние.</span><span class="sxs-lookup"><span data-stu-id="77d63-116">The parent status could not be returned.</span></span>|  
|<span data-ttu-id="77d63-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="77d63-117">E_INVALIDARG</span></span>|<span data-ttu-id="77d63-118">`pPotentialParentFrame` или `pIsParent` равно null.</span><span class="sxs-lookup"><span data-stu-id="77d63-118">`pPotentialParentFrame` or `pIsParent` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="77d63-119">Исключения</span><span class="sxs-lookup"><span data-stu-id="77d63-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77d63-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="77d63-120">Remarks</span></span>  

 <span data-ttu-id="77d63-121">`IsMatchingParentFrame` Возвращает значение, `true` Если объект Frame, передаваемый в метод, является родительским для объекта Frame, для которого был вызван метод.</span><span class="sxs-lookup"><span data-stu-id="77d63-121">`IsMatchingParentFrame` returns `true` if the frame object you pass to the method is the parent of the frame object on which the method was called.</span></span> <span data-ttu-id="77d63-122">При вызове метода для фрейма, который не является дочерним по отношению к указанному кадру, возвращается ошибка.</span><span class="sxs-lookup"><span data-stu-id="77d63-122">If you call the method on a frame that is not a child of the specified frame, it returns an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77d63-123">Требования</span><span class="sxs-lookup"><span data-stu-id="77d63-123">Requirements</span></span>  

 <span data-ttu-id="77d63-124">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77d63-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77d63-125">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="77d63-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77d63-126">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77d63-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77d63-127">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77d63-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77d63-128">См. также</span><span class="sxs-lookup"><span data-stu-id="77d63-128">See also</span></span>

- [<span data-ttu-id="77d63-129">Интерфейс ICorDebugNativeFrame2</span><span class="sxs-lookup"><span data-stu-id="77d63-129">ICorDebugNativeFrame2 Interface</span></span>](icordebugnativeframe2-interface.md)
- [<span data-ttu-id="77d63-130">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="77d63-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="77d63-131">Отладка</span><span class="sxs-lookup"><span data-stu-id="77d63-131">Debugging</span></span>](index.md)
