---
description: Дополнительные сведения см. в справочнике по классам WMI
title: Справочные сведения по классам WMI
ms.date: 03/30/2017
ms.assetid: b95a51f5-8251-4619-ae05-7de88cb90f9a
ms.openlocfilehash: 6413065b5740b190aee122ef34727da120737afa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757026"
---
# <a name="wmi-class-reference"></a><span data-ttu-id="3420f-103">Справочные сведения по классам WMI</span><span class="sxs-lookup"><span data-stu-id="3420f-103">WMI Class Reference</span></span>

<span data-ttu-id="3420f-104">В этом разделе перечислены все классы WMI, предоставляемые поставщиком WMI для Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3420f-104">This section lists all the WMI classes exposed by the Windows Communication Foundation (WCF) WMI provider.</span></span>  
  
## <a name="accessing-wmi-instances"></a><span data-ttu-id="3420f-105">Доступ к экземплярам WMI</span><span class="sxs-lookup"><span data-stu-id="3420f-105">Accessing WMI Instances</span></span>  

 <span data-ttu-id="3420f-106">Все классы, перечисленные в ссылках на объект WMI, невозможно создать напрямую, за исключением классов службы, домена приложения, контракта, ServiceToEndpointAssociation и конечной точки.</span><span class="sxs-lookup"><span data-stu-id="3420f-106">All the classes listed in the WMI Object Reference cannot be directly instantiated, except for Service, AppDomain, Contract, ServiceAppDomain, ServiceToEndpointAssociation and Endpoint.</span></span> <span data-ttu-id="3420f-107">Чтобы получить доступ к другим экземплярам, можно получить доступ к свойствам указанных выше классов верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="3420f-107">To access other instances, you can access the properties of the previously mentioned top level classes.</span></span> <span data-ttu-id="3420f-108">Например, можно получить доступ к экземпляру TransportBindingElement из экземпляра конечной точки — > Binding-> BindingElements.</span><span class="sxs-lookup"><span data-stu-id="3420f-108">For example, you can access the TransportBindingElement instance from the Endpoint instance -> Binding -> BindingElements.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3420f-109">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="3420f-109">In This Section</span></span>  

 [<span data-ttu-id="3420f-110">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="3420f-110">ActivityTransfer</span></span>](activitytransfer.md)  
  
 [<span data-ttu-id="3420f-111">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="3420f-111">AppDomainInfo</span></span>](appdomaininfo.md)  
  
 [<span data-ttu-id="3420f-112">AspNetCompatibilityRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="3420f-112">AspNetCompatibilityRequirementsAttribute</span></span>](aspnetcompatibilityrequirementsattribute.md)  
  
 [<span data-ttu-id="3420f-113">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="3420f-113">AsymmetricSecurityBindingElement</span></span>](asymmetricsecuritybindingelement.md)  
  
 <span data-ttu-id="3420f-114">"Класс поведения"</span><span class="sxs-lookup"><span data-stu-id="3420f-114">"Behavior class"</span></span>  
  
 [<span data-ttu-id="3420f-115">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="3420f-115">BinaryMessageEncodingBindingElement</span></span>](binarymessageencodingbindingelement.md)  
  
 [<span data-ttu-id="3420f-116">Вязывания</span><span class="sxs-lookup"><span data-stu-id="3420f-116">Binding</span></span>](binding.md)  
  
 [<span data-ttu-id="3420f-117">BindingElement</span><span class="sxs-lookup"><span data-stu-id="3420f-117">BindingElement</span></span>](bindingelement.md)  
  
 [<span data-ttu-id="3420f-118">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="3420f-118">CallbackBehavior</span></span>](callbackbehavior.md)  
  
 [<span data-ttu-id="3420f-119">Класс Channel</span><span class="sxs-lookup"><span data-stu-id="3420f-119">Channel class</span></span>](channel-class.md)  
  
 [<span data-ttu-id="3420f-120">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="3420f-120">ChannelPoolSettings</span></span>](channelpoolsettings.md)  
  
 [<span data-ttu-id="3420f-121">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="3420f-121">ClientCredentials</span></span>](clientcredentials.md)  
  
 [<span data-ttu-id="3420f-122">ClientViaBehavior</span><span class="sxs-lookup"><span data-stu-id="3420f-122">ClientViaBehavior</span></span>](clientviabehavior.md)  
  
 [<span data-ttu-id="3420f-123">CompositeDuplexBindingElement</span><span class="sxs-lookup"><span data-stu-id="3420f-123">CompositeDuplexBindingElement</span></span>](compositeduplexbindingelement.md)  
  
 [<span data-ttu-id="3420f-124">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="3420f-124">ConnectionOrientedTransportBindingElement</span></span>](connectionorientedtransportbindingelement.md)  
  
 [<span data-ttu-id="3420f-125">Архивирован</span><span class="sxs-lookup"><span data-stu-id="3420f-125">Contract</span></span>](contract.md)  
  
 [<span data-ttu-id="3420f-126">CustomBindingElement</span><span class="sxs-lookup"><span data-stu-id="3420f-126">CustomBindingElement</span></span>](custombindingelement.md)  
  
 [<span data-ttu-id="3420f-127">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="3420f-127">DeliveryRequirementsAttribute</span></span>](deliveryrequirementsattribute.md)  
  
 [<span data-ttu-id="3420f-128">Конечная точка</span><span class="sxs-lookup"><span data-stu-id="3420f-128">Endpoint</span></span>](endpoint.md)  
  
 [<span data-ttu-id="3420f-129">HttpsTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="3420f-129">HttpsTransportBindingElement</span></span>](httpstransportbindingelement.md)  
  
 [<span data-ttu-id="3420f-130">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="3420f-130">HttpTransportBindingElement</span></span>](httptransportbindingelement.md)  
  
 [<span data-ttu-id="3420f-131">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="3420f-131">LocalServiceSecuritySettings</span></span>](localservicesecuritysettings.md)  
  
 [<span data-ttu-id="3420f-132">MatchAllEndpointBehavior</span><span class="sxs-lookup"><span data-stu-id="3420f-132">MatchAllEndpointBehavior</span></span>](matchallendpointbehavior.md)  
  
 [<span data-ttu-id="3420f-133">MessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="3420f-133">MessageEncodingBindingElement</span></span>](messageencodingbindingelement.md)  
  
 [<span data-ttu-id="3420f-134">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="3420f-134">MsmqBindingElementBase</span></span>](msmqbindingelementbase.md)  
  
 [<span data-ttu-id="3420f-135">MsmqIntegrationBindingElement</span><span class="sxs-lookup"><span data-stu-id="3420f-135">MsmqIntegrationBindingElement</span></span>](msmqintegrationbindingelement.md)  
  
 [<span data-ttu-id="3420f-136">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="3420f-136">MsmqTransportBindingElement</span></span>](msmqtransportbindingelement.md)  
  
 [<span data-ttu-id="3420f-137">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="3420f-137">MtomMessageEncodingBindingElement</span></span>](mtommessageencodingbindingelement.md)  
  
 [<span data-ttu-id="3420f-138">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="3420f-138">MustUnderstandBehavior</span></span>](mustunderstandbehavior.md)  
  
 [<span data-ttu-id="3420f-139">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="3420f-139">NamedPipeConnectionPoolSettings</span></span>](namedpipeconnectionpoolsettings.md)  
  
 [<span data-ttu-id="3420f-140">NamedPipeTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="3420f-140">NamedPipeTransportBindingElement</span></span>](namedpipetransportbindingelement.md)  
  
 [<span data-ttu-id="3420f-141">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="3420f-141">OneWayBindingElement</span></span>](onewaybindingelement.md)  
  
 <span data-ttu-id="3420f-142">"Класс операции"</span><span class="sxs-lookup"><span data-stu-id="3420f-142">"Operation class"</span></span>  
  
 [<span data-ttu-id="3420f-143">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="3420f-143">OperationBehaviorAttribute</span></span>](operationbehaviorattribute.md)  
  
 [<span data-ttu-id="3420f-144">PeerCustomResolverBindingElement</span><span class="sxs-lookup"><span data-stu-id="3420f-144">PeerCustomResolverBindingElement</span></span>](peercustomresolverbindingelement.md)  
  
 [<span data-ttu-id="3420f-145">PeerResolverBindingElement</span><span class="sxs-lookup"><span data-stu-id="3420f-145">PeerResolverBindingElement</span></span>](peerresolverbindingelement.md)  
  
 [<span data-ttu-id="3420f-146">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="3420f-146">PeerSecuritySettings</span></span>](peersecuritysettings.md)  
  
 [<span data-ttu-id="3420f-147">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="3420f-147">PeerTransportBindingElement</span></span>](peertransportbindingelement.md)  
  
 [<span data-ttu-id="3420f-148">PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="3420f-148">PeerTransportSecuritySettings</span></span>](peertransportsecuritysettings.md)  
  
 [<span data-ttu-id="3420f-149">PnrpPeerResolverBindingElement</span><span class="sxs-lookup"><span data-stu-id="3420f-149">PnrpPeerResolverBindingElement</span></span>](pnrppeerresolverbindingelement.md)  
  
 [<span data-ttu-id="3420f-150">PrivacyNoticeBindingElement</span><span class="sxs-lookup"><span data-stu-id="3420f-150">PrivacyNoticeBindingElement</span></span>](privacynoticebindingelement.md)  
  
 [<span data-ttu-id="3420f-151">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="3420f-151">ReliableSessionBindingElement</span></span>](reliablesessionbindingelement.md)  
  
 [<span data-ttu-id="3420f-152">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="3420f-152">SecurityBindingElement</span></span>](securitybindingelement.md)  
  
 [<span data-ttu-id="3420f-153">Служба</span><span class="sxs-lookup"><span data-stu-id="3420f-153">Service</span></span>](service.md)  
  
 [<span data-ttu-id="3420f-154">ServiceAppDomain</span><span class="sxs-lookup"><span data-stu-id="3420f-154">ServiceAppDomain</span></span>](serviceappdomain.md)  
  
 [<span data-ttu-id="3420f-155">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="3420f-155">ServiceAuthorizationBehavior</span></span>](serviceauthorizationbehavior.md)  
  
 [<span data-ttu-id="3420f-156">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="3420f-156">ServiceBehaviorAttribute</span></span>](servicebehaviorattribute.md)  
  
 [<span data-ttu-id="3420f-157">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="3420f-157">ServiceCredentials</span></span>](servicecredentials.md)  
  
 [<span data-ttu-id="3420f-158">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="3420f-158">ServiceDebugBehavior</span></span>](servicedebugbehavior.md)  
  
 [<span data-ttu-id="3420f-159">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="3420f-159">ServiceMetadataBehavior</span></span>](servicemetadatabehavior.md)  
  
 [<span data-ttu-id="3420f-160">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="3420f-160">ServiceSecurityAuditBehavior</span></span>](servicesecurityauditbehavior.md)  
  
 [<span data-ttu-id="3420f-161">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="3420f-161">ServiceThrottlingBehavior</span></span>](servicethrottlingbehavior.md)  
  
 [<span data-ttu-id="3420f-162">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="3420f-162">ServiceTimeoutsBehavior</span></span>](servicetimeoutsbehavior.md)  
  
 [<span data-ttu-id="3420f-163">ServiceToEndpointAssociation</span><span class="sxs-lookup"><span data-stu-id="3420f-163">ServiceToEndpointAssociation</span></span>](servicetoendpointassociation.md)  
  
 [<span data-ttu-id="3420f-164">SslStreamSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="3420f-164">SslStreamSecurityBindingElement</span></span>](sslstreamsecuritybindingelement.md)  
  
 [<span data-ttu-id="3420f-165">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="3420f-165">SymmetricSecurityBindingElement</span></span>](symmetricsecuritybindingelement.md)  
  
 [<span data-ttu-id="3420f-166">SynchronousReceiveBehavior</span><span class="sxs-lookup"><span data-stu-id="3420f-166">SynchronousReceiveBehavior</span></span>](synchronousreceivebehavior.md)  
  
 [<span data-ttu-id="3420f-167">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="3420f-167">TcpConnectionPoolSettings</span></span>](tcpconnectionpoolsettings.md)  
  
 [<span data-ttu-id="3420f-168">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="3420f-168">TcpTransportBindingElement</span></span>](tcptransportbindingelement.md)  
  
 [<span data-ttu-id="3420f-169">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="3420f-169">TextMessageEncodingBindingElement</span></span>](textmessageencodingbindingelement.md)  
  
 [<span data-ttu-id="3420f-170">TraceListener</span><span class="sxs-lookup"><span data-stu-id="3420f-170">TraceListener</span></span>](tracelistener.md)  
  
 [<span data-ttu-id="3420f-171">TraceListenerArgument</span><span class="sxs-lookup"><span data-stu-id="3420f-171">TraceListenerArgument</span></span>](tracelistenerargument.md)  
  
 [<span data-ttu-id="3420f-172">TransactedBatchingBehavior</span><span class="sxs-lookup"><span data-stu-id="3420f-172">TransactedBatchingBehavior</span></span>](transactedbatchingbehavior.md)  
  
 [<span data-ttu-id="3420f-173">TransactionFlowAttribute</span><span class="sxs-lookup"><span data-stu-id="3420f-173">TransactionFlowAttribute</span></span>](transactionflowattribute.md)  
  
 [<span data-ttu-id="3420f-174">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="3420f-174">TransactionFlowBindingElement</span></span>](transactionflowbindingelement.md)  
  
 [<span data-ttu-id="3420f-175">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="3420f-175">TransportBindingElement</span></span>](transportbindingelement.md)  
  
 [<span data-ttu-id="3420f-176">TransportSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="3420f-176">TransportSecurityBindingElement</span></span>](transportsecuritybindingelement.md)  
  
 [<span data-ttu-id="3420f-177">UseManagedPresentationBindingElement</span><span class="sxs-lookup"><span data-stu-id="3420f-177">UseManagedPresentationBindingElement</span></span>](usemanagedpresentationbindingelement.md)  
  
 [<span data-ttu-id="3420f-178">WindowsStreamSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="3420f-178">WindowsStreamSecurityBindingElement</span></span>](windowsstreamsecuritybindingelement.md)  
  
 [<span data-ttu-id="3420f-179">WSAT_TraceEvent</span><span class="sxs-lookup"><span data-stu-id="3420f-179">WSAT_TraceEvent</span></span>](wsat-traceevent.md)  
  
 [<span data-ttu-id="3420f-180">WSAT_TraceProvider</span><span class="sxs-lookup"><span data-stu-id="3420f-180">WSAT_TraceProvider</span></span>](wsat-traceprovider.md)  
  
 [<span data-ttu-id="3420f-181">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="3420f-181">WSAT_TraceRecord</span></span>](wsat-tracerecord.md)  
  
 [<span data-ttu-id="3420f-182">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="3420f-182">XmlDictionaryReaderQuotas</span></span>](xmldictionaryreaderquotas.md)  
  
 [<span data-ttu-id="3420f-183">XmlSerializerOperationBehavior</span><span class="sxs-lookup"><span data-stu-id="3420f-183">XmlSerializerOperationBehavior</span></span>](xmlserializeroperationbehavior.md)
