---
description: 'Дополнительные сведения о методе: ICorDebugAppDomain:: Attach'
title: Метод ICorDebugAppDomain::IsAttached
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.IsAttached
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::IsAttached
helpviewer_keywords:
- IsAttached method [.NET Framework debugging]
- ICorDebugAppDomain::IsAttached method [.NET Framework debugging]
ms.assetid: af0c67c7-f53e-47c9-b84b-be50bd04903e
topic_type:
- apiref
ms.openlocfilehash: 79427d08be9ffea253695b67767d68589edf6979
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772389"
---
# <a name="icordebugappdomainisattached-method"></a><span data-ttu-id="128d4-103">Метод ICorDebugAppDomain::IsAttached</span><span class="sxs-lookup"><span data-stu-id="128d4-103">ICorDebugAppDomain::IsAttached Method</span></span>

<span data-ttu-id="128d4-104">Возвращает значение, указывающее, присоединен ли отладчик к домену приложения.</span><span class="sxs-lookup"><span data-stu-id="128d4-104">Gets a value that indicates whether the debugger is attached to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="128d4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="128d4-105">Syntax</span></span>  
  
```cpp  
HRESULT IsAttached (  
    [out] BOOL  *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="128d4-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="128d4-106">Parameters</span></span>  

 `pbAttached`  
 <span data-ttu-id="128d4-107">[out] `true` значение, если отладчик присоединен к домену приложения; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="128d4-107">[out] `true` if the debugger is attached to the application domain; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="128d4-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="128d4-108">Remarks</span></span>  

 <span data-ttu-id="128d4-109">Методы ICorDebugController нельзя использовать до тех пор, пока отладчик не подключится к домену приложения.</span><span class="sxs-lookup"><span data-stu-id="128d4-109">The ICorDebugController methods cannot be used until the debugger attaches to the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="128d4-110">Требования</span><span class="sxs-lookup"><span data-stu-id="128d4-110">Requirements</span></span>  

 <span data-ttu-id="128d4-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="128d4-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="128d4-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="128d4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="128d4-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="128d4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="128d4-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="128d4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
