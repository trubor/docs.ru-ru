---
description: 'Дополнительные сведения о методе: ICorDebugProcess2:: Жетреференцевалуефромгчандле'
title: Метод ICorDebugProcess2::GetReferenceValueFromGCHandle
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetReferenceValueFromGCHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetReferenceValueFromGCHandle
helpviewer_keywords:
- GetReferenceValueFromGCHandle method [.NET Framework debugging]
- ICorDebugProcess2::GetReferenceValueFromGCHandle method [.NET Framework debugging]
ms.assetid: 8bdd7f4c-19f2-4ede-875e-603773e8c128
topic_type:
- apiref
ms.openlocfilehash: 02047dee9116d34a365242f2a532766eb60e1c81
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650239"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a><span data-ttu-id="a6d39-103">Метод ICorDebugProcess2::GetReferenceValueFromGCHandle</span><span class="sxs-lookup"><span data-stu-id="a6d39-103">ICorDebugProcess2::GetReferenceValueFromGCHandle Method</span></span>

<span data-ttu-id="a6d39-104">Возвращает указатель ссылки на указанный управляемый объект, который имеет обработчик сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="a6d39-104">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6d39-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a6d39-105">Syntax</span></span>  
  
```cpp  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6d39-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a6d39-106">Parameters</span></span>  

 `handle`  
 <span data-ttu-id="a6d39-107">окне Указатель на управляемый объект, который имеет обработчик сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="a6d39-107">[in] A pointer to a managed object that has a garbage collection handle.</span></span> <span data-ttu-id="a6d39-108">Это значение является <xref:System.IntPtr> объектом и может быть получено из объекта <xref:System.Runtime.InteropServices.GCHandle> для управляемого объекта.</span><span class="sxs-lookup"><span data-stu-id="a6d39-108">This value is a <xref:System.IntPtr> object and can be retrieved from the <xref:System.Runtime.InteropServices.GCHandle> for the managed object.</span></span>  
  
 `pOutValue`  
 <span data-ttu-id="a6d39-109">заполняет Указатель на адрес объекта ICorDebugReferenceValue, который представляет ссылку на указанный управляемый объект.</span><span class="sxs-lookup"><span data-stu-id="a6d39-109">[out] A pointer to the address of an ICorDebugReferenceValue object that represents a reference to the specified managed object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6d39-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="a6d39-110">Remarks</span></span>  

 <span data-ttu-id="a6d39-111">Не путайте возвращаемое ссылочное значение со ссылочным значением сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="a6d39-111">Do not confuse the returned reference value with a garbage collection reference value.</span></span>  
  
 <span data-ttu-id="a6d39-112">Возвращаемая ссылка ведет себя как обычная ссылка.</span><span class="sxs-lookup"><span data-stu-id="a6d39-112">The returned reference behaves like a normal reference.</span></span> <span data-ttu-id="a6d39-113">Он отключен, когда выполнение кода продолжится после точки останова.</span><span class="sxs-lookup"><span data-stu-id="a6d39-113">It is disabled when code execution continues after a breakpoint.</span></span> <span data-ttu-id="a6d39-114">Время существования целевого объекта не зависит от времени существования ссылочного значения.</span><span class="sxs-lookup"><span data-stu-id="a6d39-114">The lifetime of the target object is not affected by the lifetime of the reference value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a6d39-115">`GetReferenceValueFromGCHandle`Метод не проверяет этот обработчик.</span><span class="sxs-lookup"><span data-stu-id="a6d39-115">The `GetReferenceValueFromGCHandle` method does not validate the handle.</span></span> <span data-ttu-id="a6d39-116">Таким образом, `GetReferenceValueFromGCHandle` метод может привести к повреждению отладчика и отлаживаемого кода при передаче недопустимого маркера.</span><span class="sxs-lookup"><span data-stu-id="a6d39-116">Therefore, the `GetReferenceValueFromGCHandle` method can potentially corrupt both the debugger and the code being debugged if an invalid handle is passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6d39-117">Требования</span><span class="sxs-lookup"><span data-stu-id="a6d39-117">Requirements</span></span>  

 <span data-ttu-id="a6d39-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6d39-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6d39-119">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a6d39-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a6d39-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6d39-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6d39-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6d39-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
