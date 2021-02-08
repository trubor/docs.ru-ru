---
description: 'Дополнительные сведения о методе: IcorDebugVariableHome:: Жетливеранже'
title: 'Метод IcorDebugVariableHome:: Жетливеранже'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetLiveRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetLiveRange
helpviewer_keywords:
- ICorDebugVariableHome::GetLiveRange method [.NET Framework debugging]
- GetLiveRange method, ICorDebugVariableFrame interface [.NET Framework debugging]
ms.assetid: 87277e1a-1595-4729-9e25-d1c3ac18ce5f
topic_type:
- apiref
ms.openlocfilehash: daa53a164c7660826d44285ce21ecea1b649a727
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800842"
---
# <a name="icordebugvariablehomegetliverange-method"></a><span data-ttu-id="4acd8-103">Метод IcorDebugVariableHome:: Жетливеранже</span><span class="sxs-lookup"><span data-stu-id="4acd8-103">IcorDebugVariableHome::GetLiveRange Method</span></span>

<span data-ttu-id="4acd8-104">Возвращает собственный диапазон, в котором эта переменная находится в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="4acd8-104">Gets the native range over which this variable is live.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4acd8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4acd8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLiveRange(  
    [out] ULONG32* pStartOffset,  
    [out] ULONG32 *pEndOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4acd8-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="4acd8-106">Parameters</span></span>  

 `pStartOffset`  
 <span data-ttu-id="4acd8-107">заполняет Логическое смещение, при котором переменная впервые находится в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="4acd8-107">[out] The logical offset at which the variable is first live.</span></span>  
  
 `pEndOffset`  
 <span data-ttu-id="4acd8-108">заполняет Логическое смещение сразу после точки, в которой переменная была последней динамической.</span><span class="sxs-lookup"><span data-stu-id="4acd8-108">[out] The logical offset immediately after the point at which the variable is last live.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4acd8-109">Требования</span><span class="sxs-lookup"><span data-stu-id="4acd8-109">Requirements</span></span>  

 <span data-ttu-id="4acd8-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4acd8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4acd8-111">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4acd8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4acd8-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4acd8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4acd8-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4acd8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4acd8-114">См. также</span><span class="sxs-lookup"><span data-stu-id="4acd8-114">See also</span></span>

- [<span data-ttu-id="4acd8-115">Интерфейс ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="4acd8-115">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
