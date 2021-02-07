---
description: 'Дополнительные сведения: указатель функции WAITORTIMERCALLBACK'
title: Указатель функции WAITORTIMERCALLBACK
ms.date: 03/30/2017
api_name:
- WAITORTIMERCALLBACK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAITORTIMERCALLBACK
helpviewer_keywords:
- WAITORTIMERCALLBACK function pointer [.NET Framework hosting]
ms.assetid: 1fec4aef-0a06-4df0-bae7-d31a9ef9603d
topic_type:
- apiref
ms.openlocfilehash: 6fd9e7eab56e48086eefcb26fc48cbf5f45d4a0e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679060"
---
# <a name="waitortimercallback-function-pointer"></a><span data-ttu-id="9c57a-103">Указатель функции WAITORTIMERCALLBACK</span><span class="sxs-lookup"><span data-stu-id="9c57a-103">WAITORTIMERCALLBACK Function Pointer</span></span>

<span data-ttu-id="9c57a-104">Указывает на функцию, которая уведомляет узел о том, что дескриптор ожидания ( <xref:System.Threading.WaitHandle> ) либо получил сигнал, либо превысил время ожидания.</span><span class="sxs-lookup"><span data-stu-id="9c57a-104">Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.</span></span>  
  
 <span data-ttu-id="9c57a-105">Этот указатель функции является устаревшим в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9c57a-105">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c57a-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9c57a-106">Syntax</span></span>  
  
```cpp  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c57a-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="9c57a-107">Parameters</span></span>  

 `lpParameter`  
 <span data-ttu-id="9c57a-108">окне Указатель на объект, содержащий сведения, определенные узлом.</span><span class="sxs-lookup"><span data-stu-id="9c57a-108">[in] A pointer to an object that contains information defined by the host.</span></span>  
  
 `TimerOrWaitFired`  
 <span data-ttu-id="9c57a-109">[входные] `true` значение, если истекло время ожидания дескриптора ожидания или `false` он был сигнальным.</span><span class="sxs-lookup"><span data-stu-id="9c57a-109">[in] `true` if the wait handle timed out, or `false` if it was signaled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c57a-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="9c57a-110">Remarks</span></span>  

 <span data-ttu-id="9c57a-111">Функция, к которой `WAITORTIMERCALLBACK` points является функцией обратного вызова и должна быть реализована модулем записи размещающего приложения.</span><span class="sxs-lookup"><span data-stu-id="9c57a-111">The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c57a-112">Требования</span><span class="sxs-lookup"><span data-stu-id="9c57a-112">Requirements</span></span>  

 <span data-ttu-id="9c57a-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c57a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c57a-114">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9c57a-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9c57a-115">**Библиотека:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="9c57a-115">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="9c57a-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c57a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c57a-117">См. также</span><span class="sxs-lookup"><span data-stu-id="9c57a-117">See also</span></span>

- [<span data-ttu-id="9c57a-118">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="9c57a-118">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
