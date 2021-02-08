---
description: 'Дополнительные сведения о методе: IDebugAutoAttach:: присоединение'
title: Метод IDebugAutoAttach::AutoAttach
ms.date: 03/30/2017
api_name:
- IDebugAutoAttach.AutoAttach
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IDebugAutoAttach::AutoAttach
helpviewer_keywords:
- AutoAttach method [.NET Framework debugging]
- IDebugAutoAttach::AutoAttach method [.NET Framework debugging]
ms.assetid: 3cf3bd9c-7d88-4afa-a476-94cdc7609aa6
topic_type:
- apiref
ms.openlocfilehash: 8abd35b1d94fc074d4dafe424c52c274b1de1541
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800361"
---
# <a name="idebugautoattachautoattach-method"></a><span data-ttu-id="3ca0c-103">Метод IDebugAutoAttach::AutoAttach</span><span class="sxs-lookup"><span data-stu-id="3ca0c-103">IDebugAutoAttach::AutoAttach Method</span></span>

<span data-ttu-id="3ca0c-104">Выполняет вызванное сервером автоматическое присоединение отладчика.</span><span class="sxs-lookup"><span data-stu-id="3ca0c-104">Performs server-invoked debugger auto attach.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ca0c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3ca0c-105">Syntax</span></span>  
  
```cpp  
HRESULT AutoAttach  
(  
    [in]  REFGUID   guidPort,  
    [in]  DWORD     dwPid,  
    [in]  AUTOATTACH_PROGRAM_TYPE dwProgramType,  
    [in]  DWORD     dwProgramId,  
    [in]  LPCWSTR   pszSessionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ca0c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="3ca0c-106">Parameters</span></span>  

 `guidPort`  
 <span data-ttu-id="3ca0c-107">окне Всегда имеет значение `GUID_NULL` .</span><span class="sxs-lookup"><span data-stu-id="3ca0c-107">[in] Always set to `GUID_NULL`.</span></span>  
  
 `dwPid`  
 <span data-ttu-id="3ca0c-108">окне Идентификатор процесса, обычно полученный с помощью `GetCurrentProcessId` функции.</span><span class="sxs-lookup"><span data-stu-id="3ca0c-108">[in] Process ID, normally retrieved with the `GetCurrentProcessId` function.</span></span>  
  
 `dwProgramType`  
 <span data-ttu-id="3ca0c-109">окне Тип программы: `AUTOATTACH_PROGRAM_WIN32` , `AUTOATTACH_PROGRAM_COMPLUS` или `AUTOATTACH_PROGRAM_UNKNOWN` .</span><span class="sxs-lookup"><span data-stu-id="3ca0c-109">[in] Program type: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, or `AUTOATTACH_PROGRAM_UNKNOWN`.</span></span>  
  
 `dwProgramId`  
 <span data-ttu-id="3ca0c-110">окне Идентификатор программы.</span><span class="sxs-lookup"><span data-stu-id="3ca0c-110">[in] Program ID.</span></span>  
  
 `pszSessionId`  
 <span data-ttu-id="3ca0c-111">окне Строка, передаваемая командой Debug.</span><span class="sxs-lookup"><span data-stu-id="3ca0c-111">[in] String passed by the debug verb.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ca0c-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="3ca0c-112">Return Value</span></span>  

 <span data-ttu-id="3ca0c-113">S_OK, если метод выполнен.</span><span class="sxs-lookup"><span data-stu-id="3ca0c-113">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ca0c-114">Требования</span><span class="sxs-lookup"><span data-stu-id="3ca0c-114">Requirements</span></span>  

 <span data-ttu-id="3ca0c-115">**Заголовок:** Дбгаутоаттач. h</span><span class="sxs-lookup"><span data-stu-id="3ca0c-115">**Header:** DbgAutoAttach.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ca0c-116">См. также</span><span class="sxs-lookup"><span data-stu-id="3ca0c-116">See also</span></span>

- [<span data-ttu-id="3ca0c-117">Интерфейс IDebugAutoAttach</span><span class="sxs-lookup"><span data-stu-id="3ca0c-117">IDebugAutoAttach Interface</span></span>](idebugautoattach-interface.md)
