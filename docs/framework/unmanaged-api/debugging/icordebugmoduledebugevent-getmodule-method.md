---
description: 'Дополнительные сведения о методе: Икордебугмодуледебужевент:: module'
title: Метод ICorDebugModuleDebugEvent::GetModule
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
ms.openlocfilehash: c6d7171da231576ff90f54aaefe4b473af0afd40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790741"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="0986a-103">Метод ICorDebugModuleDebugEvent::GetModule</span><span class="sxs-lookup"><span data-stu-id="0986a-103">ICorDebugModuleDebugEvent::GetModule Method</span></span>

<span data-ttu-id="0986a-104">Возвращает объединенный модуль, который только что был загружен или выгружен.</span><span class="sxs-lookup"><span data-stu-id="0986a-104">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0986a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0986a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0986a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0986a-106">Parameters</span></span>  

 `ppModule`  
 <span data-ttu-id="0986a-107">[out] Указатель на адрес объекта ICorDebugModule, представляющего объединенный модуль, который был только что загружен или выгружен.</span><span class="sxs-lookup"><span data-stu-id="0986a-107">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0986a-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="0986a-108">Remarks</span></span>  

 <span data-ttu-id="0986a-109">Можно вызвать метод [GetEventKind](icordebugdebugevent-geteventkind-method.md) , чтобы определить, был ли модуль загружен или выгружен.</span><span class="sxs-lookup"><span data-stu-id="0986a-109">You can call the [GetEventKind](icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0986a-110">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="0986a-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0986a-111">Требования</span><span class="sxs-lookup"><span data-stu-id="0986a-111">Requirements</span></span>  

 <span data-ttu-id="0986a-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0986a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0986a-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0986a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0986a-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0986a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0986a-115">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0986a-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0986a-116">См. также</span><span class="sxs-lookup"><span data-stu-id="0986a-116">See also</span></span>

- [<span data-ttu-id="0986a-117">Интерфейс ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="0986a-117">ICorDebugModuleDebugEvent Interface</span></span>](icordebugmoduledebugevent-interface.md)
- [<span data-ttu-id="0986a-118">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="0986a-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
