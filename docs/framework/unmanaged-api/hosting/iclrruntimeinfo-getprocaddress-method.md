---
description: 'Дополнительные сведения о методе ICLRRuntimeInfo:: GetProcAddress'
title: Метод ICLRRuntimeInfo::GetProcAddress
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetProcAddress
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetProcAddress
helpviewer_keywords:
- GetProcAddress method [.NET Framework hosting]
- ICLRRuntimeInfo::GetProcAddress method [.NET Framework hosting]
ms.assetid: a7732bfc-689a-4926-88fd-4f81e6f9ed78
topic_type:
- apiref
ms.openlocfilehash: 1e5d08ed118930418106b28541b4081d6acad927
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637148"
---
# <a name="iclrruntimeinfogetprocaddress-method"></a><span data-ttu-id="f61e2-103">Метод ICLRRuntimeInfo::GetProcAddress</span><span class="sxs-lookup"><span data-stu-id="f61e2-103">ICLRRuntimeInfo::GetProcAddress Method</span></span>

<span data-ttu-id="f61e2-104">Возвращает адрес указанной функции, которая была экспортирована из среды CLR, связанной с этим интерфейсом.</span><span class="sxs-lookup"><span data-stu-id="f61e2-104">Gets the address of a specified function that was exported from the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="f61e2-105">Этот метод заменяет функцию [жетреалпрокаддресс](getrealprocaddress-function.md) .</span><span class="sxs-lookup"><span data-stu-id="f61e2-105">This method supersedes the [GetRealProcAddress](getrealprocaddress-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f61e2-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f61e2-106">Syntax</span></span>  
  
```cpp  
HRESULT GetProcAddress(  
     [in]  LPCSTR pszProcName,  
     [out, retval] LPVOID *ppProc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f61e2-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="f61e2-107">Parameters</span></span>  

 `pszProcName`  
 <span data-ttu-id="f61e2-108">окне Имя экспортированной функции.</span><span class="sxs-lookup"><span data-stu-id="f61e2-108">[in] The name of the exported function.</span></span>  
  
 `ppProc`  
 <span data-ttu-id="f61e2-109">заполняет Адрес экспортированной функции.</span><span class="sxs-lookup"><span data-stu-id="f61e2-109">[out] The address of the exported function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f61e2-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="f61e2-110">Return Value</span></span>  

 <span data-ttu-id="f61e2-111">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="f61e2-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f61e2-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f61e2-112">HRESULT</span></span>|<span data-ttu-id="f61e2-113">Описание:</span><span class="sxs-lookup"><span data-stu-id="f61e2-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f61e2-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="f61e2-114">S_OK</span></span>|<span data-ttu-id="f61e2-115">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="f61e2-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="f61e2-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="f61e2-116">E_POINTER</span></span>|<span data-ttu-id="f61e2-117">`pszProcName` или `ppProc` равно null.</span><span class="sxs-lookup"><span data-stu-id="f61e2-117">`pszProcName` or `ppProc` is null.</span></span>|  
|<span data-ttu-id="f61e2-118">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="f61e2-118">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="f61e2-119">Указанная функция не является экспортированной функцией.</span><span class="sxs-lookup"><span data-stu-id="f61e2-119">The specified function is not an exported function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f61e2-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="f61e2-120">Remarks</span></span>  

 <span data-ttu-id="f61e2-121">Этот метод приводит к тому, что среда CLR загружается, но не инициализируется.</span><span class="sxs-lookup"><span data-stu-id="f61e2-121">This method causes the CLR to be loaded but not initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f61e2-122">Требования</span><span class="sxs-lookup"><span data-stu-id="f61e2-122">Requirements</span></span>  

 <span data-ttu-id="f61e2-123">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f61e2-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f61e2-124">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="f61e2-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f61e2-125">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f61e2-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f61e2-126">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f61e2-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f61e2-127">См. также</span><span class="sxs-lookup"><span data-stu-id="f61e2-127">See also</span></span>

- [<span data-ttu-id="f61e2-128">Интерфейс ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="f61e2-128">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="f61e2-129">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="f61e2-129">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="f61e2-130">Размещение</span><span class="sxs-lookup"><span data-stu-id="f61e2-130">Hosting</span></span>](index.md)
