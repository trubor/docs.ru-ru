---
description: 'Дополнительные сведения о методе: IHostSecurityManager:: Опенсреадтокен'
title: Метод IHostSecurityManager::OpenThreadToken
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.OpenThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::OpenThreadToken
helpviewer_keywords:
- IHostSecurityManager::OpenThreadToken method [.NET Framework hosting]
- OpenThreadToken method [.NET Framework hosting]
ms.assetid: d5999052-8bf0-4a9e-8621-da6284406b18
topic_type:
- apiref
ms.openlocfilehash: 9e0273f379f4adcf71396630b367a94c623ae15f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671570"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a><span data-ttu-id="1221c-103">Метод IHostSecurityManager::OpenThreadToken</span><span class="sxs-lookup"><span data-stu-id="1221c-103">IHostSecurityManager::OpenThreadToken Method</span></span>

<span data-ttu-id="1221c-104">Открывает маркер доступа на уровне пользователей, связанный с выполняющимся в данный момент потоком.</span><span class="sxs-lookup"><span data-stu-id="1221c-104">Opens the discretionary access token associated with the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1221c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1221c-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,
    [in]  BOOL     bOpenAsSelf,
    [out] HANDLE   *phThreadToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1221c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1221c-106">Parameters</span></span>  

 `dwDesiredAccess`  
 <span data-ttu-id="1221c-107">окне Маска значений доступа, указывающих запрошенные типы доступа к токену потока.</span><span class="sxs-lookup"><span data-stu-id="1221c-107">[in] A mask of access values that specify the requested types of access to the thread token.</span></span> <span data-ttu-id="1221c-108">Эти значения определены в `OpenThreadToken` функции Win32.</span><span class="sxs-lookup"><span data-stu-id="1221c-108">These values are defined in the Win32 `OpenThreadToken` function.</span></span> <span data-ttu-id="1221c-109">Запрошенные типы доступа согласовываются с избирательным списком управления доступом (DACL) маркера, чтобы определить, какие типы доступа следует предоставить или запретить.</span><span class="sxs-lookup"><span data-stu-id="1221c-109">The requested access types are reconciled against the token's discretionary access control list (DACL) to determine which types of access to grant or deny.</span></span>  
  
 `bOpenAsSelf`  
 <span data-ttu-id="1221c-110">[входные] `true` значение, чтобы указать, что проверка доступа должна выполняться с помощью контекста безопасности процесса для вызывающего потока; `false` значение, чтобы указать, что проверка доступа должна выполняться с использованием контекста безопасности для самого вызывающего потока.</span><span class="sxs-lookup"><span data-stu-id="1221c-110">[in] `true` to specify that the access check should be made using the security context of the process for the calling thread; `false` to specify that the access check should be performed using the security context for the calling thread itself.</span></span> <span data-ttu-id="1221c-111">Если поток олицетворяет клиента, контекст безопасности может быть таким же, как у клиентского процесса.</span><span class="sxs-lookup"><span data-stu-id="1221c-111">If the thread is impersonating a client, the security context can be that of a client process.</span></span>  
  
 `phThreadToken`  
 <span data-ttu-id="1221c-112">заполняет Указатель на вновь открытый маркер доступа.</span><span class="sxs-lookup"><span data-stu-id="1221c-112">[out] A pointer to the newly opened access token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1221c-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="1221c-113">Return Value</span></span>  
  
|<span data-ttu-id="1221c-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1221c-114">HRESULT</span></span>|<span data-ttu-id="1221c-115">Описание:</span><span class="sxs-lookup"><span data-stu-id="1221c-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1221c-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="1221c-116">S_OK</span></span>|<span data-ttu-id="1221c-117">`OpenThreadToken` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="1221c-117">`OpenThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="1221c-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1221c-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1221c-119">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="1221c-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1221c-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1221c-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1221c-121">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="1221c-121">The call timed out.</span></span>|  
|<span data-ttu-id="1221c-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1221c-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1221c-123">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="1221c-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1221c-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1221c-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1221c-125">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="1221c-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1221c-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1221c-126">E_FAIL</span></span>|<span data-ttu-id="1221c-127">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="1221c-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1221c-128">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="1221c-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1221c-129">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1221c-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1221c-130">Remarks</span><span class="sxs-lookup"><span data-stu-id="1221c-130">Remarks</span></span>  

 <span data-ttu-id="1221c-131">`IHostSecurityManager::OpenThreadToken` ведет себя аналогично соответствующей функции Win32 с тем же именем, за исключением того, что функция Win32 позволяет вызывающему объекту передать маркер произвольному потоку, а `IHostSecurityManager::OpenThreadToken` открывает только маркер, связанный с вызывающим потоком.</span><span class="sxs-lookup"><span data-stu-id="1221c-131">`IHostSecurityManager::OpenThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::OpenThreadToken` opens only the token associated with the calling thread.</span></span>  
  
 <span data-ttu-id="1221c-132">`HANDLE`Тип не совместим с COM, то есть его размер зависит от операционной системы и требует настраиваемого маршалирования.</span><span class="sxs-lookup"><span data-stu-id="1221c-132">The `HANDLE` type is not COM-compliant, that is, its size is specific to the operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="1221c-133">Таким же маркер предназначен только для использования внутри процесса между средой CLR и узлом.</span><span class="sxs-lookup"><span data-stu-id="1221c-133">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1221c-134">Требования</span><span class="sxs-lookup"><span data-stu-id="1221c-134">Requirements</span></span>  

 <span data-ttu-id="1221c-135">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1221c-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1221c-136">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1221c-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1221c-137">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1221c-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1221c-138">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1221c-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1221c-139">См. также</span><span class="sxs-lookup"><span data-stu-id="1221c-139">See also</span></span>

- [<span data-ttu-id="1221c-140">Интерфейс IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="1221c-140">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="1221c-141">Интерфейс IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="1221c-141">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
