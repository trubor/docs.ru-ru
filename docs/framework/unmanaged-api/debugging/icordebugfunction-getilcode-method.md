---
description: 'Дополнительные сведения: метод ICorDebugFunction:: GetILCode'
title: Метод ICorDebugFunction::GetILCode
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetILCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetILCode
helpviewer_keywords:
- ICorDebugFunction::GetILCode method [.NET Framework debugging]
- GetILCode method [.NET Framework debugging]
ms.assetid: f794dd47-a7cd-47f6-96e9-a41a4dae8e72
topic_type:
- apiref
ms.openlocfilehash: 3b7bb29a028b189b24d3fbf02edc8190d9989a51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692528"
---
# <a name="icordebugfunctiongetilcode-method"></a><span data-ttu-id="c6e50-103">Метод ICorDebugFunction::GetILCode</span><span class="sxs-lookup"><span data-stu-id="c6e50-103">ICorDebugFunction::GetILCode Method</span></span>

<span data-ttu-id="c6e50-104">Возвращает экземпляр ICorDebugCode, представляющий код на языке MSIL, связанный с данным объектом ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="c6e50-104">Gets the ICorDebugCode instance that represents the Microsoft intermediate language (MSIL) code associated with this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6e50-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c6e50-105">Syntax</span></span>  
  
```cpp  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6e50-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c6e50-106">Parameters</span></span>  

 `ppCode`  
 <span data-ttu-id="c6e50-107">заполняет Указатель на `ICorDebugCode` экземпляр или значение null, если функция не была скомпилирована в MSIL.</span><span class="sxs-lookup"><span data-stu-id="c6e50-107">[out] A pointer to the `ICorDebugCode` instance, or null, if the function was not compiled into MSIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6e50-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="c6e50-108">Remarks</span></span>  

 <span data-ttu-id="c6e50-109">Если функция "изменить и продолжить" была разрешена для этой функции, метод получит `GetILCode` код MSIL, соответствующий измененной версии кода этой функции в общеязыковой среде выполнения (CLR).</span><span class="sxs-lookup"><span data-stu-id="c6e50-109">If Edit and Continue has been allowed on this function, the `GetILCode` method will get the MSIL code corresponding to this function's edited version of the code in the common language runtime (CLR).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6e50-110">Требования</span><span class="sxs-lookup"><span data-stu-id="c6e50-110">Requirements</span></span>  

 <span data-ttu-id="c6e50-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6e50-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6e50-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c6e50-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6e50-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6e50-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6e50-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6e50-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
