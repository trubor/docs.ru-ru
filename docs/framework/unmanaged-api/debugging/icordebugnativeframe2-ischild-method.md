---
description: 'Дополнительные сведения о методе: ICorDebugNativeFrame2:: Child'
title: Метод ICorDebugNativeFrame2::IsChild
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.IsChild Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::IsChild
helpviewer_keywords:
- IsChild method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsChild method [.NET Framework debugging]
ms.assetid: 9e2aae09-49cb-4fbd-81e5-e29cd864a88b
topic_type:
- apiref
ms.openlocfilehash: 7c698c5a49ee445b4ba9c591c96f700f86a86c32
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722299"
---
# <a name="icordebugnativeframe2ischild-method"></a><span data-ttu-id="23f33-103">Метод ICorDebugNativeFrame2::IsChild</span><span class="sxs-lookup"><span data-stu-id="23f33-103">ICorDebugNativeFrame2::IsChild Method</span></span>

<span data-ttu-id="23f33-104">Определяет, является ли текущий кадр дочерним кадром.</span><span class="sxs-lookup"><span data-stu-id="23f33-104">Determines whether the current frame is a child frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23f33-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="23f33-105">Syntax</span></span>  
  
```cpp  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23f33-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="23f33-106">Parameters</span></span>  

 `pIsChild`  
 <span data-ttu-id="23f33-107">заполняет Логическое значение, указывающее, является ли текущий кадр дочерним кадром.</span><span class="sxs-lookup"><span data-stu-id="23f33-107">[out] A Boolean value that specifies whether the current frame is a child frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23f33-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="23f33-108">Return Value</span></span>  

 <span data-ttu-id="23f33-109">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="23f33-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="23f33-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="23f33-110">HRESULT</span></span>|<span data-ttu-id="23f33-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="23f33-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="23f33-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="23f33-112">S_OK</span></span>|<span data-ttu-id="23f33-113">Состояние дочернего элемента успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="23f33-113">The child status was successfully returned.</span></span>|  
|<span data-ttu-id="23f33-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="23f33-114">E_FAIL</span></span>|<span data-ttu-id="23f33-115">Не удалось вернуть состояние дочернего элемента.</span><span class="sxs-lookup"><span data-stu-id="23f33-115">The child status could not be returned.</span></span>|  
|<span data-ttu-id="23f33-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="23f33-116">E_INVALIDARG</span></span>|<span data-ttu-id="23f33-117">Параметр `pIsChild` имеет значение null.</span><span class="sxs-lookup"><span data-stu-id="23f33-117">`pIsChild` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="23f33-118">Исключения</span><span class="sxs-lookup"><span data-stu-id="23f33-118">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23f33-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="23f33-119">Remarks</span></span>  

 <span data-ttu-id="23f33-120">`IsChild`Метод возвращает значение, `true` Если объект Frame, для которого вызывается метод, является дочерним по отношению к другому кадру.</span><span class="sxs-lookup"><span data-stu-id="23f33-120">The `IsChild` method returns `true` if the frame object on which you call the method is a child of another frame.</span></span> <span data-ttu-id="23f33-121">В этом случае используйте метод [IsMatchingParentFrame](icordebugnativeframe2-ismatchingparentframe-method.md) , чтобы проверить, является ли кадр родительским.</span><span class="sxs-lookup"><span data-stu-id="23f33-121">If this is the case, use the [IsMatchingParentFrame](icordebugnativeframe2-ismatchingparentframe-method.md) method to check whether a frame is its parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23f33-122">Требования</span><span class="sxs-lookup"><span data-stu-id="23f33-122">Requirements</span></span>  

 <span data-ttu-id="23f33-123">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23f33-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23f33-124">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="23f33-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="23f33-125">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23f33-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23f33-126">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23f33-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23f33-127">См. также</span><span class="sxs-lookup"><span data-stu-id="23f33-127">See also</span></span>

- [<span data-ttu-id="23f33-128">Интерфейс ICorDebugNativeFrame2</span><span class="sxs-lookup"><span data-stu-id="23f33-128">ICorDebugNativeFrame2 Interface</span></span>](icordebugnativeframe2-interface.md)
- [<span data-ttu-id="23f33-129">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="23f33-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="23f33-130">Отладка</span><span class="sxs-lookup"><span data-stu-id="23f33-130">Debugging</span></span>](index.md)
