---
description: 'Дополнительные сведения о методе ICorDebugType:: coclass'
title: Метод ICorDebugType::GetClass
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetClass
helpviewer_keywords:
- ICorDebugType::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: 2644f48b-db3c-429f-ae62-76f1c98a1af5
topic_type:
- apiref
ms.openlocfilehash: 2e8d68fbc8909599ca649ba0e226cc84af820939
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658351"
---
# <a name="icordebugtypegetclass-method"></a><span data-ttu-id="9f49e-103">Метод ICorDebugType::GetClass</span><span class="sxs-lookup"><span data-stu-id="9f49e-103">ICorDebugType::GetClass Method</span></span>

<span data-ttu-id="9f49e-104">Возвращает указатель интерфейса на объект ICorDebugClass, представляющий универсальный тип, экземпляр которого не был создан.</span><span class="sxs-lookup"><span data-stu-id="9f49e-104">Gets an interface pointer to an ICorDebugClass that represents the uninstantiated generic type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f49e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9f49e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f49e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="9f49e-106">Parameters</span></span>  

 `ppClass`  
 <span data-ttu-id="9f49e-107">заполняет Указатель на адрес `ICorDebugClass` интерфейса, представляющий универсальный тип, экземпляр которого не был создан.</span><span class="sxs-lookup"><span data-stu-id="9f49e-107">[out] A pointer to the address of an `ICorDebugClass` interface that represents the uninstantiated generic type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f49e-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="9f49e-108">Remarks</span></span>  

 <span data-ttu-id="9f49e-109">`GetClass` может вызываться только при определенных условиях.</span><span class="sxs-lookup"><span data-stu-id="9f49e-109">`GetClass` can be called only under certain conditions.</span></span> <span data-ttu-id="9f49e-110">Вызовите метод [ICorDebugType:: GetType](icordebugtype-gettype-method.md) перед вызовом метода `GetClass` .</span><span class="sxs-lookup"><span data-stu-id="9f49e-110">Call [ICorDebugType::GetType](icordebugtype-gettype-method.md) before calling `GetClass`.</span></span> <span data-ttu-id="9f49e-111">Если `ICorDebugType::GetType` возвращает значение корелементтипе, которое равно ELEMENT_TYPE_CLASS или ELEMENT_TYPE_VALUETYPE, `GetClass` можно вызвать метод, чтобы получить неэкземплярный тип для универсального типа.</span><span class="sxs-lookup"><span data-stu-id="9f49e-111">If `ICorDebugType::GetType` returns a CorElementType value that is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, `GetClass` can be called to get the uninstantiated type for a generic type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f49e-112">Требования</span><span class="sxs-lookup"><span data-stu-id="9f49e-112">Requirements</span></span>  

 <span data-ttu-id="9f49e-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f49e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f49e-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9f49e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f49e-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f49e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f49e-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f49e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
