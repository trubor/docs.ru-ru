---
description: 'Дополнительные сведения: привязки WS-MetadataExchange'
title: Привязки WS-MetadataExchange
ms.date: 03/30/2017
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
ms.openlocfilehash: 3bcea573ad436a85285fab5657e58defa9113d9c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643947"
---
# <a name="ws-metadataexchange-bindings"></a><span data-ttu-id="2097b-103">Привязки WS-MetadataExchange</span><span class="sxs-lookup"><span data-stu-id="2097b-103">WS-MetadataExchange Bindings</span></span>

<span data-ttu-id="2097b-104">В этом разделе описано, как создавать привязки обмена метаданными по умолчанию для различных транспортов.</span><span class="sxs-lookup"><span data-stu-id="2097b-104">This topic describes how the default metadata exchange bindings are constructed for various transports.</span></span>  
  
## <a name="the-default-bindings"></a><span data-ttu-id="2097b-105">Привязки по умолчанию</span><span class="sxs-lookup"><span data-stu-id="2097b-105">The Default Bindings</span></span>  
  
|<span data-ttu-id="2097b-106">Имя привязки по умолчанию</span><span class="sxs-lookup"><span data-stu-id="2097b-106">Default Binding Name</span></span>|<span data-ttu-id="2097b-107">Создание привязки</span><span class="sxs-lookup"><span data-stu-id="2097b-107">How the binding is constructed</span></span>|  
|--------------------------|------------------------------------|  
|<span data-ttu-id="2097b-108">mexHttpBinding</span><span class="sxs-lookup"><span data-stu-id="2097b-108">mexHttpBinding</span></span>|<span data-ttu-id="2097b-109">Привязка <xref:System.ServiceModel.WSHttpBinding> с отключенной безопасностью транспортного уровня.</span><span class="sxs-lookup"><span data-stu-id="2097b-109">A <xref:System.ServiceModel.WSHttpBinding> with transport-level security disabled.</span></span>|  
|<span data-ttu-id="2097b-110">mexHttpsBinding</span><span class="sxs-lookup"><span data-stu-id="2097b-110">mexHttpsBinding</span></span>|<span data-ttu-id="2097b-111">Привязка <xref:System.ServiceModel.WSHttpBinding> с поддержкой безопасности транспортного уровня.</span><span class="sxs-lookup"><span data-stu-id="2097b-111">A <xref:System.ServiceModel.WSHttpBinding> that supports transport-level security.</span></span>|  
|<span data-ttu-id="2097b-112">mexNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="2097b-112">mexNamedPipeBinding</span></span>|<span data-ttu-id="2097b-113">Привязка <xref:System.ServiceModel.Channels.CustomBinding> с элементом <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> и значениями по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="2097b-113">A  <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> using the default values.</span></span>|  
|<span data-ttu-id="2097b-114">mexTcpBinding</span><span class="sxs-lookup"><span data-stu-id="2097b-114">mexTcpBinding</span></span>|<span data-ttu-id="2097b-115">Привязка <xref:System.ServiceModel.Channels.CustomBinding> с элементом <xref:System.ServiceModel.Channels.TcpTransportBindingElement> и значениями по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="2097b-115">A <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.TcpTransportBindingElement> using default values.</span></span>|
