---
description: 'Дополнительные сведения о методе: ICorDebugStepper2:: SetJMC'
title: Метод ICorDebugStepper2::SetJMC
ms.date: 03/30/2017
api_name:
- ICorDebugStepper2.SetJMC
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper2::SetJMC
helpviewer_keywords:
- ICorDebugStepper2::SetJMC method [.NET Framework debugging]
- SetJMC method [.NET Framework debugging]
ms.assetid: f5cdc135-6db4-4b32-9dd1-260ec58b774f
topic_type:
- apiref
ms.openlocfilehash: 07178ab90bb392e64c9d8a8fddf961efbb268002
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717541"
---
# <a name="icordebugstepper2setjmc-method"></a><span data-ttu-id="f6ea4-103">Метод ICorDebugStepper2::SetJMC</span><span class="sxs-lookup"><span data-stu-id="f6ea4-103">ICorDebugStepper2::SetJMC Method</span></span>

<span data-ttu-id="f6ea4-104">Задает значение, указывающее, следует ли выполнить шаги для этого параметра ICorDebugStepper только с помощью кода, созданного разработчиком приложения.</span><span class="sxs-lookup"><span data-stu-id="f6ea4-104">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span> <span data-ttu-id="f6ea4-105">Этот процесс также известен как отладка "только мой код" (JMC).</span><span class="sxs-lookup"><span data-stu-id="f6ea4-105">This process is also known as just my code (JMC) debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6ea4-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f6ea4-106">Syntax</span></span>  
  
```cpp  
HRESULT SetJMC (  
    [in] BOOL    fIsJMCStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6ea4-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="f6ea4-107">Parameters</span></span>  

 `fIsJMCStepper`  
 <span data-ttu-id="f6ea4-108">окне Установите в значение `true` только для шага с помощью кода, созданного разработчиком приложения; в противном случае задайте для значение `false` .</span><span class="sxs-lookup"><span data-stu-id="f6ea4-108">[in] Set to `true` to step only through code that is authored by an application's developer; otherwise, set to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6ea4-109">Требования</span><span class="sxs-lookup"><span data-stu-id="f6ea4-109">Requirements</span></span>  

 <span data-ttu-id="f6ea4-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6ea4-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6ea4-111">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f6ea4-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6ea4-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6ea4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6ea4-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6ea4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
