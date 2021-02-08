---
description: Дополнительные сведения о функции Жеткоррекуиредверсион
title: Функция GetCORRequiredVersion
ms.date: 03/30/2017
api_name:
- GetCORRequiredVersion
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetCORRequiredVersion
helpviewer_keywords:
- GetCORRequiredVersion function [.NET Framework hosting]
ms.assetid: 1588fe7b-c378-4f4b-9c4b-48647f1119cc
topic_type:
- apiref
ms.openlocfilehash: ea1b928054e3ec6080b00e2a41228035f50c0f84
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785358"
---
# <a name="getcorrequiredversion-function"></a><span data-ttu-id="91a13-103">Функция GetCORRequiredVersion</span><span class="sxs-lookup"><span data-stu-id="91a13-103">GetCORRequiredVersion Function</span></span>

<span data-ttu-id="91a13-104">Возвращает требуемый номер версии среды CLR.</span><span class="sxs-lookup"><span data-stu-id="91a13-104">Gets the required common language runtime (CLR) version number.</span></span>  
  
 <span data-ttu-id="91a13-105">Эта функция является устаревшей в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="91a13-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91a13-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="91a13-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCORRequiredVersion (  
    [out] LPWSTR   pbuffer,  
    [in]  DWORD    cchBuffer,  
    [out] DWORD   *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91a13-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="91a13-107">Parameters</span></span>  

 `pbuffer`  
 <span data-ttu-id="91a13-108">заполняет Буфер, содержащий строку, указывающую номер версии.</span><span class="sxs-lookup"><span data-stu-id="91a13-108">[out] A buffer containing a string that specifies the version number.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="91a13-109">окне Размер буфера в байтах.</span><span class="sxs-lookup"><span data-stu-id="91a13-109">[in] The size, in bytes, of the buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="91a13-110">заполняет Число байтов, возвращенных в буфере.</span><span class="sxs-lookup"><span data-stu-id="91a13-110">[out] The number of bytes returned in the buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91a13-111">Требования</span><span class="sxs-lookup"><span data-stu-id="91a13-111">Requirements</span></span>  

 <span data-ttu-id="91a13-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91a13-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91a13-113">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="91a13-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="91a13-114">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="91a13-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="91a13-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91a13-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91a13-116">См. также</span><span class="sxs-lookup"><span data-stu-id="91a13-116">See also</span></span>

- [<span data-ttu-id="91a13-117">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="91a13-117">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
