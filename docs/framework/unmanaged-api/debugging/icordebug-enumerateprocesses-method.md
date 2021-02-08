---
description: 'Дополнительные сведения: метод ICorDebug:: EnumerateProcesses'
title: Метод ICorDebug::EnumerateProcesses
ms.date: 03/30/2017
api_name:
- ICorDebug.EnumerateProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- EnumerateProcesses
helpviewer_keywords:
- EnumerateProcesses method [.NET Framework debugging]
- ICorDebug::EnumerateProcesses method [.NET Framework debugging]
ms.assetid: ba25d166-1d28-4f1d-aca2-de298bbca669
topic_type:
- apiref
ms.openlocfilehash: 44ee21a820a1c9f94f1d66c93ff040b504bfcc93
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791586"
---
# <a name="icordebugenumerateprocesses-method"></a><span data-ttu-id="b45fa-103">Метод ICorDebug::EnumerateProcesses</span><span class="sxs-lookup"><span data-stu-id="b45fa-103">ICorDebug::EnumerateProcesses Method</span></span>

<span data-ttu-id="b45fa-104">Возвращает перечислитель для отлаживаемых процессов.</span><span class="sxs-lookup"><span data-stu-id="b45fa-104">Gets an enumerator for the processes that are being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b45fa-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b45fa-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateProcesses (  
    [out] ICorDebugProcessEnum      **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b45fa-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b45fa-106">Parameters</span></span>  

 `ppProcess`  
 <span data-ttu-id="b45fa-107">Указатель на адрес объекта Икордебугпроцессенум, который является перечислителем для отлаживаемых процессов.</span><span class="sxs-lookup"><span data-stu-id="b45fa-107">A pointer to the address of an ICorDebugProcessEnum object that is the enumerator for the processes being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b45fa-108">Требования</span><span class="sxs-lookup"><span data-stu-id="b45fa-108">Requirements</span></span>  

 <span data-ttu-id="b45fa-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b45fa-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b45fa-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b45fa-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b45fa-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b45fa-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b45fa-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b45fa-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b45fa-113">См. также</span><span class="sxs-lookup"><span data-stu-id="b45fa-113">See also</span></span>

- [<span data-ttu-id="b45fa-114">Интерфейс ICorDebug</span><span class="sxs-lookup"><span data-stu-id="b45fa-114">ICorDebug Interface</span></span>](icordebug-interface.md)
