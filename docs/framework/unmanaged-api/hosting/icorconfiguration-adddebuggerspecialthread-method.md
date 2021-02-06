---
description: 'Дополнительные сведения о методе: ICorConfiguration:: АдддебугжерспеЦиалсреад'
title: Метод ICorConfiguration::AddDebuggerSpecialThread
ms.date: 03/30/2017
api_name:
- ICorConfiguration.AddDebuggerSpecialThread
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AddDebuggerSpecialThread
helpviewer_keywords:
- AddDebuggerSpecialThread method [.NET Framework hosting]
- ICorConfiguration::AddDebuggerSpecialThread method [.NET Framework hosting]
ms.assetid: 1f1e3239-438e-4be9-a3bb-7d0722d3a76d
topic_type:
- apiref
ms.openlocfilehash: b6904c2e4d5c265244ac096e0d64c2fc7f5d1be5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636719"
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a><span data-ttu-id="c49ab-103">Метод ICorConfiguration::AddDebuggerSpecialThread</span><span class="sxs-lookup"><span data-stu-id="c49ab-103">ICorConfiguration::AddDebuggerSpecialThread Method</span></span>

<span data-ttu-id="c49ab-104">Указывает службам отладки, что определенному потоку должен быть разрешено продолжать выполнение, пока отладчик не остановит работу приложения во время управляемых или неуправляемых сценариев отладки.</span><span class="sxs-lookup"><span data-stu-id="c49ab-104">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c49ab-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c49ab-105">Syntax</span></span>  
  
```cpp  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c49ab-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c49ab-106">Parameters</span></span>  

 `dwSpecialThreadId`  
 <span data-ttu-id="c49ab-107">окне Идентификатор потока, который должен быть разрешен для продолжения выполнения.</span><span class="sxs-lookup"><span data-stu-id="c49ab-107">[in] The ID of the thread that should be allowed to continue executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c49ab-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="c49ab-108">Remarks</span></span>  

 <span data-ttu-id="c49ab-109">Указанный поток не может выполнять управляемый код или вводить среду выполнения каким бы то ни было образом.</span><span class="sxs-lookup"><span data-stu-id="c49ab-109">The specified thread will not be allowed to run managed code or enter the runtime in any way.</span></span> <span data-ttu-id="c49ab-110">Примером такого потока может быть внутрипроцессный поток для поддержки устаревших отладчиков скриптов.</span><span class="sxs-lookup"><span data-stu-id="c49ab-110">An example of such a thread would be an in-process thread to support legacy script debuggers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c49ab-111">Требования</span><span class="sxs-lookup"><span data-stu-id="c49ab-111">Requirements</span></span>  

 <span data-ttu-id="c49ab-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c49ab-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c49ab-113">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c49ab-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c49ab-114">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c49ab-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c49ab-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c49ab-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c49ab-116">См. также</span><span class="sxs-lookup"><span data-stu-id="c49ab-116">See also</span></span>

- [<span data-ttu-id="c49ab-117">Интерфейс ICorConfiguration</span><span class="sxs-lookup"><span data-stu-id="c49ab-117">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)
