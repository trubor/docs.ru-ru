---
description: 'Подробнее: интеграция с приложениями COM обзор'
title: Общие сведения об интеграции с приложениями COM
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
ms.openlocfilehash: a179fd73c8065fff1e16d3f86202d717df155b81
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802818"
---
# <a name="integrating-with-com-applications-overview"></a><span data-ttu-id="c4bb9-103">Общие сведения об интеграции с приложениями COM</span><span class="sxs-lookup"><span data-stu-id="c4bb9-103">Integrating with COM Applications Overview</span></span>

<span data-ttu-id="c4bb9-104">Windows Communication Foundation (WCF) предоставляет разработчику управляемого кода обширную среду для создания подключенных приложений.</span><span class="sxs-lookup"><span data-stu-id="c4bb9-104">Windows Communication Foundation (WCF) provides the managed code developer with a rich environment for creating connected applications.</span></span> <span data-ttu-id="c4bb9-105">Однако если у вас есть существенные инвестиции в неуправляемый код на основе COM и вы не хотите выполнять миграцию, веб-службы WCF можно интегрировать непосредственно в существующий код с помощью моникера службы WCF.</span><span class="sxs-lookup"><span data-stu-id="c4bb9-105">However, if you have a substantial investment in unmanaged COM-based code and do not want to migrate, you can still integrate WCF Web services directly into your existing code by using the WCF service moniker.</span></span> <span data-ttu-id="c4bb9-106">Моникер служб можно использовать в широком наборе сред разработки на базе модели COM, например в Office VBA, Visual Basic 6.0 и Visual C++ 6.0.</span><span class="sxs-lookup"><span data-stu-id="c4bb9-106">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>

> [!NOTE]
> <span data-ttu-id="c4bb9-107">Моникер службы использует канал связи WCF для всего обмена данными.</span><span class="sxs-lookup"><span data-stu-id="c4bb9-107">The service moniker uses a WCF communication channel for all communication.</span></span> <span data-ttu-id="c4bb9-108">Механизмы безопасности и идентификации для этого канала отличаются от механизмов, используемых в стандартных прокси-средствах COM и DCOM.</span><span class="sxs-lookup"><span data-stu-id="c4bb9-108">The security and identity mechanisms for that channel differ from those used in standard COM and DCOM proxies.</span></span> <span data-ttu-id="c4bb9-109">Кроме того, поскольку моникер службы использует канал связи WCF, время ожидания по умолчанию составляет одну минуту для всех вызовов.</span><span class="sxs-lookup"><span data-stu-id="c4bb9-109">In addition, because the service moniker uses a WCF communication channel the default timeout period is one minute for all calls.</span></span>

<span data-ttu-id="c4bb9-110">Моникер службы используется с `GetObject` функцией для предоставления неуправляемому разработчику строго типизированного, зависящего от com подхода к вызову веб-служб WCF.</span><span class="sxs-lookup"><span data-stu-id="c4bb9-110">The service moniker is used with the `GetObject` function to provide the unmanaged developer with a strongly-typed, COM-specific approach for calling WCF Web services.</span></span> <span data-ttu-id="c4bb9-111">Для этого требуется локальное, видимое COM определение контракта веб-службы WCF и используемой привязки.</span><span class="sxs-lookup"><span data-stu-id="c4bb9-111">This requires a local, COM-visible definition of the WCF Web service contract and the binding that is to be used.</span></span> <span data-ttu-id="c4bb9-112">Как и другие клиенты WCF, моникер службы должен создать типизированный канал для службы, хотя эта конструкция канала прозрачна для программиста COM при первом вызове метода.</span><span class="sxs-lookup"><span data-stu-id="c4bb9-112">Like other WCF clients, the service moniker must construct a typed channel to the service, though this channel construction occurs transparently to the COM programmer on the first method call.</span></span>

<span data-ttu-id="c4bb9-113">В общих случаях с другими клиентами WCF при использовании моникера приложения указывают адрес, привязку и контракт для взаимодействия со службой.</span><span class="sxs-lookup"><span data-stu-id="c4bb9-113">In common with other WCF clients, when using the moniker, applications specify the address, binding and contract to communicate with a service.</span></span> <span data-ttu-id="c4bb9-114">Контракт можно задать одним из следующих способов.</span><span class="sxs-lookup"><span data-stu-id="c4bb9-114">The contract can be specified in one of the following ways:</span></span>

