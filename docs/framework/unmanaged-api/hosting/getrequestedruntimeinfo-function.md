---
description: Дополнительные сведения о функции GetRequestedRuntimeInfo
title: Функция GetRequestedRuntimeInfo
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeInfo
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeInfo
helpviewer_keywords:
- GetRequestedRuntimeInfo function [.NET Framework hosting]
ms.assetid: 0dfd7cdc-c116-4e25-b56a-ac7b0378c942
topic_type:
- apiref
ms.openlocfilehash: 63d0bdcd07be5727cddc0acc352e8358b5ff0090
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785293"
---
# <a name="getrequestedruntimeinfo-function"></a><span data-ttu-id="83852-103">Функция GetRequestedRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="83852-103">GetRequestedRuntimeInfo Function</span></span>

<span data-ttu-id="83852-104">Возвращает сведения о версии и каталоге о среде CLR, запрашиваемой приложением.</span><span class="sxs-lookup"><span data-stu-id="83852-104">Gets version and directory information about the common language runtime (CLR) requested by an application.</span></span>  
  
 <span data-ttu-id="83852-105">Эта функция является устаревшей в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="83852-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83852-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="83852-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeInfo (  
    [in]  LPCWSTR  pExe,
    [in]  LPCWSTR  pwszVersion,
    [in]  LPCWSTR  pConfigurationFile,
    [in]  DWORD    startupFlags,
    [in]  DWORD    runtimeInfoFlags,
    [out] LPWSTR   pDirectory,
    [in]  DWORD    dwDirectory,
    [out] DWORD   *dwDirectoryLength,
    [out] LPWSTR   pVersion,
    [in]  DWORD    cchBuffer,
    [out] DWORD   *dwlength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83852-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="83852-107">Parameters</span></span>  

 `pExe`  
 <span data-ttu-id="83852-108">окне Имя приложения.</span><span class="sxs-lookup"><span data-stu-id="83852-108">[in] The name of the application.</span></span>  
  
 `pwszVersion`  
 <span data-ttu-id="83852-109">окне Строка, указывающая номер версии среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="83852-109">[in] A string specifying the version number of the runtime.</span></span>  
  
 `pConfigurationFile`  
 <span data-ttu-id="83852-110">окне Имя файла конфигурации, связанного с `pExe` .</span><span class="sxs-lookup"><span data-stu-id="83852-110">[in] The name of the configuration file that is associated with `pExe`.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="83852-111">окне Одно или несколько значений перечисления [STARTUP_FLAGS](startup-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="83852-111">[in] One or more of the [STARTUP_FLAGS](startup-flags-enumeration.md) enumeration values.</span></span>  
  
 `runtimeInfoFlags`  
 <span data-ttu-id="83852-112">окне Одно или несколько значений перечисления [RUNTIME_INFO_FLAGS](runtime-info-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="83852-112">[in] One or more of the [RUNTIME_INFO_FLAGS](runtime-info-flags-enumeration.md) enumeration values.</span></span>  
  
 `pDirectory`  
 <span data-ttu-id="83852-113">заполняет Буфер, содержащий путь к каталогу среды выполнения после успешного завершения.</span><span class="sxs-lookup"><span data-stu-id="83852-113">[out] A buffer that contains the directory path to the runtime upon successful completion.</span></span>  
  
 `dwDirectory`  
 <span data-ttu-id="83852-114">окне Длина буфера каталога.</span><span class="sxs-lookup"><span data-stu-id="83852-114">[in] The length of the directory buffer.</span></span>  
  
 `dwDirectoryLength`  
 <span data-ttu-id="83852-115">заполняет Указатель на длину строки пути к каталогу.</span><span class="sxs-lookup"><span data-stu-id="83852-115">[out] A pointer to the length of the directory path string.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="83852-116">заполняет Буфер, содержащий номер версии среды выполнения после успешного завершения.</span><span class="sxs-lookup"><span data-stu-id="83852-116">[out] A buffer that contains the version number of the runtime upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="83852-117">окне Длина буфера строки версии.</span><span class="sxs-lookup"><span data-stu-id="83852-117">[in] The length of the version string buffer.</span></span>  
  
 `dwlength`  
 <span data-ttu-id="83852-118">заполняет Указатель на длину строки версии.</span><span class="sxs-lookup"><span data-stu-id="83852-118">[out] A pointer to the length of the version string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83852-119">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="83852-119">Return Value</span></span>  

 <span data-ttu-id="83852-120">Этот метод возвращает коды стандартных ошибок модели COM, как определено в файле WinError. h, в дополнение к следующим значениям.</span><span class="sxs-lookup"><span data-stu-id="83852-120">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="83852-121">Код возврата</span><span class="sxs-lookup"><span data-stu-id="83852-121">Return code</span></span>|<span data-ttu-id="83852-122">Описание</span><span class="sxs-lookup"><span data-stu-id="83852-122">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="83852-123">S_OK</span><span class="sxs-lookup"><span data-stu-id="83852-123">S_OK</span></span>|<span data-ttu-id="83852-124">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="83852-124">The method completed successfully.</span></span>|  
|<span data-ttu-id="83852-125">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="83852-125">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="83852-126">Буфер каталога недостаточно велик для хранения пути к каталогу.</span><span class="sxs-lookup"><span data-stu-id="83852-126">The directory buffer is not large enough to store the directory path.</span></span><br /><br /> <span data-ttu-id="83852-127">-или-</span><span class="sxs-lookup"><span data-stu-id="83852-127">- or -</span></span><br /><br /> <span data-ttu-id="83852-128">Буфер версии недостаточно велик для хранения строки версии.</span><span class="sxs-lookup"><span data-stu-id="83852-128">The version buffer is not large enough to store the version string.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83852-129">Remarks</span><span class="sxs-lookup"><span data-stu-id="83852-129">Remarks</span></span>  

 <span data-ttu-id="83852-130">`GetRequestedRuntimeInfo`Метод возвращает сведения времени выполнения о версии, загруженной в процесс, что не обязательно является последней версией, установленной на компьютере.</span><span class="sxs-lookup"><span data-stu-id="83852-130">The `GetRequestedRuntimeInfo` method returns run-time information about the version loaded into the process, which is not necessarily the latest version installed on the computer.</span></span>  
  
 <span data-ttu-id="83852-131">В платформа .NET Framework версии 2,0 можно получить сведения о последней установленной версии с помощью `GetRequestedRuntimeInfo` метода следующим образом.</span><span class="sxs-lookup"><span data-stu-id="83852-131">In the .NET Framework version 2.0, you can get information about the latest installed version by using the `GetRequestedRuntimeInfo` method as follows:</span></span>  
  
- <span data-ttu-id="83852-132">Укажите для `pExe` `pwszVersion` параметров, и `pConfigurationFile` значение null.</span><span class="sxs-lookup"><span data-stu-id="83852-132">Specify the `pExe`, `pwszVersion`, and `pConfigurationFile` parameters as null.</span></span>  
  
- <span data-ttu-id="83852-133">Укажите флаг RUNTIME_INFO_UPGRADE_VERSION в `RUNTIME_INFO_FLAGS` перечислениях для `runtimeInfoFlags` параметра.</span><span class="sxs-lookup"><span data-stu-id="83852-133">Specify the RUNTIME_INFO_UPGRADE_VERSION flag in the `RUNTIME_INFO_FLAGS` enumerations for the `runtimeInfoFlags` parameter.</span></span>  
  
 <span data-ttu-id="83852-134">`GetRequestedRuntimeInfo`Метод не возвращает последнюю версию среды CLR в следующих случаях:</span><span class="sxs-lookup"><span data-stu-id="83852-134">The `GetRequestedRuntimeInfo` method does not return the latest CLR version in the following circumstances:</span></span>  
  
- <span data-ttu-id="83852-135">Существует файл конфигурации приложения, указывающий загрузку определенной версии среды CLR.</span><span class="sxs-lookup"><span data-stu-id="83852-135">An application configuration file that specifies loading a particular CLR version exists.</span></span> <span data-ttu-id="83852-136">Обратите внимание, что платформа .NET Framework будет использовать файл конфигурации, даже если для параметра указано значение NULL `pConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="83852-136">Note that the .NET Framework will use the configuration file even if you specify null for the `pConfigurationFile` parameter.</span></span>  
  
- <span data-ttu-id="83852-137">Метод [CorBindToRuntimeEx](corbindtoruntimeex-function.md) был вызван с указанием более ранней версии среды CLR.</span><span class="sxs-lookup"><span data-stu-id="83852-137">The [CorBindToRuntimeEx](corbindtoruntimeex-function.md) method was called specifying an earlier CLR version.</span></span>  
  
- <span data-ttu-id="83852-138">В настоящее время выполняется приложение, которое было скомпилировано для более ранней версии среды CLR.</span><span class="sxs-lookup"><span data-stu-id="83852-138">An application that was compiled for an earlier CLR version is currently running.</span></span>  
  
 <span data-ttu-id="83852-139">Для `runtimeInfoFlags` параметра можно указать только одну из констант архитектуры `RUNTIME_INFO_FLAGS` перечисления в один момент времени:</span><span class="sxs-lookup"><span data-stu-id="83852-139">For the `runtimeInfoFlags` parameter, you can specify only one of the architecture constants of the `RUNTIME_INFO_FLAGS` enumeration at a time:</span></span>  
  
- <span data-ttu-id="83852-140">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="83852-140">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
- <span data-ttu-id="83852-141">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="83852-141">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
- <span data-ttu-id="83852-142">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="83852-142">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83852-143">Требования</span><span class="sxs-lookup"><span data-stu-id="83852-143">Requirements</span></span>  

 <span data-ttu-id="83852-144">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83852-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83852-145">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="83852-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="83852-146">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="83852-146">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83852-147">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83852-147">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83852-148">См. также</span><span class="sxs-lookup"><span data-stu-id="83852-148">See also</span></span>

- [<span data-ttu-id="83852-149">Функция GetRequestedRuntimeVersion</span><span class="sxs-lookup"><span data-stu-id="83852-149">GetRequestedRuntimeVersion Function</span></span>](getrequestedruntimeversion-function.md)
- [<span data-ttu-id="83852-150">Функция GetVersionFromProcess</span><span class="sxs-lookup"><span data-stu-id="83852-150">GetVersionFromProcess Function</span></span>](getversionfromprocess-function.md)
- [<span data-ttu-id="83852-151">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="83852-151">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
