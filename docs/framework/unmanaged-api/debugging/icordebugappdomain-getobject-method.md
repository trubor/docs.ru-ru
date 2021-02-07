---
description: 'Дополнительные сведения о методе: ICorDebugAppDomain:: GetObject'
title: Метод ICorDebugAppDomain::GetObject
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetObject
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetObject
helpviewer_keywords:
- ICorDebugAppDomain::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 78232e6f-ae18-4cfa-a6cd-e79471cf9d76
topic_type:
- apiref
ms.openlocfilehash: 59389e2a4ca72f8dcdd7117213e968440d30aaa6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754216"
---
# <a name="icordebugappdomaingetobject-method"></a><span data-ttu-id="fc6fb-103">Метод ICorDebugAppDomain::GetObject</span><span class="sxs-lookup"><span data-stu-id="fc6fb-103">ICorDebugAppDomain::GetObject Method</span></span>

<span data-ttu-id="fc6fb-104">Возвращает указатель интерфейса на домен приложения среды CLR.</span><span class="sxs-lookup"><span data-stu-id="fc6fb-104">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc6fb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fc6fb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc6fb-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="fc6fb-106">Parameters</span></span>  

 `ppObject`  
 <span data-ttu-id="fc6fb-107">заполняет Указатель на адрес объекта интерфейса ICorDebugValue, который представляет домен приложения среды CLR.</span><span class="sxs-lookup"><span data-stu-id="fc6fb-107">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc6fb-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="fc6fb-108">Return Value</span></span>  

 <span data-ttu-id="fc6fb-109">Если управляемый <xref:System.AppDomain?displayProperty=nameWithType> объект не был создан для этого домена приложения, метод возвращает `S_FALSE` и помещает `NULL` в `*ppObject` .</span><span class="sxs-lookup"><span data-stu-id="fc6fb-109">If a managed <xref:System.AppDomain?displayProperty=nameWithType> object hasn't been constructed for this application domain, the method returns `S_FALSE` and places `NULL` in `*ppObject`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc6fb-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="fc6fb-110">Remarks</span></span>  

 <span data-ttu-id="fc6fb-111">Каждый домен приложения в процессе может иметь управляемый <xref:System.AppDomain?displayProperty=nameWithType> объект в среде выполнения, который представляет его.</span><span class="sxs-lookup"><span data-stu-id="fc6fb-111">Each application domain in a process may have a managed <xref:System.AppDomain?displayProperty=nameWithType> object in the runtime that represents it.</span></span> <span data-ttu-id="fc6fb-112">Эта функция получает объект интерфейса ICorDebugValue, соответствующий этому управляемому <xref:System.AppDomain?displayProperty=nameWithType> объекту.</span><span class="sxs-lookup"><span data-stu-id="fc6fb-112">This function gets an ICorDebugValue interface object that corresponds to this managed <xref:System.AppDomain?displayProperty=nameWithType> object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc6fb-113">Требования</span><span class="sxs-lookup"><span data-stu-id="fc6fb-113">Requirements</span></span>  

 <span data-ttu-id="fc6fb-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc6fb-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc6fb-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc6fb-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc6fb-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc6fb-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc6fb-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc6fb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
