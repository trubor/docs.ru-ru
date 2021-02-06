---
description: 'Дополнительные сведения о методе: ICorDebugThread2:: Жетконнектионид'
title: Метод ICorDebugThread2::GetConnectionID
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetConnectionID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetConnectionID
helpviewer_keywords:
- ICorDebugThread2::GetConnectionID method [.NET Framework debugging]
- GetConnectionID method [.NET Framework debugging]
ms.assetid: 9c76b587-f941-4fa1-8b86-f3494fb10c8e
topic_type:
- apiref
ms.openlocfilehash: 0f8035e703d3638b11f4206d9c47e39fe487d71d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658741"
---
# <a name="icordebugthread2getconnectionid-method"></a><span data-ttu-id="1123f-103">Метод ICorDebugThread2::GetConnectionID</span><span class="sxs-lookup"><span data-stu-id="1123f-103">ICorDebugThread2::GetConnectionID Method</span></span>

<span data-ttu-id="1123f-104">Возвращает идентификатор соединения для этого объекта ICorDebugThread2.</span><span class="sxs-lookup"><span data-stu-id="1123f-104">Gets the connection identifier for this ICorDebugThread2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1123f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1123f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1123f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1123f-106">Parameters</span></span>  

 `pdwConnectionId`  
 <span data-ttu-id="1123f-107">заполняет Значение типа `CONNID` , представляющее идентификатор соединения.</span><span class="sxs-lookup"><span data-stu-id="1123f-107">[out] A `CONNID` that represents the connection identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1123f-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="1123f-108">Remarks</span></span>  

 <span data-ttu-id="1123f-109">`GetConnectionID`Метод возвращает ноль в `pdwConnectionId` параметре, если этот поток не является частью соединения.</span><span class="sxs-lookup"><span data-stu-id="1123f-109">The `GetConnectionID` method returns zero in the `pdwConnectionId` parameter, if this thread is not part of a connection.</span></span>  
  
 <span data-ttu-id="1123f-110">Если этот поток подключен к экземпляру Microsoft SQL Server 2005 Analysis Services (SSAS), то `CONNID` сопоставляется с идентификатором серверного процесса (SPID).</span><span class="sxs-lookup"><span data-stu-id="1123f-110">If this thread is connected to an instance of Microsoft SQL Server 2005 Analysis Services (SSAS), the `CONNID` maps to a server process identifier (SPID).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1123f-111">Требования</span><span class="sxs-lookup"><span data-stu-id="1123f-111">Requirements</span></span>  

 <span data-ttu-id="1123f-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1123f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1123f-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1123f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1123f-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1123f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1123f-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1123f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
