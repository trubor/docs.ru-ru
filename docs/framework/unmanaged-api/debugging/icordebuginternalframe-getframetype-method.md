---
description: 'Дополнительные сведения о методе: ICorDebugInternalFrame:: GetFrameType'
title: Метод ICorDebugInternalFrame::GetFrameType
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame.GetFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame::GetFrameType
helpviewer_keywords:
- GetFrameType method [.NET Framework debugging]
- ICorDebugInternalFrame::GetFrameType method [.NET Framework debugging]
ms.assetid: da278a29-dc2e-4bf7-96ce-801bdc4d7025
topic_type:
- apiref
ms.openlocfilehash: ea96f032ebfa5914503287d124242b74a84ea11f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791183"
---
# <a name="icordebuginternalframegetframetype-method"></a><span data-ttu-id="32a27-103">Метод ICorDebugInternalFrame::GetFrameType</span><span class="sxs-lookup"><span data-stu-id="32a27-103">ICorDebugInternalFrame::GetFrameType Method</span></span>

<span data-ttu-id="32a27-104">Возвращает тип этого внутреннего кадра.</span><span class="sxs-lookup"><span data-stu-id="32a27-104">Gets the type of this internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32a27-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="32a27-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameType (  
    [out] CorDebugInternalFrameType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32a27-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="32a27-106">Parameters</span></span>  

 `pType`  
 <span data-ttu-id="32a27-107">заполняет Указатель на значение перечисления CorDebugInternalFrameType, указывающее тип внутреннего кадра, представленного этим `ICorDebugInternalFrame` объектом.</span><span class="sxs-lookup"><span data-stu-id="32a27-107">[out] A pointer to a value of the CorDebugInternalFrameType enumeration that indicates the type of internal frame represented by this `ICorDebugInternalFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32a27-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="32a27-108">Remarks</span></span>  

 <span data-ttu-id="32a27-109">Тип внутреннего кадра никогда не будет STUBFRAME_NONE.</span><span class="sxs-lookup"><span data-stu-id="32a27-109">The internal frame type will never be STUBFRAME_NONE.</span></span> <span data-ttu-id="32a27-110">Отладчики должны корректно пропускать нераспознаваемые типы внутренних кадров.</span><span class="sxs-lookup"><span data-stu-id="32a27-110">Debuggers should gracefully ignore unrecognized internal frame types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32a27-111">Требования</span><span class="sxs-lookup"><span data-stu-id="32a27-111">Requirements</span></span>  

 <span data-ttu-id="32a27-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32a27-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32a27-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="32a27-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32a27-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32a27-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32a27-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32a27-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
