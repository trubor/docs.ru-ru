---
description: 'Дополнительные сведения: метод ICLRRuntimeInfo:: LoadLibrary'
title: Метод ICLRRuntimeInfo::LoadLibrary
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.LoadLibrary
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::LoadLibrary
helpviewer_keywords:
- ICLRRuntimeInfo::LoadLibrary method [.NET Framework hosting]
- LoadLibrary method [.NET Framework hosting]
ms.assetid: 4517ada3-4417-4ac5-a150-73da7a87c686
topic_type:
- apiref
ms.openlocfilehash: 47557934868c7c1b68b23bf4eded0e90705d7252
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785059"
---
# <a name="iclrruntimeinfoloadlibrary-method"></a><span data-ttu-id="44650-103">Метод ICLRRuntimeInfo::LoadLibrary</span><span class="sxs-lookup"><span data-stu-id="44650-103">ICLRRuntimeInfo::LoadLibrary Method</span></span>

<span data-ttu-id="44650-104">Загружает библиотеку платформа .NET Framework из среды CLR, представленной интерфейсом [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="44650-104">Loads a .NET Framework library from the common language runtime (CLR) represented by an [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="44650-105">Этот метод заменяет функцию [лоадлибраришим](loadlibraryshim-function.md) .</span><span class="sxs-lookup"><span data-stu-id="44650-105">This method supersedes the [LoadLibraryShim](loadlibraryshim-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44650-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="44650-106">Syntax</span></span>  
  
```cpp  
HRESULT LoadLibrary(  
     [in]  LPCWSTR pwzDllName,  
     [out, retval] HMODULE *phndModule);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44650-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="44650-107">Parameters</span></span>  

 `pwzDllName`  
 <span data-ttu-id="44650-108">окне Имя загружаемой сборки.</span><span class="sxs-lookup"><span data-stu-id="44650-108">[in] The name of the assembly to be loaded.</span></span>  
  
 `phndModule`  
 <span data-ttu-id="44650-109">заполняет Маркер загруженной сборки.</span><span class="sxs-lookup"><span data-stu-id="44650-109">[out] A handle to the loaded assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44650-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="44650-110">Return Value</span></span>  

 <span data-ttu-id="44650-111">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="44650-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="44650-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="44650-112">HRESULT</span></span>|<span data-ttu-id="44650-113">Описание:</span><span class="sxs-lookup"><span data-stu-id="44650-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="44650-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="44650-114">S_OK</span></span>|<span data-ttu-id="44650-115">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="44650-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="44650-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="44650-116">E_POINTER</span></span>|<span data-ttu-id="44650-117">`pwzDllName` или `phndModule` равно null.</span><span class="sxs-lookup"><span data-stu-id="44650-117">`pwzDllName` or `phndModule` is null.</span></span>|  
|<span data-ttu-id="44650-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="44650-118">E_OUTOFMEMORY</span></span>|<span data-ttu-id="44650-119">Недостаточно памяти для выполнения запроса.</span><span class="sxs-lookup"><span data-stu-id="44650-119">Not enough memory is available to handle the request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44650-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="44650-120">Remarks</span></span>  

 <span data-ttu-id="44650-121">Этот метод загружает только библиотеки DLL, входящие в распространяемый пакет платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="44650-121">This method only loads DLLs included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="44650-122">Он не может загружать сборки, созданные пользователем.</span><span class="sxs-lookup"><span data-stu-id="44650-122">It can not load user-generated assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44650-123">Требования</span><span class="sxs-lookup"><span data-stu-id="44650-123">Requirements</span></span>  

 <span data-ttu-id="44650-124">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44650-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44650-125">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="44650-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="44650-126">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="44650-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="44650-127">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44650-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44650-128">См. также</span><span class="sxs-lookup"><span data-stu-id="44650-128">See also</span></span>

- [<span data-ttu-id="44650-129">Интерфейс ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="44650-129">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="44650-130">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="44650-130">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="44650-131">Размещение</span><span class="sxs-lookup"><span data-stu-id="44650-131">Hosting</span></span>](index.md)
