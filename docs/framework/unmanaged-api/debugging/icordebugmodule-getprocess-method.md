---
description: 'Дополнительные сведения о методе: ICorDebugModule:: onprocess'
title: Метод ICorDebugModule::GetProcess
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetProcess method [.NET Framework debugging]
ms.assetid: 5e13446c-0271-446c-924a-9072c0e6eeae
topic_type:
- apiref
ms.openlocfilehash: eb8497ac8ec6913fe079d6f5f148d3769bf6633a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691631"
---
# <a name="icordebugmodulegetprocess-method"></a><span data-ttu-id="ce339-103">Метод ICorDebugModule::GetProcess</span><span class="sxs-lookup"><span data-stu-id="ce339-103">ICorDebugModule::GetProcess Method</span></span>

<span data-ttu-id="ce339-104">Возвращает содержащий процесс этого модуля.</span><span class="sxs-lookup"><span data-stu-id="ce339-104">Gets the containing process of this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce339-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ce339-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce339-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ce339-106">Parameters</span></span>  

 `ppProcess`  
 <span data-ttu-id="ce339-107">заполняет Указатель на адрес объекта ICorDebugProcess, который представляет процесс, содержащий этот модуль.</span><span class="sxs-lookup"><span data-stu-id="ce339-107">[out] A pointer to the address of an ICorDebugProcess object that represents the process containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce339-108">Требования</span><span class="sxs-lookup"><span data-stu-id="ce339-108">Requirements</span></span>  

 <span data-ttu-id="ce339-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce339-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce339-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ce339-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce339-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce339-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce339-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce339-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
