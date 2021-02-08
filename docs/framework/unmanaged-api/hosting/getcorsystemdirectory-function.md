---
description: Дополнительные сведения о функции GetCORSystemDirectory
title: Функция GetCORSystemDirectory
ms.date: 03/30/2017
api_name:
- GetCORSystemDirectory
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORSystemDirectory
helpviewer_keywords:
- GetCORSystemDirectory function [.NET Framework hosting]
ms.assetid: 3dcd16a7-dafc-4ca8-b5cd-20ffb37db91d
topic_type:
- apiref
ms.openlocfilehash: 267736c2f8cdea03fbd9f77108a3d88193830ab4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785345"
---
# <a name="getcorsystemdirectory-function"></a><span data-ttu-id="2b346-103">Функция GetCORSystemDirectory</span><span class="sxs-lookup"><span data-stu-id="2b346-103">GetCORSystemDirectory Function</span></span>

<span data-ttu-id="2b346-104">Возвращает каталог установки среды CLR, который загружается в процесс.</span><span class="sxs-lookup"><span data-stu-id="2b346-104">Returns the installation directory of the common language runtime (CLR) that is loaded into the process.</span></span> <span data-ttu-id="2b346-105">Каталог установки полностью квалифицирован, например "c:\windows\microsoft.net\framework\v1.0.3705".</span><span class="sxs-lookup"><span data-stu-id="2b346-105">The installation directory is fully qualified, for example, "c:\windows\microsoft.net\framework\v1.0.3705".</span></span>  
  
 <span data-ttu-id="2b346-106">Эта функция является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="2b346-106">This function is deprecated.</span></span> <span data-ttu-id="2b346-107">Он заменяется методом [ICLRRuntimeInfo:: GetRuntimeDirectory](iclrruntimeinfo-getruntimedirectory-method.md) , предоставленным в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="2b346-107">It is superseded by the [ICLRRuntimeInfo::GetRuntimeDirectory](iclrruntimeinfo-getruntimedirectory-method.md) method provided in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b346-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2b346-108">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (
    [out] LPWSTR  pbuffer,
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="2b346-109">Параметры</span><span class="sxs-lookup"><span data-stu-id="2b346-109">Parameters</span></span>  

 `pbuffer`  
 <span data-ttu-id="2b346-110">заполняет Буфер, в котором среда выполнения возвращает строку, содержащую полное имя каталога установки для среды выполнения, которая загружается в процесс.</span><span class="sxs-lookup"><span data-stu-id="2b346-110">[out] A buffer in which the runtime returns a string that contains the fully qualified name of the installation directory for the runtime that is loaded into the process.</span></span> <span data-ttu-id="2b346-111">Если среда выполнения еще не загружена в процесс, функция возвращает соответствующие сведения о каталоге для последней версии среды выполнения, установленной на компьютере.</span><span class="sxs-lookup"><span data-stu-id="2b346-111">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="2b346-112">окне Размер (в байтах) `pbuffer` .</span><span class="sxs-lookup"><span data-stu-id="2b346-112">[in] The size, in bytes, of `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="2b346-113">заполняет Число символов, возвращаемых в `pbuffer` .</span><span class="sxs-lookup"><span data-stu-id="2b346-113">[out] The number of characters returned in `pbuffer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b346-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="2b346-114">Remarks</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="2b346-115">Не используйте эту функцию в процессах, работающих в среде CLR версии 4.</span><span class="sxs-lookup"><span data-stu-id="2b346-115">Do not use this function in processes that are running version 4 of the CLR.</span></span> <span data-ttu-id="2b346-116">Если на компьютере установлена более ранняя версия среды CLR, эта функция возвращает каталог установки для этой версии.</span><span class="sxs-lookup"><span data-stu-id="2b346-116">If an earlier version of the CLR is installed on the computer, this function returns the installation directory for that version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b346-117">Требования</span><span class="sxs-lookup"><span data-stu-id="2b346-117">Requirements</span></span>  

 <span data-ttu-id="2b346-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b346-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b346-119">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2b346-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2b346-120">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2b346-120">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2b346-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b346-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b346-122">См. также</span><span class="sxs-lookup"><span data-stu-id="2b346-122">See also</span></span>

- [<span data-ttu-id="2b346-123">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="2b346-123">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
