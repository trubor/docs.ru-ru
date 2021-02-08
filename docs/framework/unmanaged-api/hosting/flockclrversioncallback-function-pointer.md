---
description: 'Дополнительные сведения: указатель функции FLockClrVersionCallback'
title: Указатель функции FLockClrVersionCallback
ms.date: 03/30/2017
api_name:
- FLockClrVersionCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FLockClrVersionCallback
helpviewer_keywords:
- FLockClrVersionCallback function pointer [.NET Framework hosting]
ms.assetid: 98a4762d-9ad2-45bd-9d03-39064a028b44
topic_type:
- apiref
ms.openlocfilehash: 3506cd30ab2a9e5a06b03f5010c9870280a38378
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785384"
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="93d99-103">Указатель функции FLockClrVersionCallback</span><span class="sxs-lookup"><span data-stu-id="93d99-103">FLockClrVersionCallback Function Pointer</span></span>

<span data-ttu-id="93d99-104">Указывает на функцию, которая вызывается средой CLR для указания того, что инициализация запущена или завершена.</span><span class="sxs-lookup"><span data-stu-id="93d99-104">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="93d99-105">Этот указатель функции является устаревшим в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="93d99-105">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93d99-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="93d99-106">Syntax</span></span>  
  
```cpp  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="93d99-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="93d99-107">Remarks</span></span>  

 <span data-ttu-id="93d99-108">Эта функция реализуется узлом.</span><span class="sxs-lookup"><span data-stu-id="93d99-108">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93d99-109">Требования</span><span class="sxs-lookup"><span data-stu-id="93d99-109">Requirements</span></span>  

 <span data-ttu-id="93d99-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93d99-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93d99-111">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="93d99-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="93d99-112">**Библиотека:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="93d99-112">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="93d99-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93d99-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93d99-114">См. также</span><span class="sxs-lookup"><span data-stu-id="93d99-114">See also</span></span>

- [<span data-ttu-id="93d99-115">Функция LockClrVersion</span><span class="sxs-lookup"><span data-stu-id="93d99-115">LockClrVersion Function</span></span>](lockclrversion-function.md)
- [<span data-ttu-id="93d99-116">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="93d99-116">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
