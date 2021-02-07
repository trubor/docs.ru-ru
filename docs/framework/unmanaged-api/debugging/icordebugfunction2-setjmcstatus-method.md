---
description: 'Дополнительные сведения о методе: ICorDebugFunction2:: Сетжмкстатус'
title: Метод ICorDebugFunction2::SetJMCStatus
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::SetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 22c27b01-2869-4214-b840-5921f7c874fc
topic_type:
- apiref
ms.openlocfilehash: d2df9d47808b0220a91bd344e7600f8d16eccdb4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692193"
---
# <a name="icordebugfunction2setjmcstatus-method"></a><span data-ttu-id="b9f60-103">Метод ICorDebugFunction2::SetJMCStatus</span><span class="sxs-lookup"><span data-stu-id="b9f60-103">ICorDebugFunction2::SetJMCStatus Method</span></span>

<span data-ttu-id="b9f60-104">Помечает функцию, представленную этим ICorDebugFunction2, для Только мой код пошагового выполнения.</span><span class="sxs-lookup"><span data-stu-id="b9f60-104">Marks the function represented by this ICorDebugFunction2 for Just My Code stepping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9f60-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b9f60-105">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9f60-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b9f60-106">Parameters</span></span>  

 `bIsJustMyCode`  
 <span data-ttu-id="b9f60-107">окне Установите значение, чтобы `true` пометить функцию как пользовательский код; в противном случае задайте для значение `false` .</span><span class="sxs-lookup"><span data-stu-id="b9f60-107">[in] Set to `true` to mark the function as user code; otherwise, set to `false`.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="b9f60-108">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="b9f60-108">Return Values</span></span>  
  
|<span data-ttu-id="b9f60-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b9f60-109">HRESULT</span></span>|<span data-ttu-id="b9f60-110">Описание</span><span class="sxs-lookup"><span data-stu-id="b9f60-110">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b9f60-111">Функция была успешно помечена.</span><span class="sxs-lookup"><span data-stu-id="b9f60-111">The function was successfully marked.</span></span>|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|<span data-ttu-id="b9f60-112">Функция не может быть помечена как пользовательский код, так как ее отладка невозможна.</span><span class="sxs-lookup"><span data-stu-id="b9f60-112">The function could not be marked as user code because it cannot be debugged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9f60-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="b9f60-113">Remarks</span></span>  

 <span data-ttu-id="b9f60-114">Только мой код пошаговое средство пропускает код, не являющийся пользовательским.</span><span class="sxs-lookup"><span data-stu-id="b9f60-114">A Just My Code stepper will skip non-user code.</span></span> <span data-ttu-id="b9f60-115">Пользовательский код должен быть подмножеством отлаживаемого кода.</span><span class="sxs-lookup"><span data-stu-id="b9f60-115">User code must be a subset of debuggable code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9f60-116">Требования</span><span class="sxs-lookup"><span data-stu-id="b9f60-116">Requirements</span></span>  

 <span data-ttu-id="b9f60-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9f60-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9f60-118">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b9f60-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9f60-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9f60-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9f60-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9f60-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
