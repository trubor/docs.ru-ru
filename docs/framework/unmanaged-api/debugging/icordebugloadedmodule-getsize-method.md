---
description: 'Дополнительные сведения о методе: Икордебуглоадедмодуле:: resize'
title: Метод ICorDebugLoadedModule::GetSize
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
ms.openlocfilehash: 6701d2578559a039f352df19bf9e859658c6687f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801245"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="7106e-103">Метод ICorDebugLoadedModule::GetSize</span><span class="sxs-lookup"><span data-stu-id="7106e-103">ICorDebugLoadedModule::GetSize Method</span></span>

<span data-ttu-id="7106e-104">Возвращает размер в байтах загруженного модуля.</span><span class="sxs-lookup"><span data-stu-id="7106e-104">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7106e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7106e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7106e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7106e-106">Parameters</span></span>  

 `pcBytes`  
 <span data-ttu-id="7106e-107">[out] Указатель на число байтов в загруженном модуле.</span><span class="sxs-lookup"><span data-stu-id="7106e-107">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7106e-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="7106e-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7106e-109">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="7106e-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7106e-110">Требования</span><span class="sxs-lookup"><span data-stu-id="7106e-110">Requirements</span></span>  

 <span data-ttu-id="7106e-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7106e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7106e-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7106e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7106e-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7106e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7106e-114">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7106e-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7106e-115">См. также</span><span class="sxs-lookup"><span data-stu-id="7106e-115">See also</span></span>

- [<span data-ttu-id="7106e-116">Интерфейс ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="7106e-116">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="7106e-117">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="7106e-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
