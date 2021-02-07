---
description: 'Дополнительные сведения о методе: ICLRMetaHost:: Жетверсионфромфиле'
title: Метод ICLRMetaHost::GetVersionFromFile
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetVersionFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetVersionFromFile
helpviewer_keywords:
- ICLRMetaHost::GetVersionFromFile method [.NET Framework hosting]
- GetVersionFromFile method [.NET Framework hosting]
ms.assetid: 55bb3eb4-f665-42fc-973c-465567570e82
topic_type:
- apiref
ms.openlocfilehash: 0122c4aba3b8454a84540b22e815c61a2cb25df8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689057"
---
# <a name="iclrmetahostgetversionfromfile-method"></a><span data-ttu-id="147f0-103">Метод ICLRMetaHost::GetVersionFromFile</span><span class="sxs-lookup"><span data-stu-id="147f0-103">ICLRMetaHost::GetVersionFromFile Method</span></span>

<span data-ttu-id="147f0-104">Возвращает исходную версию компиляции платформа .NET Framework сборки (хранящейся в метаданных) по указанному пути к файлу.</span><span class="sxs-lookup"><span data-stu-id="147f0-104">Gets an assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="147f0-105">Этот метод заменяет функцию [жетфилеверсион](getfileversion-function.md) .</span><span class="sxs-lookup"><span data-stu-id="147f0-105">This method supersedes the [GetFileVersion](getfileversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="147f0-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="147f0-106">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionFromFile (  
    [in] LPCWSTR pwzFilePath,  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBuffer);  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="147f0-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="147f0-107">Parameters</span></span>  

 `pwzFilePath`  
 <span data-ttu-id="147f0-108">окне Полный путь к файлу сборки.</span><span class="sxs-lookup"><span data-stu-id="147f0-108">[in] The complete assembly file path.</span></span>  
  
 `pwzbuffer`  
 <span data-ttu-id="147f0-109">заполняет Версия компиляции платформа .NET Framework, хранящаяся в метаданных, в формате "v *A*. *B*[.*X*] ".</span><span class="sxs-lookup"><span data-stu-id="147f0-109">[out] The .NET Framework compilation version stored in the metadata, in the format "v *A*.*B*[.*X*]".</span></span> <span data-ttu-id="147f0-110">*A*, *B* и *X* — это десятичные числа, соответствующие основной версии, дополнительной версии и номеру сборки.</span><span class="sxs-lookup"><span data-stu-id="147f0-110">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="147f0-111">Длина этой строки ограничена MAX_PATH.</span><span class="sxs-lookup"><span data-stu-id="147f0-111">The length of this string is limited to MAX_PATH.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="147f0-112">Эти выходные данные соответствуют имени каталога для платформа .NET Framework версии, как отображается в разделе К:\виндовс\микрософт.нет\фрамеворк.</span><span class="sxs-lookup"><span data-stu-id="147f0-112">This output matches the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="147f0-113">Примеры значений: "v 1.0.3705", "v 1.1.4322", "v 2.0.50727" и "v 4.0. *X*", где *X* зависит от установленного номера сборки.</span><span class="sxs-lookup"><span data-stu-id="147f0-113">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="147f0-114">Обратите внимание, что требуется префикс "v".</span><span class="sxs-lookup"><span data-stu-id="147f0-114">Note that the "v" prefix is required.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="147f0-115">[вход, выход] Размер `pwzbuffer` во избежание переполнения буфера.</span><span class="sxs-lookup"><span data-stu-id="147f0-115">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="147f0-116">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="147f0-116">Return Value</span></span>  

 <span data-ttu-id="147f0-117">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="147f0-117">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="147f0-118">HRESULT</span><span class="sxs-lookup"><span data-stu-id="147f0-118">HRESULT</span></span>|<span data-ttu-id="147f0-119">Описание:</span><span class="sxs-lookup"><span data-stu-id="147f0-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="147f0-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="147f0-120">S_OK</span></span>|<span data-ttu-id="147f0-121">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="147f0-121">The method completed successfully.</span></span>|  
|<span data-ttu-id="147f0-122">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="147f0-122">E_POINTER</span></span>|<span data-ttu-id="147f0-123">`pwzbuffer` или `pcchBuffer` равно null.</span><span class="sxs-lookup"><span data-stu-id="147f0-123">`pwzbuffer` or `pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="147f0-124">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="147f0-124">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="147f0-125">Буфер слишком мал.</span><span class="sxs-lookup"><span data-stu-id="147f0-125">The buffer is too small.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="147f0-126">Требования</span><span class="sxs-lookup"><span data-stu-id="147f0-126">Requirements</span></span>  

 <span data-ttu-id="147f0-127">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="147f0-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="147f0-128">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="147f0-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="147f0-129">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="147f0-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="147f0-130">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="147f0-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="147f0-131">См. также</span><span class="sxs-lookup"><span data-stu-id="147f0-131">See also</span></span>

- [<span data-ttu-id="147f0-132">Интерфейс ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="147f0-132">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="147f0-133">Размещение</span><span class="sxs-lookup"><span data-stu-id="147f0-133">Hosting</span></span>](index.md)
