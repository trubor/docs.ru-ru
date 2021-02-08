---
description: 'Дополнительные сведения о: интерфейс ICorRuntimeHost'
title: Интерфейс ICorRuntimeHost
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost
helpviewer_keywords:
- ICorRuntimeHost interface [.NET Framework hosting]
ms.assetid: 4369533d-7834-4497-bc37-bfea0ad737b1
topic_type:
- apiref
ms.openlocfilehash: cd50d31668b2dd0718dbe644343bfe314a0afdbe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789662"
---
# <a name="icorruntimehost-interface"></a><span data-ttu-id="65f1b-103">Интерфейс ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="65f1b-103">ICorRuntimeHost Interface</span></span>

<span data-ttu-id="65f1b-104">Предоставляет методы, позволяющие основному приложению запускать и прекращать работу среды CLR, создавать и настраивать домены приложений, получать доступ к домену по умолчанию и перечислять все домены, выполняющиеся в процессе.</span><span class="sxs-lookup"><span data-stu-id="65f1b-104">Provides methods that enable the host to start and stop the common language runtime (CLR) explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>  
  
 <span data-ttu-id="65f1b-105">В платформа .NET Framework версии 2,0 этот интерфейс заменен [ICLRRuntimeHost](iclrruntimehost-interface.md).</span><span class="sxs-lookup"><span data-stu-id="65f1b-105">In the .NET Framework version 2.0, this interface is superceded by [ICLRRuntimeHost](iclrruntimehost-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="65f1b-106">Методы</span><span class="sxs-lookup"><span data-stu-id="65f1b-106">Methods</span></span>  
  
|<span data-ttu-id="65f1b-107">Метод</span><span class="sxs-lookup"><span data-stu-id="65f1b-107">Method</span></span>|<span data-ttu-id="65f1b-108">Описание</span><span class="sxs-lookup"><span data-stu-id="65f1b-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="65f1b-109">Метод CloseEnum</span><span class="sxs-lookup"><span data-stu-id="65f1b-109">CloseEnum Method</span></span>](icorruntimehost-closeenum-method.md)|<span data-ttu-id="65f1b-110">Сбрасывает перечислитель домена обратно в начало списка доменов.</span><span class="sxs-lookup"><span data-stu-id="65f1b-110">Resets a domain enumerator back to the beginning of the domain list.</span></span>|  
|[<span data-ttu-id="65f1b-111">Метод CreateDomain</span><span class="sxs-lookup"><span data-stu-id="65f1b-111">CreateDomain Method</span></span>](icorruntimehost-createdomain-method.md)|<span data-ttu-id="65f1b-112">Создает домен приложения.</span><span class="sxs-lookup"><span data-stu-id="65f1b-112">Creates an application domain.</span></span> <span data-ttu-id="65f1b-113">Вызывающий объект получает указатель интерфейса типа <xref:System._AppDomain> на экземпляр типа <xref:System.AppDomain?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="65f1b-113">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>|  
|[<span data-ttu-id="65f1b-114">Метод CreateDomainEx</span><span class="sxs-lookup"><span data-stu-id="65f1b-114">CreateDomainEx Method</span></span>](icorruntimehost-createdomainex-method.md)|<span data-ttu-id="65f1b-115">Создает домен приложения.</span><span class="sxs-lookup"><span data-stu-id="65f1b-115">Creates an application domain.</span></span> <span data-ttu-id="65f1b-116">Этот метод позволяет вызывающему объекту передать экземпляр IAppDomainSetup для настройки дополнительных функций возвращаемого <xref:System._AppDomain> экземпляра.</span><span class="sxs-lookup"><span data-stu-id="65f1b-116">This method allows the caller to pass an IAppDomainSetup instance to configure additional features of the returned <xref:System._AppDomain> instance.</span></span>|  
|[<span data-ttu-id="65f1b-117">Метод CreateDomainSetup</span><span class="sxs-lookup"><span data-stu-id="65f1b-117">CreateDomainSetup Method</span></span>](icorruntimehost-createdomainsetup-method.md)|<span data-ttu-id="65f1b-118">Возвращает указатель интерфейса типа `IAppDomainSetup` на <xref:System.AppDomainSetup> экземпляр.</span><span class="sxs-lookup"><span data-stu-id="65f1b-118">Gets an interface pointer of type `IAppDomainSetup` to an <xref:System.AppDomainSetup> instance.</span></span> <span data-ttu-id="65f1b-119">`IAppDomainSetup` предоставляет методы для настройки аспектов домена приложения перед его созданием.</span><span class="sxs-lookup"><span data-stu-id="65f1b-119">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>|  
|[<span data-ttu-id="65f1b-120">Метод CreateEvidence</span><span class="sxs-lookup"><span data-stu-id="65f1b-120">CreateEvidence Method</span></span>](icorruntimehost-createevidence-method.md)|<span data-ttu-id="65f1b-121">Возвращает указатель интерфейса типа <xref:System.Security.Principal.IIdentity> , который позволяет основному приложению создавать доказательства безопасности для передачи в [CreateDomain](icorruntimehost-createdomain-method.md) или [CreateDomainEx](icorruntimehost-createdomainex-method.md).</span><span class="sxs-lookup"><span data-stu-id="65f1b-121">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity>, which allows the host to create security evidence to pass to [CreateDomain](icorruntimehost-createdomain-method.md) or [CreateDomainEx](icorruntimehost-createdomainex-method.md).</span></span>|  
|[<span data-ttu-id="65f1b-122">Метод CreateLogicalThreadState</span><span class="sxs-lookup"><span data-stu-id="65f1b-122">CreateLogicalThreadState Method</span></span>](icorruntimehost-createlogicalthreadstate-method.md)|<span data-ttu-id="65f1b-123">Не используется.</span><span class="sxs-lookup"><span data-stu-id="65f1b-123">Do not use.</span></span>|  
|[<span data-ttu-id="65f1b-124">Метод CurrentDomain</span><span class="sxs-lookup"><span data-stu-id="65f1b-124">CurrentDomain Method</span></span>](icorruntimehost-currentdomain-method.md)|<span data-ttu-id="65f1b-125">Возвращает указатель интерфейса типа <xref:System._AppDomain> , который представляет домен, загруженный в текущем потоке.</span><span class="sxs-lookup"><span data-stu-id="65f1b-125">Gets an interface pointer of type <xref:System._AppDomain> that represents the domain loaded on the current thread.</span></span>|  
|[<span data-ttu-id="65f1b-126">Метод DeleteLogicalThreadState</span><span class="sxs-lookup"><span data-stu-id="65f1b-126">DeleteLogicalThreadState Method</span></span>](icorruntimehost-deletelogicalthreadstate-method.md)|<span data-ttu-id="65f1b-127">Не используется.</span><span class="sxs-lookup"><span data-stu-id="65f1b-127">Do not use.</span></span>|  
|[<span data-ttu-id="65f1b-128">Метод EnumDomains</span><span class="sxs-lookup"><span data-stu-id="65f1b-128">EnumDomains Method</span></span>](icorruntimehost-enumdomains-method.md)|<span data-ttu-id="65f1b-129">Возвращает перечислитель для доменов в текущем процессе.</span><span class="sxs-lookup"><span data-stu-id="65f1b-129">Gets an enumerator for the domains in the current process.</span></span>|  
|[<span data-ttu-id="65f1b-130">Метод настройки</span><span class="sxs-lookup"><span data-stu-id="65f1b-130">GetConfiguration Method</span></span>](icorruntimehost-getconfiguration-method.md)|<span data-ttu-id="65f1b-131">Возвращает объект, позволяющий ведущему приложению указать конфигурацию обратного вызова среды CLR.</span><span class="sxs-lookup"><span data-stu-id="65f1b-131">Gets an object that allows the host to specify the callback configuration of the CLR.</span></span>|  
|[<span data-ttu-id="65f1b-132">Метод GetDefaultDomain</span><span class="sxs-lookup"><span data-stu-id="65f1b-132">GetDefaultDomain Method</span></span>](icorruntimehost-getdefaultdomain-method.md)|<span data-ttu-id="65f1b-133">Возвращает указатель интерфейса типа <xref:System._AppDomain> , представляющий домен по умолчанию для текущего процесса.</span><span class="sxs-lookup"><span data-stu-id="65f1b-133">Gets an interface pointer of type <xref:System._AppDomain> that represents the default domain for the current process.</span></span>|  
|[<span data-ttu-id="65f1b-134">Метод LocksHeldByLogicalThread</span><span class="sxs-lookup"><span data-stu-id="65f1b-134">LocksHeldByLogicalThread Method</span></span>](icorruntimehost-locksheldbylogicalthread-method.md)|<span data-ttu-id="65f1b-135">Не используется.</span><span class="sxs-lookup"><span data-stu-id="65f1b-135">Do not use.</span></span>|  
|[<span data-ttu-id="65f1b-136">Метод MapFile</span><span class="sxs-lookup"><span data-stu-id="65f1b-136">MapFile Method</span></span>](icorruntimehost-mapfile-method.md)|<span data-ttu-id="65f1b-137">Сопоставляет указанный файл с памятью.</span><span class="sxs-lookup"><span data-stu-id="65f1b-137">Maps the specified file into memory.</span></span> <span data-ttu-id="65f1b-138">Этот метод устарел.</span><span class="sxs-lookup"><span data-stu-id="65f1b-138">This method is obsolete.</span></span>|  
|[<span data-ttu-id="65f1b-139">Метод NextDomain</span><span class="sxs-lookup"><span data-stu-id="65f1b-139">NextDomain Method</span></span>](icorruntimehost-nextdomain-method.md)|<span data-ttu-id="65f1b-140">Возвращает указатель интерфейса на следующий домен в перечислении.</span><span class="sxs-lookup"><span data-stu-id="65f1b-140">Gets an interface pointer to the next domain in the enumeration.</span></span>|  
|[<span data-ttu-id="65f1b-141">Метод Start</span><span class="sxs-lookup"><span data-stu-id="65f1b-141">Start Method</span></span>](icorruntimehost-start-method.md)|<span data-ttu-id="65f1b-142">Запускает среду CLR.</span><span class="sxs-lookup"><span data-stu-id="65f1b-142">Starts the CLR.</span></span>|  
|[<span data-ttu-id="65f1b-143">Метод завершения</span><span class="sxs-lookup"><span data-stu-id="65f1b-143">Stop Method</span></span>](icorruntimehost-stop-method.md)|<span data-ttu-id="65f1b-144">Останавливает выполнение кода в среде выполнения для текущего процесса.</span><span class="sxs-lookup"><span data-stu-id="65f1b-144">Stops the execution of code in the runtime for the current process.</span></span>|  
|[<span data-ttu-id="65f1b-145">Метод SwitchInLogicalThreadState</span><span class="sxs-lookup"><span data-stu-id="65f1b-145">SwitchInLogicalThreadState Method</span></span>](icorruntimehost-switchinlogicalthreadstate-method.md)|<span data-ttu-id="65f1b-146">Не используется.</span><span class="sxs-lookup"><span data-stu-id="65f1b-146">Do not use.</span></span>|  
|[<span data-ttu-id="65f1b-147">Метод SwitchOutLogicalThreadState</span><span class="sxs-lookup"><span data-stu-id="65f1b-147">SwitchOutLogicalThreadState Method</span></span>](icorruntimehost-switchoutlogicalthreadstate-method.md)|<span data-ttu-id="65f1b-148">Не используется.</span><span class="sxs-lookup"><span data-stu-id="65f1b-148">Do not use.</span></span>|  
|[<span data-ttu-id="65f1b-149">Метод UnloadDomain</span><span class="sxs-lookup"><span data-stu-id="65f1b-149">UnloadDomain Method</span></span>](icorruntimehost-unloaddomain-method.md)|<span data-ttu-id="65f1b-150">Выгружает указанный домен приложения из текущего процесса.</span><span class="sxs-lookup"><span data-stu-id="65f1b-150">Unloads the specified application domain from the current process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="65f1b-151">Требования</span><span class="sxs-lookup"><span data-stu-id="65f1b-151">Requirements</span></span>  

 <span data-ttu-id="65f1b-152">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65f1b-152">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65f1b-153">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="65f1b-153">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="65f1b-154">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="65f1b-154">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65f1b-155">**Платформа .NET Framework версии:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="65f1b-155">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65f1b-156">См. также</span><span class="sxs-lookup"><span data-stu-id="65f1b-156">See also</span></span>

- <xref:System.AppDomain>
- [<span data-ttu-id="65f1b-157">Размещение</span><span class="sxs-lookup"><span data-stu-id="65f1b-157">Hosting</span></span>](index.md)
- [<span data-ttu-id="65f1b-158">Интерфейс ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="65f1b-158">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- <span data-ttu-id="65f1b-159">[Хост-приложения среды выполнения](/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="65f1b-159">[Runtime Hosts](/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span></span>
- [<span data-ttu-id="65f1b-160">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="65f1b-160">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="65f1b-161">Компонентный класс CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="65f1b-161">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
