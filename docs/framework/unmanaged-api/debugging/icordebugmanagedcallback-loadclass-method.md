---
description: 'Дополнительные сведения о методе: ICorDebugManagedCallback:: LoadClass'
title: Метод ICorDebugManagedCallback::LoadClass
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadClass
helpviewer_keywords:
- ICorDebugManagedCallback::LoadClass method [.NET Framework debugging]
- LoadClass method [.NET Framework debugging]
ms.assetid: e58dac7b-85c3-41ca-b9aa-3a7fc9ae6680
topic_type:
- apiref
ms.openlocfilehash: 6f670a2f0798c7edfdc4292334cf9534e59a3007
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660613"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a><span data-ttu-id="d6d90-103">Метод ICorDebugManagedCallback::LoadClass</span><span class="sxs-lookup"><span data-stu-id="d6d90-103">ICorDebugManagedCallback::LoadClass Method</span></span>

<span data-ttu-id="d6d90-104">Уведомляет отладчик о том, что класс был загружен.</span><span class="sxs-lookup"><span data-stu-id="d6d90-104">Notifies the debugger that a class has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6d90-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d6d90-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6d90-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d6d90-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="d6d90-107">окне Указатель на объект ICorDebugAppDomain, представляющий домен приложения, в который был загружен класс.</span><span class="sxs-lookup"><span data-stu-id="d6d90-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the class has been loaded.</span></span>  
  
 `c`  
 <span data-ttu-id="d6d90-108">окне Указатель на объект ICorDebugClass, представляющий класс.</span><span class="sxs-lookup"><span data-stu-id="d6d90-108">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6d90-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="d6d90-109">Remarks</span></span>  

 <span data-ttu-id="d6d90-110">Этот обратный вызов происходит, только если для модуля, содержащего класс, была включена загрузка класса.</span><span class="sxs-lookup"><span data-stu-id="d6d90-110">This callback occurs only if class loading has been enabled for the module that contains the class.</span></span> <span data-ttu-id="d6d90-111">Загрузка класса всегда включена для динамических модулей.</span><span class="sxs-lookup"><span data-stu-id="d6d90-111">Class loading is always enabled for dynamic modules.</span></span>  
  
 <span data-ttu-id="d6d90-112">`LoadClass`Обратный вызов предоставляет соответствующее время для привязки точек останова к вновь созданным классам в динамических модулях.</span><span class="sxs-lookup"><span data-stu-id="d6d90-112">The `LoadClass` callback provides an appropriate time to bind breakpoints to newly generated classes in dynamic modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6d90-113">Требования</span><span class="sxs-lookup"><span data-stu-id="d6d90-113">Requirements</span></span>  

 <span data-ttu-id="d6d90-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6d90-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6d90-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d6d90-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d6d90-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6d90-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6d90-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6d90-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6d90-118">См. также</span><span class="sxs-lookup"><span data-stu-id="d6d90-118">See also</span></span>

- [<span data-ttu-id="d6d90-119">Метод UnloadClass</span><span class="sxs-lookup"><span data-stu-id="d6d90-119">UnloadClass Method</span></span>](icordebugmanagedcallback-unloadclass-method.md)
- [<span data-ttu-id="d6d90-120">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="d6d90-120">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
