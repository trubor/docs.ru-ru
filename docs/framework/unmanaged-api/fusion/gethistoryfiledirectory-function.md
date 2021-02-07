---
description: Дополнительные сведения о функции Жесисторифиледиректори
title: Функция GetHistoryFileDirectory
ms.date: 03/30/2017
api_name:
- GetHistoryFileDirectory
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- GetHistoryFileDirectory
helpviewer_keywords:
- GetHistoryFileDirectory function [.NET Framework fusion]
ms.assetid: 93232222-926e-42ac-b85d-8a6d33977672
topic_type:
- apiref
ms.openlocfilehash: 960bc75d69f4be6d1639e109d6327b5e65d3e129
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760970"
---
# <a name="gethistoryfiledirectory-function"></a><span data-ttu-id="b61e1-103">Функция GetHistoryFileDirectory</span><span class="sxs-lookup"><span data-stu-id="b61e1-103">GetHistoryFileDirectory Function</span></span>

<span data-ttu-id="b61e1-104">Возвращает путь к каталогу журнала приложения.</span><span class="sxs-lookup"><span data-stu-id="b61e1-104">Retrieves the path of the application history directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b61e1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b61e1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b61e1-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b61e1-106">Parameters</span></span>  

 `wzDir`  
 <span data-ttu-id="b61e1-107">заполняет Буфер для хранения пути к каталогу журнала приложения.</span><span class="sxs-lookup"><span data-stu-id="b61e1-107">[out] A buffer to hold the path to the application history directory.</span></span>  
  
 `pdwSize`  
 <span data-ttu-id="b61e1-108">[вход, выход] Длина буфера.</span><span class="sxs-lookup"><span data-stu-id="b61e1-108">[in, out] The length of the buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b61e1-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="b61e1-109">Return Value</span></span>  

 <span data-ttu-id="b61e1-110">Этот метод возвращает коды стандартных ошибок COM, как определено в файле WinError. h, а также следующие значения.</span><span class="sxs-lookup"><span data-stu-id="b61e1-110">This method returns standard COM error codes, as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="b61e1-111">Код возврата</span><span class="sxs-lookup"><span data-stu-id="b61e1-111">Return code</span></span>|<span data-ttu-id="b61e1-112">Описание</span><span class="sxs-lookup"><span data-stu-id="b61e1-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="b61e1-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="b61e1-113">S_OK</span></span>|<span data-ttu-id="b61e1-114">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="b61e1-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="b61e1-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b61e1-115">E_INVALIDARG</span></span>|<span data-ttu-id="b61e1-116">`wzDir` или `pdwSize` имеет значение null, или строка версии неверна.</span><span class="sxs-lookup"><span data-stu-id="b61e1-116">`wzDir` or `pdwSize` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b61e1-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="b61e1-117">Remarks</span></span>  

 <span data-ttu-id="b61e1-118">При успешном завершении `pdwSize` аргументу присваивается длина строки пути.</span><span class="sxs-lookup"><span data-stu-id="b61e1-118">On successful completion, the `pdwSize` argument is set to the length of the path string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b61e1-119">Требования</span><span class="sxs-lookup"><span data-stu-id="b61e1-119">Requirements</span></span>  

 <span data-ttu-id="b61e1-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b61e1-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b61e1-121">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="b61e1-121">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b61e1-122">**Библиотека:** Fusion.dll и Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="b61e1-122">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="b61e1-123">Используйте Fusion.dll вместо Mscorwks.dll, чтобы убедиться в правильности целевой версии платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b61e1-123">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="b61e1-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b61e1-124">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b61e1-125">См. также</span><span class="sxs-lookup"><span data-stu-id="b61e1-125">See also</span></span>

- [<span data-ttu-id="b61e1-126">Функция CreateHistoryReader</span><span class="sxs-lookup"><span data-stu-id="b61e1-126">CreateHistoryReader Function</span></span>](createhistoryreader-function.md)
- [<span data-ttu-id="b61e1-127">Функция NukeDownloadedCache</span><span class="sxs-lookup"><span data-stu-id="b61e1-127">NukeDownloadedCache Function</span></span>](nukedownloadedcache-function.md)
- [<span data-ttu-id="b61e1-128">Глобальные статические функции Fusion</span><span class="sxs-lookup"><span data-stu-id="b61e1-128">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
