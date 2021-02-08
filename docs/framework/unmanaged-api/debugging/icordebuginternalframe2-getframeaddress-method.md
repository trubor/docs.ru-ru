---
description: 'Дополнительные сведения о методе: ICorDebugInternalFrame2:: Жетфрамеаддресс'
title: Метод ICorDebugInternalFrame2::GetFrameAddress
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2.GetFrameAddress Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2::GetFrameAddress
helpviewer_keywords:
- GetFrameAddress method [.NET Framework debugging]
- ICorDebugInternalFrame2::GetFrameAddress method [.NET Framework debugging]
ms.assetid: 4ee8d058-ffc8-4967-9133-a5adfef4e518
topic_type:
- apiref
ms.openlocfilehash: bb745424680c5b9a5277badfbe2d96db46e2e3d8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791118"
---
# <a name="icordebuginternalframe2getframeaddress-method"></a><span data-ttu-id="50e3d-103">Метод ICorDebugInternalFrame2::GetFrameAddress</span><span class="sxs-lookup"><span data-stu-id="50e3d-103">ICorDebugInternalFrame2::GetFrameAddress Method</span></span>

<span data-ttu-id="50e3d-104">Возвращает адрес стека внутреннего кадра.</span><span class="sxs-lookup"><span data-stu-id="50e3d-104">Returns the stack address of the internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50e3d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="50e3d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50e3d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="50e3d-106">Parameters</span></span>  

 `pAddress`  
 <span data-ttu-id="50e3d-107">заполняет Указатель на объект `CORDB_ADDRESS` для внутреннего кадра.</span><span class="sxs-lookup"><span data-stu-id="50e3d-107">[out] Pointer to the `CORDB_ADDRESS` for the internal frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50e3d-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="50e3d-108">Return Value</span></span>  

 <span data-ttu-id="50e3d-109">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="50e3d-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="50e3d-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="50e3d-110">HRESULT</span></span>|<span data-ttu-id="50e3d-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="50e3d-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="50e3d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="50e3d-112">S_OK</span></span>|<span data-ttu-id="50e3d-113">Адрес внутреннего кадра успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="50e3d-113">The address of the internal frame was successfully returned.</span></span>|  
|<span data-ttu-id="50e3d-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="50e3d-114">E_FAIL</span></span>|<span data-ttu-id="50e3d-115">Не удалось вернуть адрес внутреннего кадра.</span><span class="sxs-lookup"><span data-stu-id="50e3d-115">The address of the internal frame could not be returned.</span></span>|  
|<span data-ttu-id="50e3d-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="50e3d-116">E_INVALIDARG</span></span>|<span data-ttu-id="50e3d-117">Параметр `pAddress` равен `null`.</span><span class="sxs-lookup"><span data-stu-id="50e3d-117">`pAddress` is `null`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50e3d-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="50e3d-118">Remarks</span></span>  

 <span data-ttu-id="50e3d-119">Значение, возвращаемое в, `pAddress` можно использовать для определения расположения внутреннего кадра относительно других кадров в стеке.</span><span class="sxs-lookup"><span data-stu-id="50e3d-119">The value returned in `pAddress` can be used to determine the location of the internal frame relative to other frames on the stack.</span></span> <span data-ttu-id="50e3d-120">Даже на компьютерах на базе IA-64 внутренний кадр находится только в стеке и не имеет соответствующего указателя на резервное хранилище.</span><span class="sxs-lookup"><span data-stu-id="50e3d-120">Even on IA-64-based computers, the internal frame lives on the stack only, and there is no corresponding pointer to a backing store.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50e3d-121">Требования</span><span class="sxs-lookup"><span data-stu-id="50e3d-121">Requirements</span></span>  

 <span data-ttu-id="50e3d-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50e3d-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50e3d-123">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="50e3d-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50e3d-124">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50e3d-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50e3d-125">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50e3d-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50e3d-126">См. также</span><span class="sxs-lookup"><span data-stu-id="50e3d-126">See also</span></span>

- [<span data-ttu-id="50e3d-127">Интерфейс ICorDebugInternalFrame2</span><span class="sxs-lookup"><span data-stu-id="50e3d-127">ICorDebugInternalFrame2 Interface</span></span>](icordebuginternalframe2-interface.md)
- [<span data-ttu-id="50e3d-128">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="50e3d-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="50e3d-129">Отладка</span><span class="sxs-lookup"><span data-stu-id="50e3d-129">Debugging</span></span>](index.md)
