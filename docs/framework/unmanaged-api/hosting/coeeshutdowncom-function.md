---
description: Дополнительные сведения о функции Коишутдовнком
title: Функция CoEEShutDownCOM
ms.date: 03/30/2017
api_name:
- CoEEShutDownCOM
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoEEShutDownCOM
helpviewer_keywords:
- CoEEShutDownCOM function [.NET Framework hosting]
ms.assetid: b634cae2-632f-4737-9be4-92d0652844d7
topic_type:
- apiref
ms.openlocfilehash: 4f1ac8107c9a121ebf52ef21a5f2c9006880914f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799867"
---
# <a name="coeeshutdowncom-function"></a><span data-ttu-id="7bb56-103">Функция CoEEShutDownCOM</span><span class="sxs-lookup"><span data-stu-id="7bb56-103">CoEEShutDownCOM Function</span></span>

<span data-ttu-id="7bb56-104">Заставляет общеязыковую среду выполнения (CLR) освобождать все указатели интерфейсов, содержащиеся внутри вызываемых оболочек времени выполнения (RCW).</span><span class="sxs-lookup"><span data-stu-id="7bb56-104">Forces the common language runtime (CLR) to release all interface pointers it holds inside runtime callable wrappers (RCW).</span></span> <span data-ttu-id="7bb56-105">Это приведет к освобождению всех кэшей RCW.</span><span class="sxs-lookup"><span data-stu-id="7bb56-105">This has the effect of releasing all RCW caches.</span></span> <span data-ttu-id="7bb56-106">Эта глобальная функция является устаревшей в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7bb56-106">This global function is deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="7bb56-107">Вместо этого используйте точку входа для конкретной среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="7bb56-107">Instead, use the entry point for a specific runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bb56-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7bb56-108">Syntax</span></span>  
  
```cpp  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="7bb56-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="7bb56-109">Remarks</span></span>  

 <span data-ttu-id="7bb56-110">`CoEEShutDownCOM`Функция сначала освобождает все вызываемые оболочки RCW во всех контекстах и во всех кэшах, а затем удаляет все уведомления о разрыве, существующие в программе установки.</span><span class="sxs-lookup"><span data-stu-id="7bb56-110">The `CoEEShutDownCOM` function first releases all the RCWs in all contexts and in all caches, and then removes any tear-down notification existing in setup.</span></span> <span data-ttu-id="7bb56-111">Выгрузка библиотек DLL не выполняется.</span><span class="sxs-lookup"><span data-stu-id="7bb56-111">No DLL unloading occurs.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="7bb56-112">Эта функция влияет на все среды выполнения, загруженные в процесс.</span><span class="sxs-lookup"><span data-stu-id="7bb56-112">This function affects all runtimes that are loaded into the process.</span></span>  
  
 <span data-ttu-id="7bb56-113">Начиная с платформа .NET Framework 4, вызовите точку входа для этой функции в конкретной среде выполнения, которую необходимо изменить.</span><span class="sxs-lookup"><span data-stu-id="7bb56-113">Beginning with the .NET Framework 4, call the entry point for this function on the specific runtime you want to affect.</span></span> <span data-ttu-id="7bb56-114">Чтобы получить точку входа, вызовите метод [ICLRRuntimeInfo:: GetProcAddress](iclrruntimeinfo-getprocaddress-method.md) и укажите "коишутдовнком".</span><span class="sxs-lookup"><span data-stu-id="7bb56-114">To get the entry point, call the [ICLRRuntimeInfo::GetProcAddress](iclrruntimeinfo-getprocaddress-method.md) method and specify "CoEEShutDownCOM".</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bb56-115">Требования</span><span class="sxs-lookup"><span data-stu-id="7bb56-115">Requirements</span></span>  

 <span data-ttu-id="7bb56-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bb56-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bb56-117">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="7bb56-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7bb56-118">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7bb56-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7bb56-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bb56-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bb56-120">См. также</span><span class="sxs-lookup"><span data-stu-id="7bb56-120">See also</span></span>

- [<span data-ttu-id="7bb56-121">Глобальные статические функции метаданных</span><span class="sxs-lookup"><span data-stu-id="7bb56-121">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
