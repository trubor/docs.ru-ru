---
description: 'Дополнительные сведения о методе: ICorDebugEval2:: NewStringWithLength'
title: Метод ICorDebugEval2::NewStringWithLength
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewStringWithLength
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewStringWithLength
helpviewer_keywords:
- NewStringWithLength method [.NET Framework debugging]
- ICorDebugEval2::NewStringWithLength method [.NET Framework debugging]
ms.assetid: d5f54a34-6335-4708-b407-a756ec70fab4
topic_type:
- apiref
ms.openlocfilehash: 23864dabefcb4fc12f73c66bc2d19a6cca1aacf0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693529"
---
# <a name="icordebugeval2newstringwithlength-method"></a><span data-ttu-id="b7c53-103">Метод ICorDebugEval2::NewStringWithLength</span><span class="sxs-lookup"><span data-stu-id="b7c53-103">ICorDebugEval2::NewStringWithLength Method</span></span>

<span data-ttu-id="b7c53-104">Создает строку указанной длины с указанным содержимым.</span><span class="sxs-lookup"><span data-stu-id="b7c53-104">Creates a string of the specified length, with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7c53-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b7c53-105">Syntax</span></span>  
  
```cpp  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7c53-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b7c53-106">Parameters</span></span>  

 `string`  
 <span data-ttu-id="b7c53-107">окне Указатель на строковое значение.</span><span class="sxs-lookup"><span data-stu-id="b7c53-107">[in] A pointer to the string value.</span></span>  
  
 `uiLength`  
 <span data-ttu-id="b7c53-108">окне Длина строки.</span><span class="sxs-lookup"><span data-stu-id="b7c53-108">[in] Length of the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7c53-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="b7c53-109">Remarks</span></span>  

 <span data-ttu-id="b7c53-110">Если конечный нуль-символ строки должен быть в управляемой строке, вызывающий `NewStringWithLength` метод должен обеспечить, чтобы длина строки включала завершающий нуль-символ.</span><span class="sxs-lookup"><span data-stu-id="b7c53-110">If the string's trailing null character is expected to be in the managed string, the caller of the `NewStringWithLength` method must ensure that the string length includes the trailing null character.</span></span>  
  
 <span data-ttu-id="b7c53-111">Строка всегда создается в домене приложения, в котором в данный момент выполняется поток.</span><span class="sxs-lookup"><span data-stu-id="b7c53-111">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7c53-112">Требования</span><span class="sxs-lookup"><span data-stu-id="b7c53-112">Requirements</span></span>  

 <span data-ttu-id="b7c53-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7c53-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7c53-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7c53-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7c53-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7c53-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7c53-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7c53-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
