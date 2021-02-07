---
description: 'Дополнительные сведения о методе: ICLRMetaHost:: ExitProcess'
title: Метод ICLRMetaHost::ExitProcess
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.ExitProcess
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::ExitProcess
helpviewer_keywords:
- ICLRMetaHost::ExitProcess method [.NET Framework hosting]
- ExitProcess method, ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: b4df98cc-4e4e-407b-b8f4-e0076afef3a4
topic_type:
- apiref
ms.openlocfilehash: 3bc832538a5ad2b457de758fc35a632b09c02974
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689161"
---
# <a name="iclrmetahostexitprocess-method"></a><span data-ttu-id="d5df1-103">Метод ICLRMetaHost::ExitProcess</span><span class="sxs-lookup"><span data-stu-id="d5df1-103">ICLRMetaHost::ExitProcess Method</span></span>

<span data-ttu-id="d5df1-104">Пытается корректно завершить работу всех загруженных сред выполнения, а затем завершить процесс.</span><span class="sxs-lookup"><span data-stu-id="d5df1-104">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="d5df1-105">Заменяет функцию [корекситпроцесс](corexitprocess-function.md) .</span><span class="sxs-lookup"><span data-stu-id="d5df1-105">Supersedes the [CorExitProcess](corexitprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5df1-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d5df1-106">Syntax</span></span>  
  
```cpp  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5df1-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="d5df1-107">Parameters</span></span>  

 `iExitCode`  
 <span data-ttu-id="d5df1-108">окне Код выхода для процесса.</span><span class="sxs-lookup"><span data-stu-id="d5df1-108">[in] The exit code for the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5df1-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="d5df1-109">Return Value</span></span>  

 <span data-ttu-id="d5df1-110">Этот метод никогда не возвращает, поэтому возвращаемое значение не определено.</span><span class="sxs-lookup"><span data-stu-id="d5df1-110">This method never returns, so its return value is undefined.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5df1-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="d5df1-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5df1-112">Требования</span><span class="sxs-lookup"><span data-stu-id="d5df1-112">Requirements</span></span>  

 <span data-ttu-id="d5df1-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5df1-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5df1-114">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="d5df1-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d5df1-115">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d5df1-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d5df1-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5df1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5df1-117">См. также</span><span class="sxs-lookup"><span data-stu-id="d5df1-117">See also</span></span>

- [<span data-ttu-id="d5df1-118">Интерфейс ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="d5df1-118">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="d5df1-119">Размещение</span><span class="sxs-lookup"><span data-stu-id="d5df1-119">Hosting</span></span>](index.md)
