---
description: 'Дополнительные сведения о методе: ICorDebugModule:: EnableJITDebugging'
title: Метод ICorDebugModule::EnableJITDebugging
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableJITDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableJITDebugging
helpviewer_keywords:
- ICorDebugModule::EnableJITDebugging method [.NET Framework debugging]
- EnableJITDebugging method [.NET Framework debugging]
ms.assetid: 0a65e2a4-5bb6-496c-ae6f-40474426b5a6
topic_type:
- apiref
ms.openlocfilehash: 30077bd586e1cb9cb8766290804e31f5999d9e72
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722689"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a><span data-ttu-id="e324c-103">Метод ICorDebugModule::EnableJITDebugging</span><span class="sxs-lookup"><span data-stu-id="e324c-103">ICorDebugModule::EnableJITDebugging Method</span></span>

<span data-ttu-id="e324c-104">Определяет, сохраняет ли JIT-компилятор сведения об отладке для методов в этом модуле.</span><span class="sxs-lookup"><span data-stu-id="e324c-104">Controls whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e324c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e324c-105">Syntax</span></span>  
  
```cpp  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e324c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e324c-106">Parameters</span></span>  

 `bTrackJITInfo`  
 <span data-ttu-id="e324c-107">окне Установите это значение, чтобы `true` разрешить JIT-компилятору сохранять сведения о сопоставлении между версией MSIL и версией каждого метода в этом модуле, скомпилированном по требованию.</span><span class="sxs-lookup"><span data-stu-id="e324c-107">[in] Set this value to `true` to enable the JIT compiler to preserve mapping information between the Microsoft intermediate language (MSIL) version and the JIT-compiled version of each method in this module.</span></span>  
  
 `bAllowJitOpts`  
 <span data-ttu-id="e324c-108">окне Установите это значение, чтобы `true` разрешить JIT-компилятору создавать код с определенными оптимизацией JIT для отладки.</span><span class="sxs-lookup"><span data-stu-id="e324c-108">[in] Set this value to `true` to enable the JIT compiler to generate code with certain JIT-specific optimizations for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e324c-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="e324c-109">Remarks</span></span>  

 <span data-ttu-id="e324c-110">JIT-отладка включается по умолчанию для всех модулей, загружаемых при активном отладчике.</span><span class="sxs-lookup"><span data-stu-id="e324c-110">JIT debugging is enabled by default for all modules that are loaded when the debugger is active.</span></span> <span data-ttu-id="e324c-111">Программное включение или отключение параметров переопределяет глобальные параметры.</span><span class="sxs-lookup"><span data-stu-id="e324c-111">Programmatically enabling or disabling the settings overrides global settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e324c-112">Требования</span><span class="sxs-lookup"><span data-stu-id="e324c-112">Requirements</span></span>  

 <span data-ttu-id="e324c-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e324c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e324c-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e324c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e324c-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e324c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e324c-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e324c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
