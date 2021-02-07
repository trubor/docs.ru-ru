---
description: 'Дополнительные сведения о: интерфейс ICLRRuntimeHost'
title: Интерфейс ICLRRuntimeHost
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost
helpviewer_keywords:
- ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: cb0c5f65-3791-47bc-b833-2f84f4101ba5
topic_type:
- apiref
ms.openlocfilehash: 92bab42fa1cf2cca5caa0eb039c88fec3e65390c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753891"
---
# <a name="iclrruntimehost-interface"></a><span data-ttu-id="c9b05-103">Интерфейс ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="c9b05-103">ICLRRuntimeHost Interface</span></span>

<span data-ttu-id="c9b05-104">Предоставляет функциональные возможности, аналогичные интерфейсу [ICorRuntimeHost](icorruntimehost-interface.md) , предоставленному в платформа .NET Framework версии 1, со следующими изменениями:</span><span class="sxs-lookup"><span data-stu-id="c9b05-104">Provides functionality similar to that of the [ICorRuntimeHost](icorruntimehost-interface.md) interface provided in the .NET Framework version 1, with the following changes:</span></span>  
  
- <span data-ttu-id="c9b05-105">Добавление метода [SetHostControl](iclrruntimehost-sethostcontrol-method.md) для задания интерфейса элемента управления ведущего приложения.</span><span class="sxs-lookup"><span data-stu-id="c9b05-105">The addition of the [SetHostControl](iclrruntimehost-sethostcontrol-method.md) method to set the host control interface.</span></span>  
  
- <span data-ttu-id="c9b05-106">Пропуск некоторых методов, предоставляемых `ICorRuntimeHost` .</span><span class="sxs-lookup"><span data-stu-id="c9b05-106">The omission of some methods provided by `ICorRuntimeHost`.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c9b05-107">Методы</span><span class="sxs-lookup"><span data-stu-id="c9b05-107">Methods</span></span>  
  
