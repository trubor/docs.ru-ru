---
description: Дополнительные сведения о функции GetVersionFromProcess
title: Функция GetVersionFromProcess
ms.date: 03/30/2017
api_name:
- GetVersionFromProcess
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetVersionFromProcess
helpviewer_keywords:
- GetVersionFromProcess function [.NET Framework hosting]
ms.assetid: a9f7f824-64a1-408d-8607-91c7f19d21fe
topic_type:
- apiref
ms.openlocfilehash: ab665d2984f79baf049009690b36782528094937
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785254"
---
# <a name="getversionfromprocess-function"></a><span data-ttu-id="3cc0e-103">Функция GetVersionFromProcess</span><span class="sxs-lookup"><span data-stu-id="3cc0e-103">GetVersionFromProcess Function</span></span>

<span data-ttu-id="3cc0e-104">Возвращает номер версии общеязыковой среды выполнения (CLR), связанной с указанным обработчиком процесса.</span><span class="sxs-lookup"><span data-stu-id="3cc0e-104">Gets the version number of the common language runtime (CLR) that is associated with the specified process handle.</span></span>  
  
 <span data-ttu-id="3cc0e-105">Эта функция является устаревшей в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3cc0e-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cc0e-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3cc0e-106">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3cc0e-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="3cc0e-107">Parameters</span></span>  

 `hProcess`  
 <span data-ttu-id="3cc0e-108">окне Обработчик процесса.</span><span class="sxs-lookup"><span data-stu-id="3cc0e-108">[in] A handle to a process.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="3cc0e-109">заполняет Буфер, содержащий строку номера версии после успешного завершения метода.</span><span class="sxs-lookup"><span data-stu-id="3cc0e-109">[out] A buffer that contains the version number string upon successful completion of the method.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="3cc0e-110">окне Длина буфера версии.</span><span class="sxs-lookup"><span data-stu-id="3cc0e-110">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="3cc0e-111">заполняет Указатель на длину строки номера версии.</span><span class="sxs-lookup"><span data-stu-id="3cc0e-111">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3cc0e-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="3cc0e-112">Return Value</span></span>  

 <span data-ttu-id="3cc0e-113">Этот метод возвращает коды стандартных ошибок модели COM, как определено в файле WinError. h, в дополнение к следующим значениям.</span><span class="sxs-lookup"><span data-stu-id="3cc0e-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="3cc0e-114">Код возврата</span><span class="sxs-lookup"><span data-stu-id="3cc0e-114">Return code</span></span>|<span data-ttu-id="3cc0e-115">Описание</span><span class="sxs-lookup"><span data-stu-id="3cc0e-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="3cc0e-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="3cc0e-116">S_OK</span></span>|<span data-ttu-id="3cc0e-117">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="3cc0e-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="3cc0e-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3cc0e-118">E_INVALIDARG</span></span>|<span data-ttu-id="3cc0e-119">`pVersion` имеет значение NULL и не `cchBuffer` имеет значение null, или наоборот.</span><span class="sxs-lookup"><span data-stu-id="3cc0e-119">`pVersion` is null and `cchBuffer` is not null, or vice versa.</span></span><br /><br /> <span data-ttu-id="3cc0e-120">-или-</span><span class="sxs-lookup"><span data-stu-id="3cc0e-120">-or-</span></span><br /><br /> <span data-ttu-id="3cc0e-121">`hProcess` не является допустимым маркером для процесса.</span><span class="sxs-lookup"><span data-stu-id="3cc0e-121">`hProcess` is not a valid handle to a process.</span></span><br /><br /> <span data-ttu-id="3cc0e-122">-или-</span><span class="sxs-lookup"><span data-stu-id="3cc0e-122">-or-</span></span><br /><br /> <span data-ttu-id="3cc0e-123">Среда CLR не загружена.</span><span class="sxs-lookup"><span data-stu-id="3cc0e-123">The CLR is not loaded.</span></span>|  
|<span data-ttu-id="3cc0e-124">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="3cc0e-124">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="3cc0e-125">`cchBuffer` параметр имеет значение null или меньше длины строки версии.</span><span class="sxs-lookup"><span data-stu-id="3cc0e-125">`cchBuffer` is null or less than the length of the version string.</span></span>|  
|<span data-ttu-id="3cc0e-126">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="3cc0e-126">E_NOTIMPL</span></span>|<span data-ttu-id="3cc0e-127">Этот метод недоступен в операционной системе Microsoft Windows 95, Microsoft Windows 98 или Microsoft Windows Millennium Edition.</span><span class="sxs-lookup"><span data-stu-id="3cc0e-127">This method is not available on the Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows Millennium Edition operating system.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3cc0e-128">Требования</span><span class="sxs-lookup"><span data-stu-id="3cc0e-128">Requirements</span></span>  

 <span data-ttu-id="3cc0e-129">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3cc0e-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cc0e-130">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3cc0e-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3cc0e-131">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3cc0e-131">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3cc0e-132">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cc0e-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cc0e-133">См. также</span><span class="sxs-lookup"><span data-stu-id="3cc0e-133">See also</span></span>

- [<span data-ttu-id="3cc0e-134">Функция GetRequestedRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="3cc0e-134">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="3cc0e-135">Функция GetRequestedRuntimeVersion</span><span class="sxs-lookup"><span data-stu-id="3cc0e-135">GetRequestedRuntimeVersion Function</span></span>](getrequestedruntimeversion-function.md)
- [<span data-ttu-id="3cc0e-136">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="3cc0e-136">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
