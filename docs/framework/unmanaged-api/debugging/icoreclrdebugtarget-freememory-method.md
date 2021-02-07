---
description: 'Дополнительные сведения о методе: ICoreClrDebugTarget:: FreeMemory'
title: Метод ICoreClrDebugTarget::FreeMemory
ms.date: 03/30/2017
api_name:
- ICoreDebugTarget.FreeMemory
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::FreeMemory
helpviewer_keywords:
- remote debugging API [Silverlight]
- FreeMemory method, ICoreClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::FreeMemory method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 98f2a0db-a6ec-4f9b-861d-f82485237d08
topic_type:
- apiref
ms.openlocfilehash: 9572e0c3df1fdd064e78ba170d39c1415c68dc85
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690006"
---
# <a name="icoreclrdebugtargetfreememory-method"></a><span data-ttu-id="c08a3-103">Метод ICoreClrDebugTarget::FreeMemory</span><span class="sxs-lookup"><span data-stu-id="c08a3-103">ICoreClrDebugTarget::FreeMemory Method</span></span>

<span data-ttu-id="c08a3-104">Освобождает память, выделенную методам [ICoreClrDebugTarget:: EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) и [ICoreClrDebugTarget:: EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c08a3-104">Frees the memory allocated by the [ICoreClrDebugTarget::EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) and [ICoreClrDebugTarget::EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md) methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c08a3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c08a3-105">Syntax</span></span>  
  
```cpp  
void FreeMemory (  
     [in] void*pMemory);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c08a3-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c08a3-106">Parameters</span></span>  

 `pMemory`  
 <span data-ttu-id="c08a3-107">окне Указатель на массив, возвращаемый методом [ICoreClrDebugTarget:: EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) или [ICoreClrDebugTarget:: EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c08a3-107">[in] A pointer to the array that is returned by either the [ICoreClrDebugTarget::EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) or the [ICoreClrDebugTarget::EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c08a3-108">Требования</span><span class="sxs-lookup"><span data-stu-id="c08a3-108">Requirements</span></span>  

 <span data-ttu-id="c08a3-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c08a3-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c08a3-110">**Заголовок:** Кореклрремотедебуггингинтерфацес. h</span><span class="sxs-lookup"><span data-stu-id="c08a3-110">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="c08a3-111">**Библиотека:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="c08a3-111">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="c08a3-112">**Платформа .NET Framework версии:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="c08a3-112">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c08a3-113">См. также</span><span class="sxs-lookup"><span data-stu-id="c08a3-113">See also</span></span>

- [<span data-ttu-id="c08a3-114">Интерфейс ICoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="c08a3-114">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)