- <span data-ttu-id="c4bb9-115">Типизированный контракт: контракт регистрируется как видимый для модели COM тип на клиентском компьютере.</span><span class="sxs-lookup"><span data-stu-id="c4bb9-115">Typed contract – the contract is registered as a COM visible type on the client machine.</span></span>

- <span data-ttu-id="c4bb9-116">Контракт WSDL: контракт предоставляется в виде документа WSDL.</span><span class="sxs-lookup"><span data-stu-id="c4bb9-116">WSDL contract – the contract is supplied in the form of a WSDL document.</span></span>

- <span data-ttu-id="c4bb9-117">Контракт MEX: контракт получается в среде выполнения из конечной точки обмена метаданными (MEX).</span><span class="sxs-lookup"><span data-stu-id="c4bb9-117">MEX contract – the contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>

## <a name="parameters-supported-by-the-service-moniker"></a><span data-ttu-id="c4bb9-118">Параметры, поддерживаемые моникером служб</span><span class="sxs-lookup"><span data-stu-id="c4bb9-118">Parameters Supported by the Service Moniker</span></span>

<span data-ttu-id="c4bb9-119">В следующей таблице представлены параметры, поддерживаемые моникером служб.</span><span class="sxs-lookup"><span data-stu-id="c4bb9-119">The following table shows the parameters that are supported by the service moniker.</span></span>

|<span data-ttu-id="c4bb9-120">Параметр</span><span class="sxs-lookup"><span data-stu-id="c4bb9-120">Parameter</span></span>|<span data-ttu-id="c4bb9-121">Описание</span><span class="sxs-lookup"><span data-stu-id="c4bb9-121">Description</span></span>|
|---------------|-----------------|
|`address`|<span data-ttu-id="c4bb9-122">URL-адрес службы.</span><span class="sxs-lookup"><span data-stu-id="c4bb9-122">URL location of the service.</span></span>|
|`binding`|<span data-ttu-id="c4bb9-123">Имя раздела привязки из конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="c4bb9-123">Binding section name from the application configuration.</span></span>|
|`bindingConfiguration`|<span data-ttu-id="c4bb9-124">Именованный экземпляр привязки из именованного раздела привязки.</span><span class="sxs-lookup"><span data-stu-id="c4bb9-124">Named binding instance from within the named binding section.</span></span>|
|`contract`|<span data-ttu-id="c4bb9-125">Идентификатор интерфейса (IID), представляющий контракт службы или имя контракта (из MEX).</span><span class="sxs-lookup"><span data-stu-id="c4bb9-125">Interface identifier (IID) that represents the service contract or the contract name (from MEX).</span></span>|
|`wsdl`|<span data-ttu-id="c4bb9-126">Документ WSDL, обеспечивающий альтернативную форму определения контракта.</span><span class="sxs-lookup"><span data-stu-id="c4bb9-126">WSDL document that provides an alternative form of contract definition.</span></span>|
|`spnIdentity`|<span data-ttu-id="c4bb9-127">Идентификатор имени участника на уровне сервера (SPN), который должен использоваться для взаимодействия со службой.</span><span class="sxs-lookup"><span data-stu-id="c4bb9-127">Server principal name (SPN) identity to be used to communicate with the service.</span></span>|
|`upnIdentity`|<span data-ttu-id="c4bb9-128">Идентификатор имени участника-пользователя (UPN), который должен использоваться для взаимодействия со службой.</span><span class="sxs-lookup"><span data-stu-id="c4bb9-128">User principal name (UPN) identity to be used to communicate with the service.</span></span>|
|`dnsIdentity`|<span data-ttu-id="c4bb9-129">Идентификатор DNS, который должен использоваться для взаимодействия со службой.</span><span class="sxs-lookup"><span data-stu-id="c4bb9-129">DNS identity to be used to communicate with the service.</span></span>|
|`mexAddress`|<span data-ttu-id="c4bb9-130">URL-адрес конечной точки службы для обмена метаданными (MEX).</span><span class="sxs-lookup"><span data-stu-id="c4bb9-130">URL location of the Metadata Exchange (MEX) endpoint of the service.</span></span>|
|`mexBinding`|<span data-ttu-id="c4bb9-131">Имя раздела привязки из конфигурации приложения для соединения с конечной точкой MEX.</span><span class="sxs-lookup"><span data-stu-id="c4bb9-131">Binding section name from the application configuration to connect with the MEX endpoint.</span></span>|
|`mexBindingConfiguration`|<span data-ttu-id="c4bb9-132">Именованный экземпляр привязки из именованного раздела привязки для соединения с конечной точкой MEX.</span><span class="sxs-lookup"><span data-stu-id="c4bb9-132">Named binding instance from within the named binding section to connect with the MEX endpoint.</span></span>|
|`bindingNamespace`|<span data-ttu-id="c4bb9-133">Пространство имен для имени раздела привязки, полученное в результате MEX.</span><span class="sxs-lookup"><span data-stu-id="c4bb9-133">Namespace of the binding section name from the retrieved MEX.</span></span>|
|`contractNamespace`|<span data-ttu-id="c4bb9-134">Пространство имен контракта, полученное в результате MEX.</span><span class="sxs-lookup"><span data-stu-id="c4bb9-134">Namespace of the contract from the retrieved MEX.</span></span>|
|`mexSpnIdentity`|<span data-ttu-id="c4bb9-135">Идентификатор имени участника на уровне сервера (SPN), который должен использоваться для взаимодействия с конечной точкой MEX.</span><span class="sxs-lookup"><span data-stu-id="c4bb9-135">Server principal name (SPN) identity to be used to communicate with the MEX endpoint.</span></span>|
|`mexUpnIdentity`|<span data-ttu-id="c4bb9-136">Идентификатор имени участника-пользователя (UPN), который должен использоваться для взаимодействия с конечной точкой MEX.</span><span class="sxs-lookup"><span data-stu-id="c4bb9-136">User principal name (UPN) identity to be used to communicate with the MEX endpoint.</span></span>|
|`mexDnsIdentity`|<span data-ttu-id="c4bb9-137">Идентификатор DNS, который должен использоваться для взаимодействия с конечной точкой MEX.</span><span class="sxs-lookup"><span data-stu-id="c4bb9-137">DNS identity to be used to communicate with the MEX endpoint.</span></span>|
|`serializer`|<span data-ttu-id="c4bb9-138">Позволяет задать использование сериализатора "xml" или "datacontract".</span><span class="sxs-lookup"><span data-stu-id="c4bb9-138">Specify the use of either the "xml" or "datacontract" serializer.</span></span>|

