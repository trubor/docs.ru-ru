---
description: 'Дополнительные сведения о методе: ICorDebugController::D етач'
title: Метод ICorDebugController::Detach
ms.date: 03/30/2017
api_name:
- ICorDebugController.Detach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Detach
helpviewer_keywords:
- Detach method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Detach method [.NET Framework debugging]
ms.assetid: 06fae364-f2c6-4a50-aa7e-3da9f2684dc3
topic_type:
- apiref
ms.openlocfilehash: 763386fa72fab023becf4a360556e61d500c7949
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764671"
---
# <a name="icordebugcontrollerdetach-method"></a><span data-ttu-id="f1834-103">Метод ICorDebugController::Detach</span><span class="sxs-lookup"><span data-stu-id="f1834-103">ICorDebugController::Detach Method</span></span>

<span data-ttu-id="f1834-104">Отсоединяет отладчик от процесса или домена приложения.</span><span class="sxs-lookup"><span data-stu-id="f1834-104">Detaches the debugger from the process or application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1834-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f1834-105">Syntax</span></span>  
  
```cpp  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="f1834-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="f1834-106">Remarks</span></span>  

 <span data-ttu-id="f1834-107">Процесс или домен приложения продолжит выполнение в обычном режиме, но объект "ICorDebugProcess" или "ICorDebugAppDomain" больше не является допустимым, и последующие обратные вызовы выполняться не будут.</span><span class="sxs-lookup"><span data-stu-id="f1834-107">The process or application domain continues execution normally, but the "ICorDebugProcess" or "ICorDebugAppDomain" object is no longer valid and no further callbacks will occur.</span></span>  
  
 <span data-ttu-id="f1834-108">В платформа .NET Framework версии 2,0, если включена отладка неуправляемого кода, этот метод завершится ошибкой из-за ограничений операционной системы.</span><span class="sxs-lookup"><span data-stu-id="f1834-108">In the .NET Framework version 2.0, if unmanaged debugging is enabled, this method will fail due to operating system limitations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1834-109">Требования</span><span class="sxs-lookup"><span data-stu-id="f1834-109">Requirements</span></span>  

 <span data-ttu-id="f1834-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1834-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1834-111">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f1834-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1834-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1834-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1834-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1834-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1834-114">См. также</span><span class="sxs-lookup"><span data-stu-id="f1834-114">See also</span></span>
