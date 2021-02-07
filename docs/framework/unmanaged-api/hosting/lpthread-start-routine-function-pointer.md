---
description: 'Дополнительные сведения: указатель функции LPTHREAD_START_ROUTINE'
title: Указатель функции LPTHREAD_START_ROUTINE
ms.date: 03/30/2017
api_name:
- LPTHREAD_START_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPTHREAD_START_ROUTINE
helpviewer_keywords:
- LPTHREAD_START_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 7b9b93b0-fe92-42ba-8693-701168a29dde
topic_type:
- apiref
ms.openlocfilehash: 9f79cffb0b5290031915b453353dd47cb3959970
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679814"
---
# <a name="lpthread_start_routine-function-pointer"></a><span data-ttu-id="66963-103">Указатель функции LPTHREAD_START_ROUTINE</span><span class="sxs-lookup"><span data-stu-id="66963-103">LPTHREAD_START_ROUTINE Function Pointer</span></span>

<span data-ttu-id="66963-104">Указывает на функцию, которая уведомляет узел о начале выполнения потока.</span><span class="sxs-lookup"><span data-stu-id="66963-104">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 <span data-ttu-id="66963-105">Этот указатель функции является устаревшим в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="66963-105">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66963-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="66963-106">Syntax</span></span>  
  
```cpp  
typedef DWORD (__stdcall *LPTHREAD_START_ROUTINE) (  
    [in] LPVOID lpThreadParameter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66963-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="66963-107">Parameters</span></span>  

 `lpThreadParameter`  
 <span data-ttu-id="66963-108">окне Указатель на код, который начал выполнять.</span><span class="sxs-lookup"><span data-stu-id="66963-108">[in] A pointer to the code that has started executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66963-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="66963-109">Remarks</span></span>  

 <span data-ttu-id="66963-110">Функция, к которой `LPTHREAD_START_ROUTINE` points является функцией обратного вызова и должна быть реализована модулем записи размещающего приложения.</span><span class="sxs-lookup"><span data-stu-id="66963-110">The function to which `LPTHREAD_START_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66963-111">Требования</span><span class="sxs-lookup"><span data-stu-id="66963-111">Requirements</span></span>  

 <span data-ttu-id="66963-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66963-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66963-113">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="66963-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="66963-114">**Библиотека:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="66963-114">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="66963-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66963-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66963-116">См. также</span><span class="sxs-lookup"><span data-stu-id="66963-116">See also</span></span>

- [<span data-ttu-id="66963-117">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="66963-117">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
