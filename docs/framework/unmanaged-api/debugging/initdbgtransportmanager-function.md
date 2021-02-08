---
description: Дополнительные сведения о функции InitDbgTransportManager
title: Функция InitDbgTransportManager
ms.date: 03/30/2017
api_name:
- InitDbgTransportManager
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- InitDbgTransportManager
helpviewer_keywords:
- remote debugging API [Silverlight]
- InitDbgTransportManager function
- Silverlight, remote debugging
ms.assetid: a30102ff-c52e-48c9-b3a9-aa14286a42b2
topic_type:
- apiref
ms.openlocfilehash: 19cdfcbe3a5b120c11fc781476410833997b8c6e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790442"
---
# <a name="initdbgtransportmanager-function"></a><span data-ttu-id="e7877-103">Функция InitDbgTransportManager</span><span class="sxs-lookup"><span data-stu-id="e7877-103">InitDbgTransportManager Function</span></span>

<span data-ttu-id="e7877-104">Инициализирует диспетчер транспорта для подключения к удаленному целевому объекту для процесса и перечисления среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="e7877-104">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7877-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e7877-105">Syntax</span></span>  
  
```cpp  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e7877-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="e7877-106">Return Value</span></span>  

 <span data-ttu-id="e7877-107">S_OK</span><span class="sxs-lookup"><span data-stu-id="e7877-107">S_OK</span></span>  
 <span data-ttu-id="e7877-108">Успешно.</span><span class="sxs-lookup"><span data-stu-id="e7877-108">Success.</span></span>  
  
 <span data-ttu-id="e7877-109">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="e7877-109">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="e7877-110">Функции не удалось выделить память для диспетчера транспорта.</span><span class="sxs-lookup"><span data-stu-id="e7877-110">The function was unable to allocate memory for a transport manager.</span></span>  
  
 <span data-ttu-id="e7877-111">E_FAIL (или другие коды возврата E_)</span><span class="sxs-lookup"><span data-stu-id="e7877-111">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="e7877-112">Прочие сбои.</span><span class="sxs-lookup"><span data-stu-id="e7877-112">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7877-113">Требования</span><span class="sxs-lookup"><span data-stu-id="e7877-113">Requirements</span></span>  

 <span data-ttu-id="e7877-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7877-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7877-115">**Заголовок:** Кореклрремотедебуггингинтерфацес. h</span><span class="sxs-lookup"><span data-stu-id="e7877-115">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="e7877-116">**Библиотека:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="e7877-116">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="e7877-117">**Платформа .NET Framework версии:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="e7877-117">**.NET Framework Versions:** 3.5 SP1</span></span>
