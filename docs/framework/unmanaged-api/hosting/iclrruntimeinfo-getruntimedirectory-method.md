---
description: 'Дополнительные сведения: метод ICLRRuntimeInfo:: GetRuntimeDirectory'
title: Метод ICLRRuntimeInfo::GetRuntimeDirectory
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetRuntimeDirectory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetRuntimeDirectory
helpviewer_keywords:
- GetRuntimeDirectory method [.NET Framework hosting]
- ICLRRuntimeInfo::GetRuntimeDirectory method [.NET Framework hosting]
ms.assetid: 4401546e-4d48-453f-a1fb-b2ebda54df5c
topic_type:
- apiref
ms.openlocfilehash: 1e833887568d0a61e9ff9ec358b6979a4bacce41
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637096"
---
# <a name="iclrruntimeinfogetruntimedirectory-method"></a><span data-ttu-id="fcbc5-103">Метод ICLRRuntimeInfo::GetRuntimeDirectory</span><span class="sxs-lookup"><span data-stu-id="fcbc5-103">ICLRRuntimeInfo::GetRuntimeDirectory Method</span></span>

<span data-ttu-id="fcbc5-104">Возвращает каталог установки среды CLR, связанной с этим интерфейсом.</span><span class="sxs-lookup"><span data-stu-id="fcbc5-104">Gets the installation directory of the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="fcbc5-105">Этот метод заменяет функцию [GetCORSystemDirectory](getcorsystemdirectory-function.md) , указанную в платформа .NET Framework версиях 2,0, 3,0 и 3,5.</span><span class="sxs-lookup"><span data-stu-id="fcbc5-105">This method supersedes the [GetCORSystemDirectory](getcorsystemdirectory-function.md) function provided in the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcbc5-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fcbc5-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRuntimeDirectory(  
[out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
[in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fcbc5-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="fcbc5-107">Parameters</span></span>  

 `pwzBuffer`  
 <span data-ttu-id="fcbc5-108">заполняет Возвращает каталог установки среды CLR.</span><span class="sxs-lookup"><span data-stu-id="fcbc5-108">[out] Returns the CLR installation directory.</span></span> <span data-ttu-id="fcbc5-109">Путь установки является полным; Например, "c:\windows\microsoft.net\framework\v1.0.3705 \\ ".</span><span class="sxs-lookup"><span data-stu-id="fcbc5-109">The installation path is fully qualified; for example, "c:\windows\microsoft.net\framework\v1.0.3705\\".</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="fcbc5-110">[вход, выход] Указывает размер `pwzBuffer` во избежание переполнения буфера.</span><span class="sxs-lookup"><span data-stu-id="fcbc5-110">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="fcbc5-111">Если `pwzBuffer` параметр имеет значение null, `pchBuffer` возвращает требуемый размер `pwzBuffer` .</span><span class="sxs-lookup"><span data-stu-id="fcbc5-111">If `pwzBuffer` is null, `pchBuffer` returns the required size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fcbc5-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="fcbc5-112">Return Value</span></span>  

 <span data-ttu-id="fcbc5-113">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="fcbc5-113">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="fcbc5-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fcbc5-114">HRESULT</span></span>|<span data-ttu-id="fcbc5-115">Описание:</span><span class="sxs-lookup"><span data-stu-id="fcbc5-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fcbc5-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="fcbc5-116">S_OK</span></span>|<span data-ttu-id="fcbc5-117">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="fcbc5-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="fcbc5-118">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="fcbc5-118">E_POINTER</span></span>|<span data-ttu-id="fcbc5-119">`pwzBuffer` или `pchBuffer` равно null.</span><span class="sxs-lookup"><span data-stu-id="fcbc5-119">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fcbc5-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="fcbc5-120">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcbc5-121">Требования</span><span class="sxs-lookup"><span data-stu-id="fcbc5-121">Requirements</span></span>  

 <span data-ttu-id="fcbc5-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcbc5-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcbc5-123">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="fcbc5-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="fcbc5-124">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fcbc5-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fcbc5-125">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcbc5-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcbc5-126">См. также</span><span class="sxs-lookup"><span data-stu-id="fcbc5-126">See also</span></span>

- [<span data-ttu-id="fcbc5-127">Интерфейс ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="fcbc5-127">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="fcbc5-128">Размещение</span><span class="sxs-lookup"><span data-stu-id="fcbc5-128">Hosting</span></span>](index.md)
