---
description: 'Дополнительные сведения: указатель функции Фексекутеинаппдомаинкаллбакк'
title: Указатель функции FExecuteInAppDomainCallback
ms.date: 03/30/2017
api_name:
- FExecuteInAppDomainCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FExecuteInAppDomainCallback
helpviewer_keywords:
- FExecuteInAppDomainCallback function pointer [.NET Framework hosting]
ms.assetid: 2709f18f-3eee-497f-bc33-3ab7a485599b
topic_type:
- apiref
ms.openlocfilehash: 97c7fe14a3eafd6f4626d8729be3b45ad5502f1a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785400"
---
# <a name="fexecuteinappdomaincallback-function-pointer"></a><span data-ttu-id="2efac-103">Указатель функции FExecuteInAppDomainCallback</span><span class="sxs-lookup"><span data-stu-id="2efac-103">FExecuteInAppDomainCallback Function Pointer</span></span>

<span data-ttu-id="2efac-104">Указывает на функцию, которая вызывается средой CLR для выполнения управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="2efac-104">Points to a function that is called by the common language runtime (CLR) to execute managed code.</span></span>  
  
 <span data-ttu-id="2efac-105">Этот указатель функции является устаревшим в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="2efac-105">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2efac-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2efac-106">Syntax</span></span>  
  
```cpp  
typedef HRESULT (__stdcall *FExecuteInAppDomainCallback) (  
    [in] void  *cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2efac-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="2efac-107">Parameters</span></span>  

 `cookie`  
 <span data-ttu-id="2efac-108">окне Указатель на непрозрачную память, выделенную вызывающим объектом, содержащую управляемый код для выполнения.</span><span class="sxs-lookup"><span data-stu-id="2efac-108">[in] A pointer to opaque caller-allocated memory that contains the managed code to be executed.</span></span>  
  
 <span data-ttu-id="2efac-109">Выделение и время существования этой памяти управляются вызывающим объектом (то есть средой CLR).</span><span class="sxs-lookup"><span data-stu-id="2efac-109">The allocation and lifetime of this memory are controlled by the caller (that is, the CLR).</span></span> <span data-ttu-id="2efac-110">Это не управляемая средой CLR память в куче.</span><span class="sxs-lookup"><span data-stu-id="2efac-110">This is not CLR managed-heap memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2efac-111">Требования</span><span class="sxs-lookup"><span data-stu-id="2efac-111">Requirements</span></span>  

 <span data-ttu-id="2efac-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2efac-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2efac-113">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2efac-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2efac-114">**Библиотека:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="2efac-114">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="2efac-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2efac-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2efac-116">См. также</span><span class="sxs-lookup"><span data-stu-id="2efac-116">See also</span></span>

- [<span data-ttu-id="2efac-117">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="2efac-117">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