|<span data-ttu-id="c9b05-108">Метод</span><span class="sxs-lookup"><span data-stu-id="c9b05-108">Method</span></span>|<span data-ttu-id="c9b05-109">Описание</span><span class="sxs-lookup"><span data-stu-id="c9b05-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c9b05-110">Метод ExecuteApplication</span><span class="sxs-lookup"><span data-stu-id="c9b05-110">ExecuteApplication Method</span></span>](iclrruntimehost-executeapplication-method.md)|<span data-ttu-id="c9b05-111">Используется в сценариях развертывания ClickOnce на основе манифеста для указания приложения, которое должно быть активировано в новом домене.</span><span class="sxs-lookup"><span data-stu-id="c9b05-111">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span>|  
|[<span data-ttu-id="c9b05-112">Метод ExecuteInAppDomain</span><span class="sxs-lookup"><span data-stu-id="c9b05-112">ExecuteInAppDomain Method</span></span>](iclrruntimehost-executeinappdomain-method.md)|<span data-ttu-id="c9b05-113">Указывает, <xref:System.AppDomain> в котором следует выполнить указанный управляемый код.</span><span class="sxs-lookup"><span data-stu-id="c9b05-113">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>|  
|[<span data-ttu-id="c9b05-114">Метод ExecuteInDefaultAppDomain</span><span class="sxs-lookup"><span data-stu-id="c9b05-114">ExecuteInDefaultAppDomain Method</span></span>](iclrruntimehost-executeindefaultappdomain-method.md)|<span data-ttu-id="c9b05-115">Вызывает указанный метод указанного типа в указанной сборке.</span><span class="sxs-lookup"><span data-stu-id="c9b05-115">Invokes the specified method of the specified type in the specified assembly.</span></span>|  
|[<span data-ttu-id="c9b05-116">Метод GetCLRControl</span><span class="sxs-lookup"><span data-stu-id="c9b05-116">GetCLRControl Method</span></span>](iclrruntimehost-getclrcontrol-method.md)|<span data-ttu-id="c9b05-117">Возвращает указатель интерфейса типа [ICLRControl](iclrcontrol-interface.md) , который может использоваться узлами для настройки аспектов среды CLR.</span><span class="sxs-lookup"><span data-stu-id="c9b05-117">Gets an interface pointer of type [ICLRControl](iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="c9b05-118">Метод GetCurrentAppDomainId</span><span class="sxs-lookup"><span data-stu-id="c9b05-118">GetCurrentAppDomainId Method</span></span>](iclrruntimehost-getcurrentappdomainid-method.md)|<span data-ttu-id="c9b05-119">Возвращает числовой идентификатор объекта <xref:System.AppDomain> , который выполняется в данный момент.</span><span class="sxs-lookup"><span data-stu-id="c9b05-119">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>|  
|[<span data-ttu-id="c9b05-120">Метод SetHostControl</span><span class="sxs-lookup"><span data-stu-id="c9b05-120">SetHostControl Method</span></span>](iclrruntimehost-sethostcontrol-method.md)|<span data-ttu-id="c9b05-121">Задает интерфейс элемента управления ведущего приложения.</span><span class="sxs-lookup"><span data-stu-id="c9b05-121">Sets the host control interface.</span></span> <span data-ttu-id="c9b05-122">`SetHostControl`Перед вызовом необходимо вызвать `Start` .</span><span class="sxs-lookup"><span data-stu-id="c9b05-122">You must call `SetHostControl` before calling `Start`.</span></span>|  
|[<span data-ttu-id="c9b05-123">Метод Start</span><span class="sxs-lookup"><span data-stu-id="c9b05-123">Start Method</span></span>](iclrruntimehost-start-method.md)|<span data-ttu-id="c9b05-124">Инициализирует среду CLR в процессе.</span><span class="sxs-lookup"><span data-stu-id="c9b05-124">Initializes the CLR into a process.</span></span>|  
|[<span data-ttu-id="c9b05-125">Метод завершения</span><span class="sxs-lookup"><span data-stu-id="c9b05-125">Stop Method</span></span>](iclrruntimehost-stop-method.md)|<span data-ttu-id="c9b05-126">Останавливает выполнение кода средой выполнения.</span><span class="sxs-lookup"><span data-stu-id="c9b05-126">Stops the execution of code by the runtime.</span></span>|  
|[<span data-ttu-id="c9b05-127">Метод UnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="c9b05-127">UnloadAppDomain Method</span></span>](iclrruntimehost-unloadappdomain-method.md)|<span data-ttu-id="c9b05-128">Выгружает объект <xref:System.AppDomain> , соответствующий указанному числовому идентификатору.</span><span class="sxs-lookup"><span data-stu-id="c9b05-128">Unloads the <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9b05-129">Remarks</span><span class="sxs-lookup"><span data-stu-id="c9b05-129">Remarks</span></span>  

 <span data-ttu-id="c9b05-130">Начиная с платформа .NET Framework 4, используйте интерфейс [ICLRMetaHost](iclrmetahost-interface.md) для получения указателя на интерфейс [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , а затем вызовите метод [ICLRRuntimeInfo::-interface](iclrruntimeinfo-getinterface-method.md) , чтобы получить указатель на `ICLRRuntimeHost` .</span><span class="sxs-lookup"><span data-stu-id="c9b05-130">Starting with the .NET Framework 4, use the [ICLRMetaHost](iclrmetahost-interface.md) interface to get a pointer to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface, and then call the [ICLRRuntimeInfo::GetInterface](iclrruntimeinfo-getinterface-method.md) method to get a pointer to `ICLRRuntimeHost`.</span></span> <span data-ttu-id="c9b05-131">В более ранних версиях платформа .NET Framework узел получает указатель на `ICLRRuntimeHost` экземпляр, вызывая [CorBindToRuntimeEx](corbindtoruntimeex-function.md) или [корбиндтокуррентрунтиме](corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="c9b05-131">In earlier versions of the .NET Framework, the host gets a pointer to an `ICLRRuntimeHost` instance by calling [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span> <span data-ttu-id="c9b05-132">Чтобы реализовать реализации любой из технологий, предоставляемых в платформа .NET Framework версии 2,0, необходимо использовать `ICLRRuntimeHost` вместо `ICorRuntimeHost` .</span><span class="sxs-lookup"><span data-stu-id="c9b05-132">To provide implementations of any of the technologies provided in the .NET Framework version 2.0, you must use `ICLRRuntimeHost` instead of `ICorRuntimeHost`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c9b05-133">Не вызывайте метод [Start](iclrruntimehost-start-method.md) перед вызовом метода [ExecuteApplication](iclrruntimehost-executeapplication-method.md) для активации приложения на основе манифеста.</span><span class="sxs-lookup"><span data-stu-id="c9b05-133">Do not call the [Start](iclrruntimehost-start-method.md) method before calling the [ExecuteApplication](iclrruntimehost-executeapplication-method.md) method to activate a manifest-based application.</span></span> <span data-ttu-id="c9b05-134">Если `Start` метод вызывается первым, `ExecuteApplication` вызов метода завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="c9b05-134">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9b05-135">Требования</span><span class="sxs-lookup"><span data-stu-id="c9b05-135">Requirements</span></span>  

 <span data-ttu-id="c9b05-136">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9b05-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9b05-137">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c9b05-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c9b05-138">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c9b05-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c9b05-139">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9b05-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9b05-140">См. также</span><span class="sxs-lookup"><span data-stu-id="c9b05-140">See also</span></span>

- [<span data-ttu-id="c9b05-141">Функция CorBindToCurrentRuntime</span><span class="sxs-lookup"><span data-stu-id="c9b05-141">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="c9b05-142">Функция CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="c9b05-142">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="c9b05-143">Интерфейс ICLRControl</span><span class="sxs-lookup"><span data-stu-id="c9b05-143">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="c9b05-144">Интерфейс ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="c9b05-144">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="c9b05-145">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="c9b05-145">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="c9b05-146">Кокласс CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="c9b05-146">CLRRuntimeHost Coclass</span></span>](clrruntimehost-coclass.md)
