---
description: 'Дополнительные сведения о методе: Икордебуглоадедмодуле:: GetBaseAddress'
title: Метод ICorDebugLoadedModule::GetBaseAddress
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
ms.openlocfilehash: 2852131d543cfb9593cf4ff607d1f752226c2880
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801271"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="6ec5f-103">Метод ICorDebugLoadedModule::GetBaseAddress</span><span class="sxs-lookup"><span data-stu-id="6ec5f-103">ICorDebugLoadedModule::GetBaseAddress Method</span></span>

<span data-ttu-id="6ec5f-104">Получает базовый адрес загруженного модуля.</span><span class="sxs-lookup"><span data-stu-id="6ec5f-104">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ec5f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6ec5f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ec5f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6ec5f-106">Parameters</span></span>  

 `pAddress`  
 <span data-ttu-id="6ec5f-107">[out] Указатель на базовый адрес загруженного модуля.</span><span class="sxs-lookup"><span data-stu-id="6ec5f-107">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ec5f-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="6ec5f-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6ec5f-109">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="6ec5f-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ec5f-110">Требования</span><span class="sxs-lookup"><span data-stu-id="6ec5f-110">Requirements</span></span>  

 <span data-ttu-id="6ec5f-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ec5f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ec5f-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6ec5f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6ec5f-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6ec5f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ec5f-114">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ec5f-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ec5f-115">См. также</span><span class="sxs-lookup"><span data-stu-id="6ec5f-115">See also</span></span>

- [<span data-ttu-id="6ec5f-116">Интерфейс ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="6ec5f-116">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="6ec5f-117">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="6ec5f-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
