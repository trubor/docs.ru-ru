---
description: 'Дополнительные сведения о методе: Иклрвалидатор:: Validate'
title: Метод ICLRValidator::Validate
ms.date: 03/30/2017
api_name:
- ICLRValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator::Validate
helpviewer_keywords:
- Validate method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::Validate method [.NET Framework hosting]
ms.assetid: 0b1b432a-d234-4002-839b-81366c3a8bdc
topic_type:
- apiref
ms.openlocfilehash: a188315d44021fc8bf40be9bb9aecac436351467
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636748"
---
# <a name="iclrvalidatorvalidate-method"></a><span data-ttu-id="d423b-103">Метод ICLRValidator::Validate</span><span class="sxs-lookup"><span data-stu-id="d423b-103">ICLRValidator::Validate Method</span></span>

<span data-ttu-id="d423b-104">Проверяет переносимый исполняемый (PE) или промежуточный язык Майкрософт (MSIL) в указанном файле.</span><span class="sxs-lookup"><span data-stu-id="d423b-104">Validates the portable executable (PE) or Microsoft intermediate language (MSIL) in the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d423b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d423b-105">Syntax</span></span>  
  
```cpp  
HRESULT Validate (  
    [in] IVEHandler        *veh,  
    [in] unsigned long      ulAppDomainId,  
    [in] unsigned long      ulFlags,  
    [in] unsigned long      ulMaxError,  
    [in] unsigned long      token,  
    [in] LPWSTR             fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long      ulSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="d423b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d423b-106">Parameters</span></span>  

 `veh`  
 <span data-ttu-id="d423b-107">окне Указатель на `IVEHandler` экземпляр, который обрабатывает ошибки проверки.</span><span class="sxs-lookup"><span data-stu-id="d423b-107">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `ulAppDomainId`  
 <span data-ttu-id="d423b-108">окне Идентификатор текущего <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="d423b-108">[in] The identifier for the current <xref:System.AppDomain>.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="d423b-109">окне Сочетание значений [валидаторфлагс](validatorflags-enumeration.md) , указывающих тип проверки, которую следует выполнить.</span><span class="sxs-lookup"><span data-stu-id="d423b-109">[in] A combination of [ValidatorFlags](validatorflags-enumeration.md) values, indicating the kind of validation that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="d423b-110">окне Максимальное число ошибок, которое необходимо разрешить перед выходом из проверки.</span><span class="sxs-lookup"><span data-stu-id="d423b-110">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="d423b-111">[in] Не используется.</span><span class="sxs-lookup"><span data-stu-id="d423b-111">[in] Unused.</span></span>  
  
 `fileName`  
 <span data-ttu-id="d423b-112">окне Имя проверяемого файла.</span><span class="sxs-lookup"><span data-stu-id="d423b-112">[in] The name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="d423b-113">окне Указатель на файловый буфер.</span><span class="sxs-lookup"><span data-stu-id="d423b-113">[in] A pointer to the file buffer.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="d423b-114">окне Размер проверяемого файла в байтах.</span><span class="sxs-lookup"><span data-stu-id="d423b-114">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d423b-115">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="d423b-115">Return Value</span></span>  
  
|<span data-ttu-id="d423b-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d423b-116">HRESULT</span></span>|<span data-ttu-id="d423b-117">Описание:</span><span class="sxs-lookup"><span data-stu-id="d423b-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d423b-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="d423b-118">S_OK</span></span>|<span data-ttu-id="d423b-119">`Validate` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="d423b-119">`Validate` returned successfully.</span></span>|  
|<span data-ttu-id="d423b-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d423b-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d423b-121">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="d423b-121">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d423b-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d423b-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d423b-123">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="d423b-123">The call timed out.</span></span>|  
|<span data-ttu-id="d423b-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d423b-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d423b-125">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="d423b-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d423b-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d423b-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d423b-127">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="d423b-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d423b-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d423b-128">E_FAIL</span></span>|<span data-ttu-id="d423b-129">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="d423b-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d423b-130">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="d423b-130">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d423b-131">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d423b-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d423b-132">Требования</span><span class="sxs-lookup"><span data-stu-id="d423b-132">Requirements</span></span>  

 <span data-ttu-id="d423b-133">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d423b-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d423b-134">**Заголовок:** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="d423b-134">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="d423b-135">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d423b-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d423b-136">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d423b-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d423b-137">См. также</span><span class="sxs-lookup"><span data-stu-id="d423b-137">See also</span></span>

- [<span data-ttu-id="d423b-138">Интерфейс ICLRValidator</span><span class="sxs-lookup"><span data-stu-id="d423b-138">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)
