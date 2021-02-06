---
description: 'Дополнительные сведения о методе: ICorDebugModule:: resize'
title: Метод ICorDebugModule::GetSize
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetSize method [.NET Framework debugging]
ms.assetid: 5c68375d-145d-46ef-a7c8-2dc4257472de
topic_type:
- apiref
ms.openlocfilehash: b2179c8830911e417ccd482fe72438c4cd7fd3df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660158"
---
# <a name="icordebugmodulegetsize-method"></a><span data-ttu-id="4c6c4-103">Метод ICorDebugModule::GetSize</span><span class="sxs-lookup"><span data-stu-id="4c6c4-103">ICorDebugModule::GetSize Method</span></span>

<span data-ttu-id="4c6c4-104">Возвращает размер модуля (в байтах).</span><span class="sxs-lookup"><span data-stu-id="4c6c4-104">Gets the size, in bytes, of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c6c4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4c6c4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
    [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c6c4-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="4c6c4-106">Parameters</span></span>  

 `pcBytes`  
 <span data-ttu-id="4c6c4-107">заполняет Размер модуля в байтах.</span><span class="sxs-lookup"><span data-stu-id="4c6c4-107">[out] The size of the module in bytes.</span></span>  
  
 <span data-ttu-id="4c6c4-108">Если модуль был создан из генератора образов в машинном кодах (NGen.exe), размер модуля будет равен нулю.</span><span class="sxs-lookup"><span data-stu-id="4c6c4-108">If the module was produced from the native image generator (NGen.exe), the size of the module will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c6c4-109">Требования</span><span class="sxs-lookup"><span data-stu-id="4c6c4-109">Requirements</span></span>  

 <span data-ttu-id="4c6c4-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c6c4-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c6c4-111">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4c6c4-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4c6c4-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c6c4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c6c4-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c6c4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
