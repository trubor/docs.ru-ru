---
description: 'Дополнительные сведения о методе: ICorDebugManagedCallback:: Унлоадкласс'
title: Метод ICorDebugManagedCallback::UnloadClass
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadClass
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadClass method [.NET Framework debugging]
- UnloadClass method [.NET Framework debugging]
ms.assetid: 66a59b18-ce9a-41f4-b23b-4dd6753d6d36
topic_type:
- apiref
ms.openlocfilehash: b76caf39611b0f59c74b4ae47d167e6f232a6dbc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660223"
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a><span data-ttu-id="ef08c-103">Метод ICorDebugManagedCallback::UnloadClass</span><span class="sxs-lookup"><span data-stu-id="ef08c-103">ICorDebugManagedCallback::UnloadClass Method</span></span>

<span data-ttu-id="ef08c-104">Уведомляет отладчик о выгрузке класса.</span><span class="sxs-lookup"><span data-stu-id="ef08c-104">Notifies the debugger that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef08c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ef08c-105">Syntax</span></span>  
  
```cpp  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef08c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ef08c-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="ef08c-107">окне Указатель на объект ICorDebugAppDomain, представляющий домен приложения, содержащий класс.</span><span class="sxs-lookup"><span data-stu-id="ef08c-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the class.</span></span>  
  
 `c`  
 <span data-ttu-id="ef08c-108">окне Указатель на объект ICorDebugClass, представляющий класс.</span><span class="sxs-lookup"><span data-stu-id="ef08c-108">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef08c-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="ef08c-109">Remarks</span></span>  

 <span data-ttu-id="ef08c-110">После этого вызова не следует ссылаться на класс.</span><span class="sxs-lookup"><span data-stu-id="ef08c-110">The class should not be referenced after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef08c-111">Требования</span><span class="sxs-lookup"><span data-stu-id="ef08c-111">Requirements</span></span>  

 <span data-ttu-id="ef08c-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef08c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef08c-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ef08c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef08c-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef08c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef08c-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef08c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef08c-116">См. также</span><span class="sxs-lookup"><span data-stu-id="ef08c-116">See also</span></span>

- [<span data-ttu-id="ef08c-117">Метод LoadClass</span><span class="sxs-lookup"><span data-stu-id="ef08c-117">LoadClass Method</span></span>](icordebugmanagedcallback-loadclass-method.md)
- [<span data-ttu-id="ef08c-118">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="ef08c-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
