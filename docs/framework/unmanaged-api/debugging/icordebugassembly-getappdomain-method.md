---
description: 'Дополнительные сведения о методе: ICorDebugAssembly:: onappdomain'
title: Метод ICorDebugAssembly::GetAppDomain
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetAppDomain
helpviewer_keywords:
- ICorDebugAssembly::GetAppDomain method [.NET Framework debugging]
- GetAppDomain method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 14e18510-23ac-4cba-9f96-c86147a2df9d
topic_type:
- apiref
ms.openlocfilehash: f67b2a211b080843e2bd7b8820a5bf54dae638e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712107"
---
# <a name="icordebugassemblygetappdomain-method"></a><span data-ttu-id="a7796-103">Метод ICorDebugAssembly::GetAppDomain</span><span class="sxs-lookup"><span data-stu-id="a7796-103">ICorDebugAssembly::GetAppDomain Method</span></span>

<span data-ttu-id="a7796-104">Возвращает указатель интерфейса на домен приложения, содержащий данный `ICorDebugAssembly` экземпляр.</span><span class="sxs-lookup"><span data-stu-id="a7796-104">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7796-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a7796-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7796-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a7796-106">Parameters</span></span>  

 `ppAppDomain`  
 <span data-ttu-id="a7796-107">заполняет Указатель на адрес интерфейса ICorDebugAppDomain, который представляет домен приложения.</span><span class="sxs-lookup"><span data-stu-id="a7796-107">[out] A pointer to the address of an ICorDebugAppDomain interface that represents the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7796-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="a7796-108">Remarks</span></span>  

 <span data-ttu-id="a7796-109">Если эта сборка является системной, `GetAppDomain` возвращает значение null.</span><span class="sxs-lookup"><span data-stu-id="a7796-109">If this assembly is the system assembly, `GetAppDomain` returns null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7796-110">Требования</span><span class="sxs-lookup"><span data-stu-id="a7796-110">Requirements</span></span>  

 <span data-ttu-id="a7796-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7796-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7796-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a7796-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7796-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7796-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7796-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7796-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
