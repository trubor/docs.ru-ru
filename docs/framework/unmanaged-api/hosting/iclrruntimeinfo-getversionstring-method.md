---
description: 'Дополнительные сведения: метод ICLRRuntimeInfo:: GetVersionString'
title: Метод ICLRRuntimeInfo::GetVersionString
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetVersionString
helpviewer_keywords:
- ICLRRuntimeInfo::GetVersionString method [.NET Framework hosting]
- GetVersionString method, ICLRRuntimeInfo interface [.NET Framework hosting]
ms.assetid: 98b097ef-2276-4dd9-8551-b03c972e8179
topic_type:
- apiref
ms.openlocfilehash: 1c7603f4e9bb1142c415ba9da7a05a52d2d5e776
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753878"
---
# <a name="iclrruntimeinfogetversionstring-method"></a><span data-ttu-id="0c34f-103">Метод ICLRRuntimeInfo::GetVersionString</span><span class="sxs-lookup"><span data-stu-id="0c34f-103">ICLRRuntimeInfo::GetVersionString Method</span></span>

<span data-ttu-id="0c34f-104">Возвращает сведения о версии среды CLR, связанные с заданным интерфейсом [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="0c34f-104">Gets common language runtime (CLR) version information associated with a given [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="0c34f-105">Этот метод заменяет следующие функции:</span><span class="sxs-lookup"><span data-stu-id="0c34f-105">This method supersedes the following functions:</span></span>  
  
- [<span data-ttu-id="0c34f-106">GetRequestedRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="0c34f-106">GetRequestedRuntimeInfo</span></span>](getrequestedruntimeinfo-function.md)  
  
- [<span data-ttu-id="0c34f-107">жетрекуестедрунтимеверсион</span><span class="sxs-lookup"><span data-stu-id="0c34f-107">GetRequestedRuntimeVersion</span></span>](getrequestedruntimeversion-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="0c34f-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0c34f-108">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionString(  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c34f-109">Параметры</span><span class="sxs-lookup"><span data-stu-id="0c34f-109">Parameters</span></span>  

 `pwzBuffer`  
 <span data-ttu-id="0c34f-110">заполняет Версия компиляции платформа .NET Framework в формате "v *A*. *B*[.*X*] ".</span><span class="sxs-lookup"><span data-stu-id="0c34f-110">[out] The .NET Framework compilation version in the format "v *A*.*B*[.*X*]".</span></span> <span data-ttu-id="0c34f-111">*A*, *B* и *X* — это десятичные числа, соответствующие основной версии, дополнительной версии и номеру сборки.</span><span class="sxs-lookup"><span data-stu-id="0c34f-111">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="0c34f-112">*X* является необязательным.</span><span class="sxs-lookup"><span data-stu-id="0c34f-112">*X* is optional.</span></span> <span data-ttu-id="0c34f-113">Если значение *X* отсутствует, конечная точка отсутствует.</span><span class="sxs-lookup"><span data-stu-id="0c34f-113">If *X* is not present, there is no trailing period.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0c34f-114">Этот параметр должен соответствовать имени каталога для платформа .NET Framework версии, как показано в разделе К:\виндовс\микрософт.нет\фрамеворк.</span><span class="sxs-lookup"><span data-stu-id="0c34f-114">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="0c34f-115">Примеры значений: "v 1.0.3705", "v 1.1.4322", "v 2.0.50727" и "v 4.0. *x*", где *x* зависит от установленного номера сборки.</span><span class="sxs-lookup"><span data-stu-id="0c34f-115">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*x*", where *x* depends on the build number installed.</span></span> <span data-ttu-id="0c34f-116">Обратите внимание, что префикс "v" является обязательным.</span><span class="sxs-lookup"><span data-stu-id="0c34f-116">Note that the "v" prefix is mandatory.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="0c34f-117">[вход, выход] Указывает размер `pwzBuffer` во избежание переполнения буфера.</span><span class="sxs-lookup"><span data-stu-id="0c34f-117">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="0c34f-118">Если `pwzBuffer` имеет значение `null` , функция `pchBuffer` возвращает требуемый размер, `pwzBuffer` чтобы разрешить предварительное выделение.</span><span class="sxs-lookup"><span data-stu-id="0c34f-118">If `pwzBuffer` is `null`, `pchBuffer` returns the required size of `pwzBuffer` to allow preallocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0c34f-119">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="0c34f-119">Return Value</span></span>  

 <span data-ttu-id="0c34f-120">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="0c34f-120">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0c34f-121">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0c34f-121">HRESULT</span></span>|<span data-ttu-id="0c34f-122">Описание:</span><span class="sxs-lookup"><span data-stu-id="0c34f-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0c34f-123">S_OK</span><span class="sxs-lookup"><span data-stu-id="0c34f-123">S_OK</span></span>|<span data-ttu-id="0c34f-124">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="0c34f-124">The method completed successfully.</span></span>|  
|<span data-ttu-id="0c34f-125">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="0c34f-125">E_POINTER</span></span>|<span data-ttu-id="0c34f-126">`pwzBuffer` или `pchBuffer` равно null.</span><span class="sxs-lookup"><span data-stu-id="0c34f-126">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0c34f-127">Требования</span><span class="sxs-lookup"><span data-stu-id="0c34f-127">Requirements</span></span>  

 <span data-ttu-id="0c34f-128">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c34f-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c34f-129">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="0c34f-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0c34f-130">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0c34f-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0c34f-131">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c34f-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c34f-132">См. также</span><span class="sxs-lookup"><span data-stu-id="0c34f-132">See also</span></span>

- [<span data-ttu-id="0c34f-133">Интерфейс ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="0c34f-133">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="0c34f-134">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="0c34f-134">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="0c34f-135">Интерфейсы размещения CLR, добавленные в версиях .NET Framework 4 и 4.5</span><span class="sxs-lookup"><span data-stu-id="0c34f-135">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="0c34f-136">Размещение</span><span class="sxs-lookup"><span data-stu-id="0c34f-136">Hosting</span></span>](index.md)
