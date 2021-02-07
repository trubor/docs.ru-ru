---
description: 'Дополнительные сведения о методе: ICorDebugAssembly:: onprocess'
title: Метод ICorDebugAssembly::GetProcess
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetProcess
helpviewer_keywords:
- ICorDebugAssembly::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: ea52be06-0a16-4f57-afca-4287d72e76c4
topic_type:
- apiref
ms.openlocfilehash: b121d7f892f6e2e2aa76290d4aee51767c72e9fc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754154"
---
# <a name="icordebugassemblygetprocess-method"></a><span data-ttu-id="26d7b-103">Метод ICorDebugAssembly::GetProcess</span><span class="sxs-lookup"><span data-stu-id="26d7b-103">ICorDebugAssembly::GetProcess Method</span></span>

<span data-ttu-id="26d7b-104">Возвращает указатель интерфейса на процесс, в котором выполняется данный экземпляр ICorDebugAssembly.</span><span class="sxs-lookup"><span data-stu-id="26d7b-104">Gets an interface pointer to the process in which this ICorDebugAssembly instance is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26d7b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="26d7b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26d7b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="26d7b-106">Parameters</span></span>  

 `ppProcess`  
 <span data-ttu-id="26d7b-107">заполняет Указатель на интерфейс ICorDebugProcess, представляющий процесс.</span><span class="sxs-lookup"><span data-stu-id="26d7b-107">[out] A pointer to an ICorDebugProcess interface that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26d7b-108">Требования</span><span class="sxs-lookup"><span data-stu-id="26d7b-108">Requirements</span></span>  

 <span data-ttu-id="26d7b-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26d7b-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26d7b-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="26d7b-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26d7b-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26d7b-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26d7b-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26d7b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
