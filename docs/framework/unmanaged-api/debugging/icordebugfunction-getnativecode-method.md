---
description: 'Дополнительные сведения: метод ICorDebugFunction:: Жетнативекоде'
title: Метод ICorDebugFunction::GetNativeCode
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetNativeCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetNativeCode
helpviewer_keywords:
- GetNativeCode method [.NET Framework debugging]
- ICorDebugFunction::GetNativeCode method [.NET Framework debugging]
ms.assetid: c8a34916-0eef-4987-8d29-c8bcb4be9cf6
topic_type:
- apiref
ms.openlocfilehash: 8938e11a5fdc3aa693faf04eec639941475d95ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692450"
---
# <a name="icordebugfunctiongetnativecode-method"></a><span data-ttu-id="41ad8-103">Метод ICorDebugFunction::GetNativeCode</span><span class="sxs-lookup"><span data-stu-id="41ad8-103">ICorDebugFunction::GetNativeCode Method</span></span>

<span data-ttu-id="41ad8-104">Возвращает машинный код для функции, представленной этим экземпляром ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="41ad8-104">Gets the native code for the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41ad8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="41ad8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41ad8-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="41ad8-106">Parameters</span></span>  

 `ppCode`  
 <span data-ttu-id="41ad8-107">заполняет Указатель на экземпляр ICorDebugCode, представляющий машинный код для этой функции, или значение null, если эта функция является кодом MSIL, который не был скомпилирован JIT-КОМПИЛЯТОРом.</span><span class="sxs-lookup"><span data-stu-id="41ad8-107">[out] A pointer to the ICorDebugCode instance that represents the native code for this function, or null, if this function is Microsoft intermediate language (MSIL) code that has not been just-in-time (JIT) compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41ad8-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="41ad8-108">Remarks</span></span>  

 <span data-ttu-id="41ad8-109">Если функция, представленная этим `ICorDebugFunction` экземпляром, скомпилирована JIT-компилятором более одного раза, как в случае универсальных типов, `GetNativeCode` возвращает произвольный объект машинного кода.</span><span class="sxs-lookup"><span data-stu-id="41ad8-109">If the function that is represented by this `ICorDebugFunction` instance has been JIT-compiled more than once, as in the case of generic types, `GetNativeCode` returns a random native code object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41ad8-110">Требования</span><span class="sxs-lookup"><span data-stu-id="41ad8-110">Requirements</span></span>  

 <span data-ttu-id="41ad8-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41ad8-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41ad8-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="41ad8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41ad8-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41ad8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41ad8-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41ad8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
