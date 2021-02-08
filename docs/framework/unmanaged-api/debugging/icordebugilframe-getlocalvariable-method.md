---
description: 'Дополнительные сведения о методе: ICorDebugILFrame:: Жетлокалвариабле'
title: Метод ICorDebugILFrame::GetLocalVariable
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetLocalVariable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetLocalVariable
helpviewer_keywords:
- ICorDebugILFrame::GetLocalVariable method [.NET Framework debugging]
- GetLocalVariable method [.NET Framework debugging]
ms.assetid: c8706356-d50b-4f87-a40c-39c3b7f4fd38
topic_type:
- apiref
ms.openlocfilehash: c4bb3e5a5d970539607efbaf55f3f7f08f7e72af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791378"
---
# <a name="icordebugilframegetlocalvariable-method"></a><span data-ttu-id="64fe7-103">Метод ICorDebugILFrame::GetLocalVariable</span><span class="sxs-lookup"><span data-stu-id="64fe7-103">ICorDebugILFrame::GetLocalVariable Method</span></span>

<span data-ttu-id="64fe7-104">Возвращает значение указанной локальной переменной в кадре стека MSIL.</span><span class="sxs-lookup"><span data-stu-id="64fe7-104">Gets the value of the specified local variable in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64fe7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="64fe7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariable (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64fe7-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="64fe7-106">Parameters</span></span>  

 `dwIndex`  
 <span data-ttu-id="64fe7-107">окне Индекс локальной переменной в этом кадре стека MSIL.</span><span class="sxs-lookup"><span data-stu-id="64fe7-107">[in] The index of the local variable in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="64fe7-108">[из] Указатель на адрес объекта ICorDebugValue, представляющего извлеченное значение.</span><span class="sxs-lookup"><span data-stu-id="64fe7-108">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64fe7-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="64fe7-109">Remarks</span></span>  

 <span data-ttu-id="64fe7-110">`GetLocalVariable`Метод можно использовать либо в кадре стека MSIL, либо в кадре JIT-компиляции.</span><span class="sxs-lookup"><span data-stu-id="64fe7-110">The `GetLocalVariable` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64fe7-111">Требования</span><span class="sxs-lookup"><span data-stu-id="64fe7-111">Requirements</span></span>  

 <span data-ttu-id="64fe7-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64fe7-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64fe7-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="64fe7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64fe7-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64fe7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64fe7-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64fe7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
