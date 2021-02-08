---
description: Дополнительные сведения о функции Жетфилеверсион
title: Функция GetFileVersion
ms.date: 03/30/2017
api_name:
- GetFileVersion
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetFileVersion
helpviewer_keywords:
- GetFileVersion function [.NET Framework hosting]
ms.assetid: b3222c85-da88-4485-97d7-3a6ee3e8d358
topic_type:
- apiref
ms.openlocfilehash: 7de19484f2f8123d61eb94e6a5ae09f56a3b5541
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785306"
---
# <a name="getfileversion-function"></a><span data-ttu-id="8fc21-103">Функция GetFileVersion</span><span class="sxs-lookup"><span data-stu-id="8fc21-103">GetFileVersion Function</span></span>

<span data-ttu-id="8fc21-104">Возвращает сведения о версии среды CLR указанного файла, используя указанный буфер.</span><span class="sxs-lookup"><span data-stu-id="8fc21-104">Gets the common language runtime (CLR) version information of the specified file, using the specified buffer.</span></span>  
  
 <span data-ttu-id="8fc21-105">Эта функция является устаревшей в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="8fc21-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fc21-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8fc21-106">Syntax</span></span>  
  
```cpp  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,
    [in, out] LPWSTR   szBuffer,
    [in]  DWORD        cchBuffer,
    [out] DWORD        *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8fc21-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="8fc21-107">Parameters</span></span>  

 `szFilename`  
 <span data-ttu-id="8fc21-108">окне Путь к файлу, который необходимо проверить.</span><span class="sxs-lookup"><span data-stu-id="8fc21-108">[in] The path of the file to be examined.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="8fc21-109">[вход, выход] Буфер, выделенный для возвращаемой информации о версии.</span><span class="sxs-lookup"><span data-stu-id="8fc21-109">[in, out] The buffer allocated for the version information that is returned.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="8fc21-110">окне Размер (в расширенных символах) `szBuffer` .</span><span class="sxs-lookup"><span data-stu-id="8fc21-110">[in] The size, in wide characters, of `szBuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="8fc21-111">заполняет Размер возвращаемого объекта (в байтах) `szBuffer` .</span><span class="sxs-lookup"><span data-stu-id="8fc21-111">[out] The size, in bytes, of the returned `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fc21-112">Требования</span><span class="sxs-lookup"><span data-stu-id="8fc21-112">Requirements</span></span>  

 <span data-ttu-id="8fc21-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fc21-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fc21-114">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8fc21-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8fc21-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fc21-115">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fc21-116">См. также</span><span class="sxs-lookup"><span data-stu-id="8fc21-116">See also</span></span>

- [<span data-ttu-id="8fc21-117">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="8fc21-117">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
