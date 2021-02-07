---
description: 'Дополнительные сведения о методе ICorDebugFrame:: с кодом'
title: Метод ICorDebugFrame::GetCode
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCode
helpviewer_keywords:
- GetCode method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCode method [.NET Framework debugging]
ms.assetid: fbaa0794-a031-4015-8beb-2749e47ac340
topic_type:
- apiref
ms.openlocfilehash: f45e0a29530a8b4ddbeaa92db4489a030ac1ae79
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693035"
---
# <a name="icordebugframegetcode-method"></a><span data-ttu-id="77abb-103">Метод ICorDebugFrame::GetCode</span><span class="sxs-lookup"><span data-stu-id="77abb-103">ICorDebugFrame::GetCode Method</span></span>

<span data-ttu-id="77abb-104">Возвращает указатель на код, связанный с этим кадром стека.</span><span class="sxs-lookup"><span data-stu-id="77abb-104">Gets a pointer to the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77abb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="77abb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCode (  
    [out] ICorDebugCode      **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77abb-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="77abb-106">Parameters</span></span>  

 `ppCode`  
 <span data-ttu-id="77abb-107">заполняет Указатель на адрес объекта ICorDebugCode, представляющий код, связанный с этим кадром.</span><span class="sxs-lookup"><span data-stu-id="77abb-107">[out] A pointer to the address of an ICorDebugCode object that represents the code associated with this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77abb-108">Требования</span><span class="sxs-lookup"><span data-stu-id="77abb-108">Requirements</span></span>  

 <span data-ttu-id="77abb-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77abb-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77abb-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="77abb-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77abb-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77abb-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77abb-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77abb-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
