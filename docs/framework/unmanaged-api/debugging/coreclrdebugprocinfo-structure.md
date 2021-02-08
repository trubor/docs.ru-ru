---
description: 'Дополнительные сведения о: структура CoreClrDebugProcInfo'
title: Структура CoreClrDebugProcInfo
ms.date: 03/30/2017
api_name:
- CoreClrDebugProcInfo
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CoreClrDebugProcInfo
helpviewer_keywords:
- remote debugging API [Silverlight]
- CoreClrDebugProcInfo structure
- Silverlight, remote debugging
ms.assetid: 4ddc37da-5c94-4beb-b61c-b54071c0e749
topic_type:
- apiref
ms.openlocfilehash: 04befb057be689e68dd3571a13990da9af64551f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801492"
---
# <a name="coreclrdebugprocinfo-structure"></a><span data-ttu-id="5f7b5-103">Структура CoreClrDebugProcInfo</span><span class="sxs-lookup"><span data-stu-id="5f7b5-103">CoreClrDebugProcInfo Structure</span></span>

<span data-ttu-id="5f7b5-104">Представляет процесс, который выполняется на удаленном компьютере.</span><span class="sxs-lookup"><span data-stu-id="5f7b5-104">Represents a process that is running on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f7b5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5f7b5-105">Syntax</span></span>  
  
```cpp  
struct  CoreClrDebugProcInfo {  
    DWORD m_dwPID;  
    DWORD m_dwInternalID;  
    WCHAR m_wszName[256];  
};  
```  
  
## <a name="members"></a><span data-ttu-id="5f7b5-106">Члены</span><span class="sxs-lookup"><span data-stu-id="5f7b5-106">Members</span></span>  
  
|<span data-ttu-id="5f7b5-107">Член</span><span class="sxs-lookup"><span data-stu-id="5f7b5-107">Member</span></span>|<span data-ttu-id="5f7b5-108">Описание</span><span class="sxs-lookup"><span data-stu-id="5f7b5-108">Description</span></span>|  
|------------|-----------------|  
|`m_dwPID`|<span data-ttu-id="5f7b5-109">Идентификатор процесса, назначенный операционной системой.</span><span class="sxs-lookup"><span data-stu-id="5f7b5-109">OS-assigned process identifier.</span></span>|  
|`m_dwInternalID`|<span data-ttu-id="5f7b5-110">Идентификатор процесса, назначенный прокси-сервером удаленной отладки, работающим на целевом компьютере.</span><span class="sxs-lookup"><span data-stu-id="5f7b5-110">Process identifier that is assigned by the remote debugging proxy running on the target machine.</span></span> <span data-ttu-id="5f7b5-111">Этот идентификатор перезапускается реже, чем идентификатор ОС.</span><span class="sxs-lookup"><span data-stu-id="5f7b5-111">This identifier recycles less often than the OS identifier.</span></span>|  
|`m_wszName`|<span data-ttu-id="5f7b5-112">Командная строка процесса.</span><span class="sxs-lookup"><span data-stu-id="5f7b5-112">Command-line of the process.</span></span> <span data-ttu-id="5f7b5-113">Этот член может быть усечен.</span><span class="sxs-lookup"><span data-stu-id="5f7b5-113">This member may be truncated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5f7b5-114">Требования</span><span class="sxs-lookup"><span data-stu-id="5f7b5-114">Requirements</span></span>  

 <span data-ttu-id="5f7b5-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f7b5-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f7b5-116">**Заголовок:** Кореклрремотедебуггингинтерфацес. h</span><span class="sxs-lookup"><span data-stu-id="5f7b5-116">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="5f7b5-117">**Библиотека:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="5f7b5-117">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="5f7b5-118">**Платформа .NET Framework версии:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="5f7b5-118">**.NET Framework Versions:** 3.5 SP1</span></span>
