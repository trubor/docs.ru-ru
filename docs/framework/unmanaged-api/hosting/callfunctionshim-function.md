---
description: Дополнительные сведения о функции Каллфунктионшим
title: Функция CallFunctionShim
ms.date: 03/30/2017
api_name:
- CallFunctionShim
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CallFunctionShim
helpviewer_keywords:
- CallfunctionShim function [.NET Framework hosting]
ms.assetid: 37118465-ddf3-41f0-bf27-335b72777e63
topic_type:
- apiref
ms.openlocfilehash: 7ddd16a06005011adcf41190929fd62f4132f14d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799958"
---
# <a name="callfunctionshim-function"></a><span data-ttu-id="0edc7-103">Функция CallFunctionShim</span><span class="sxs-lookup"><span data-stu-id="0edc7-103">CallFunctionShim Function</span></span>

<span data-ttu-id="0edc7-104">Вызывает функцию с указанным именем и параметрами в указанной библиотеке.</span><span class="sxs-lookup"><span data-stu-id="0edc7-104">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 <span data-ttu-id="0edc7-105">Эта функция является устаревшей в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="0edc7-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0edc7-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0edc7-106">Syntax</span></span>  
  
```cpp  
HRESULT CallFunctionShim (  
    [in] LPCWSTR     szDllName,  
    [in] LPCSTR      szFunctionName,  
    [in] LPVOID      lpvArgument1,  
    [in] LPVOID      lpvArgument2,  
    [in] LPCWSTR     szVersion,  
    [in] LPVOID      pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0edc7-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="0edc7-107">Parameters</span></span>  

 `szDllName`  
 <span data-ttu-id="0edc7-108">окне Имя библиотеки, содержащей функцию.</span><span class="sxs-lookup"><span data-stu-id="0edc7-108">[in] The name of the library containing the function.</span></span>  
  
 `szFunctionName`  
 <span data-ttu-id="0edc7-109">окне Имя функции.</span><span class="sxs-lookup"><span data-stu-id="0edc7-109">[in] The name of the function.</span></span>  
  
 `lpvArgument1`  
 <span data-ttu-id="0edc7-110">окне Первый аргумент для передачи в функцию.</span><span class="sxs-lookup"><span data-stu-id="0edc7-110">[in] The first argument to pass to the function.</span></span>  
  
 `lpvArgument2`  
 <span data-ttu-id="0edc7-111">окне Второй аргумент для передачи в функцию.</span><span class="sxs-lookup"><span data-stu-id="0edc7-111">[in] The second argument to pass to the function.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="0edc7-112">окне Версия библиотеки, которая содержит функцию.</span><span class="sxs-lookup"><span data-stu-id="0edc7-112">[in] The version of the library that contains the function.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="0edc7-113">[in] Зарезервирован для будущего использования.</span><span class="sxs-lookup"><span data-stu-id="0edc7-113">[in] Reserved for future use.</span></span> <span data-ttu-id="0edc7-114">В этом параметре следует передать ноль.</span><span class="sxs-lookup"><span data-stu-id="0edc7-114">Pass zero in this parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0edc7-115">Требования</span><span class="sxs-lookup"><span data-stu-id="0edc7-115">Requirements</span></span>  

 <span data-ttu-id="0edc7-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0edc7-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0edc7-117">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0edc7-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0edc7-118">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0edc7-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0edc7-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0edc7-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0edc7-120">См. также</span><span class="sxs-lookup"><span data-stu-id="0edc7-120">See also</span></span>

- [<span data-ttu-id="0edc7-121">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="0edc7-121">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