> [!NOTE]
> <span data-ttu-id="c4bb9-139">Даже при использовании с полностью основанными на COM клиентами для моникера службы требуется WCF, а на клиентском компьютере должна быть установлена поддержка платформа .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="c4bb9-139">Even when used with entirely COM-based clients, the service moniker requires WCF and the supporting .NET Framework 2.0 to be installed on the client computer.</span></span> <span data-ttu-id="c4bb9-140">Также важно, чтобы в клиентские приложения, использующие моникер служб, была загружена соответствующая версия среды выполнения платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c4bb9-140">It is also critical that client applications that use the service moniker load the appropriate version of the .NET Framework runtime.</span></span> <span data-ttu-id="c4bb9-141">При использовании моникера в приложениях Office может потребоваться файл конфигурации, чтобы обеспечить загрузку надлежащей версии .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c4bb9-141">When using the moniker within Office applications, a configuration file may be required to ensure that the correct framework version is loaded.</span></span> <span data-ttu-id="c4bb9-142">Например, при использовании Excel файл Excel.exe.config, расположенный в том же каталоге, что и файл Excel.exe, должен содержать следующий текст:</span><span class="sxs-lookup"><span data-stu-id="c4bb9-142">For example, with Excel, the following text should be placed in a file called Excel.exe.config in the same directory as the Excel.exe file:</span></span>
>
> `<?xml version="1.0" encoding="utf-8"?>`
>
> <span data-ttu-id="c4bb9-143">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span><span class="sxs-lookup"><span data-stu-id="c4bb9-143">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span></span>
>
> `<startup>`
>
> `<requiredRuntime version="v2.0.50727" />`
>
> `</startup>`
>
> `</configuration>`

## <a name="see-also"></a><span data-ttu-id="c4bb9-144">См. также</span><span class="sxs-lookup"><span data-stu-id="c4bb9-144">See also</span></span>

- [<span data-ttu-id="c4bb9-145">Практическое руководство. Регистрация и настройка моникера службы</span><span class="sxs-lookup"><span data-stu-id="c4bb9-145">How to: Register and Configure a Service Moniker</span></span>](how-to-register-and-configure-a-service-moniker.md)
