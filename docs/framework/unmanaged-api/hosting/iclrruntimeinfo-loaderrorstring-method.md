---
description: 'Дополнительные сведения: метод ICLRRuntimeInfo:: Лоадеррорстринг'
title: Метод ICLRRuntimeInfo::LoadErrorString
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.LoadErrorString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::LoadErrorString
helpviewer_keywords:
- ICLRRuntimeInfo::LoadErrorString method [.NET Framework hosting]
- LoadErrorString method [.NET Framework hosting]
ms.assetid: 52c543ab-9ef5-4ee7-b836-c0ffc35cd45b
topic_type:
- apiref
ms.openlocfilehash: 0523b5b89072db50c83c52065c22e9df7167a027
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785072"
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="cff31-103">Метод ICLRRuntimeInfo::LoadErrorString</span><span class="sxs-lookup"><span data-stu-id="cff31-103">ICLRRuntimeInfo::LoadErrorString Method</span></span>

<span data-ttu-id="cff31-104">Преобразует значение HRESULT в соответствующее сообщение об ошибке для указанного языка и региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="cff31-104">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="cff31-105">Этот метод заменяет следующие функции:</span><span class="sxs-lookup"><span data-stu-id="cff31-105">This method supersedes the following functions:</span></span>  
  
- [<span data-ttu-id="cff31-106">лоадстрингрк</span><span class="sxs-lookup"><span data-stu-id="cff31-106">LoadStringRC</span></span>](loadstringrc-function.md)  
  
- [<span data-ttu-id="cff31-107">лоадстрингрцекс</span><span class="sxs-lookup"><span data-stu-id="cff31-107">LoadStringRCEx</span></span>](loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="cff31-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cff31-108">Syntax</span></span>  
  
```cpp  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cff31-109">Параметры</span><span class="sxs-lookup"><span data-stu-id="cff31-109">Parameters</span></span>  

 `iResourceID`  
 <span data-ttu-id="cff31-110">окне Значение HRESULT для преобразования.</span><span class="sxs-lookup"><span data-stu-id="cff31-110">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="cff31-111">заполняет Строка сообщения, связанная с данным значением HRESULT.</span><span class="sxs-lookup"><span data-stu-id="cff31-111">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="cff31-112">[вход, выход] Размер `pwzbuffer` во избежание переполнения буфера.</span><span class="sxs-lookup"><span data-stu-id="cff31-112">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="cff31-113">Если `pwzbuffer` параметр имеет значение null, `pcchBuffer` то предоставляет ожидаемый размер `pwzbuffer` для разрешения предварительного выделения.</span><span class="sxs-lookup"><span data-stu-id="cff31-113">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="cff31-114">окне Идентификатор языка и региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="cff31-114">[in] The culture identifier.</span></span> <span data-ttu-id="cff31-115">Чтобы использовать язык и региональные параметры по умолчанию, необходимо указать значение-1.</span><span class="sxs-lookup"><span data-stu-id="cff31-115">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cff31-116">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="cff31-116">Return Value</span></span>  

 <span data-ttu-id="cff31-117">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="cff31-117">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="cff31-118">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cff31-118">HRESULT</span></span>|<span data-ttu-id="cff31-119">Описание:</span><span class="sxs-lookup"><span data-stu-id="cff31-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cff31-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="cff31-120">S_OK</span></span>|<span data-ttu-id="cff31-121">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="cff31-121">The method completed successfully.</span></span>|  
|<span data-ttu-id="cff31-122">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="cff31-122">E_POINTER</span></span>|<span data-ttu-id="cff31-123">Параметр `pcchBuffer` имеет значение null.</span><span class="sxs-lookup"><span data-stu-id="cff31-123">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="cff31-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="cff31-124">E_INVALIDARG</span></span>|<span data-ttu-id="cff31-125">Параметр `pwzBuffer` имеет значение null.</span><span class="sxs-lookup"><span data-stu-id="cff31-125">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cff31-126">Требования</span><span class="sxs-lookup"><span data-stu-id="cff31-126">Requirements</span></span>  

 <span data-ttu-id="cff31-127">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cff31-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cff31-128">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="cff31-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="cff31-129">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cff31-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cff31-130">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cff31-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cff31-131">См. также</span><span class="sxs-lookup"><span data-stu-id="cff31-131">See also</span></span>

- [<span data-ttu-id="cff31-132">Интерфейс ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="cff31-132">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="cff31-133">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="cff31-133">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="cff31-134">Размещение</span><span class="sxs-lookup"><span data-stu-id="cff31-134">Hosting</span></span>](index.md)
