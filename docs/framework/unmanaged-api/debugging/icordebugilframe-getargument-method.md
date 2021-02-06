---
description: 'Дополнительные сведения о методе: ICorDebugILFrame:: Argument'
title: Метод ICorDebugILFrame::GetArgument
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetArgument
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetArgument
helpviewer_keywords:
- GetArgument method [.NET Framework debugging]
- ICorDebugILFrame::GetArgument method [.NET Framework debugging]
ms.assetid: 4e2fd423-f643-4c27-ba5f-41b5ebc3b416
topic_type:
- apiref
ms.openlocfilehash: c845f3c07502f3b1ce564833ee6ef98e3305463f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650512"
---
# <a name="icordebugilframegetargument-method"></a><span data-ttu-id="3cafa-103">Метод ICorDebugILFrame::GetArgument</span><span class="sxs-lookup"><span data-stu-id="3cafa-103">ICorDebugILFrame::GetArgument Method</span></span>

<span data-ttu-id="3cafa-104">Возвращает значение указанного аргумента в кадре стека MSIL.</span><span class="sxs-lookup"><span data-stu-id="3cafa-104">Gets the value of the specified argument in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cafa-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3cafa-105">Syntax</span></span>  
  
```cpp  
HRESULT GetArgument (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3cafa-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="3cafa-106">Parameters</span></span>  

 `dwIndex`  
 <span data-ttu-id="3cafa-107">окне Индекс аргумента в этом кадре стека MSIL.</span><span class="sxs-lookup"><span data-stu-id="3cafa-107">[in] The index of the argument in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="3cafa-108">[из] Указатель на адрес объекта ICorDebugValue, представляющего извлеченное значение.</span><span class="sxs-lookup"><span data-stu-id="3cafa-108">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3cafa-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="3cafa-109">Remarks</span></span>  

 <span data-ttu-id="3cafa-110">`GetArgument`Метод можно использовать либо в кадре стека MSIL, либо в кадре JIT-компиляции.</span><span class="sxs-lookup"><span data-stu-id="3cafa-110">The `GetArgument` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cafa-111">Требования</span><span class="sxs-lookup"><span data-stu-id="3cafa-111">Requirements</span></span>  

 <span data-ttu-id="3cafa-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3cafa-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cafa-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3cafa-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3cafa-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3cafa-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3cafa-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cafa-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
