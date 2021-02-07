---
description: Дополнительные сведения о функции RunDll32ShimW
title: Функция RunDll32ShimW
ms.date: 03/30/2017
api_name:
- RunDll32ShimW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- RunDll32ShimW
helpviewer_keywords:
- RunDll32ShimW function [.NET Framework hosting]
ms.assetid: 9ea07b57-96e2-44df-8711-8fe6c119087f
topic_type:
- apiref
ms.openlocfilehash: d01021358a6cddf15d1a0e1b223c9acff3c64ff7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679502"
---
# <a name="rundll32shimw-function"></a><span data-ttu-id="219c8-103">Функция RunDll32ShimW</span><span class="sxs-lookup"><span data-stu-id="219c8-103">RunDll32ShimW Function</span></span>

<span data-ttu-id="219c8-104">Выполняет указанную команду.</span><span class="sxs-lookup"><span data-stu-id="219c8-104">Executes the specified command.</span></span>  
  
 <span data-ttu-id="219c8-105">Эта функция является устаревшей в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="219c8-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="219c8-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="219c8-106">Syntax</span></span>  
  
```cpp  
HRESULT RunDll32ShimW (  
    [in] HWND        hwnd,  
    [in] HINSTANCE   hinst,  
    [in] LPCWSTR     lpszCmdLine,  
    [in] int         nCmdShow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="219c8-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="219c8-107">Parameters</span></span>  

 `hwnd`  
 <span data-ttu-id="219c8-108">окне Маркер окна, в котором будут отображаться выходные данные команды.</span><span class="sxs-lookup"><span data-stu-id="219c8-108">[in] A handle to a window in which the command output will be displayed.</span></span>  
  
 `hinst`  
 <span data-ttu-id="219c8-109">окне Маркер библиотеки, которая содержит команду.</span><span class="sxs-lookup"><span data-stu-id="219c8-109">[in] A handle to the library that contains the command.</span></span>  
  
 `lpszCmdLine`  
 <span data-ttu-id="219c8-110">окне Строка, указывающая выполняемую команду.</span><span class="sxs-lookup"><span data-stu-id="219c8-110">[in] A string that specifies the command to be executed.</span></span>  
  
 `nCmdShow`  
 <span data-ttu-id="219c8-111">окне Целое число, указывающее режим просмотра для окна вывода.</span><span class="sxs-lookup"><span data-stu-id="219c8-111">[in] An integer that specifies the display mode for the output window.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="219c8-112">Требования</span><span class="sxs-lookup"><span data-stu-id="219c8-112">Requirements</span></span>  

 <span data-ttu-id="219c8-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="219c8-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="219c8-114">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="219c8-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="219c8-115">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="219c8-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="219c8-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="219c8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="219c8-117">См. также</span><span class="sxs-lookup"><span data-stu-id="219c8-117">See also</span></span>

- [<span data-ttu-id="219c8-118">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="219c8-118">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
