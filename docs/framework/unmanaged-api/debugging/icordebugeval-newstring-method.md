---
description: 'Дополнительные сведения о методе: ICorDebugEval:: NewString'
title: Метод ICorDebugEval::NewString
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewString
helpviewer_keywords:
- NewString method [.NET Framework debugging]
- ICorDebugEval::NewString method [.NET Framework debugging]
ms.assetid: 29e7a14b-d50e-4852-bfda-011b76c0c9ee
topic_type:
- apiref
ms.openlocfilehash: 21eb49900d84cb1ad1f68a701998a4a778c3ef17
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693841"
---
# <a name="icordebugevalnewstring-method"></a><span data-ttu-id="50758-103">Метод ICorDebugEval::NewString</span><span class="sxs-lookup"><span data-stu-id="50758-103">ICorDebugEval::NewString Method</span></span>

<span data-ttu-id="50758-104">Выделяет новый экземпляр строки с указанным содержимым.</span><span class="sxs-lookup"><span data-stu-id="50758-104">Allocates a new string instance with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50758-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="50758-105">Syntax</span></span>  
  
```cpp  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50758-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="50758-106">Parameters</span></span>  

 `string`  
 <span data-ttu-id="50758-107">окне Указатель на содержимое строки.</span><span class="sxs-lookup"><span data-stu-id="50758-107">[in] Pointer to the contents for the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50758-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="50758-108">Remarks</span></span>  

 <span data-ttu-id="50758-109">Строка всегда создается в домене приложения, в котором в данный момент выполняется поток.</span><span class="sxs-lookup"><span data-stu-id="50758-109">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50758-110">Требования</span><span class="sxs-lookup"><span data-stu-id="50758-110">Requirements</span></span>  

 <span data-ttu-id="50758-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50758-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50758-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="50758-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50758-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50758-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50758-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50758-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
