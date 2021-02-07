---
description: 'Дополнительные сведения о: HttpTransportBindingElement'
title: HttpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
ms.openlocfilehash: 6c516dd7124d52828145787d55421d12031c2d36
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757375"
---
# <a name="httptransportbindingelement"></a><span data-ttu-id="9e039-103">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9e039-103">HttpTransportBindingElement</span></span>

<span data-ttu-id="9e039-104">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9e039-104">HttpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e039-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9e039-105">Syntax</span></span>  
  
```csharp
class HttpTransportBindingElement : TransportBindingElement  
{  
  boolean AllowCookies;  
  string AuthenticationScheme;  
  boolean BypassProxyOnLocal;  
  string HostNameComparisonMode;  
  boolean KeepAliveEnabled;  
  sint32 MaxBufferSize;  
  string ProxyAddress;  
  string ProxyAuthenticationScheme;  
  string Realm;  
  string TransferMode;  
  boolean UnsafeConnectionNtlmAuthentication;  
  boolean UseDefaultWebProxy;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="9e039-106">Методы</span><span class="sxs-lookup"><span data-stu-id="9e039-106">Methods</span></span>  

 <span data-ttu-id="9e039-107">Класс HttpTransportBindingElement не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="9e039-107">The HttpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9e039-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="9e039-108">Properties</span></span>  

 <span data-ttu-id="9e039-109">Класс HttpTransportBindingElement имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="9e039-109">The HttpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="allowcookies"></a><span data-ttu-id="9e039-110">AllowCookies</span><span class="sxs-lookup"><span data-stu-id="9e039-110">AllowCookies</span></span>  

 <span data-ttu-id="9e039-111">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="9e039-111">Data type: boolean</span></span>  
  
 <span data-ttu-id="9e039-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="9e039-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9e039-113">Значение, определяющее, принимает ли клиент файлы Cookie и распространяет ли он их на будущие запросы.</span><span class="sxs-lookup"><span data-stu-id="9e039-113">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span>  
  
### <a name="authenticationscheme"></a><span data-ttu-id="9e039-114">AuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="9e039-114">AuthenticationScheme</span></span>  

 <span data-ttu-id="9e039-115">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="9e039-115">Data type: string</span></span>  
  
 <span data-ttu-id="9e039-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="9e039-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9e039-117">Схема проверки подлинности, используемая для проверки подлинности клиентских запросов, обрабатываемых HTTP-прослушивателем.</span><span class="sxs-lookup"><span data-stu-id="9e039-117">The authentication scheme used to authenticate client requests being processed by an HTTP listener.</span></span>  
  
### <a name="bypassproxyonlocal"></a><span data-ttu-id="9e039-118">BypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="9e039-118">BypassProxyOnLocal</span></span>  

 <span data-ttu-id="9e039-119">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="9e039-119">Data type: boolean</span></span>  
  
 <span data-ttu-id="9e039-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="9e039-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9e039-121">Значение, указывающее, игнорируются ли прокси-серверы для локальных адресов.</span><span class="sxs-lookup"><span data-stu-id="9e039-121">A value that indicates whether proxies are ignored for local addresses.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="9e039-122">HostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="9e039-122">HostNameComparisonMode</span></span>  

 <span data-ttu-id="9e039-123">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="9e039-123">Data type: string</span></span>  
  
 <span data-ttu-id="9e039-124">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="9e039-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9e039-125">Значение, указывающее, используется ли имя узла для доступа к службе при сопоставлении по универсальному коду ресурса (URI).</span><span class="sxs-lookup"><span data-stu-id="9e039-125">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="keepaliveenabled"></a><span data-ttu-id="9e039-126">KeepAliveEnabled</span><span class="sxs-lookup"><span data-stu-id="9e039-126">KeepAliveEnabled</span></span>  

 <span data-ttu-id="9e039-127">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="9e039-127">Data type: boolean</span></span>  
  
 <span data-ttu-id="9e039-128">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="9e039-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9e039-129">Когда включено, соединения HTTP остаются в активном состоянии независимо от уровня активности.</span><span class="sxs-lookup"><span data-stu-id="9e039-129">When enabled, HTTP connections are kept alive regardless of activity level.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="9e039-130">MaxBufferSize</span><span class="sxs-lookup"><span data-stu-id="9e039-130">MaxBufferSize</span></span>  

 <span data-ttu-id="9e039-131">Тип данных: sint32</span><span class="sxs-lookup"><span data-stu-id="9e039-131">Data type: sint32</span></span>  
  
 <span data-ttu-id="9e039-132">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="9e039-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9e039-133">Максимальный размер буферного пула.</span><span class="sxs-lookup"><span data-stu-id="9e039-133">The maximum size of the buffer pool.</span></span>  
  
### <a name="proxyaddress"></a><span data-ttu-id="9e039-134">ProxyAddress</span><span class="sxs-lookup"><span data-stu-id="9e039-134">ProxyAddress</span></span>  

 <span data-ttu-id="9e039-135">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="9e039-135">Data type: string</span></span>  
  
 <span data-ttu-id="9e039-136">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="9e039-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9e039-137">Универсальный код ресурса (URI), который содержит адрес прокси-сервера, используемого для выполнения HTTP-запросов.</span><span class="sxs-lookup"><span data-stu-id="9e039-137">A URI that contains the address of the proxy to use for HTTP requests.</span></span>  
  
### <a name="proxyauthenticationscheme"></a><span data-ttu-id="9e039-138">ProxyAuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="9e039-138">ProxyAuthenticationScheme</span></span>  

 <span data-ttu-id="9e039-139">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="9e039-139">Data type: string</span></span>  
  
 <span data-ttu-id="9e039-140">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="9e039-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9e039-141">Схема проверки подлинности, используемая для проверки подлинности клиентских запросов, обрабатываемых прокси-сервером HTTP.</span><span class="sxs-lookup"><span data-stu-id="9e039-141">The authentication scheme used to authenticate client requests being processed by an HTTP proxy.</span></span>  
  
### <a name="realm"></a><span data-ttu-id="9e039-142">Realm</span><span class="sxs-lookup"><span data-stu-id="9e039-142">Realm</span></span>  

 <span data-ttu-id="9e039-143">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="9e039-143">Data type: string</span></span>  
  
 <span data-ttu-id="9e039-144">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="9e039-144">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9e039-145">Область проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="9e039-145">The authentication realm.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="9e039-146">TransferMode</span><span class="sxs-lookup"><span data-stu-id="9e039-146">TransferMode</span></span>  

 <span data-ttu-id="9e039-147">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="9e039-147">Data type: string</span></span>  
  
 <span data-ttu-id="9e039-148">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="9e039-148">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9e039-149">Значение, указывающее статус сообщения: помещено в буфер или поток, запрос или ответ.</span><span class="sxs-lookup"><span data-stu-id="9e039-149">A value that specifies whether messages are buffered or streamed or a request or response.</span></span>  
  
### <a name="unsafeconnectionntlmauthentication"></a><span data-ttu-id="9e039-150">UnsafeConnectionNtlmAuthentication</span><span class="sxs-lookup"><span data-stu-id="9e039-150">UnsafeConnectionNtlmAuthentication</span></span>  

 <span data-ttu-id="9e039-151">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="9e039-151">Data type: boolean</span></span>  
  
 <span data-ttu-id="9e039-152">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="9e039-152">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9e039-153">Значение, указывающее, разрешено ли на сервере совместное использование небезопасных подключений.</span><span class="sxs-lookup"><span data-stu-id="9e039-153">A value that indicates whether Unsafe Connection Sharing is enabled on the server.</span></span>  
  
### <a name="usedefaultwebproxy"></a><span data-ttu-id="9e039-154">UseDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="9e039-154">UseDefaultWebProxy</span></span>  

 <span data-ttu-id="9e039-155">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="9e039-155">Data type: boolean</span></span>  
  
 <span data-ttu-id="9e039-156">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="9e039-156">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9e039-157">Значение, указывающее, используются ли параметры прокси-сервера компьютера или пользователя.</span><span class="sxs-lookup"><span data-stu-id="9e039-157">A value that indicates whether the machine-wide proxy settings are used rather than the user specific settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e039-158">Требования</span><span class="sxs-lookup"><span data-stu-id="9e039-158">Requirements</span></span>  
  
|<span data-ttu-id="9e039-159">MOF</span><span class="sxs-lookup"><span data-stu-id="9e039-159">MOF</span></span>|<span data-ttu-id="9e039-160">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="9e039-160">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9e039-161">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="9e039-161">Namespace</span></span>|<span data-ttu-id="9e039-162">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="9e039-162">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9e039-163">См. также</span><span class="sxs-lookup"><span data-stu-id="9e039-163">See also</span></span>

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
