---
description: Дополнительные сведения о функции Клркреатеинстанце
title: Функция CLRCreateInstance
ms.date: 03/30/2017
api_name:
- CLRCreateInstance
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- CLRCreateInstance
helpviewer_keywords:
- CLRCreateInstance function [.NET Framework hosting]
ms.assetid: 5de13327-96c6-4697-a89e-b8bf40717855
topic_type:
- apiref
ms.openlocfilehash: 5d25ca8ea33aacf88a3359335b2b4bbfb91c06eb
ms.sourcegitcommit: 80f38cb67bd02f51d5722fa13d0ea207e3b14a8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/26/2021
ms.locfileid: "105610880"
---
# <a name="clrcreateinstance-function"></a><span data-ttu-id="da282-103">Функция CLRCreateInstance</span><span class="sxs-lookup"><span data-stu-id="da282-103">CLRCreateInstance Function</span></span>

<span data-ttu-id="da282-104">Предоставляет один из трех интерфейсов: [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md)или [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="da282-104">Provides one of three interfaces: [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md), or [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da282-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="da282-105">Syntax</span></span>  
  
```cpp  
HRESULT CLRCreateInstance(  
    [in]  REFCLSID  clsid,  
    [in]  REFIID     riid,  
    [out] LPVOID  * ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da282-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="da282-106">Parameters</span></span>  

 `clsid`  
 <span data-ttu-id="da282-107">окне Один из трех идентификаторов класса: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy или CLSID_CLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="da282-107">[in] One of three class identifiers: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy, or CLSID_CLRDebugging.</span></span>  
  
 `riid`  
 <span data-ttu-id="da282-108">окне Один из трех идентификаторов интерфейса (идентификаторов IID): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy или IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="da282-108">[in] One of three interface identifiers (IIDs): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy, or IID_ICLRDebugging.</span></span>  
  
 `ppInterface`  
 <span data-ttu-id="da282-109">заполняет Один из трех интерфейсов: [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md)или [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="da282-109">[out] One of three interfaces: [ICLRMetaHost](iclrmetahost-interface.md), [ICLRMetaHostPolicy](iclrmetahostpolicy-interface.md), or [ICLRDebugging](../debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da282-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="da282-110">Return Value</span></span>  

 <span data-ttu-id="da282-111">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="da282-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="da282-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="da282-112">HRESULT</span></span>|<span data-ttu-id="da282-113">Описание:</span><span class="sxs-lookup"><span data-stu-id="da282-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="da282-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="da282-114">S_OK</span></span>|<span data-ttu-id="da282-115">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="da282-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="da282-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="da282-116">E_POINTER</span></span>|<span data-ttu-id="da282-117">Параметр `ppInterface` имеет значение null.</span><span class="sxs-lookup"><span data-stu-id="da282-117">`ppInterface` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da282-118">Комментарии</span><span class="sxs-lookup"><span data-stu-id="da282-118">Remarks</span></span>  

 <span data-ttu-id="da282-119">В следующей таблице приведены поддерживаемые сочетания для `clsid` и `riid` .</span><span class="sxs-lookup"><span data-stu-id="da282-119">The following table shows the supported combinations for `clsid` and `riid`.</span></span>  
  
|`clsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="da282-120">CLSID_CLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="da282-120">CLSID_CLRMetaHost</span></span>|<span data-ttu-id="da282-121">IID_ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="da282-121">IID_ICLRMetaHost</span></span>|  
|<span data-ttu-id="da282-122">CLSID_CLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="da282-122">CLSID_CLRMetaHostPolicy</span></span>|<span data-ttu-id="da282-123">IID_ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="da282-123">IID_ICLRMetaHostPolicy</span></span>|  
|<span data-ttu-id="da282-124">CLSID_CLRDebugging</span><span class="sxs-lookup"><span data-stu-id="da282-124">CLSID_CLRDebugging</span></span>|<span data-ttu-id="da282-125">IID_ICLRDebugging</span><span class="sxs-lookup"><span data-stu-id="da282-125">IID_ICLRDebugging</span></span>|  
  
 <span data-ttu-id="da282-126">В следующем коде показано, как использовать `CLRCreateInstance` для получения всех трех интерфейсов:</span><span class="sxs-lookup"><span data-stu-id="da282-126">The following code shows how to use `CLRCreateInstance` to get all three interfaces:</span></span>  
  
```cpp  
#include <metahost.h>  
#pragma comment(lib, "mscoree.lib")  
  
ICLRMetaHost       *pMetaHost       = NULL;  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
ICLRDebugging      *pCLRDebugging   = NULL;  
HRESULT hr;  
hr = CLRCreateInstance(CLSID_CLRMetaHost, IID_ICLRMetaHost,  
                    (LPVOID*)&pMetaHost);  
hr = CLRCreateInstance (CLSID_CLRMetaHostPolicy, IID_ICLRMetaHostPolicy,  
                    (LPVOID*)&pMetaHostPolicy);  
hr = CLRCreateInstance (CLSID_CLRDebugging, IID_ICLRDebugging,  
                    (LPVOID*)&pCLRDebugging);  
```  

<span data-ttu-id="da282-127">`CreateInterface`Функция имеет псевдоним для `CLRCreateInstance` .</span><span class="sxs-lookup"><span data-stu-id="da282-127">The `CreateInterface` function is aliased to `CLRCreateInstance`.</span></span>  <span data-ttu-id="da282-128">`CLRCreateInstance`Функции и `CreateInterface` могут быть взаимозаменяемы.</span><span class="sxs-lookup"><span data-stu-id="da282-128">Both `CLRCreateInstance` and `CreateInterface` functions can be used interchangeably.</span></span> <span data-ttu-id="da282-129">Пример:</span><span class="sxs-lookup"><span data-stu-id="da282-129">For example:</span></span>

```cpp
HMODULE hModule = LoadLibrary(L"mscoree.dll");
CreateInterfaceFnPtr createInterface = (CreateInterfaceFnPtr)GetProcAddress(hModule, "CreateInterface");
HRESULT hr;
hr = createInterface(CLSID_CLRMetaHost, IID_ICLRMetaHost, (LPVOID*)&pMetaHost);
hr = createInterface (CLSID_CLRMetaHostPolicy, IID_ICLRMetaHostPolicy,  (LPVOID*)&pMetaHostPolicy);  
hr = createInterface (CLSID_CLRDebugging, IID_ICLRDebugging,  (LPVOID*)&pCLRDebugging); 
```
  
## <a name="requirements"></a><span data-ttu-id="da282-130">Требования</span><span class="sxs-lookup"><span data-stu-id="da282-130">Requirements</span></span>  

 <span data-ttu-id="da282-131">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da282-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da282-132">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="da282-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="da282-133">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="da282-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="da282-134">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da282-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da282-135">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="da282-135">See also</span></span>

- [<span data-ttu-id="da282-136">Размещение</span><span class="sxs-lookup"><span data-stu-id="da282-136">Hosting</span></span>](index.md)
