---
description: 'Дополнительные сведения о: структура Кореклрдебугрунтимеинфо'
title: Структура CoreClrDebugRuntimeInfo
ms.date: 03/30/2017
api_name:
- CoreClrDebugRuntimeInfo
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CoreClrDebugRuntimeInfo
helpviewer_keywords:
- remote debugging API [Silverlight]
- CoreDebugRuntimeInfo structure
- Silverlight, remote debugging
ms.assetid: bd01c30f-b7a8-4179-9497-622b6599b1a6
topic_type:
- apiref
ms.openlocfilehash: 588e8bd1598996d1676e2df5517bd9a52eb59df4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661718"
---
# <a name="coreclrdebugruntimeinfo-structure"></a><span data-ttu-id="02819-103">Структура CoreClrDebugRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="02819-103">CoreClrDebugRuntimeInfo Structure</span></span>

<span data-ttu-id="02819-104">Представляет экземпляр среды CLR, который загружается в процессе на удаленном компьютере.</span><span class="sxs-lookup"><span data-stu-id="02819-104">Represents a common language runtime (CLR) instance that is loaded in a process on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02819-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="02819-105">Syntax</span></span>  
  
```cpp  
struct  CoreClrDebugRuntimeInfo {  
    DWORD m_dwInternalID;  
};  
```  
  
## <a name="members"></a><span data-ttu-id="02819-106">Члены</span><span class="sxs-lookup"><span data-stu-id="02819-106">Members</span></span>  
  
|<span data-ttu-id="02819-107">Член</span><span class="sxs-lookup"><span data-stu-id="02819-107">Member</span></span>|<span data-ttu-id="02819-108">Описание</span><span class="sxs-lookup"><span data-stu-id="02819-108">Description</span></span>|  
|------------|-----------------|  
|`m_dwInternalID`|<span data-ttu-id="02819-109">Идентификатор среды выполнения, назначаемый прокси-сервером удаленной отладки, работающим на целевом компьютере.</span><span class="sxs-lookup"><span data-stu-id="02819-109">Runtime identifier that is assigned by the remote debugging proxy running on the target machine.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="02819-110">Требования</span><span class="sxs-lookup"><span data-stu-id="02819-110">Requirements</span></span>  

 <span data-ttu-id="02819-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02819-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02819-112">**Заголовок:** Кореклрремотедебуггингинтерфацес. h</span><span class="sxs-lookup"><span data-stu-id="02819-112">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="02819-113">**Библиотека:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="02819-113">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="02819-114">**Платформа .NET Framework версии:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="02819-114">**.NET Framework Versions:** 3.5 SP1</span></span>
