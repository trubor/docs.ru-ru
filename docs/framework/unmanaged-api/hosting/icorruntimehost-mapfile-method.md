---
description: 'Дополнительные сведения о методе: ICorRuntimeHost:: сопоставления'
title: Метод ICorRuntimeHost::MapFile
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.MapFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::MapFile
helpviewer_keywords:
- ICorRuntimeHost::MapFile method [.NET Framework hosting]
- MapFile method [.NET Framework hosting]
ms.assetid: 45ae0502-0a31-4342-b7e3-f36e1cf738f3
topic_type:
- apiref
ms.openlocfilehash: 80c01a036de83b32b9d0de745d76bb97825c980b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789636"
---
# <a name="icorruntimehostmapfile-method"></a><span data-ttu-id="dfaef-103">Метод ICorRuntimeHost::MapFile</span><span class="sxs-lookup"><span data-stu-id="dfaef-103">ICorRuntimeHost::MapFile Method</span></span>

<span data-ttu-id="dfaef-104">Сопоставляет указанный файл с памятью.</span><span class="sxs-lookup"><span data-stu-id="dfaef-104">Maps the specified file into memory.</span></span> <span data-ttu-id="dfaef-105">Этот метод устарел.</span><span class="sxs-lookup"><span data-stu-id="dfaef-105">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfaef-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dfaef-106">Syntax</span></span>  
  
```cpp  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dfaef-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="dfaef-107">Parameters</span></span>  

 `hFile`  
 <span data-ttu-id="dfaef-108">окне Описатель файла для сопоставления.</span><span class="sxs-lookup"><span data-stu-id="dfaef-108">[in] The handle of the file to be mapped.</span></span>  
  
 `hMapAddress`  
 <span data-ttu-id="dfaef-109">заполняет Начальный адрес памяти, с которого начинается сопоставление файла.</span><span class="sxs-lookup"><span data-stu-id="dfaef-109">[out] The starting memory address at which to begin mapping the file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfaef-110">Требования</span><span class="sxs-lookup"><span data-stu-id="dfaef-110">Requirements</span></span>  

 <span data-ttu-id="dfaef-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfaef-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfaef-112">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="dfaef-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dfaef-113">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dfaef-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dfaef-114">**Версия платформа .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="dfaef-114">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfaef-115">См. также</span><span class="sxs-lookup"><span data-stu-id="dfaef-115">See also</span></span>

- [<span data-ttu-id="dfaef-116">Интерфейс ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="dfaef-116">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
