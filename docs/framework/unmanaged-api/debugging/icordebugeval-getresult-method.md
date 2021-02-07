---
description: 'Дополнительные сведения о методе: ICorDebugEval:: with Result'
title: Метод ICorDebugEval::GetResult
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetResult
helpviewer_keywords:
- ICorDebugEval::GetResult method [.NET Framework debugging]
- GetResult method [.NET Framework debugging]
ms.assetid: 50dbb9af-58a1-41f4-b56d-3da20011884f
topic_type:
- apiref
ms.openlocfilehash: 03ab00f5c9a538e11a2046da9cbfd5ad7225231c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694244"
---
# <a name="icordebugevalgetresult-method"></a><span data-ttu-id="252f2-103">Метод ICorDebugEval::GetResult</span><span class="sxs-lookup"><span data-stu-id="252f2-103">ICorDebugEval::GetResult Method</span></span>

<span data-ttu-id="252f2-104">Возвращает результаты этой оценки.</span><span class="sxs-lookup"><span data-stu-id="252f2-104">Gets the results of this evaluation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="252f2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="252f2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="252f2-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="252f2-106">Parameters</span></span>  

 `ppResult`  
 <span data-ttu-id="252f2-107">заполняет Указатель на адрес объекта ICorDebugValue, который представляет результаты этой оценки, если вычисление завершается нормально.</span><span class="sxs-lookup"><span data-stu-id="252f2-107">[out] Pointer to the address of an ICorDebugValue object that represents the results of this evaluation, if the evaluation completes normally.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="252f2-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="252f2-108">Remarks</span></span>  

 <span data-ttu-id="252f2-109">`GetResult`Метод действителен только после завершения оценки.</span><span class="sxs-lookup"><span data-stu-id="252f2-109">The `GetResult` method is valid only after the evaluation is completed.</span></span>  
  
 <span data-ttu-id="252f2-110">Если вычисление завершается обычным образом, `ppResult` задает результаты.</span><span class="sxs-lookup"><span data-stu-id="252f2-110">If the evaluation completes normally, `ppResult` specifies the results.</span></span> <span data-ttu-id="252f2-111">Если оно завершается с исключением, результатом является исключение.</span><span class="sxs-lookup"><span data-stu-id="252f2-111">If it terminates with an exception, the result is the exception thrown.</span></span> <span data-ttu-id="252f2-112">Если вычисление выполнялось для нового объекта, результатом является ссылка на новый объект.</span><span class="sxs-lookup"><span data-stu-id="252f2-112">If the evaluation was for a new object, the result is the reference to the new object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="252f2-113">Требования</span><span class="sxs-lookup"><span data-stu-id="252f2-113">Requirements</span></span>  

 <span data-ttu-id="252f2-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="252f2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="252f2-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="252f2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="252f2-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="252f2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="252f2-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="252f2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
