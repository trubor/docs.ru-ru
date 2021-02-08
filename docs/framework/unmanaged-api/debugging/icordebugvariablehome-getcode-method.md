---
description: 'Дополнительные сведения о методе: ICorDebugVariableHome:: a Code'
title: 'Метод ICorDebugVariableHome:: с кодом'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetCode
helpviewer_keywords:
- ICorDebugVariableHome::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: ef002890-4a7b-4a5d-abbf-16c60083f794
topic_type:
- apiref
ms.openlocfilehash: e3ff96816e580fe3cd1cee782dc5bd4166f08a14
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794641"
---
# <a name="icordebugvariablehomegetcode-method"></a><span data-ttu-id="c07ac-103">Метод ICorDebugVariableHome:: с кодом</span><span class="sxs-lookup"><span data-stu-id="c07ac-103">ICorDebugVariableHome::GetCode Method</span></span>

<span data-ttu-id="c07ac-104">Возвращает экземпляр "ICorDebugCode", который содержит этот объект [ICorDebugVariableHome](icordebugvariablehome-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c07ac-104">Gets the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c07ac-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c07ac-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c07ac-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c07ac-106">Parameters</span></span>  

 `ppCode`  
 <span data-ttu-id="c07ac-107">заполняет Указатель на адрес экземпляра ICorDebugCode, который содержит этот объект [ICorDebugVariableHome](icordebugvariablehome-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c07ac-107">[out] A pointer to the address of the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c07ac-108">Требования</span><span class="sxs-lookup"><span data-stu-id="c07ac-108">Requirements</span></span>  

 <span data-ttu-id="c07ac-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c07ac-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c07ac-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c07ac-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c07ac-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c07ac-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c07ac-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c07ac-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c07ac-113">См. также</span><span class="sxs-lookup"><span data-stu-id="c07ac-113">See also</span></span>

- [<span data-ttu-id="c07ac-114">Интерфейс ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="c07ac-114">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
